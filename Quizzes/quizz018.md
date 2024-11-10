# The function that produces the table of Truth for 3 inputs, add a column for the boolean equation
AB+(not B)+not(CB)


# Question
<img width="1237" alt="Screenshot 2024-11-10 at 0 43 49 PM" src="https://github.com/user-attachments/assets/95b52977-2f16-42bc-9046-f4badb678064">


# Code
```.py

print("Truth Table")
print(f"A B C  result")
def truth():
     for A in [0,1]:
          for B in [0,1]:
               for C in [0,1]:
                    part1=A and B
                    part2=not B
                    part3=not(C and B)
                    resultt=part2 or part1 or part3
                    print(f"{A} { B} {C}   {int(  resultt)}")
truth()


```
# Evidence
![Screenshot 2024-11-10 at 0 26 38 PM](https://github.com/user-attachments/assets/f49b975f-9037-4e2d-a217-c3370be1b4de)
