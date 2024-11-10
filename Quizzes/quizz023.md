# a program that produces n random values from the equation below, where m and s are the other inputs of the function 

# Question
<img width="1227" alt="Screenshot 2024-11-10 at 1 56 26 PM" src="https://github.com/user-attachments/assets/03ea9e8c-2104-4093-ac93-8f218d510ff5">

# Coode
```.py

import random

random.seed(1234)

def grapher(n, m, s):
    for i in range(n):
        x = random.randint(0, 100)
        y = x ** (0.5 * ((m / s) ** 2))
        print(f"{x}      {y:.3g}")
grapher(5, 3, 2)

```

# Evidence

![Screenshot 2024-11-10 at 1 55 52 PM](https://github.com/user-attachments/assets/bbbf47f5-3e98-43ef-99b7-350806701380)
