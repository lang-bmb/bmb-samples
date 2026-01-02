# BMB Samples

> Example Programs and Tutorials for BMB Language

BMB 프로그래밍 언어의 예제 프로그램 및 튜토리얼 모음.

## Quick Start

```bash
# Clone
git clone https://github.com/lang-bmb/bmb-samples
cd bmb-samples

# Run an example
bmb run basics/01_hello.bmb

# Verify contracts
bmb verify contracts/01_preconditions.bmb
```

## Directory Structure

```
bmb-samples/
├── basics/                 # Basic syntax examples
│   ├── 01_hello.bmb        # Hello World
│   ├── 02_variables.bmb    # Variables and types
│   ├── 03_functions.bmb    # Function definitions
│   ├── 04_if_else.bmb      # Conditionals
│   ├── 05_loops.bmb        # Loops (for, while)
│   └── 06_pattern_match.bmb # Pattern matching
│
├── contracts/              # Contract verification examples
│   ├── 01_preconditions.bmb
│   ├── 02_postconditions.bmb
│   ├── 03_invariants.bmb
│   └── 04_refinement_types.bmb
│
├── data_structures/        # Data structure examples
│   ├── struct.bmb          # Structs
│   ├── enum.bmb            # Enums and variants
│   ├── arrays.bmb          # Fixed-size arrays
│   └── references.bmb      # References and borrowing
│
├── algorithms/             # Algorithm implementations
│   ├── sort/
│   │   ├── bubble.bmb
│   │   ├── quick.bmb
│   │   └── merge.bmb
│   ├── search/
│   │   ├── binary.bmb
│   │   └── linear.bmb
│   └── math/
│       ├── fibonacci.bmb
│       ├── factorial.bmb
│       └── gcd.bmb
│
├── projects/               # Complete project examples
│   ├── calculator/         # CLI calculator
│   ├── todo-cli/           # Todo list manager
│   └── json-parser/        # JSON parser
│
└── tutorials/              # Step-by-step guides
    ├── 01_getting_started.md
    ├── 02_contracts_intro.md
    ├── 03_building_cli.md
    └── 04_testing.md
```

## Examples

### Hello World

```bmb
-- basics/01_hello.bmb
fn main() -> () = println("Hello, BMB!");
```

### Function with Contract

```bmb
-- contracts/02_postconditions.bmb
fn abs(x: i32) -> i32
  post ret >= 0
  post (ret == x) or (ret == 0 - x)
= if x >= 0 then x else 0 - x;
```

### Struct and Methods

```bmb
-- data_structures/struct.bmb
struct Point {
  x: i32,
  y: i32,
}

fn distance_squared(p1: Point, p2: Point) -> i32
  post ret >= 0
= {
  let dx = p2.x - p1.x;
  let dy = p2.y - p1.y;
  dx * dx + dy * dy
};
```

### Pattern Matching

```bmb
-- basics/06_pattern_match.bmb
enum Option<T> {
  Some(T),
  None,
}

fn unwrap_or(opt: Option<i32>, default: i32) -> i32 =
  match opt {
    Some(v) => v,
    None => default,
  };
```

## Running Examples

```bash
# Type check
bmb check basics/01_hello.bmb

# Run with interpreter
bmb run basics/01_hello.bmb

# Verify contracts
bmb verify contracts/01_preconditions.bmb

# Build native executable (requires LLVM)
bmb build projects/calculator/main.bmb -o calculator
```

## Categories

### Basics
Language fundamentals: variables, functions, control flow.

### Contracts
Contract-based verification: preconditions, postconditions, invariants.

### Data Structures
BMB data types: structs, enums, arrays, references.

### Algorithms
Classic algorithms with verified correctness via contracts.

### Projects
Complete applications demonstrating real-world BMB usage.

### Tutorials
Step-by-step guides for learning BMB.

## Contributing

1. Fork the repository
2. Add your example in the appropriate directory
3. Include comments explaining the code
4. Add contracts where applicable
5. Submit a PR

## License

MIT License
