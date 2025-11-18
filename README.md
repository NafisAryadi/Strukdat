# **Expression Interpreter & Control-Flow Runner**

This project implements a simple interpreter capable of evaluating arithmetic expressions, assigning variables, handling conditional logic, printing output, and executing basic control-flow commands. The interpreter processes instructions provided in a `.txt` file and executes them sequentially.

---

## **Features**

### **1. Variable Management**

* Supports variables `a` through `i`.
* Allows direct assignment (`a = 5`) and computed assignment (`a = 3+2*4`).
* Automatically converts floating-point results to integers when the value is whole.

### **2. Arithmetic Expression Evaluation**

* Handles: `+`, `-`, `*`, `/`, `:`, `%`, `^`
* Supports multi-digit numbers, variables, and parentheses:

  * `a = (b + c) * 2`
* Prevents division by zero with safety checks.

### **3. Conditional Evaluation**

* Supports comparisons:
  `>`, `<`, `>=`, `<=`, `==`, `!=`
* Used within the `jika(condition) statement` instruction.

### **4. Control Flow**

* **`jika()`** — conditional execution based on evaluated expression.
  Example:
  `jika(a > 5) cetak("ok")`
* **`goto label`** — jumps to a labeled line for low-level flow control.
* **Label detection** uses matching substrings inside a line.

### **5. Output Handling**

* **`cetak()`** — prints values, text inside quotes, or variables.
  Example:

  * `cetak("Hello")`
  * `cetak(a)`

### **6. Stack-Based Expression Conversion**

The interpreter converts infix expressions to postfix using:

* Operator priority levels
* Operator stack
* Output queue
  Then evaluates the expression from the postfix form.

---

## **How It Works**

1. The interpreter loads instructions from `run.txt`.
2. Each line is parsed to determine whether it is:

   * A variable assignment
   * An expression to compute
   * A conditional instruction
   * A `cetak()` command
   * A `goto` command
3. Expressions are processed using:

   * Operator precedence
   * Parentheses matching
   * Stack evaluation
4. Control-flow instructions may redirect execution to different lines.

---

## **File Structure**

```
├── program.py        # This interpreter
└── run.txt           # File containing instructions to execute
```

---

## **Example run.txt**

```
a = 5
b = 3
jika(a > b) cetak("a lebih besar")
cetak(a)
```

---

## **Usage**

1. Place instructions in `run.txt`.
2. Run the interpreter:

```bash
python program.py
```

3. Output appears in the terminal based on the executed instructions.

---

## **Notes**

* All variables default to `0`.
* Supports nested parentheses.
* Division by zero terminates the program safely.
* `goto` behaves as a simple jump operation and should be used carefully to avoid infinite loops.
