# Introduction to Rust

This is a short section where you have to fill in relevant blocks of code, to complete the Rust program as decided. We will start off with simple programming questions, and then move on to some neat features of Rust, and why Rust is such a nice language to work with.
There are links attached to each title, for you to read up and understand what to fill out. Upload this same markdown file in your repository, with all the blanks filled up. This folder contains additional learning resources for you to explore, and we **strongly recommend** you get a good grasp of Rust while filling out your application.

1. [**Hello World!**](https://doc.rust-lang.org/book/ch01-02-hello-world.html)  
    Write a simple program that prints "Hello, World!" to the console.

    ```rust
    fn main() {
        // Write your code here
    }
    ```
    
2. [**FizzBuzz**](https://doc.rust-lang.org/book/ch03-05-control-flow.html)
	Write a program, which prints the first 100  natural numbers, but prints `Fizz` if the number is divisible by 3, `Buzz` if the number is divisible by 5, and `FizzBuzz` if it is divisible by both.
	```rust
	fn main() {
		for n in 1..=100 {
		}
	}
	```
	
3. [**Is anyone there?**](https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html)
	A very common design question, iswhat to return when nothing is there to return? For example, in a tree data structure, what do we return as a child of a node, when the node has no children? In C++, we usually return a `nullptr`, but this can lead to a myriad of issues - trying to dereference a `nullptr` just being one of them. This question has two subparts.
	a) Find an element in an array: 
	```rust
	fn find_element(arr: &[i32], target: i32) -> /*what should the return type be?*/ {
    	for (i, &val) in arr.iter().enumerate() {
        	// What should we check here?
    	}
    	// What should we return here?
	}
	```
	
	b) Use a match statement to print the element's index if it was found, and print "Not Found" otherwise.
	```rust
	let numbers = vec![1, 2, 3, 4, 5];
	// Fill in your code here
	```
	
4. [**Owners and Borrowers**](https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html)
	Ownership is a fundamental concept of Rust. This ensures a variable can only be changed at one place at a time, and other references to that can only be immutable. Here are some questions to test your understanding about ownership and borrowing.
	a) How do I borrow?
	```rust
	fn main() {
    	let s1 = String::from("Hello");
    	let s2 = //??? Borrow s1
    }
    ```
    
    b) What is wrong here? Why?
    ```rust
    fn main() {
    	let s1 = String::from("Hello");
    	let s2 = s1; 
    	println!("{}", s1);
    }
    ```
    
    c) I've seemed to get a hang on ownership, but this is tripping me up. What is this? What can it do? Are there any drawbacks? How is it different from borrowing or taking ownership?
    ```rust
    fn modify_string(s: &mut String) {
    	s.push_str("This is pushed");
	}
	```
