
# Control Structures in C++

## Table of Contents
1. **Introduction to Control Structures**
2. **Vocabulary**
3. **Decision-Making Structures**
   - `if` Statements
   - `if-else` Statements
   - Nested `if-else`
   - `switch` Statements
4. **Looping Structures**
   - `for` Loop
   - `while` Loop
   - `do-while` Loop
5. **Jump Statements**
   - `break`
   - `continue`
   - `goto`
6. **Assignments**
   - Assignment 1: Decision-Making Practice
   - Assignment 2: Looping Practice
   - Assignment 3: Comprehensive Exercise
7. **Assignment Solutions**

---

## 1. Introduction to Control Structures
Control structures in C++ determine the flow of program execution based on conditions or iterations. These structures can broadly be categorized into:
- **Decision-making structures**: Allow the program to make decisions and execute certain code based on conditions.
- **Looping structures**: Enable repetitive execution of code blocks.
- **Jump statements**: Alter the flow of execution by jumping to another point in the program.

## 2. Vocabulary
- **Condition**: A boolean expression that evaluates to `true` or `false`.
- **Branching**: Executing different code paths based on a condition.
- **Iteration**: Repeatedly executing a block of code.
- **Control variable**: A variable that influences the execution of control structures.
- **Break**: Exits the current loop or `switch` statement.
- **Continue**: Skips the rest of the current iteration and moves to the next one.
- **Goto**: Transfers control to a labeled statement.

## 3. Decision-Making Structures
### `if` Statements
The `if` statement executes a block of code if a condition evaluates to `true`.

**Syntax:**
```cpp
if (condition) {
    // Code to execute if condition is true
}
```
**Example:**
```cpp
int x = 10;
if (x > 5) {
    std::cout << "x is greater than 5" << std::endl;
}
```

### `if-else` Statements
The `if-else` statement provides an alternative block to execute if the condition is `false`.

**Syntax:**
```cpp
if (condition) {
    // Code to execute if condition is true
} else {
    // Code to execute if condition is false
}
```
**Example:**
```cpp
int x = 3;
if (x > 5) {
    std::cout << "x is greater than 5" << std::endl;
} else {
    std::cout << "x is not greater than 5" << std::endl;
}
```

### Nested `if-else`
Allows multiple levels of decision-making.

**Example:**
```cpp
int x = 20;
if (x > 0) {
    if (x % 2 == 0) {
        std::cout << "x is a positive even number" << std::endl;
    } else {
        std::cout << "x is a positive odd number" << std::endl;
    }
}
```

### `switch` Statements
Used to execute one block of code from multiple options.

**Syntax:**
```cpp
switch (variable) {
    case value1:
        // Code to execute for value1
        break;
    case value2:
        // Code to execute for value2
        break;
    default:
        // Code to execute if no case matches
}
```
**Example:**
```cpp
char grade = 'B';
switch (grade) {
    case 'A':
        std::cout << "Excellent!" << std::endl;
        break;
    case 'B':
        std::cout << "Good!" << std::endl;
        break;
    default:
        std::cout << "Needs improvement." << std::endl;
}
```

## 4. Looping Structures
### `for` Loop
The `for` loop is used when the number of iterations is known.

**Syntax:**
```cpp
for (initialization; condition; update) {
    // Code to execute
}
```
**Example:**
```cpp
for (int i = 0; i < 5; i++) {
    std::cout << i << " ";
}
```

### `while` Loop
The `while` loop executes a block of code as long as a condition is `true`.

**Syntax:**
```cpp
while (condition) {
    // Code to execute
}
```
**Example:**
```cpp
int x = 0;
while (x < 5) {
    std::cout << x << " ";
    x++;
}
```

### `do-while` Loop
The `do-while` loop guarantees execution of the code block at least once.

**Syntax:**
```cpp
do {
    // Code to execute
} while (condition);
```
**Example:**
```cpp
int x = 0;
do {
    std::cout << x << " ";
    x++;
} while (x < 5);
```

## 5. Jump Statements
### `break`
Exits the nearest enclosing loop or `switch` statement.

**Example:**
```cpp
for (int i = 0; i < 10; i++) {
    if (i == 5) break;
    std::cout << i << " ";
}
```

### `continue`
Skips the rest of the current iteration and proceeds to the next.

**Example:**
```cpp
for (int i = 0; i < 10; i++) {
    if (i == 5) continue;
    std::cout << i << " ";
}
```

### `goto`
Transfers control to a labeled statement.

**Example:**
```cpp
int x = 0;
label:
    std::cout << x << " ";
    x++;
    if (x < 5) goto label;
```