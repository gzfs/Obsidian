*Algorithm* is any well-defined computational procedure that takes some value, or set of values, as input and produces some value, or set of values, as output in a finite amount of time. An *Algorithm* is thus a sequence of computational steps that transform the input into the output.

*Instance* of a problem consists of the input needed to compute a solution to the problem.

*Exponentiation* ($x^n$) is normally not calculated in Constant Time unless it's base is 2 i.e. $2^{n}$. Computers perform *Bit-Shifting* in Constant Times and this operation becomes invalid if the Bit Shift fails to fit in a single word.
### Insertion Sort
**Input:** A sequence of *n* numbers $a_{1}, a_{2}, a_{3} ... a_{n}$.
**Output:** A permutation  $a^{'}_{1}, a^{'}_{2}, a^{'}_{3} ... a^{'}_{n}$ of the input sequence such that $a^{'}_{1} \le a^{'}_{1} \le a^{'}_{1} \le ... a^{'}_{n}$

