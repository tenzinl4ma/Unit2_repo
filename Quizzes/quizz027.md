# Question
![Screenshot 2024-11-18 at 10 14 15 PM](https://github.com/user-attachments/assets/24a733b5-c60d-4eaf-bfd0-65d608afbfa0)



# Code
```.py
def sorting_key(item):
    value = item[1]
    if isinstance(value, int):  
        return (0, value)  
    elif isinstance(value, str):  
        return (1, len(value))  
    else:  
        return (2, 0)  
def sort_dict(test):
    # Sort dictionary items using the custom sorting key
    sorted_items = sorted(test.items(), key=sorting_key)
    sorted_dict = dict(sorted_items)
    print(sorted_dict)
print(sort_dict({'python': 3, 'java': 8, 'c++': 5, 'javascript': 2})) 
print(sort_dict({'apple': 'red', 'banana': 2, 'orange': 'orange', 'grape': 1, 'kiwi': 'brown',
                 'pear': 8}))  
print(sort_dict({'apple': 5, 'banana': 2, 'orange': 8, 'grape': 1}))  


```

# Evidence
<img width="908" alt="Screenshot 2024-12-01 at 9 46 31 PM" src="https://github.com/user-attachments/assets/27f0fafa-a6ab-40af-aba6-0b2755e70cd6">
