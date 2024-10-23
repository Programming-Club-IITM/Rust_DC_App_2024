# Introduction to Rust

This is a short section where you have to fill in relevant blocks of code, to complete the Rust program as decided. We will start off with simple programming questions, and then move on to some neat features of Rust, and why Rust is such a nice language to work with.
There are links attached to each title, for you to read up and understand what to fill out. Upload this same markdown file in your repository, with all the blanks filled up. This folder contains additional learning resources for you to explore, and we **strongly recommend** you get a good grasp of Rust while filling out your application.

1. [**Hello World!**](https://doc.rust-lang.org/book/ch01-02-hello-world.html)  
    Write a simple program that prints "Hello, World!" to the console.

    ```rust
    fn main() {
        // Write your code here
    	println!("Hello, world!");
    }
    ```
    
2. [**FizzBuzz**](https://doc.rust-lang.org/book/ch03-05-control-flow.html)
	Write a program, which prints the first 100  natural numbers, but prints `Fizz` if the number is divisible by 3, `Buzz` if the number is divisible by 5, and `FizzBuzz` if it is divisible by both.
	```rust
	fn main() {
		for n in 1..=100 {
 			let mut flag=0;
 			if n % 3 == 0 {
 				flag=1;
 				print!("Fizz");
 			}
 			if n % 5 == 0 {
 				flag=1;
 				print!("Buzz");
			}
 			if flag == 0{
 				print!("{n}");
 			}
			print!("\n");
		}
	}	
	```
	
3. [**Is anyone there?**](https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html)
	A very common design question, iswhat to return when nothing is there to return? For example, in a tree data structure, what do we return as a child of a node, when the node has no children? In C++, we usually return a `nullptr`, but this can lead to a myriad of issues - trying to dereference a `nullptr` just being one of them. This question has two subparts.
	a) Find an element in an array: 
	```rust
	fn find_element(arr: &[i32], target: i32) -> isize {
	    for (i, &val) in arr.iter().enumerate() {
	        if val == target{
 		    let m = i as isize;
	            return m; 
	        }
	    }
 	return -1;
	}
	```
	
	b) Use a match statement to print the element's index if it was found, and print "Not Found" otherwise.
	```rust
	let numbers = vec![1, 2, 3, 4, 5];
	let target:i32 = 2;
	let g = find_element(&numbers, target);
 	if g == -1{
 		println!("Not Found");
	}
 	else{
 		println!("{g}");
 	}
	```
	
4. [**Owners and Borrowers**](https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html)
	Ownership is a fundamental concept of Rust. This ensures a variable can only be changed at one place at a time, and other references to that can only be immutable. Here are some questions to test your understanding about ownership and borrowing.
	a) How do I borrow?
	```rust
	fn main() {
    	let s1 = String::from("Hello");
    	let s2 = &s1;
    }
    ```
    
    b) What is wrong here? Why?
    ```rust
    fn main() {
    	let s1 = String::from("Hello");
    	let s2 = s1; 
    	println!("{}", s1);
    //here ownership is transferred from s1 to s2 so when we print we should print s2 or else it would show error//
    }
    ```
    
    c) I've seemed to get a hang on ownership, but this is tripping me up. What is this? What can it do? Are there any drawbacks? How is it different from borrowing or taking ownership?
    ```rust
    fn modify_string(s: &mut String) {
    	s.push_str("This is pushed");

	Here, mutable borrowing is taking place. The function is taking a mutable reference from s and passing into the body of the function. Further, the second line of code is also valid. Since we have taken mutable reference from s, we are allowed to change it without gaining ownership , which is happening in second line of code. This function appends "This is pushed" to the original string. The drawback is that we cant define any immutable references in the function ahead as then the scope of immutable reference and mutable reference would overlap and would show error. We also cant take another mutable reference because of the same reason. In the code, we are doing mutable borrowing which is different from immutable borrowing and taking ownership. When you take ownership, you have complete control over the value of the string and can change and do whatever you want. In immutable borrowing, we borrow the value of the string and use it. We are only allowed to use it without changing its value. In mutable borrowing, we are borrowing the value from the string and are also allowed to change its value as long as it is defined. The original string has complete control and can still use it whenever it wants.
	```
