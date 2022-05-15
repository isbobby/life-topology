### Sequence
> [!Definition] 
> A **sequence** is a function whose domain is either all the integers between two integers (finite sequence) or all the integers greater than or equal to an integer (infinite sequence)

### Summation
> [!Summation Notation] 
> Summation sequence $\sum_{k=m}^{n} a^{k}$ contains upper limit $n$, lower limit $m$ where $k$ is the index of the summation sequence.

### Production Notation
> [!Product Notation]
> Production notation $\prod_{k=m}^{n} a_{k}$ contains upper limit $n$, lower limit $m$ and $k$ is the index of the product sequence

### Properties of Summations and Products
**Summing of summation sequences**
$$\sum_{k=m}^{n} a_{k} + \sum_{k=m}^{n} b_{k} = \sum_{k=m}^{n} (a_{k} + b_{k})$$

**Distributive law for summation sequences**
$$c \times \sum_{k=m}^{n} a_{k} = \sum_{k=m}^{n} (c \times a_{k})$$

**Product of two product sequences**
$$\prod_{k=m}^{n} a_{k} \times \prod_{k=m}^{n} b_{k} = \prod_{k=m}^{n} (a_{k} \times b_{k})$$

### Change of Variables in Sequences
The limits and index of a summation sequence can be replaced and still produce the same result. The procedure of doing so is - define a change of variable, then calculate the new lower and upper limits, and lastly calculate the new general term of the summation.

1. Given a sequence, define new variable
	
	$\sum_{1}^{6}{k+1}$, change of variable: $j = k + 1$

2. Calculate new upper and lower limits
	- when $k = 1$, $j = 1 + 1  = 2$
	- when $k = 6$, $j = 6 + 1  = 7$

3. Replace the general term, here, the new term will be $j$ since $k + 1 = j$

4. The new limits and general term results in a difference sequence which produces the same result
	
	$\sum_{1}^{6}{k+1} = \sum_{2}^{7}{j}$

### Factorial and "n choose r" Notation
>[!Factorial]
>$n!$ or n factorial is defined to be the product of all the integers from 1 to n

>[!n choose r]
>The "n choose r" notation represents the number of subsets of size r that can be chosen from a set with n elements
>$${n \choose r} =\frac{n!}{r!(n-r)!}$$

### Application -  Converting from Base 10 to Base 2
Conversion of an integer from base 10 to base 2 can be done by repeatedly dividing an integer by 2, and use the remainder of each division to determine the coefficients of powers.

For example, 38 can be repeatedly divided by 2 in the following way
1. $38 = 2 \times 19$ -  38 can be represented by two 19s
2. $19 = 2 \times 9 + 1$ 19 can be represented by two 9 + 1
3. $9 = 2 \times 4 + 1$ 9 can be represented by two 4 + 1
4. $4 = 2 \times 2 + 0$ 
5. $2 = 2 \times 1 + 0$
6. $1 = 2 \times 0 + 1$

The first division represents the coefficient of $2^0$, the remainder of $n^{th}$ division represents the coefficient of $2^{n-1}$. For example, 38 contains two 19s (see 1), and one 19 contains two 9s plus 1. Since 38 has two 19s, then 38 contains four 9s plus $2^1$.