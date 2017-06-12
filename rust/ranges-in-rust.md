# Ranges in Rust

Rust has a datatype similar to Ruby that is Range. That difference is that in Ruby ranges are inclusive by default.
In Rust the inclusive option is experimental.

```rust
for x in 1..5 {
    println!("{}", x);
}
// Will print
// 1
// 2
// 3
// 4
```
