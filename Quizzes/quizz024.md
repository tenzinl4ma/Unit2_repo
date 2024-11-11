# A grapher of data form the dictionary

# Question

![Screenshot 2024-11-11 at 5 06 44 PM](https://github.com/user-attachments/assets/5cf1c4f4-f72e-46c5-8f0b-b751ceb70888)


# Code
```.py
import matplotlib.pyplot as plt

# Define the data dictionary
data = {
    'x': [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19],
    'y': [24, 1, 2, 25, 26, 21, 23, 34, 49, 2, 19, 32, 7, 17, 36, 7, 45, 28, 40, 46]
}


data["title"] = "quiz_data_science"

plt.plot(data['x'], data['y'], color="red", marker='o', linestyle='-')
plt.title(data["title"])
plt.xlabel("X values")
plt.ylabel("Y values")
plt.show()




````



# Evidence 
<img width="683" alt="Screenshot 2024-11-11 at 5 05 47 PM" src="https://github.com/user-attachments/assets/9e5baa18-5000-4091-af51-af6685b5b923">
