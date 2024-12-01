# Question
![Screenshot 2024-11-18 at 10 14 15 PM](https://github.com/user-attachments/assets/24a733b5-c60d-4eaf-bfd0-65d608afbfa0)



# Code
```.py
def diction(dictt):
    items = list(dictt.items())
    for i in range(len(items)):
        for j in range(i + 1, len(items)):
            if items[i][1] > items[j][1]: 
                items[i], items[j] = items[j], items[i]  
    newdict = dict(items)
    print(newdict)
diction(dictt={'c':3,'d':4,'a':1,'b':2})
diction(dictt= {'apple':5, 'banana': 2, 'orange': 8, 'grape': 1})
diction(dictt={'python': 3, 'java': 8, 'c++': 5, 'javascript': 2})
diction(dictt={'c': 3, 'd': 4, 'a': 1, 'b': 2})
```

# Evidence
<img width="908" alt="Screenshot 2024-12-01 at 9 46 31 PM" src="https://github.com/user-attachments/assets/27f0fafa-a6ab-40af-aba6-0b2755e70cd6">
