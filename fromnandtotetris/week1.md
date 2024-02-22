# Week 1
## Introduction
### Unit 0.0: Introduction
![alt text](images/image.png)
### Unit 0.1: The Road Ahead
- Don’t worry about the how worry about the what?
- Hello World, is kind of a simple program but not really at the same time. Since printing a text involves in changing the colours on a screen, sending these instructions to the “monitor”, etc.
### Unit 0.2: From Nand to Hack
![alt](images/image-20240110-152709.png)
![alt](images/image-20240110-152856.png)
![alt](images/image-20240110-153413.png)
![alt](images/image-20240110-153524.png)

### Unit 0.3: From Hack to Tetris
This lecture explains about the second part of this course. 
### Unit 0.4: Project 0 Overview

## Boolean Functions and Gate Logic
### Unit 1.1: Boolean Logic
AND, OR, XOR, NOT

![alt](images/image-20240111-000601.png)
What is nice about boolean functions is that they can only accept a constant number of inputs.
#### Boolean Identities
| Commutative Laws | Associative Laws | Distributive Laws | De Morgan Laws |
|------------------|------------------|-------------------|----------------|
|(x AND y) = (y AND x)|((x AND y) AND z) = (x AND (y AND z))|(x AND (y OR z)) = (x AND y) OR (x AND z)|NOT(x AND y) = NOT(x) OR NOT(y)|
|(x OR y) = (y OR x)|((x OR y) OR z) = (x OR (y OR z))|(x OR (y AND z)) = (x OR y) AND (x OR z)|NOT(x OR y) = NOT(x) AND NOT(y)|
|(x XOR y) = (y XOR x)|((x XOR y) XOR z) = (x XOR (y XOR z))|(x XOR (y AND z)) = (x XOR y) AND (x XOR z)||

![alt](images/image-20240131-153917.png)
### Unit 1.2: Boolean Functions Synthesis
> Key idea of this lecture is constructing the disjunctive normal form of a boolean function. DNF

The point is given a truth table construct a boolean function. That’s how logic gates are designed. For example a half adder.

![alt](images/image-20240111-002708.png)
For each of the 1s in a row we design a function that achieves a 1 on that row and 0 everywhere else. Then we OR all these expression together.

> Any boolean function can be represented using an expression containing AND, OR, and NOT operations. Actually we can do it with just AND and NOT operations. Because of de Morgan’s.

| x | y | NAND |
| --- | --- | --- |
|0|0|1|
|1|0|1|
|0|1|1|
|1|1|0|

> By only using NAND operation we can represent any boolean function.

### Unit 1.3: Logic Gates
Logic Gates:
- elementary ( nand, or, and)
- composite - made up from elementary logic gates or composite ones ( adder, Mux … )
#### Nand
![](images/image-20240111-220656.png)
![](images/image-20240111-220728.png)
![](images/image-20240111-221050.png)

Implementation is different than the interface. It is hidden, if we want to see it we have to explore the next level of the abstraction.
![](images/image-20240111-221355.png)

### Unit 1.4: Hardware Description Language
![](images/image-20240112-212912.png)

Implementation of a Xor logic with And, Not and Or gates.
![](images/image-20240112-213209.png)

All the connections need to be named.
Then in the PARTS section we describe all the connections coming in and out of individual gates.
![](images/image-20240112-214044.png)

As many gates/chips we have in our diagram we will have that many statements in the PARTS section. Inputs and outputs are already described in the IN and OUT sections.
HDL is a declarative language.

Before using a gate we need to know the gates interface/api and properly use it.

`Not(in= , out=), And(a= , b= ,out=), Or(a= , b= ,out=)`

VHDL and Verilog are the type of common hdls. There are many more.

### Unit 1.5: Hardware Simulation
Idea is to create an HDL code + test script load it into hardware simulator and test the logic.
Quite involved lecture. Mostly the idea is to explain the .hdl files.
.cmp files are used as a source of truth on how the logic should work. What outputs for which inputs.
.out is what your hdl program actually returns given a .tst file.
And a .tst file is sort of a script that instead of manually flipping bits let’s say it can do that for us, once we direct it how. For example we can say, change input a to 0 and input b to zero, then run simulation…

#### Unit 1.6: Multi-Bit Buses
As the name suggests we need these when manipulating bunch of bits together as one entity. Bunch of bits together are called a bus.
![](images/image-20240122-221351.png)
![](images/image-20240122-221426.png)

When we declare, `a[16]` that means a is a 16 bit bus. 
![](images/image-20240130-212305.png)
 
### Unit 1.7: Project 1 Overview

> Dmux and Mux gates should be reviewed.
![](images/image-20240130-212731.png)
![](images/image-20240131-212455.png)
![](images/image-20240130-213944.png)
![](images/image-20240205-220535.png)

| Elementary Logic Gates | 16-bit Variants |
| --- | --- |
| Not - First to implement, it is simple since `Not(a) = Nand(a, a)` | Not16|
| And - After implementing a not gate, it is easy since `And(a,b) = Not(Nand(a, b))` | And16|
| Or(a, b) = Not(Not(Or(a,b))) = Not(Nota And Notb) = Nota Nand Notb | Or16 |
| Xor - using dnf from the truth table of Xor `Xor(a, b) = And(a, not(b)) or And(not(a), b)` | Xor16 |
| Mux `if (sel == 0) out = a, else out = b Mux(a,b,s) = And(a, Not(s)) or And(b, s)` | Mux4Way16 |
| Dmux | |
 
 
### Unit 1.8: Perspectives
![](images/image-20240207-230950.png)
- we can build a computer with just nand gates or nor gates
- nmos implementation of a nand gate

Week 2
Boolean Arithmetic and the ALU Roadmap
We will be focusing on creating adders, chips designed to add numbers. We will then build an ALU, which is designed to perform arithmetic and logical operations. Then a CPU from an ALU.
Key concepts: Binary numbers, binary addition, the two's complement method, half-adders, full-adders, n-bit adders, counters, Arithmetic Logic Unit (ALU), combinational logic.
Unit 2.1: Binary Numbers
Nothing new here.
Unit 2.2: Binary Addition
Addition we will implement in hardware. Then Subtraction and which is greater we get for free. Multiplication and Division will be implemented with software.
Open image-20240110-161439.png
image-20240110-161439.png
Addition is not really mathematical since if adding two numbers exceeds the words size, the computer will just  ignore the extra bits.
 
 
 
 
 
 
 
Build an Adder:
Half adder - add two bits
Full adder - adds three bits
Adder - adds two numbers
Half Adder
Open image-20240110-161729.png
image-20240110-161729.png
As long as the carry from before was  a 0, then we just adding two bits. No matter what all the other bits in either number look like. So we will focus on that slice.
Implementing the half adder is very easy, one xor gate and one and gate.
a
b
sum
carry
0
0
0
0
1
0
1
0
0
1
1
0
1
1
0
1
Full Adder
Now we have really three inputs, when we looking at a slice. We have the a, b but also c ( carry ).
a
b
c
sum
carry
0
0
0
0
0
0
0
1
1
0
0
1
0
1
0
0
1
1
0
1
1
0
0
1
0
1
0
1
0
1
1
1
0
0
1
1
1
1
1
1
 
https://www.youtube.com/watch?v=Z_DYRgtAXfw

How to go from a half adder to a full adder can be done with figuring out the kmaps. And then sort of working it out by using half adders. The final diagram is two full adders and an or gate.
Multi-bit Adder
For example, a 16 bit adder will have one half adder for the right most bits. Then 15 full adders for the rest. We can also just do 16 full adders.
Unit 2.3: Negative Numbers
Sign Bit
This representation is not popular. The first digit represents the sign only, the rest is about the magnitude. One shortcoming is that 0 and negative 0 have two different representations. Also adding a number with it’s complement through the usual digit wise addition does not produce 0.
Two’s Complement

Idea: In order to represent (-x), we represent it as the positive number from calculating (2^n - x).
We get one extra negative number compared to the previous approach. 

Having n bits to represent a number, we have 2^(n-1) - 1, positive numbers and, 2^(n-1) negative numbers. 
Two’s complement allows us to get subtraction for free. Key idea here is to understand how to compute (-x), since y - x = y + (-x)

-x = 2^n - x = 1 + (2^n - 1) - x, since 2^n - 1 - is all 1s (111..11), subtracting a number from this is very easy since we never need to borrow. Then add one.
Unit 2.4: ALU
Open image-20240215-212016.png
image-20240215-212016.png
Open image-20240215-212115.png
image-20240215-212115.png
Open image-20240215-212258.png
image-20240215-212258.png
Open image-20240215-212408.png
image-20240215-212408.png

if out == 0 then zr = 1, else zr = 0
if out < 0 then ng = 1, else ng = 0
The reason for these will be apparent later when we build a whole computer
Unit 2.5: Project 2 Overview
Done completed.
Unit 2.6: Perspectives
Week 3
Module 3: Memory Roadmap
Unit 3.1: Sequential Logic
