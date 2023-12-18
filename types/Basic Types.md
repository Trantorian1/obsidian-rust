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
## Fixed length integers

> ℹ️ Rust does not support variable-length integers, and instead forces the use of fixed-length integers.

| Type    | Bytes                   | Range                   |
| ------- | ----------------------- | ----------------------- |
| `i8`    | 1                       | -2^7 to 2^7-1           |
| `u8`   | 1                       | 0 to 2^8-1              |
| `i16`   | 2                       | -2^15 to 2^15-1         |
| `u16`  | 2                       | 0 to 2^16-1             |
| `i32`   | 4                       | -2^31 to 2^31-1         |
| `u32`  | 4                       | 0 to 2^31-1             |
| `i64`   | 8                       | -2^63 to 2^63-1         |
| `u64`  | 8                       | 0 to 2^63-1             |
| `i128`  | 16                      | -2^127 to 2^127-1       |
| `u128` | 16                      | 0 to 2^128              |
| `isize` | depends on architecture | depends on architecture |

> ℹ️ `isize` is the Rust equivalent to `size_t` in C and represents the maximum supported value under the current architecture. This will for example be `ui64` on a 64-bit compute, and `ui16` on a 16-bit micro controller.

---

## Floating point types

Rust supports two types of floating point integers:

| Type  | Bytes | Range |
| ----- | ----- | ----- |
| `f32` | 32    | 1.2E-38 to 3.4E+38 |
| `f64` | 64    | 2.3E-308 to 1.7E+308 |


---

## Other basic types

> ℹ️ Note that the `char` type (and for that matter `String` too) is `utf-8` encoded.

| Type   | Bytes | Range             |
| ------ | ----- | ----------------- |
| `bool` | 1     | `true` or `false` |
| `char` | 4     | `utf-8`                  |

