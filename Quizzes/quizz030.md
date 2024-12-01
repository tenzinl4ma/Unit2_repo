# Question
<img width="1003" alt="Screenshot 2024-12-01 at 9 52 52 PM" src="https://github.com/user-attachments/assets/1cea5757-24c9-4512-bb51-b06f1a92c236">


# Code
```.py
import requests
import matplotlib.pyplot as plt
from matplotlib.gridspec import GridSpec

server_ip = "192.168.4.137"
response = requests.get(f"http://{server_ip}/readings")
data = response.json()

readings = data['readings'][0]
temp = []
hum = []

# Collect temperature and humidity data
for r in readings:
    if r['sensor_id'] == 11:
        value = float(r['value'])
        temp.append(int(value))
    elif r['sensor_id'] == 10:
        value = float(r['value'])
        hum.append(int(value))

print(f"this is the length of temp: {len(hum)} and this is the length of hum: {len(temp)}")

# Create figure and grid spec
fig = plt.figure(figsize=(10, 10))
grid = GridSpec(nrows=3, ncols=4, figure=fig)
plt.subplots_adjust(hspace=0.5)

# First subplot for humidity data (now the first one)
box1 = fig.add_subplot(grid[0:3, 1:3])
box1.plot(hum, label="Difference", color='orange')
box1.set_title("Difference")
box1.set_ylabel("Difference")

# Second subplot for the difference between humidity and temperature (middle one)
box2 = fig.add_subplot(grid[1, 0])
hum = hum[:len(temp)]  # Ensure both lists have the same length
difference=[]
for i in range(min(temp),len(hum)):
    diff= temp[i]-hum[i]
    difference.append(diff)



box2.plot(difference, label="humididty", color='green')
box2.set_title("Humidity")
box2.set_ylabel("Difference (°C)")

# Third subplot for temperature data (now the last one)
box3 = fig.add_subplot(grid[1, 3])
box3.plot(temp, label="Temperature")
box3.set_title("Temperature")
box3.set_ylabel("Temp (°C)")

# Show plots
plt.show()
```
Evidence
<img width="634" alt="Screenshot 2024-11-27 at 1 02 16 PM" src="https://github.com/user-attachments/assets/e2c7dcc7-c4eb-469b-98a0-fc19dbeb17d7">
