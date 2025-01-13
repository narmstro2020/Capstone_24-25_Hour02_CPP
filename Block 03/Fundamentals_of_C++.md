# Fundamentals of C++

## Table of Contents
1. **Introduction to C++**
2. **Keywords and Identifiers**
3. **Data Types and Variables**
4. **Constants and Literals**
5. **Input and Output**
6. **Operators**
    - Arithmetic Operators
    - Relational Operators
    - Logical Operators
    - Bitwise Operators
    - Assignment Operators
    - Miscellaneous Operators
7. **Assignments**
8. **Assignment Solutions**

---

## 1. Introduction to C++
C++ is a powerful, high-performance, general-purpose programming language developed by Bjarne Stroustrup as an extension of the C programming language. It supports both procedural and object-oriented programming paradigms, making it versatile for various applications such as system software, game development, and embedded systems. 

CLion, developed by JetBrains, is an Integrated Development Environment (IDE) specifically designed for C++ development. It offers features like code completion, debugging tools, and project templates, which make it easier to develop and manage C++ projects.

### Key Features of C++
- **Object-Oriented:** Supports classes, inheritance, polymorphism, and encapsulation.
- **Standard Template Library (STL):** Provides generic classes and functions for data structures and algorithms.
- **Portability:** Code can run on different platforms with minimal modification.
- **Performance:** Combines low-level hardware access with high-level abstractions for efficient execution.

### Vocabulary
- **Compiler:** A tool that translates source code into machine code.
- **Syntax:** The rules that define the structure and form of valid C++ programs.
- **IDE:** Integrated Development Environment that combines code editing, compiling, and debugging tools.

### Example
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```
This program includes the `iostream` header for input and output, and the `main` function serves as the entry point for execution.

---

## 2. Keywords and Identifiers

### Keywords
Keywords are reserved words in C++ with predefined meanings. They cannot be used as identifiers for variables, functions, or other user-defined elements.

#### Examples of Keywords:
- **Control Flow:** `if`, `else`, `for`, `while`, `switch`, `case`
- **Data Types:** `int`, `float`, `double`, `char`, `bool`
- **Access Modifiers:** `public`, `private`, `protected`
- **Others:** `return`, `const`, `static`, `virtual`, `class`

### Identifiers
Identifiers are names used to represent variables, functions, arrays, or other user-defined elements in a program. 

#### Rules for Identifiers:
1. Must begin with a letter or an underscore (_).
2. Cannot contain special characters except underscores.
3. Cannot match any C++ keywords.
4. Are case-sensitive.

### Example
```cpp
int main() {
    int age = 25; // "age" is an identifier
    float temperature = 36.6; // "temperature" is another identifier
    return 0;
}
```

---

## 3. Data Types and Variables
Data types define the type and size of data a variable can hold. C++ is a statically-typed language, meaning the type of a variable must be declared before its use.

### Built-in Data Types
1. **Integer Types:** `int`, `short`, `long`, `long long`
2. **Floating-Point Types:** `float`, `double`, `long double`
3. **Character Type:** `char`
4. **Boolean Type:** `bool`

### User-Defined Data Types
- **Structs**
- **Classes**
- **Enumerations**

### Variable Declaration
Variables are declared with a type followed by a name. Optionally, they can be initialized during declaration.
```cpp
int age = 30;
double salary = 55000.50;
char grade = 'A';
bool isEmployed = true;
```

### Scope of Variables
1. **Local Variables:** Declared inside functions or blocks.
2. **Global Variables:** Declared outside all functions.
3. **Static Variables:** Retain their values between function calls.

---

## 4. Constants and Literals
Constants are immutable values, meaning their values cannot be changed once assigned. Literals are fixed values assigned directly in the code.

### Types of Constants
1. **`const` Keyword:**
   ```cpp
   const int MAX_AGE = 100;
   ```
2. **`#define` Directive:**
   ```cpp
   #define PI 3.14159
   ```

### Types of Literals
1. **Integer Literals:** `10`, `0x1A`, `077`
2. **Floating-Point Literals:** `3.14`, `2.0e-5`
3. **Character Literals:** `'A'`, `'
'`
4. **String Literals:** `"Hello"`
5. **Boolean Literals:** `true`, `false`

---

## 5. Input and Output
C++ provides standard input/output functions through the `<iostream>` library.

### Input Using `cin`
- Used to take input from the user.
- Extracts data from the input buffer.
```cpp
int age;
std::cout << "Enter your age: ";
std::cin >> age;
```

### Output Using `cout`
- Used to print output to the console.
- Supports chaining multiple output statements using `<<`.
```cpp
std::cout << "Hello, " << "World!" << std::endl;
```

### Manipulators
Manipulators modify the formatting of output.
- `std::endl`: Inserts a newline and flushes the output buffer.
- `std::setw(n)`: Sets the width of the output.
```cpp
#include <iomanip>
std::cout << std::setw(10) << "Right-aligned";
```

---

## 6. Operators

### Arithmetic Operators
- **Addition (+):** `a + b`
- **Subtraction (-):** `a - b`
- **Multiplication (*):** `a * b`
- **Division (/):** `a / b`
- **Modulus (%):** `a % b` (only for integers)

### Relational Operators
- `==` (Equal to)
- `!=` (Not equal to)
- `>` (Greater than)
- `<` (Less than)
- `>=` (Greater than or equal to)
- `<=` (Less than or equal to)

### Logical Operators
- `&&` (AND)
- `||` (OR)
- `!` (NOT)

### Bitwise Operators
- `&` (AND)
- `|` (OR)
- `^` (XOR)
- `<<` (Left shift)
- `>>` (Right shift)

### Assignment Operators
- `=` (Assignment)
- `+=` (Add and assign)
- `-=` (Subtract and assign)

### Miscellaneous Operators
- Ternary Operator: `condition ? expr1 : expr2`
- `sizeof`: Returns the size of a data type.
- Address-of Operator: `&`
- Pointer Dereference: `*`

### Example
```cpp
int x = 10, y = 20;
int max = (x > y) ? x : y; // Ternary operator
```

---