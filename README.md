Ook.jl
======

An [Ook!](http://www.dangermouse.net/esoteric/ook.html) interpreter written
in Julia. Because Ook!.

# Usage Example

Execute a string containing a Ook! program using the `ook` function:

```
using Ook
ook("Ook. Ook. Ook. Ook. Ook. Ook.")
```

To work with a program stored in a file, use `readall` to generate a string
to pass to `ook`:

```
using Ook
path = Pkg.dir("Ook", "test", "programs", "squares.ook")
ook(readall(path))
```

If you want to observe the program state evolve operation-by-operation, you
can set the `debug` keyword argument to `false` when running `ook`:

```
using Ook
path = Pkg.dir("Ook", "test", "programs", "squares.ook")
ook(readall(path), debug = true)
```

*Be warned that the state evolution of the Ook! interpreter will produce a lot
of output for even the simplest programs.*

# Ook! Language Reference

**OP1: Ook. Ook?**

Move the Memory Pointer to the next array cell.

**OP2: Ook? Ook.**

Move the Memory Pointer to the previous array cell.

**OP3: Ook. Ook.**

Increment the array cell pointed at by the Memory Pointer.

**OP4: Ook! Ook!**

Decrement the array cell pointed at by the Memory Pointer.

**OP5: Ook. Ook!**

Read a character from STDIN and put its ASCII value into the cell
pointed at by the Memory Pointer.

**OP6: Ook! Ook.**

Print the character with ASCII value equal to the value in the cell
pointed at by the Memory Pointer.

**OP7: Ook! Ook?**

Move to the command following the matching Ook? Ook! if the value in
the cell pointed at by the Memory Pointer is zero. Note that
Ook! Ook? and Ook? Ook! commands nest like pairs of parentheses, and
matching pairs are defined in the same way as for parentheses.

**OP8: Ook? Ook!**

Move to the command following the matching Ook! Ook? if the value in
the cell pointed at by the Memory Pointer is non-zero. **Note that this
implies that the interpreter will work its way backwards through the
source code, rather than forwards.**
