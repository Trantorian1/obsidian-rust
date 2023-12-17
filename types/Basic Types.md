> In Rust, all variables are **immutable** by default

*syntax:*
- variables are defined using the `let` keyword
- variables are made mutable with the `mut` keyword
- Rust uses **type inference** to determine the type of variables
- Types can also be specified explicitly

ex:
```rust
let     i      = 0;    // immutable
let mut j      = 0;    // mutable
let     k: i32 = 0;    // i32 type
let     l      = 0i32; // i32 type

// i = 12 -> illegal!!!
j = 12;
```

---
## Fixed Length Integers

> ℹ️ Rust does not support variable-length integers, and instead forces the use of fixed-length integers.

| Type    | Bytes | Range             |
| ------- | ----- | ----------------- |
| `i8`    | 1     | -2^7 to 2^7-1     |
| `ui8`   | 1     | 0 to 2^8-1        |
| `i16`   | 2     | -2^15 to 2^15-1   |
| `ui16`  | 2     | 0 to 2^16-1       |
| `i32`   | 4     | -2^31 to 2^31-1   |
| `ui32`  | 4     | 0 to 2^31-1       |
| `i64`   | 8     | -2^63 to 2^63-1   |
| `ui64`  | 8     | 0 to 2^63-1       |
| `i128`  | 16    | -2^127 to 2^127-1 |
| `ui128` | 16    | 0 to 2^128        |

