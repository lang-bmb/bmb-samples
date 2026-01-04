# BMB Samples

> Example Programs and Tutorials for BMB Language

BMB 프로그래밍 언어의 예제 프로그램 및 튜토리얼 모음.

## Quick Start

```bash
# Clone
git clone https://github.com/lang-bmb/bmb-samples
cd bmb-samples

# Run an example
bmb run examples/basics/hello_world.bmb

# Verify contracts
bmb verify examples/contracts/preconditions.bmb
```

## Directory Structure

```
bmb-samples/
└── examples/
    ├── basics/                 # Basic syntax (5 examples)
    │   ├── hello_world.bmb     # Hello World program
    │   ├── variables.bmb       # Variable bindings
    │   ├── expressions.bmb     # Arithmetic and operators
    │   ├── conditionals.bmb    # If-then-else expressions
    │   └── loops.bmb           # Iteration via recursion
    │
    ├── functions/              # Function patterns (3 examples)
    │   ├── basic_functions.bmb # Function definitions
    │   ├── recursion.bmb       # Recursive functions
    │   └── higher_order.bmb    # Higher-order patterns
    │
    ├── contracts/              # Contract verification (4 examples)
    │   ├── preconditions.bmb   # Pre-condition examples
    │   ├── postconditions.bmb  # Post-condition examples
    │   ├── combined.bmb        # Combined pre/post
    │   └── invariants.bmb      # Loop invariants
    │
    ├── algorithms/             # Algorithm implementations (5 examples)
    │   ├── search.bmb          # Linear and binary search
    │   ├── sorting.bmb         # Sorting algorithms
    │   ├── math.bmb            # Mathematical functions
    │   ├── dynamic.bmb         # Dynamic programming
    │   └── graph.bmb           # Graph algorithms
    │
    ├── patterns/               # Design patterns (4 examples)
    │   ├── accumulator.bmb     # Tail recursion pattern
    │   ├── state_machine.bmb   # State machine encoding
    │   ├── option.bmb          # Option/Maybe pattern
    │   └── builder.bmb         # Builder pattern
    │
    ├── data_types/             # Data type operations (4 examples)
    │   ├── integers.bmb        # Integer operations
    │   ├── booleans.bmb        # Boolean logic
    │   ├── strings.bmb         # String operations
    │   └── tuples.bmb          # Pair/triple encoding
    │
    └── real_world/             # Real-world applications (6 examples)
        ├── calculator.bmb      # Arithmetic evaluator
        ├── date_utils.bmb      # Calendar calculations
        ├── validation.bmb      # Input validation
        ├── bank.bmb            # Financial transactions
        ├── game.bmb            # Game state management
        └── crypto.bmb          # Cryptographic operations
```

**Total: 31 examples** across 7 categories.

## Example Highlights

### Hello World
```bmb
-- examples/basics/hello_world.bmb
fn main() -> i64 = {
    let u = println(42);
    0
};
```

### Function with Contract
```bmb
-- examples/contracts/postconditions.bmb
fn abs(x: i64) -> i64
  post ret >= 0
  post ret == x or ret == 0 - x
= if x >= 0 then x else 0 - x;
```

### Tail Recursive Pattern
```bmb
-- examples/patterns/accumulator.bmb
fn sum_iter(n: i64, acc: i64) -> i64 =
    if n <= 0 then acc
    else sum_iter(n - 1, acc + n);

fn sum_to(n: i64) -> i64
  pre n >= 0
  post ret == n * (n + 1) / 2
= sum_iter(n, 0);
```

### Option Pattern
```bmb
-- examples/patterns/option.bmb
fn safe_divide(a: i64, b: i64) -> i64 =
    if b == 0 then none() else some(a / b);
```

### Real-World Application
```bmb
-- examples/real_world/bank.bmb
fn withdraw(account: i64, amount: i64) -> i64
  pre amount >= 0
= if amount > available_funds(account) then 0 - 1
  else make_account(get_balance(account) - amount, get_overdraft_limit(account));
```

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| **basics** | 5 | Language fundamentals: variables, expressions, control flow |
| **functions** | 3 | Function definitions, recursion, higher-order patterns |
| **contracts** | 4 | Contract-based verification: pre/post conditions, invariants |
| **algorithms** | 5 | Classic algorithms with verified correctness |
| **patterns** | 4 | Design patterns: accumulator, state machine, option, builder |
| **data_types** | 4 | Data type operations and encodings |
| **real_world** | 6 | Practical applications: banking, games, crypto |

## Running Examples

```bash
# Type check
bmb check examples/basics/hello_world.bmb

# Parse and show AST
bmb parse examples/contracts/preconditions.bmb

# Run with interpreter (future)
bmb run examples/algorithms/sorting.bmb
```

## Key Concepts Demonstrated

### Contract-Based Programming
- **Preconditions** (`pre`): Input constraints
- **Postconditions** (`post`): Output guarantees
- **Invariants**: Properties maintained across iterations

### Functional Patterns
- **Tail Recursion**: Efficient iteration via accumulator pattern
- **Higher-Order Functions**: Map, filter, reduce patterns
- **Immutability**: All values are immutable by default

### Encoding Techniques
- **Tuple Encoding**: Pack multiple values into single i64
- **State Encoding**: Represent complex state as integers
- **Bit Operations**: Boolean flags and bit manipulation

## Contributing

1. Fork the repository
2. Add your example in the appropriate directory
3. Include comments explaining the code
4. Add contracts where applicable
5. Submit a PR

## License

MIT License
