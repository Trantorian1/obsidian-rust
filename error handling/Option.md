> 📚 `Option` is Rust's way of representing optional data which has not yet been initialized. It has two *variations*: `Some` and `None`.

*ex:*
```rust
pub struct Foo {
	optional_data: Option<i32>,
}

impl Foo {
	pub fn new() -> Self {
		Self { optional_data: None, }
    }
}

fn main() {
	let mut foo = Foo::new();
	foo.optional_data = Some(12);

	// remember to use pattern matching 
	if let Some(s) = foo.optional_data {
		println!("optional data: {}", s)
	}
}
```

---
*related:* [[Pattern Matching]]