---
title: Computer Number Systems
layout: default
---

# {{page.title}}

## Base 10

Before we talk about how computer numbers work, we have to talk about how our base-10 numbers work, something you may have forgotten a long time ago.

Take a number like 1531. We can break down this numbers as follows:

$$ 1*10^3 + 5*10^2 + 3*10^1 + 1*10^0 $$

Each digit is simply a weight multiplied by the power of some *base*.
Since our base is 10, we have 10 digits, from 0-9, and we can represent every integer this way.

## Base 2

Base 2, or binary, is a system with only two digits: 0 and 1. Each digit is multiplied by a power of two.

For example, we can convert 27 (in base 10) to a binary number by adding up powers of two.


$$
\begin{align}
27_{10} &= 16 + 8 + 2 + 1 \\
	&= 1 * 2^4 + 1*2^3 + 0*2^2 + 1*2^1 + 1*2^0 \\
	&= 11011_2
\end{align}
$$


Note that the subscript of a number denotes what base it is written in.	

## Adding

## Converting between bases

