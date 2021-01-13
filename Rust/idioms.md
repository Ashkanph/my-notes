* `unwinding`: Means Rust walks back up the stack and cleans up the data from each function it encounters.

* `abort`, which ends the program without cleaning up. Memory that the program was using will then need to be cleaned up by the operating system. (Read more in error handling md file)

* `buffer overread`: In C, attempting to read beyond the end of a data structure is undefined behavior. You might get whatever is at the location in memory that would correspond to that element in the data structure, even though the memory doesn’t belong to that structure.

* `backtrace`: is a list of all the functions that have been called to get to this point. 

* `Propagating Errors`: When you’re writing a function whose implementation calls something that might fail, instead of handling the error within this function, you can return the error to the calling code so that it can decide what to do.

* `Monomorphization`: The process of turning generic code into specific code by filling in the concrete types that are used when compiled.

* `The orphan rule`, so named because the parent type is not present. This rule ensures that other people’s code can’t break your code and vice versa. Without the rule, two crates could implement the same trait for the same type, and Rust wouldn’t know which implementation to use.

* `Blanket implementations`: We can also conditionally implement a trait for any type that implements another trait. Implementations of a trait on any type that satisfies the trait bounds are called blanket implementations and are extensively used in the Rust standard library. For example, the standard library implements the ToString trait on any type that implements the Display trait. The impl block in the standard library looks similar to this code:
    ```rust
    impl<T: Display> ToString for T {  // این ایمپلمنت فقط روی تایپ‌هایی از تی که دیسپلی رو پیاده‌سازی کردن قابل اجراست
        // --snip--
    }
    ```

* ‍‍‍‍`lifetime`, which is the scope for which that reference is valid

* `borrow checker`: The Rust compiler has a borrow checker that compares scopes to determine whether all borrows are valid.

* `Lifetime elision rules`: الگوهایی هستند که به مرور فهمیدند در آنها همیشه باید لایف‌تایم برای رفرنس‌ها بکار رود و آنها را در کامپایلر گذاشتند تا دیگر نیازی به ذکر لایف‌تایم نباشد و خود کامپایلر حتی با نگذاشتن لایف‌تایم‌ها برایشان لایف‌تایم بگذارد