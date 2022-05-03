---
tags: [rust]
---

# Rust cell

The rust borrow checker ensures at compile time that references to objects
are either non-unique and immutable `&` or unique `&mut`.
When a type takes on a shared or unique reference, it's called
inherited mutability.

In cases where mutability is desired in spite of shared references, 
one may use `Cell` and `RefCell`. These enable
[interior mutability](https://doc.rust-lang.org/reference/interior-mutability.html).

`Cell` enables shared mutability for values, `RefCell` enables it for
references.

`Cell` is a simple wrapper type for the underlying data, and it does not
affect memory layout. 

```rust
pub struct Cell<T: ?Sized> {
    value: UnsafeCell<T>,
}
```

`RefCell` contains extra metadata to dynamically check
borrow constraints and so adds to the memory required to
contain the underlying type:

```rust
pub struct RefCell<T: ?Sized> {
    borrow: Cell<BorrowFlag>,
    // ...
    value: UnsafeCell<T>,
}
```

#### Further reading:
- [`std::cell`](https://doc.rust-lang.org/stable/std/cell/)