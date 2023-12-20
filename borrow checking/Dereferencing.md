*Dereferencing in Rust works mostly the same as in languages such as C and C++, with a few notable exceptions.*

---

## Custom Dereferencing

> ℹ️ Dereferencing in Rust is implemented via the `Deref` and `DerefMut` traits. These allow for custom dereferencing and dereferencing assignments on `struct`

*ex:*
```rust
use std::ops::Deref;

struct Slot<'a, T> {
	data: &'a T,
}

impl<'a, T> Deref for Slot<'a, T> {
	// Deref needs to know the 
	// dereferencing return type
    type Target = T;

	// implements actual dereferencing
    fn deref(&self) -> &'a Self::Target {
		self.data
    }
}

fn main() {
	let x = 42;
	let slot = Slot { data: &x };

	// slot can be dereference to access 'data'
	println!("{}", *slot)
}
```

---

## Auto Dereferencing

> ℹ️ Rust will keep dereferencing a variable until the correct type has been reached, avoiding the need for manual dereferencing in certain simple cases of linear dereferencing.

*ex:*
```rust
fn foo(x: &i32) -> &i32 {
	x
}

fn main() {
	let x = 12;

	// 'x' will be automatically dereferenced 
	// from &&&&&&i32to &i32
	println!("{}", foo(&&&&&&&x))
}
```

Note that this also works for structures implementing the `Deref` trait. 

*ex:*
```rust
fn greet(name: &str) {
	println!("Hello, my name is {name}!");
}

fn main() {
	let name = String::from("Trantorian");

	// Here we have a '&String', which will
	// be automatically converted to a &str
	greet(&name)
}
```

---
*related:* [[rust/types/Ownership|Ownership]]