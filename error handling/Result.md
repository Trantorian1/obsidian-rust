> 📚 `Result` is a type of [[Enums]] in Rust which represents the success of an operation. It can take two values, `Ok` or `Err`, which each wrap around a value to return.

Use `Result` to specify the success of your functions or handle errors.

*ex:*
```rust
fn canFail() -> Result<successType, failType> {
	if condition {
		Ok(succesValue) // must have type 'successType'
	} else {
		Err(failValue) // must have type 'failType'
	}
}
```

> 💡`Result` can therefore be seen as a simple alternative to most other language's `try..catch` mechanisms.

---

## Reading a Result

`Result` can be read using Rust's pattern matching capabilities. Note that this should be done using a `match` since you probably want to handle that `Err` case!

*ex:*
```rust
let mut file = match File::open("file.txt") {
	Ok(f) => {
		// file manipulation / return file
	}
	Err(e) => {
		// handle error case
	}
}
```

> ℹ️ It is also possible to use the `is_ok()` and `is_err()` methods to check for failures, however **pattern matching with** `match` **is recommended** as it is more expressive and guarantees implementations of both `Ok` and `Err` cases.

---

## Try Operator

> 📚 The **try operator**, or `?`, is a concise way to check for errors inside a function in Rust.

The `?` operator allows you to directly `return` from a function if a `Result` is erroneous, returning the `Result` in the process. This simplifies error handling by essentially hoisting any error handling code to wherever the function will be called, giving more flexibility as to how to handle failure or success cases. 

> ℹ️ Note that when using the `?` operator it is necessary for the enclosing function to return the same `Result` type as the function `?` is being applied to.

*ex:*
```rust
use std::fs::File;
use std::io;

fn open_file(file: &str) -> io::Result<File> {
    let file = File::open(file)?;

    // file handling

    Ok(file)
}

fn main() {
    match open_file("file.txt") {
        Ok(f) => {
            // success
        }
        Err(e) => {
            // fail
        },
    }
}
```

---
*related:* [[Option]] [[Enums]] [[rust/code structure/Functions|Functions]]