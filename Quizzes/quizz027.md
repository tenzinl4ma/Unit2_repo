# Question
![Screenshot 2024-11-18 at 10 14 15 PM](https://github.com/user-attachments/assets/24a733b5-c60d-4eaf-bfd0-65d608afbfa0)



# Code
```.py
def sort_dict(in_dict):
    def sort_key(item):
        value = item[1]
        if isinstance(value, int):
            return value
        elif isinstance(value, str):
            return len(value)
        return 0

    sorted_items = sorted(in_dict.items(), key=sort_key)
    return dict(sorted_items)

test1 = {'apple': 5, 'banana': 2, 'orange': 8, 'grape': 1}
test2 = {'python': 3, 'java': 8, 'c++': 5, 'javascript': 2}
test3 = {'apple': 'red', 'banana': 2, 'orange': 'orange', 'grape': 1, 'kiwi': 'brown', 'pear': 8}

print(sort_dict(test1))  # {'grape': 1, 'banana': 2, 'apple': 5, 'orange': 8}
print(sort_dict(test2))  # {'javascript': 2, 'python': 3, 'c++': 5, 'java': 8}
print(sort_dict(test3))  # {'grape': 1, 'banana': 2, 'apple': 'red', 'kiwi': 'brown', 'pear': 8, 'orange': 'orange'}

```

# Evidence
<img width="908" alt="Screenshot 2024-12-01 at 9 46 31 PM" src="https://github.com/user-attachments/assets/27f0fafa-a6ab-40af-aba6-0b2755e70cd6">
