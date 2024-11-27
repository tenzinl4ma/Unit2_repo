
# Question 
<img width="1005" alt="Screenshot 2024-11-27 at 9 40 29 AM" src="https://github.com/user-attachments/assets/48a0fa88-deb7-444a-8b5c-44362b2c3137">


# code
```.py
import requests
from matplotlib import pyplot as plt
import matplotlib
plt.style.use("ggplot")
matplotlib.use('MacOSX')

# this is the server ip
server_ip = "192.168.4.137"

# Fetching the data from server
response = requests.get(f'http://{server_ip}/readings')
data = response.json()
readings = data['readings'][0]  # Assuming data is nested this way

# Extract unique sensor IDs
ids = list(set(r['sensor_id'] for r in readings))

# Organize data by sensor ID
sensor_data = {sensor_id: [] for sensor_id in ids}
for r in readings:
    sensor_data[r['sensor_id']].append(float(r['value']))

# Check the structure of the data
print(sensor_data)

# Plot the data
plt.figure(figsize=(10, 8))

# Temperature (sensor_id 11)
plt.subplot(3, 1, 1)
plt.ylabel('Temp (°C)')
plt.plot(sensor_data[11], color="green", label="Temperature")
plt.legend()

# Pressure (sensor_id 12)
plt.subplot(3, 1, 2)
plt.ylabel('Pressure (kPa)')
plt.plot(sensor_data[12], color="red", label="Pressure")
plt.legend()

# Average plot (example: average of all sensor readings for simplicity)
average_readings = [sum(values) / len(values) for values in zip(*sensor_data.values())]
plt.subplot(3, 1, 3)
plt.ylabel('Average')
plt.plot(average_readings, color="yellow", label="Average Readings")
plt.legend()

plt.tight_layout()
plt.show()



```
# Evidence
<img width="996" alt="Screenshot 2024-11-27 at 9 42 29 AM" src="https://github.com/user-attachments/assets/65a34225-f691-4370-8cff-c54b12d528bc">


