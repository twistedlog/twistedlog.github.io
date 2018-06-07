---
layout: post
title: "Rust day 1"
categories: rust
---
I have decided to document interesting things about Rust as I learn them.

---
### INTRODUCTION

>From what I understand so far about Rust is that its a system programming language
that provides you the control of a low level language like C/C++ and safety of higher level 
languages like Python/Ruby etc.

#### Stuff I learned today

* Rust comes with a rustc compiler and build tool called Cargo

  >start a project with Cargo
  {% highlight bash %}
  $ cargo new --bin test_project
  {% endhighlight %}
  >--bin argument informs Cargo that we intend to make an executable application

  {% highlight bash %}
  $ tree test_project
    test_project
    ├── Cargo.toml
    └── src
        └── main.rs
  {% endhighlight %}
  looking at the project structure above you can see that Cargo creates a __Cargo.toml__ file
  and a __main.rs__ file under src directory.

  __src__ directory is where your Rust code will stay.
  > build your project
  {% highlight bash %}
  $ cargo build
  {% endhighlight %}
  Cargo creates a Cargo.lock file with package metadata and dependencies. 
  > run your code
  {% highlight bash %}
  $ cargo run
  {% endhighlight %}

* everything is immutable by default in Rust
  {% highlight rust %}
  let num1 = 10 // This is how you declare a variable using let
  num1 = 11 
  {% endhighlight %}
  If you try to build the code above you will see the following error
  {% highlight bash %}
  error[E0384]: cannot assign twice to immutable variable `x`
  --> src/main.rs:3:5
    |
  2 |     let x = 10;
    |         - first assignment to `x`
  3 |     x = 11;
    |     ^^^^^^ cannot assign twice to immutable variable
  {% endhighlight %}
  you can use __mut__ if you want a mutable variable
  {% highlight rust %}
  let mut num1 = 10
  num1 = 11
  {% endhighlight %} 

* __shadowing__

  shadowing basically lets to reuse the same variable name and you can change the value of the variable.
  {% highlight rust %}
  let x = 10
  let x = "foobar"  
  {% endhighlight %} 
  This is different than declaring a variable mutable in 2 ways:
  1. you have to use let to modify
  2. after you are done with modification the variable is immutable

* __expressions and return values__
  rust code will be composed of two things statements and expressions.
   
  {% highlight rust %} 
  fn main() {
      let y = {
          let mut x = 10
          x * 2
      };
      println!("y: {}", y);
  }
  {% endhighlight %}
  in the example above __y's__ value comes out to be 20. Not that __x * 2 has no semicolon__ in the end, which makes it an expressions and the result of this expression is assigned to y.

### References:
1. <https://doc.rust-lang.org/book/second-edition/>
2. <https://www.youtube.com/watch?v=ftQfpAeyxPo/>
3. <https://jvns.ca/blog/2016/09/11/rustconf-keynote/>
