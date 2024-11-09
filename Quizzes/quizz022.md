#  a program that ① show the graph and ②create a linear (H_model = m*t+b) for the data below:


# Question

<img width="691" alt="quiz_024_slide" src="https://github.com/user-attachments/assets/b9176a48-019b-4e00-b2ce-b60fceefb3e9">

# Code
```.py
import numpy as np
import matplotlib.pyplot as plt


h = [57.0, 56.0, 57.0, 56.0, 55.0, 55.0, 54.0, 54.0, 54.0, 53.0, 53.0, 54.0,
     53.0, 53.0, 52.0, 52.0, 51.0, 51.0, 51.0, 50.0, 50.0, 49.0, 50.0, 49.0,
     49.0, 48.0, 49.0, 49.0, 48.0, 48.0, 48.0, 49.0]

t = np.array([i for i in range(0, len(h) * 10, 10)])  # Convert `t` to a numpy array
plt.scatter(h, t, color="red", label="Actual Data")
m, b = np.polyfit(h, t, 1)
t_model = m * np.array(h) + b

plt.plot(h, t_model, color="blue", label=f"Model: t = {m:.2f}*h + {b:.2f}")
plt.xlabel("Height/Measurement (h)")
plt.ylabel("Time (minutes)")
plt.legend()

plt.show()


```

# Evidence
![Screenshot 2024-11-10 at 1 03 43 AM](https://github.com/user-attachments/assets/1e695696-eda7-40d8-a9eb-16a143391030)


