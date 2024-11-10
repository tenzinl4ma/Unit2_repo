# The following program generate the truth table

## Flowchart

<img width="612" alt="Screenshot 2024-09-09 at 14 14 01" src="https://github.com/user-attachments/assets/fa503135-0af1-4040-8c66-68f2ca213190">


## question 
<img width="775" alt="Screenshot 2024-10-22 at 9 35 41 AM" src="https://github.com/user-attachments/assets/141ed6b3-5d23-45f9-9606-f557d489300c">



## Code
```.py
def get_truth():
    headers = "A B C"
    table = []
    for A in [0, 1]:
        for B in [0, 1]:
            for C in [0, 1]:
                table.append(f'| {A} | {B} | {C} |')


    result = f"| {headers} |\n" + "\n".join(table)
    return result
table = get_truth()
print(table)


```


## Proof

<img width="618" alt="Screenshot 2024-10-22 at 9 37 32 AM" src="https://github.com/user-attachments/assets/fc47f2ef-c01a-4b4c-b24e-4309217a9fe3">




