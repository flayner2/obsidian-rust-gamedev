# `if let`
Rust provides a way of matching against a single case: `if let`. It is very useful, for example, when used in conjunction with `Option`, which can only contain `None` or `Some(data)`. It works the same way as `match`, but with shortened syntax.

```ad-example
collapse: open

A `match` statement:
~~~rust
match my_option {
	Some(my_value) => do_something_with(my_value).
	_ => {}
}
~~~

The equivalent `if let` statement:
~~~rust
if let Some(my_value) = my_option {
	do_something_with(my_value);
}
~~~
```