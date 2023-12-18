> Conditions in Rust are similar to that of programming languages such as C and C++, with however some notable differences regarding clarity and the addition of [[#Pattern Matching]]

---

## `If` & `else`

> ℹ️ `()` are not compulsory in conditions in Rust.

*syntax:*
```rust
if condition1 {
	// code
} else if conditon2 {
	// code
} else {
	// code
}
```

> ⚠️ Note that `{}` are **compulsory**: it is not possible to omit curly braces even for single-line conditions!

---

## Pattern Matching

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

