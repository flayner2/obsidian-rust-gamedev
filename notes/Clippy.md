# Clippy
Clippy is Rust's code-checking tool. You can run Clippy on your code by running `cargo clippy`. It will check your code for code style mistakes, primarily, and can be a great tool to learn better, idiomatic Rust. It also has different modes, such as the recommended *pedantic* mode. To enable it, add the following to the first line of your `main.rs`:

```rust
#![warn(clippy::all, clippy::pedantic)]
```