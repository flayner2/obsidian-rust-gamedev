# References
The borrowing system in Rust makes references work as a way to pass your data to other scopes without *moving* it, i.e., without making it invalid at its original scope. Consider the following:

```rust
fn main() {
	let s1 = String::from("hello");

	let len = calculate_length(s1);
	
	// s1 is no longer valid here
}

fn calculate_length(s: String) -> usize {
	s.length()
	// s1 gets dropped here
}
```

In this case, since the `String` type doesn't implement the `Copy` trait, `s1` gets dropped after the call to `calculate_length(s1)`. If we want to avoid it, we must change the function to take a reference to a `String` (`&String`) and pass a reference to `s1` (`&s1`) to it. References in rust are similar to passing a `const type &var` in C++, so, by definition, the reference is immutable. It is also useful to think of a reference in Rust as a pointer to a pointer (since the original variable holds a pointer to a value stored on the heap). But references in Rust can also work as they work in C++ by default, with the purpose of modifying the value of a variable from within a function without moving it. To do that, you need to pass a mutable reference (`&mut var`) to the variable to the function, and the function must take a mutable reference to the variable's type (`&mut T`).

```ad-example
collapse: open

Passing mutable and immutable references in Rust:
~~~rust
fn main() {
	let s1 = String::from("hello");

	let len = calculate_length(&s1); // immutable reference
	
	add_world(&mut s1); // mutable reference

	println!("{s1}"); // prints "hello, world!"
}

fn calculate_length(s: &String) -> usize {
	// this function can't modify s or s1
	s.len()
}

fn add_world(s: &mut String) {
	// this function can modify s and s1
	s.push_str(", world!");
}
~~~
```