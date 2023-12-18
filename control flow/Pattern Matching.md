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

---

## `if let`

> 📚 `if let` allows for pattern matching on a single pattern. It is useful when only a particular match is useful but should not be used for situations where all cases should be handled, for example error handling.

*syntax*
```rust
if let match = source {
	// code
}
```

*ex:*
```rust
fn optional_data(n: u32) -> Option<u32> {
	if n % 2 == 0 {
		Some(n)
	} else {
		None
	}
}

fn main() {
	if let Some(n) = optional_data(42) {
		println!("n: {}", n);
	}

	if let None = optional_data(21) {
		println!("no data!");
	}
}
```

---
*related:* [[About Error Handling]] [[rust/control flow/Conditions|Conditions]]

