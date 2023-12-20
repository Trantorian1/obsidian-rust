> 📚 **Declarative Macros** are the simplest type of Rust macros, offering a syntax similar to pattern matching for parsing the Rust AST.

*syntax*
```rust
macro_rules! macro {
	( pattern1 ) => {
		// code generation
	};
	( pattern2 ) => {
		// code generation
	}
}
```

*ex:*
```rust
macro_rules! simple_vec {
	// matches any repeating
	// expression seperated by ','
	( $($x:expr),* ) => {
		{
			let mut tmp_vec = Vec::new();

			// we use the same syntax as above to generate
			// this code as many times as $x occurs
			$(
				tmp_vec.push($x);
			)*

			tmp_vec
		}
	};
}

fn main() {
	let vec = simple_vec![0, 1, 2, 3, 4];

	println!("{vec:?}");
}
```