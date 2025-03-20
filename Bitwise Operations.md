*Bitwise Operations* are used to manipulate Binary Numbers. These operations allow us to perform various operations efficiently.

| Operation   | Symbol | Usage                                             |
| ----------- | ------ | ------------------------------------------------- |
| NOT         | ~      | Bit Inversion                                     |
| AND         | &      | Masking and checking the presence of certain Bits |
| OR          | \|     | Combining or Merging Bits                         |
| XOR         | ^      | Toggling and Swapping Bits                        |
| Left Shift  | <<     | Multiplying the Number by 2                       |
| Right Shift | >>     | Dividing the Number by 2                          |
To extract the LSB of a Binary Number: $N\bmod2$
To get the Next Significant Bit: Divide the number by 2 and take the floor of the result.

```
Result after shifting left(or right) too much is undefined Right shifting operations on negative values are undefined Right operand in shifting should be non-negative, otherwise the result is undefined The & and | operators have lower precedence than comparison operators
```

- Print Binary Representation.
	```python
	def pr_binary(num: int):
	    for i in range(10, -1, -1):
	        print((num >> i) & 1, end="")
```
- Check if an ith bit has been set.
	```python
	def is_set(num: int):
	    for i in range(10, -1, -1):
	        print("Set" if (num & (1 << i)) != 0 else "Not Set")
```
- Counting the Number of Set Bits.
	```python
	def set_count(num: int):
		count = 0
	    for i in range(10, -1, -1):
	       if (num & (1 << i)) != 0:
		       count += 1
		return count
```
- Check if the Number is Power of Two.
	```python
	def is_power(num: int):
		return num and not (num & (num - 1))
```
- Lowercase to Uppercase and Vice Versa
	```python
	chr(ord('C') | ord(' '))
	chr(ord('a') &(~(1 << 5)))
	chr(ord('A') | 1 << 5)
```
- Position of the Letter wrt. 26
	```python
 (‘A’ & 31) returns position 1
 (‘c’ & 31) returns position 3
```
- XOR Swapping
	```python
	a = a ^ b
	b = b ^ a
	a = a ^ b
```
- Clearing LSB up to ith Bit
	```python
	# Clearing LSB
	i = 4
	a = 59
	b = a & (~((1 << (i + 1)) - 1))
```
- Clearing MSB up to ith Bit
```python
# Clearing MSB
i = 4
a = 59
b = a & ((1 << (i + 1)) - 1)
```
- Other Use Cases
	```python
Set union A | B
Set intersection A & B
Set subtraction A & ~B
Set negation ALL_BITS ^ A or ~A
Set bit A |= 1 << bit
Clear bit A &= ~(1 << bit)
Test bit (A & 1 << bit) != 0
Extract last bit A&-A or A&~(A-1) or x^(x&(x-1))
Remove last bit A&(A-1)
Get all 1-bits ~0==-1
```
- Two's Complement
	```python
 Num= num1-num2;
 Num= (num1)+((~num2)+1)
```
- Gray Code
	```python
	def gray_code(n):
	    return [(i ^ (i >> 1)) for i in range(1 << n)]
```
- Gray to Binary
	```python
	def gray_to_binary(g):
	    n = 0
	    while g:
	        n ^= g
	        g >>= 1  # Right shift g
	    return n
```
