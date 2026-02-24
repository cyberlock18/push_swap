# push_swap

A 42 school project that sorts a stack of integers using two stacks and a limited set of operations, generating the shortest possible sequence of moves.

## Project Summary

**push_swap** receives a list of integers as arguments, builds them into a stack (stack_a), and outputs to standard output the ordered sequence of operations needed to sort stack_a using as few moves as possible. A second auxiliary stack (stack_b) is available. No values are printed — only the operation names.

The program uses two strategies:
- **Small stack** (≤ 5 elements): optimised insertion sort.
- **Large stack** (> 5 elements): index-based greedy/radix algorithm.

## Skills Acquired

- Algorithm design and complexity analysis (sorting algorithms)
- Doubly-linked list manipulation in C
- Stack operations and data structure design
- Argument parsing, input validation, and error handling
- Memory management and leak-free programming in C
- Working within strict compilation flags (`-Wall -Wextra -Werror`)
- Makefile project organisation with external library integration (libft)

## Build & Run

All commands must be run from the `pushswap/` directory.

```bash
cd pushswap

# Build the project (compiles libft first, then push_swap)
make

# Remove object files
make clean

# Remove object files and the binary
make fclean

# Full rebuild
make re
```

After a successful build, the binary `push_swap` is created inside `pushswap/`.

### Usage

```bash
# Sort a list of integers — prints the operation sequence
./push_swap 3 1 4 1 5 9 2 6

# Pipe output to the provided checker to verify correctness
./push_swap 3 1 4 1 5 9 2 6 | ./checker_linux 3 1 4 1 5 9 2 6

# Numbers may also be passed as a single quoted string
./push_swap "3 1 4 1 5 9 2 6"
```

The program exits silently (no output) when the input is already sorted or only one number is provided. It writes `Error` to standard error on invalid input (non-integers, duplicates, out-of-range values).

## Project Structure

```
pushswap/
├── Makefile
├── pushswap.h          # Header — structs (t_node, t_args_info) and prototypes
├── main.c              # Entry point, index assignment, sort dispatcher
├── case_smll.c         # Sorting algorithm for ≤ 5 elements
├── case_lrge.c         # Sorting algorithm for > 5 elements
├── checker_linux       # Pre-compiled checker binary (Linux)
├── libft/              # Custom C library (ft_printf, libft)
├── operations/
│   ├── swap.c          # sa, sb, ss
│   ├── push.c          # pa, pb
│   ├── rotate.c        # ra, rb
│   └── rr.c            # rr, rra, rrb, rrr
└── parsing/
    ├── validate_args.c
    ├── parse_stack.c
    ├── parsing_plus.c
    ├── parsing_plus1.c
    └── parsing_plus2.c
```

### Available Operations

| Operation | Description |
|-----------|-------------|
| `sa` / `sb` | Swap the top two elements of stack_a / stack_b |
| `ss` | `sa` and `sb` simultaneously |
| `pa` / `pb` | Push the top of stack_b to stack_a / vice-versa |
| `ra` / `rb` | Rotate stack_a / stack_b upward (top → bottom) |
| `rr` | `ra` and `rb` simultaneously |
| `rra` / `rrb` | Reverse rotate stack_a / stack_b (bottom → top) |
| `rrr` | `rra` and `rrb` simultaneously |

## Author

**ruortiz-** — [42 School](https://42.fr)