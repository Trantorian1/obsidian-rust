> ℹ️ Loops in Rust function the same as in most high-level programming languages, with ease-of functionalities such as iterable objects.

>  ⚠️ `break` exits the current loop, `return` exits the current function.
## `while`
*Function the same as in other programming languages such as C*

*ex:*
```rust
while condition {
	// code
}
```

---

## `loop`
*Functions as an infinite while loop*

*ex:*
```rust
loop {
	if condition {
		break;
	}
}

// is the same as
while true {
	if condition {
		break;
	}
}
```

---

## `for`
*Your regular for loop, with object iteration through* `IntoIterator`

*syntax:*
```rust
for val in iterable {
	println!("current element is {}", val);
}
```

*ex:*
```rust
for i in 0..10 {
	println!("i:{}", i);
}
```

As stated before, loops also work on objects which implement the `IntoIterator` trait.

*ex:*
```rust
let v = vec![1, 2, 3, 4, 5];

for value in v {
	println!("value:{}", v);
}
```

> ℹ️ Note that currently iterating over values does not give you the current index. For that, you can use the function `enumerate`.

*ex:*
```rust
for (i, j) in (12..42).enumerate() {
	println!("index:{} value:{}", i, j);
}

let v = vec![1, 2, 3, 4, 5];
for (i, val) in v.iter().enumerate() {
	println!("index:{} value:{}", i, val);
}
```

---

## Named loops

> ℹ️ Rust supports **named loops**, which allows to assign 'tags' to your loops so as to be able to target them specifically.

*syntax:*
```rust
`tag: for val in iterable {
	// code
}
```

*ex:*
```rust
`outer: for i in 0..10 {
	`inner: for j in 0..10 {
		if (condition) {
		}
	}
}
```
