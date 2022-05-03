---
tags: [pointers, c]
---

Opaque pointers are a mechanism to allow encapsulation in libraries
such that implementation details may not be relied upon by the client.

For example, here is a non-opaque type:

```c
// rectangle.h
typedef struct rectangle {
    short width;
    short height;
} rectangle_t;
```

A client of this library definition may use the implementation
details of `rectangle_t` to calculate their own `area`:

```c
int area = rect.width * rect.height;
```

However, if the implementation of `rectangle_t` changes such that
`width` and `height` are a different type, clients may need to update
their definitions and recompile. When the library functionality is
dynamically linked, there may be a mismatch in between the types
the client program is using and the types the library itself
uses.

To remedy this, opaque pointers may be used:

```c
// rectangle.h
typedef struct rectangle *rectangle_handle;

int rectangle_width(rectangle_handle);
int rectangle_height(rectangle_handle);
```

The definition of the `rectangle_t` struct will then be local to
`rectangle.c`.

This effectively separates the API from the implementation by hiding the
internals of `rectangle` in `rectangle.c`. If the types of `rectangle.width` and `rectangle.height`
change from `short` to `int` internally, the client may continue to use the
same API as before without needing to make adjustments or recompile.

