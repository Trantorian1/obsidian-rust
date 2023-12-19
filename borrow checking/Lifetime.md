> 📚 **Lifetime** determines the duration of legal access to a variable and it's value. Once the owner variable goes out of scope it's lifetime is over and any *references* are invalidated.

*ex:*
```rust
fn main() {
	let &mut vec;

	{
		let vec2 = vec![5, 6, 7, 8];
		// creates a reference to vec2
		// that will outline its source
		vec = &vec2;
	
		// vec2 goes out of scope 
		// (end of lifetime)
	}

	// this is invalid, vec pointing to variable
	// which is no longuer accessible
	println!("{vec:?}")
}```

---

## Lifetime Notation

Because of how the Rust borrow checker works, it can be necessary to specify the lifetime of variables as part of functions or structures.

*syntax*:
```rust
<'a> // where 'a represents a lifetime
```

*ex:*
```rust
// specifies that for lifetimes 'a and 'b, the
// return value must live at least as long as 'a
fn foo<'a, 'b>(a: &'a str, b: &'b str) -> &'a str {
	a
}
```

This can also be applied to structures:

```rust
// LineIterator must live at least as long
// as the string it has a reference to
struct LineIterator<'a> {
	str: &'a str,
}
```

---

## Lifetime Constraints

// TODO: finish this
// TODO: add lifetime info about mutable refences and immutable references

---
*related:* [[rust/types/Ownership|Ownership]]