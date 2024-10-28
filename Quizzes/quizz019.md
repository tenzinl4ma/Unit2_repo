




## Below are the question
<img width="961" alt="Screenshot 2024-10-28 at 7 29 27 PM" src="https://github.com/user-attachments/assets/52178bb4-eae0-43b4-afc1-cbe54cb5f545">

## This is the code
```.py


from matplotlib import pyplot as plt
import random

from Project.validation import color

random.seed(1234)
#when inputs have values, these are default
def produce(n=5,m=3,s=2):
    x,y=[],[]
    for _ in range(n):
        x.append(random.randint(0,100))
        y.append(x[-1]**(0.5*(m/s)*2))
    return x,y
x,y=produce(n=100)
plt.plot(x,y)
plt.title("Tenwang")
plt.xlabel("this is the x label")
plt.ylabel("this is the y label")

plt.show()

```
## Evidence
<img width="643" alt="Screenshot 2024-10-28 at 7 37 04 PM" src="https://github.com/user-attachments/assets/4830f61a-b598-41a5-b252-33be24762370">
