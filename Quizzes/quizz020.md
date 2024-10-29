# This is the graphing program using the matplotlib with tool pyplot


# Question



# Code
```.py

from matplotlib import pyplot as tu

x, y = [], []
start = -10
step = 0.01

# Generating x and y values for the parabola
for i in range(int(20 / step)):
    x_val = start + i * step
    x.append(x_val)
    y.append(2 * (x_val + 5) ** 2)

# Define line x and y values for additional plot (e.g., a vertical line)
linex = [-5, -5]
liney = [0, max(y)]

# Plotting the parabola
tu.plot(x, y, linewidth=2, color="red", label="Parabola")
tu.plot(linex, liney, linewidth=2, color="blue", linestyle="--", label="Vertical line")

tu.xlabel("x variable")
tu.ylabel("y variable")
tu.title("Parabola Plot")
tu.legend()
tu.ylim(0,100)
tu.show()
print(y)


```
# Evidence
<img width="663" alt="Screenshot 2024-10-29 at 5 58 37 PM" src="https://github.com/user-attachments/assets/75abe989-7fa1-4d09-9eea-caab2eb82cda">


