# Question
<img width="974" alt="Screenshot 2024-12-01 at 9 51 28 PM" src="https://github.com/user-attachments/assets/208f3378-3a66-4d6b-bd4e-932173250116">



# Code
```.py


import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(-4, 4, 500)
y = np.linspace(-4, 4, 500)

y1 = x**2
y2 = -x**2
x1 = y**2
x2 = -y**2

plt.figure(figsize=(8, 6))
plt.plot(x, y1, label="Parabola 1 (x-axis)", color="red")
plt.plot(x, y2, label="Parabola 2 (x-axis)", color="blue")
plt.plot(x1, y, label="Parabola 3 (y-axis)", color="black")
plt.plot(x2, y, label="Parabola 4 (y-axis)", color="purple")


plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.title("Four Parabolas Aligned with Axes")
plt.axhline(0, color="gray", linewidth=0.5, linestyle="--")
plt.axvline(0, color="gray", linewidth=0.5, linestyle="--")
plt.legend()
plt.grid(True)


plt.show()


```

# Evidence



