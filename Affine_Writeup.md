# Affine

Category: Cryptography, 200 points

# Description

> We have intercepted an encoded **Affine cipher**. Can you decrypt it for us?

**N=128**, what are the possible values for a?
The first three values in the ciphertext correspond to the first three letters of the flag format.

`12, 124, 95, 84, 43, 19, 124, 12, 8, 43, 54, 19, 26`

A list of numbers was given to us

# Solution

Since our N equals 128 we can assume that the numbers correspond to **ASCII** values.

The numbers they give us are the encrypted ASCII values of the flag

We know that the flag format is c3t{f14g} so the 4th and last number correspond to the open and closing curly bracket ASCII values

Since we have known plaintext values we can caculate the values of a & b

> **y = ax + b** this is the equation for the Affine encryption whereby **y = encrypted text** & **x = plaintext**.

```
26 = a(125) + b  for "}"

84 = a(123) + b  for "{"
```

Using a simple system of equations, we can calculate the value of a.

```
70 = 2a

a = 70/2
```

From there we can plug in the value of a into either of the equations and calculate the value of b.

> **Remember to follow proper modular arithmetic rules**

A handy calculator if you are lazy:
> Modular multiplicative inverse - https://www.extendedeuclideanalgorithm.com/calculator.php?mode=2&a=0&b=0
 
Next we can plug in the values of a and b into the equation and solve for x to make decryption easier.

```
b = 3

35^-1(y-3) = x

11(y - 3) = x
```

Finally, we have our equation, then we can write a small python script to run through the values and decrypt the entire thing for us.

```
x = 12, 124, 95, 84, 43, 19, 124, 12, 8, 43, 54, 19, 26

for i in range(len(x)):

	print(chr((11 * (int(x[i])-3)) % 128), end="")
```

Output:

`c3t{803c7810}`






 

