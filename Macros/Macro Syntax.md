> ℹ️ Similar to the regular type system, macros have their own argument type system and symbols to parse different values in the Rust AST. These represent the various tokens, or families of token which can be extracted from the AST.

> ⚠️ The ability of macros in Rust to specify the type of AST data they consume is one of the most powerful features of Rust macros as it allows for much deeper manipulation of sources files and very, very powerful metaprogramming.

---

## Fragment Specifier

> 📚 **Fragment Specifiers** in Rust macros allow to specify the type of AST data to parse.

### `block`

Any **block expression**. This includes any data contained between `{}`.

### `expr`

Any **expression**. See [[Expressions & Declarations]].

### `ident`

Any **identifier** or **keyword**. This can for example be a variable name or a keyword such as `let`.

### `item`

Any `item`. An `item` can be seen as a component of a crate. In less abstract term, this can be seen as a *behavior* provided by that crate, such as *structures*, *functions*, *traits*... See [this](https://doc.rust-lang.org/reference/items.html) for a more complete list.

### `lifetime`

As the name suggest, matches any **lifetime identifier**. See [[Lifetime]] for more information.

### `literal`

Any **literal expression**. This includes numerical expressions, booleans, characters as well as string literals.

### 🚧 `pat`

Any **pattern**. Frankly I don't really get this one yet so just read [this](## [`pat`](https://veykril.github.io/tlborm/decl-macros/minutiae/fragment-specifiers.html#pat)) lol.

### `pat_param`

Implements legacy functioning of the `pat` fragment specifier as before version 2021, most notably allowing for the differentiation of the `|` symbol which is otherwise consumed by the 2021 version of `pat`.

### `path`

Any **path to a type** in Rust. This can include direct path, library paths as with the `use` directive, or function type paths such as `FnMut() -> ()`.

### `stmt`

Matches any **statement** without it's trailing `;`. A statement is either an *expression* or a *decleration*. See [[Expressions & Declarations]] for more information.

### 🚧 `tt`

Matches any **token tree**. And darling if you are looking for what this means you better check [here](https://veykril.github.io/tlborm/syntax-extensions/source-analysis.html#token-trees).

### `ty`

Any **type**. So anything like `u8`, `bool`, `char`, or even a `path`.

### `vis`

Any **visibility specifier**, which includes all variation of `pub`. Check [this](https://doc.rust-lang.org/reference/visibility-and-privacy.html) for more information.

---

## Repetitions

> ℹ️ Repetitions allow to specify how many macro fragment specifier a macro parses.

*syntax:*
```rust
$(...) seperator repetition
```

*ex:*
```rust
$($x:expr),* // any expression seperated by a ','
```

- `?` one or no repetitions
- `*` zero or more repetitions
- `+` one or more repetitions