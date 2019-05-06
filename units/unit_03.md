# Digital Logic 

    Readings: Chapter B.1-B.3, B.5

> These unit notes are **not** designed to replace readings from the book! They
> are to provide structure to material covered in class and provide you an
> outline for using the book. **You are still required to do the course
> readings** in which you will find much more detail, and those details will be
> evaluated in quizzes, homework, and exams.

## Digital Logic Basics

In this unit, we will develop a basic understanding of boolean arithmetic and
circuit design, which combined, form the foundation of *digital logic*. Building
from this logic, we will see that the circuit design leads directly to the
computation logic built into processing units, or CPUs. 

In this framework, we consider two states:

* a high asserted signal or true state represented by 1,
* and a low asserted signal or false state represented by 0.

Typically, but not always, high asserted (True) is represented by high voltage
settings, while low asserted (False) is represented by low voltage. We typically
consider these voltages carried over wires and manipulated by gates, but we can
also describe this logic using equations.

Below are the standard boolean logic, both in terms of gates and formulas. In
the formulas, the output value is `x` and the first input value is `A` and the
second input value is `B`. We can also describe a **truth table*, which
describes the output based on the two inputs.

### Not

![not-gate](/imgs/logic/not.png)

![not-equation](https://latex.codecogs.com/gif.latex?x&space;=&space;\overline{A})

| A | x |
|---|---|
| 0 | 1 |
| 1 | 0 |

### And 
![and-gate](/imgs/logic/and.png)

![and-equation](https://latex.codecogs.com/gif.latex?x&space;=&space;A&space;\bullet&space;B=AB)

| A | B | x |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |


### Or

![or-gate](/imgs/logic/or.png)

![or-equation](https://latex.codecogs.com/gif.latex?x&space;=&space;A&space;&plus;&space;B)


| A | B | x |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

### Xor

![xor-gate](/imgs/logic/xor.png)

![xor-equation](https://latex.codecogs.com/gif.latex?x&space;=&space;A&space;\oplus&space;B)


| A | B | x |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### Nand

![nand-gate](/imgs//logic/nand.png)

![nand-equation](https://latex.codecogs.com/gif.latex?x&space;=&space;\overline{A&space;\bullet&space;B}&space;=&space;\overline{AB})


| A | B | x |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### Nor

![nor-gate](/imgs/logic/nor.png)

![nor-equation](https://latex.codecogs.com/gif.latex?x&space;=&space;\overline{A&space;&plus;&space;B})

| A | B | x |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |


## More Complex Circuits and Truth Tables

The above examples consider just a single gate in a circuit, but we can express
more complex boolean logic with multiple inputs/outputs using circuits. For
example, the following circuit and its truth table.

![circuit1](/imgs/logic/circuit1.png)

| A | B | C | x | y |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 1 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 |

We can further describe these results using boolean logic, in two equations

![curuit1 formula](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20x%20%3D%26%20A%20%5Cbullet%20B%20%5C%5C%20y%20%3D%26%20A%20%5Cbullet%20B%20&plus;%20C%20%5Cend%7Balign*%7D)

## Simplifying Not Gates

As not gates have a single input and output, we often will compress them down to
a simple circle on the input to the next gate. For example, the following
circuit.

![not-and](/imgs/logic/not-and.png)



May also be written this way. 

![not-and-collapsed](/imgs/logic/not-and-collapsed.png)


With the following truth table

| A | B | x |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |


The same logic of pushing the circles, can be collapsed in the output direction,
which explains the NAND and NOR gates and their truth tables.


![not-and](/imgs/logic/nand.png)

![not-and](/imgs/logic/nor.png)



## Laws of Boolean Logic 

Just like in normal arithmetic/algebra, boolean logic has a set of identities,
properties, and methods of distributing and rearranging factors in
equations. These typically take the form of traditional arithmetic/algebra, but
not always quite the same way.

### Order of Operations

1. Parenthesis
2. Not/Inverse
3. And
4. OR

### Identity Law

![identity law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%26%20A%20&plus;%200%20%3D%20A%20%5C%5C%20%26%20A%20%5Cbullet%201%20%3D%20A%20%5Cend%7Balign*%7D)

### Zero and One Law

![zero and one law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%26%20A%20&plus;%201%20%3D%201%20%5C%5C%20%26%20A%20%5Cbullet%200%20%3D%200%20%5Cend%7Balign*%7D)

### Duplication/Consumption Law

![duplication](https://latex.codecogs.com/gif.latex?A%20%3D%20A%20&plus;%20A)


### Inverse Law

![inverse law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%26%20A%20&plus;%20%5Coverline%7BA%7D%20%3D%201%20%5C%5C%20%26%20A%20%5Cbullet%20%5Coverline%7BA%7D%3D%200%20%5Cend%7Balign*%7D)

### Commutative Law

![commutative law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20A%20&plus;%20B%20%26%3D%20B%20&plus;%20A%5C%5C%20A%20%5Cbullet%20B%20%26%3D%20B%20%5Cbullet%20A%20%5Cend%7Balign*%7D)

### Associative Law

![associative law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20A%20&plus;%20%28B%20&plus;%20C%29%20%26%3D%20%28A&plus;%20B%29%20&plus;%20C%5C%5C%20A%20%5Cbullet%20%28B%20%5Cbullet%20C%29%20%26%3D%20%28A%20%5Cbullet%20B%29%20%5Cbullet%20C%20%5C%5C%20%5Cend%7Balign*%7D)

### Distributive Law

![distributive law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20A%20%5Cbullet%20%28B%20&plus;%20C%29%20%26%3D%20%28A%20%5Cbullet%20B%29%20&plus;%20%28A%20%5Cbullet%20C%29%5C%5C%20A%20&plus;%20%28B%20%5Cbullet%20C%29%20%26%3D%20%28A%20&plus;%20B%29%20%5Cbullet%20%28A%20&plus;%20C%29%20%5C%5C%20%5Cend%7Balign*%7D)

## DeMorgan's Law 

We also have a very important rule in digital logic **DeMorgan's Law**, which
describes how to distribute the not operator.

![DeMorgan's Law](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%5Coverline%7BA&plus;B%7D%20%26%3D%20%5Coverline%7BA%7D%20%5Cbullet%20%5Coverline%7BB%7D%5C%5C%20%5Coverline%7BA%20%5Cbullet%20B%7D%20%26%3D%20%5Coverline%7BA%7D%20&plus;%20%5Coverline%7BB%7D%5C%5C%20%5Cend%7Balign*%7D)

Essentially, it flips the operator, from and to or (or in reverse). This allows
us to simplify some of our gate design. For example, consider that the following
AND gate with two inverted inputs

![not-and](/imgs/logic/notted-and.png)

That can be written as the formula

![not-a-or-not-b](https://latex.codecogs.com/gif.latex?%5Coverline%7BA%7D%20%5Cbullet%20%5Coverline%7BB%7D)

And by, DeMorgan's Law, that's the same as

![not-a-or--b](https://latex.codecogs.com/gif.latex?%5Coverline%7BA%20&plus;%20B%7D)

The inverse (notting) of the result of an OR, is the same as a NOR gate.

![not-and](/imgs/logic/nor.png)

And, then using similar logic, the following gate

![not-and](/imgs/logic/notted-or.png)

Is the same as a NAND gate

![not-and](/imgs/logic/nand.png)

## Bubble Pushing

This process of applying DeMorgan's Law to gates is called **bubble pushing**,
and in the two above examples, we were pushing the bubbles from the input side
to the output side by swapping the gate between and/or. But, we can also push
the bubble from the output of a NAND or NOR gate to the next input.

Let's consider the following more complex circuit. 

![bubble0](/imgs/logic/bubble0.png)

Note that we have two inputs that are inverted, and we can then apply DeMorgan's
law to flip the gates and *push the bubble* to the output.

![bubble1](/imgs/logic/bubble1.png)

Continuing, we can push the bubble further from the outputs to the inputs of the
next gate.

![bubble2](/imgs/logic/bubble2.png)

This means we can flip the gate, and push the bubble to the final output,
resulting in the following circuit.

![bubble3](/imgs/logic/bubble3.png)

## 2-Level Logic and Minimization 

Despite the plethora of gate types, it's the case that we really only need two
gates and inversion to express any kind of logical statement: AND, OR, and
NOT. We call this *2-level Logic* because it requires just two gates (assuming
inversion is free). 

What this means is that for any truth table, with a single output and any number
of inputs, we can represent that truth table using a boolean logical expression
of AND, OR, and NOT. There are two canonical forms *sum of products* and
*product of sums*. We will use sum of products. 

For example, consider the following Truth Table

| A | B | C | x |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

We can take each line of the truth table that results in a true output, and just
consider which inputs produce those outputs.

| A | B | C | x |
|---|---|---|---|
| 0 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 |

![eq](https://latex.codecogs.com/gif.latex?%28%5Coverline%7BA%7D%5Cbullet%5Coverline%7BB%7D%5Cbullet%20C%29%20&plus;%20%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20%5Coverline%7BC%7D%29%20&plus;%20%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20C%29%20&plus;%20%28A%20%5Cbullet%20B%20%5Cbullet%20C%29%20%3D%20x)

The equation above is in canonical form, but it is important to minimize
it. Writing out this circuit would require more gates than we probably need,
costing more money, power, and making the chip more inefficient. 

We can minimize this equation by hand using the some of the rules above, plus
the fact that we can duplicate any values. That's because in boolean logic,
`E+E=E`. It's the same as saying either `E` or `E` is true is equivalent of just
testing if `E` is true.

The minimization precedes by duplicating 

![eq](https://latex.codecogs.com/gif.latex?%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20C%29)

twice more, and then rearranging to apply the distributed rule


![eq](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%28%5Coverline%7BA%7D%5Cbullet%5Coverline%7BB%7D%5Cbullet%20C%29%20&plus;%20%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20%5Coverline%7BC%7D%29%20&plus;%20%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20C%29%20&plus;%20%28A%20%5Cbullet%20B%20%5Cbullet%20C%29%20%26%3D%20x%20%5C%5C%20%28%28%5Coverline%7BA%7D%5Cbullet%5Coverline%7BB%7D%5Cbullet%20C%29%20&plus;%20%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20C%29%29%20&plus;%20%28%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20%5Coverline%7BC%7D%29%20&plus;%20%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20C%29%29%20&plus;%20%28%28A%20%5Cbullet%20%5Coverline%7BB%7D%20%5Cbullet%20C%29%20&plus;%20%28A%20%5Cbullet%20B%20%5Cbullet%20C%29%29%20%26%3D%20x%20%5C%5C%20%5Coverline%7BB%7D%5Cbullet%20C%20%5Cbullet%28%5Coverline%7BA%7D%20&plus;%20A%20%29%20&plus;%20A%5Cbullet%5Coverline%7BB%7D%5Cbullet%28%5Coverline%7BC%7D%20&plus;%20C%29%20&plus;%20A%5Cbullet%20C%20%5Cbullet%28%5Coverline%7BB%7D%20&plus;%20B%29%29%20%26%3D%20x%20%5C%5C%20%5Coverline%7BB%7D%5Cbullet%20C%20%5Cbullet%281%29%20&plus;%20A%5Cbullet%5Coverline%7BB%7D%5Cbullet%281%29%20&plus;%20A%5Cbullet%20C%20%5Cbullet%281%29%20%26%3D%20x%20%5C%5C%20%5Coverline%7BB%7D%5Cbullet%20C%20&plus;%20A%5Cbullet%5Coverline%7BB%7D%20&plus;%20A%5Cbullet%20C%20%26%3D%20x%20%5C%5C%20%5Cend%7Balign*%7D)

The final formula is

![eq](https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%20C%20&plus;%20A%5Cbullet%5Coverline%7BB%7D%20&plus;%20A%5Cbullet%20C%20%26%3D%20x)

## Karnaugh Maps (K-Maps) 

Minimizing by hand can be cumbersome, but there are more automated ways to do
this. Karnaugh Maps (K-Maps) are one way to do this. It proceeds by building a
truth-table with groupings of variables, which helps to minimize the results
when forming a sum of products.

For example, we can rewrite the truth table from above as follows

|            | ![][not-B-not-C] | ![][not-B-C] | ![][B-C] | ![][B-not-C] |
|------------|------------------|--------------|-----------|--------------|
| ![][A]     | 1                | 1            | 1         | 0            |
| ![][not-A] | 0                | 1            | 0         | 0            |


[not-B-not-C]: https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%5Coverline%7BC%7D
[not-B-C]: https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%20C
[B-C]: https://latex.codecogs.com/gif.latex?B%5Cbullet%20C
[B-not-C]: https://latex.codecogs.com/gif.latex?B%5Cbullet%20%5Coverline%7BC%7D
[A]: https://latex.codecogs.com/gif.latex?A
[not-A]: https://latex.codecogs.com/gif.latex?%5Coverline%7BA%7D

Now we can group adjacent 1's in rows and columns.  For example, these two 1's
share A and not-B in common.

|            | ![][not-B-not-C] | ![][not-B-C] | ![][B-C] | ![][B-not-C] |
|------------|------------------|--------------|----------|--------------|
| ![][A]     | (1)              | (1)          | 1        | 0            |
| ![][not-A] | 0                | 1            | 0        | 0            |

And these two, share A and C in common

|            | ![][not-B-not-C] | ![][not-B-C] | ![][B-C] | ![][B-not-C] |
|------------|------------------|--------------|----------|--------------|
| ![][A]     | 1                | (1)          | (1)      | 0            |
| ![][not-A] | 0                | 1            | 0        | 0            |

And finally, these two share not-B and C in common

|            | ![][not-B-not-C] | ![][not-B-C] | ![][B-C] | ![][B-not-C] |
|------------|------------------|--------------|----------|--------------|
| ![][A]     | 1                | (1)          | 1        | 0            |
| ![][not-A] | 0                | (1)          | 0        | 0            |

The result is again the equation. 

![eq](https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%20C%20&plus;%20A%5Cbullet%5Coverline%7BB%7D%20&plus;%20A%5Cbullet%20C%20%26%3D%20x)

But this time, we don't have to minimize by hand, but instead seek out adjacent
truths. 

## Higher-Order K-Maps

We can do K-Maps with column/row labels of any power of 2, for example, this is
a 2x2 K-Map. We can minimize in the same way, but the key idea is that every
adjacent box shares a variable in common so that you can "cover" or reduce them
out. 

For example, we can minimize from the following table

|                  | ![][not-C-not-D] | ![][not-C-D] | ![][C-D] | ![][C-not-D] |
|------------------|------------------|--------------|----------|--------------|
| ![][not-A-not-B] | 1                | 0            | 0        | 0            |
| ![][not-A-B]     | 0                | 0            | 0        | 1            |
| ![][A-B]         | 0                | 1            | 1        | 0            |
| ![][A-not-B]     | 1                | 1            | 1        | 1            |

[not-C-not-D]: https://latex.codecogs.com/gif.latex?%5Coverline%7BC%7D%5Cbullet%5Coverline%7BD%7D
[not-C-D]: https://latex.codecogs.com/gif.latex?%5Coverline%7BC%7D%5Cbullet%20D
[C-not-D]: https://latex.codecogs.com/gif.latex?C%5Cbullet%20%5Coverline%7BD%7D
[C-D]: https://latex.codecogs.com/gif.latex?C%5Cbullet%20D
[not-A-not-B]: https://latex.codecogs.com/gif.latex?%5Coverline%7BA%7D%20%5Cbullet%20%5Coverline%20%7BB%7D
[not-A-B]: https://latex.codecogs.com/gif.latex?%5Coverline%7BA%7D%20%5Cbullet%20B
[A-not-B]: https://latex.codecogs.com/gif.latex?A%20%5Cbullet%20%5Coverline%7BB%7D
[A-B]: https://latex.codecogs.com/gif.latex?A%20%5Cbullet%20B
[A-D]: https://latex.codecogs.com/gif.latex?A%20%5Cbullet%20D
[not-B-not-C-not-D]: https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%5Coverline%7BC%7D%5Cbullet%5Coverline%7BD%7D
[not-A-B-C-not-D]: https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%5Coverline%7BC%7D%5Cbullet%5Coverline%7BD%7D

We can now "cover" the entire bottom row of this table with ![][A-not-B]. 


|                  | ![][not-C-not-D] | ![][not-C-D] | ![][C-D] | ![][C-not-D] |
|------------------|------------------|--------------|----------|--------------|
| ![][not-A-not-B] | 1                | 0            | 0        | 0            |
| ![][not-A-B]     | 0                | 0            | 0        | 1            |
| ![][A-B]         | 0                | 1            | 1        | 0            |
| ![][A-not-B]     | (1)              | (1)          | (1)      | (1)          |

Then there is a block of 4 which has ![][A-D] in common

|                  | ![][not-C-not-D] | ![][not-C-D] | ![][C-D] | ![][C-not-D] |
|------------------|------------------|--------------|----------|--------------|
| ![][not-A-not-B] | 1                | 0            | 0        | 0            |
| ![][not-A-B]     | 0                | 0            | 0        | 1            |
| ![][A-B]         | 0                | (1)          | (1)      | 0            |
| ![][A-not-B]     | 1                | (1)          | (1)      | 1            |

We can then wrap around to cover these with ![][not-B-not-C-not-D] in common


|                  | ![][not-C-not-D] | ![][not-C-D] | ![][C-D] | ![][C-not-D] |
|------------------|------------------|--------------|----------|--------------|
| ![][not-A-not-B] | (1)              | 0            | 0        | 0            |
| ![][not-A-B]     | 0                | 0            | 0        | 1            |
| ![][A-B]         | 0                | 1            | 1        | 0            |
| ![][A-not-B]     | (1)              | 1            | 1        | 1            |

Finally, only one does not have a pair to cover with it ![][not-A-B-C-not-D]. 

|                  | ![][not-C-not-D] | ![][not-C-D] | ![][C-D] | ![][C-not-D] |
|------------------|------------------|--------------|----------|--------------|
| ![][not-A-not-B] | 1                | 0            | 0        | 0            |
| ![][not-A-B]     | 0                | 0            | 0        | (1)          |
| ![][A-B]         | 0                | 1            | 1        | 0            |
| ![][A-not-B]     | 1                | 1            | 1        | 1            |

This leaves us with the following sum of products

![](https://latex.codecogs.com/gif.latex?%28A%5Cbullet%5Coverline%7BB%7D%29&plus;%28A%5Cbullet%20D%29%20&plus;%20%28%5Coverline%7BB%7D%5Cbullet%5Coverline%7BC%7D%5Cbullet%5Coverline%7BD%7D%29&plus;%28%5Coverline%7BA%7D%5Cbullet%20B%20%5Cbullet%20C%20%5Cbullet%5Coverline%7BD%7D%29)

## K-Maps with "Don't Cares!"

Finally, there are times when we have K-Maps where there are values that we
don't care about, labeled here as `X`. These can have either a 0 or 1, whichever
helps the minimization. 

|                  | ![][not-C-not-D] | ![][not-C-D] | ![][C-D] | ![][C-not-D] |
|------------------|------------------|--------------|----------|--------------|
| ![][not-A-not-B] | X                | 0            | 0        | 0            |
| ![][not-A-B]     | 1                | 0            | 0        | X            |
| ![][A-B]         | 1                | 1            | 1        | 1            |
| ![][A-not-B]     | 1                | 0            | 0        | 0            |

Here, we can cover these as such,

![](https://latex.codecogs.com/gif.latex?%28A%20%5Cbullet%20B%29%20&plus;%20%28%5Coverline%7BC%7D%5Cbullet%5Coverline%7BD%7D%29%20&plus;%20%28B%20%5Cbullet%20C%20%5Cbullet%20%5Coverline%7BD%7D%29)


## Building Logic Circuits out of Truth Tables

Let's return to the minimized sum of products from before.

![eq](https://latex.codecogs.com/gif.latex?%5Coverline%7BB%7D%5Cbullet%20C%20&plus;%20A%5Cbullet%5Coverline%7BB%7D%20&plus;%20A%5Cbullet%20C%20%26%3D%20x)

How can we turn this into a circuit? The structure of the equation itself
dictates this for us: it's an OR gate with subsequent AND gates.

![](/imgs/logic/circuit2.png)

Note that an OR with multiple inputs can be written with multiple OR gates due
to the communicative rule.


## Higher Level Gates: Combination Logic

It should be clear by now that all we really need is AND and OR gates, plus
inversion, but building up large, complex circuits with such simple gates is
slow and complicated. Just like in normal programming, we can use none
combinations to build in more complex logic, much like a library call. These are
called **Combination Logic** circuits. 

Some of these are found in the book, here we discuss
* Multiplexors (or mux)
* Registers (storage gates)
* Arithmetic unit (ALU)

## MUX'es : multiplexor selector logic

A mux (or a multiplexor) is a select combination logic. The simplest version, a two-way mux,
chooses between two input signals for the output based on a selector signal.

![](/imgs/logic/two-way-mux.png)

In the two-way mux, the signal is either high or low (1 or 0), and based on that
value, either input A or B is selected to continue onto output C. We can
multiplex over any input size as long as we have enough selector bits to
enumerate our choices. For example, this is an eight-way mux

![](/imgs/logic/eight-way-mux.png)

Note that we need 3 selector signals, since `2^3` options to select between 8
inputs. 

The *width* of the multiplexor describes how many bits each of the input wires
carries. For example, we may describe a 32-bit-wide, two-way mux:

![](/imgs/logic/32-wide-mux.png)

This can be composed of many 2-bit-wide, two-way multiplexors where the selector
each selects each of the bits from one of the inputs.  Finally, it's possible to
produce a multi-bit-wide, multi-way multiplexor by combining both of these
reasoning, which is how, for example, when we provide a register number in a
R-Type instructor's binary representation, we can select input from one of the
registers.


The details on how multiplexors are built using logic gates can be found in the book.

