# Binary

---

## Prerequisites

- [Nothing](Binary.md#binary)

---

## Contents

Topics to be covered in this lesson:

- Origins
- Introduction
- What are bases?
- Why use Binary?
- Notation
- How does it work? (Translating from binary to decimal)
- Translating from decimal to binary
- Bit width and range
- Hexadecimal Notation
- How does this apply to other bases?

---



## Origins

The whole concept of binary logic in computing comes from propositions. In the words of Rosen (Discrete Mathematics and Its Applications),

> A proposition is a declarative sentence (that is, a sentence that declares a fact) that is either true or false, but not both. 

Propositions can be classified into **true** and **false** statements, thus bearing two distinct values. The foundations of logical reasoning were first laid by Aristotle in his work on syllogisms.

In 1854, George Boole, in his book "The Laws of Thought", stated the methods of producing new propositions from those that we already have. New propositions are formed from existing propositions using logical operators.

Modern logic inherited Boole, so much so that "Boolean Algebra" has been named after him.

In 1937, [Claude Shannon's master's thesis](https://www.cs.virginia.edu/~evans/greatworks/shannon38.pdf) focused on "Switching Circuits". His paper showed how circuits can implement Boolean logic. His master’s thesis received a major academic prize at MIT and laid the foundations of digital circuit design.

## Introduction

Binary is a system of representing numbers using only two symbols: 0 and 1. In the decimal system, 9 is followed by 10. In the world of binary, 1 is followed by 10. Binary symbols are often called "bits."

## What are bases?

Bases are named after the total number of unique digits used (including 0). Binary uses base 2, while the decimal system uses base 10. The base determines the place value of each digit.

Octal and Hexadecimal number systems have bases 8 and 16, respectively. In Minecraft, the signal strength of Redstone is from 0 to 15. This is why, along with Binary, we also see Redstone circuits where Hexadecimal transmission has been used.

## Notation

When talking about numbers in different bases, we must have a way to distinguish between which base we are representing that number with. 
So to fix that problem, we prefix ``0b`` when the number is in binary and ``0d`` when its in decimal. Other bases like hexadecimal and octal use ``0x`` and ``0o`` respectively.  
Here are the prefixes being used to distinguish which number we mean:  
``0b101 = 5 (five)``  
``0o101 = 65 (sixty five)``  
``0d101 = 101 (one hundred and one)``  
``0x101 = 257 (two hundred and fifty seven)``

Note: Formal textbooks use a subscript to the right of the number to indicate the base. For example, ``0b101`` is written as (101)<sub>2</sub>. However, throughout this material, we will use prefix notation, not subscript notation. Also, ``0d`` is a convention used in this material for a decimal number.

## How does it work? (Translating from binary to decimal)

We learnt that in the decimal system, each digit represents a power of 10, which means each digit increases in value by a factor of 10 when moving to the left. The rightmost digit represents 1 (10<sup>0</sup>), the next digit to the left represents 10 (10<sup>1</sup>), and so on. Let us take 0d5432 as an example.

| Th | H | T | O |
| --- | --- | --- | --- |
| 5 | 4 | 3 | 2

On expressing the number in expanded form, we get

```
0d5432
= 5000 + 400 + 30 + 2
= 5 * 1000 + 4 * 100 + 3 * 10 + 2 * 1
= 5 * 10^3 + 4 * 10^2 + 3 * 10^1 + 2 * 10^0.
```

Likewise, in a binary system, each digit doubles its value when going to the left. 

The rightmost digit represents 1 (2<sup>0</sup>), the next digit to the left represents 2 (2<sup>1</sup>), and so on.  
Let us take 0b1010 as an example.

| Eights | Fours | Twos | Ones |
| --- | --- | --- | --- |
| 1 | 0 | 1 | 0 |

These column names correspond to powers of two: 

Eights: 8 = 2<sup>3</sup>

Fours: 4 = 2<sup>2</sup>

Twos: 2 = 2<sup>1</sup>

Ones: 1 = 2<sup>0</sup>

On expressing the number in expanded form into decimal values, we get

```
0b1010
= 1 * 8 + 0 * 4 + 1 * 2 + 0 * 1
= 1 * 2^3 + 0 * 2^2 + 1 * 2^1 + 0 * 2^0
```
0b1010 is 0d10.

Another example: the binary number 101 represents the decimal number ``1 * 2^2 + 0 * 2^1 + 1 * 2^0 = 1 * 4 + 0 * 2 + 1 * 1 = 4 + 1 = 5``.

## Translating from decimal to binary

To translate a decimal number to binary, you can see what bit has the biggest value that is still below our number, and then subtract our number with the value of that bit. And we repeat this process until we have our asnwer.  
Here is an example: what is the representation of 21 in binary?
- The biggest bit we can fit is 16 (0b10000) because 32 would be too much. We now subtract the two and we get ``21 - 16 = 5``  
- Repeating the same process we find out that 4 is the biggest value we can fit below 5 so we add 4 (0b100) to our result (0b10100) and subtract ``5 - 4 = 1``
- Lastly we have that 1 is the lowest bit, so we can add that in to our result (0b10101) and ``1 - 1 = 0``, so we can stop now

To translate a decimal number to binary, you can also use the following method:
1. Divide the number by 2
2. Write down the remainder (0 or 1)
3. Repeat step 1 and 2 until the quotient becomes 0
4. The remainders, read from bottom to top, give the binary representation of the decimal number.

For example, to translate the decimal number 10 to binary, you would do the following:

* 10 / 2 = 5 with a remainder of 0, so the first digit is 0.
* 5 / 2 = 2 with a remainder of 1, so the second digit is 1.
* 2 / 2 = 1 with a remainder of 0, so the third digit is 0.
* 1 / 2 = 0 with a remainder of 1, so the last digit is 1.

The final binary representation is 1010.

## Bit width and range

In the decimal number system, the highest single digit is 9.

For 3 digits, the highest number is 0d999. ``0d999 = 0d1000 - 0d1 = 10^3 - 1`` 

For N digits, the highest number is 0d999...99, where 9 is repeated N times. ``0d999...99 = 10^N - 1``

Likewise, in the binary number system, the highest single bit is 1.

For 3 bits, the highest number is 0b111. ``0b111 = 0b1000 - 0b1 = 2^3 - 1``

For N bits, the highest number is 0b111...11, where 1 is repeated N times. ``0b111...11 = 2^N - 1``

Therefore, a binary number with N bits can represent `2^N` distinct values.

For binary (unsigned numbers:
- the minimum value is ``0``
- the maximum value is ``2^N − 1``

For example, with 4 bits:
- minimum = 0b0000 = 0
- maximum = 0b1111 = 15

## Hexadecimal notation

Hexadecimal (base 16) is commonly used as a compact way to represent binary values. Each hexadecimal digit corresponds to exactly 4 binary bits.

For example:
``0x13 = 0001 0011``

## How does this apply to other bases?

The same principles apply to other number bases, such as decimal (base 10) or hexadecimal (base 16). 
However, instead of powers of 2, the digits represent powers of the base.  
For example, in decimal, each digit represents a power of 10. In hexadecimal, each digit represents a power of 16. The process of converting between different bases is similar to the process of converting between binary and decimal, but with different base-specific calculations. It's worth noting that it is simpler to convert decimal to binary or viceversa than to convert decimal to hexadecimal or viceversa.
One might wonder why do we use different bases. The reason is convenience. Decimal is used because we have 10 fingers in our hands. Octal and Hexadecimal are used because 8 and 16 are powers of 2, so translating between these bases and binary is extremely easy.
The number `0x13` can be represented easily. The representation of the number 3 in 4 bits (for hexadecimal, and 3 bits for octal) is `0b0011`.  
The representation of 1 is ``0b0001``, so we join our representations, and we get that ``0x13 = 00010011``. The same applies the other way.

---
## What Now?

This lesson is over, however here is a list of topics recommended learning next:

- [Binary addition](Binary%20Addition.md#binary-addition)
