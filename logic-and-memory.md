# Logic and Truth

* Computers and Logic
    • Automata: computers automatically run commands based on their state
    • State: stored in memory (RAM)
    • Execution: command are executed by the processor (CPU)
    • I/O devices: keyboards, mice, screens, speakers, and internet interfaces allow interaction

* Von Neumann Architecture
    • Code is translated into machine instructions
    • Instructions are loaded into memory and executed by the CPU
    • Instructions include arithmetic, logic operations, and control flow

* Logic and Truth Tables
    • Syllogistic Logic: originates from Aristotle, involves deriving truth from premises
        - Example: "All humans are mortal. Socrates is a human. Therefore, Socrates is mortal."
    • Booleans: True or False values used in logical expressions

* Logical Operators

• AND (&&): True if both operands are true
```js
A   B   A && B
--------------
0   0      0
0   1      0
1   0      0
1   1      1

```

• OR (||): True if either operand is true
```js
A   B   A || B
--------------
0   0      0
0   1      1
1   0      1
1   1      1

```

• NOT (!): Inverts the boolean value
```js
A   !A
-------
0    1
1    0

```

* Compound Logic

• NAND: Not AND, true unless both operands are true
```js
A   B   A && B   !(A && B)
--------------------------
0   0     0          1
0   1     0          1
1   0     0          1
1   1     1          0

```

• De Morgan's Law: Logical equivalence of expressions
    • Example: `!(A && B)` is equivalent to `!A || !B`
```js
A   B   !A   !B   !A || !B
---------------------------
0   0    1    1       1
0   1    1    0       1
1   0    0    1       1
1   1    0    0       0

```

* XOR (Exclusive OR)

• XOR(^): True if exactly one operand is true
```js
A   B   A ^ B
--------------
0   0      0
0   1      1
1   0      1
1   1      0

```
• Alternative Expression: `(A && !B) || (!A && B)`

* Key Takeaways
    • Truth Tables: visual representation of logical expressions
    • Logical Equivalence: different expressions can produce the same truth values
    • Simplifying Logic: Aim for simple and clear logical expressions


# Simplifying Code Logic

Logical equivalence can be used to simplify and condense your code to make it more readable and maintainable. Here's an example to illustrate this concept.

* Counting to Zero
We will write a function that takes a number and counts from that number to zero, handling various cases including posititive and negative integers, as well as non-integers.

* Example Output:
```js
countToZero(5);
// 5
// 4
// 3
// 2
// 1
// 0

countToZero(-5);
// -5
// -4
// -3
// -2
// -1
// 0

countToZero(5.5);
// 5.5
// 5
// 4
// 3
// 2
// 1
// 0

```

* Key Points to Consider
    1. Positive Non-integer: Print the number, subtract the decimal part, and continue
    2. Negative Non-integer: Print the number, add the negative decimal part, and continue
    3. Positive Integer: Print the number, subtract 1, and continue
    4. Negative Integer: Print the number, add 1, and continue
    5. Zero: Print zero and terminate

* Checking for Integers
To determine if a number is an integer, use the modulo operator:
```js
function isInt(n) {
    return n % 1 === 0;
}
```

* Initial Verbose Solution
```js
function countToZero(n) {
    if (n > 0 && !isInt(n)) {
        console.log(n);
        countToZero(n - n % 1);
    }

    if (n < 0 && !isInt(n)) {
        console.log(n);
        countToZero(n + -(n % 1));
    }

    if (n > 0 && isInt(n)) {
        console.log(n);
        countToZero(n - 1);
    }

    if (n < 0 && isInt(n)) {
        console.log(n);
        countToZero(n + 1);
    }

    if (n === 0) {
        console.log(0);
    }
}
```

* Simplifying the Code
To simplify, we note:
    • All conditions start with `console.log(n)`
    • Modulo operation can be used to determine the decrement for non-integers
    • Decrement for integers should be based on the sign of the number

* Simplified Implementation:
```js
function countToZero(n) {
    // print the number
    console.log(n);

    // base case: end on zero
    if (n === 0) return;

    // decrement the non-integer part for non-integers
    let decrement = n % 1;

    // if number is an integer, decrement by 1 * the sign of n
    if (decrement === 0) {
        decrement = n / Math.abs(n);
    }

    // recurse
    countToZero(n - decrement);
}
```

* Recap
In this example, we learned how to simplify code logic by:
    1. Identifying common operations across conditions
    2. Using mathematical properties (e.g. modulo operation) to reduce redundancy
    3. Refactoring code to make it more concise and readable

Simplifying your code not only makes it easier to read and maintain but also helps in identifying potential errors and improving performance.



# Intro to Binary

* Understanding Numerical Bases
Numerical bases define how many digits are used in a numbering system. The base determines the range of digits and how numbers are incremented

* Base-10: Decimal
    • Commonly used in everyday life
    • Digits 0-9
    • Once you reach 9, the next digit increments to form 10, 11, etc.

    Example:
    ```js
    0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 23, ...
    ```

* Base-2: Binary
    • Used in computers
    • Digits: 0 and 1 (binary digits or bits)
    • After 1, the next digit increments like so: 10 (binary for 2), 11 (binary for 3), etc.

    Example:
    ```js
    0000 (0), 0001 (1), 0010 (2), 0011 (3), 0100 (4), 0101 (5), 0110 (6), 0111 (7), 1000 (8), ...
    ```
    To distinguis binary from decimal, prefix with `0b`:`0b1000` (binary for 8)

* Translating Binary to Decimal
To convert binary to decimal, multiply each bit by 2 raised to its position power (starting from 0 on the right) and sum the results.

Example:
Convert `0b11001010` to decimal:
```js
2^0 * 0 = 0
2^1 * 1 = 2
2^2 * 0 = 0
2^3 * 1 = 8
2^4 * 0 = 0
2^5 * 0 = 0
2^6 * 1 = 64
2^7 * 1 = 128
sum = 0 + 2 + 0 + 8 + 0 + 0 + 64 + 128 = 202
```
Thus, `ob11001010` is `202` in decimal

* Base-16: Hexadecimal
    • Digits: 0-9 and A-F (where A=10, B=11, C=12, D=13, E=14, F=15)
    • Often used as shorthand for binary
    • One hex digit represents four binary bits

    Example:
    ```js
    0 = 0b0000 = 0x0
    1 = 0b0001 = 0x1
    2 = 0b0010 = 0x2
    ...
    A = 0b1010 = 0xA
    B = 0b1011 = 0xB
    C = 0b1100 = 0xC
    D = 0b1101 = 0xD
    E = 0b1110 = 0xE
    F = 0b1111 = 0xF
    ```
    To distinguis hexadecimal from decimal, prefix with `0x`:`0xF23C`

    Example:
    Convert `0xF23C` to decimal:
    ```js
    16^0 * C = 1 * 12 = 12
    16^1 * 3 = 16 * 3 = 48
    16^2 * 2 = 256 * 2 = 512
    16^3 * F = 4096 * 15 = 61440
    Sum = 12 + 48 + 512 + 61440 = 62012
    ```
    Thus, `0xF23C` is `62012` in decimal

* Bytes and Memory
    • Byte: 8 bits
    • Kilobyte (KB): 1000 bytes
    • Megabyte (MB): 1 million bytes
    • Gigabyte (GB): 1 billion bytes
    • Terabyte (TB): 1 trillion bytes

Mnemonic for Memory Sizes:
"Kissing Mel Gibson, Teddy Pendergrass exclaimed, zesty, yo!"


* Representing Letters in Binary
Characters are represented using standard encodings like ASCII, where each character is mapped to a binary value

Example:
ASCII value for `A` = `10000001`

* Summary:
    • Base-10 (Decimal): Everyday counting (0-9)
    • Base-2 (Binary): Used in computing (0,1)
    • Base-16 (Hexadecimal): Efficient shorthand for binary (0-9, A-F)
    • Memory Representation: Binary used to represent all data types, including text and larger numerical bases for efficiency
