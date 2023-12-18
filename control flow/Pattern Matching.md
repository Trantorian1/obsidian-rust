> ℹ️ Pattern Matching serves as a more powerful **Switch** statement as compared to languages such as C or C++.

*syntax:*
```rust
match variable {
	pattern1 => {
		// code
	}
	pattern2 => {
		// code
	}
	pattern3 => {
		// code
	}
	_ => {
		// default branch
	}
}
```

> 📚 **Patterns** are either **expressions** or **values** to which a variables is **matched**.

*ex:*
```rust
let name = "Trantorian";

match name {
	// matches a value
	"The Mule" => {
		println("Taking over the Foundation!");
	}

	// matching multiple conditions
	"Hary Seldom" | "Salvador Hardin" => {
		println("Important figure of the Foundation");
	}

	// matches an expression
	tmp if tmp.chars().count() > 0 { 
		// tmp can be used inside this scope as the value which as been matched
		println!("I am {}, a cool character from the novel 'Foundation'", tmp);
	}
	
	// default branch
	_ => {
		// default code
	}
}
```

