# Short notes regarding C++

## Various

### 3 reasons to pass std::string_view by value
[Source (Arthur O'Dwyer)](https://quuxplusone.github.io/blog/2021/11/09/pass-string-view-by-value/)

Note. If the compiler is allowed to see both caller/callee together, has -O2, and decides to inline the callee into the caller, then it an usually undo all of the harm caused by an unidiomatic pass-by-reference

#### Eliminate a pointer indirection in the callee

Pass-by-value: whenever possible, pass in registers. In some cases ("non-trivial for purposes of ABI") the object is placed onto the stack, (involved memory indirection...)

Trivial types like ```int```. ```std::string_view```, ```std::span``` are always passed in registers.

#### Eliminate a spill in the caller

While passing by reference, caller must place the argument's address into a register, which forces the object onto the stack (spill in the caller - passing by reference requires an *address*).

It may results in eliminating the need for a stack frame in the caller at all.

#### Eliminate aliasing

Passing by reference may prevent the compiler from proper optimization (from the callee perspective: no information regarding i.e. who also holds a pointer to such object...)

Passing by value gives the callee a brand-new copy of the object, which for sure does not alias with any other object in the program; the compiler may use more aggressive optimization, example (Clang?)

```
void byvalue(std::string_view sv, size_t *p) {
    *p = 0;
    for (size_t i=0; i < sv.size(); ++i) *p += 1;
}

---

byvalue:
    movq %rsi, (%rdx)
    retq
```

> [!WARNING]  
> Microsoft x86-64 ABI does not pass ```std::string_view``` in registers, but by a *hidden pointer*.
> No performance gain in mentioned cases, but also no performance loss. [Footnote](https://quuxplusone.github.io/blog/2021/11/19/string-view-by-value-ps/)