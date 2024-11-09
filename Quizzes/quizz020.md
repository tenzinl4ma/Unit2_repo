# This is the graphing program using the matplotlib with tool pyplot


# Question

<img width="690" alt="quiz_022_slide" src="https://github.com/user-attachments/assets/568348ea-cb48-4db7-a890-66ce264678bb">


# Code
```.py

from matplotlib import pyplot as tu

x, y = [], []
start = -10
step = 0.01


for i in range(int(20 / step)):
    x_val = start + i * step
    x.append(x_val)
    y.append(2 * (x_val + 5) ** 2)


linex = [-5, -5]
liney = [0, max(y)]


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


