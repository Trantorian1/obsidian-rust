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

Note that there also exists a special time of lifetime, labelled `'static`, which guarantees that your variables will live as long as the program itself.

*ex:*
```rust
fn static_lifetime(a: &str) -> &'static str {
	let var = "test"

	// references to 'var' as returned by this function
	// will persist for the entire duration of the program
	var
}
```

---

## Lifetime Constraints

It is also possible to specify the duration of lifetimes in relation to each other. This functions in a similar way to *generic constraints*.

*syntax:*
```rust
fn foo<'a, 'b, 'c>(a: &'a str, b: &'b str, c: &'c str) -> &'a str
where
	'b: 'c,     // 'b must live for at least as long as 'c
	'a: 'b + 'c // it is also possible to combine lifetime durations
{
	// code...
}
```

---
*related:* [[rust/types/Ownership|Ownership]]