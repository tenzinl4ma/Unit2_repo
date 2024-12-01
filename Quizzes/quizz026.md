# Question
![Screenshot 2024-11-18 at 10 12 54 PM](https://github.com/user-attachments/assets/799a9894-3175-464c-940d-1f67e23a0618)

# Code 
```.py
def dicttion(dictt):
    newdict = {}
    for key, value in dictt.items():
        if value in newdict:
            newdict[value].append(key)
        else:
            newdict[value] = [key]
    for key, value in newdict.items():
        if len(value) == 1:  
            newdict[key] = value[0]
    print(newdict)
dicttion(dictt={'q1': True, 'q2': False, 'q3': True})
dicttion(dictt={'bob': 26, 'alice': 30, 'carl': 40})
```

# Evidence

<img width="800" alt="Screenshot 2024-12-01 at 8 34 56 PM" src="https://github.com/user-attachments/assets/9f533e00-2d4f-4e2f-b840-3442a53af238">
