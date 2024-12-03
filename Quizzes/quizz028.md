# Question




# code
```.py

import requests
from matplotlib import pyplot as plt
import numpy as np

# Server IP
server_ip = "192.168.4.137"

# Fetch data from the server
try:
    response = requests.get(f"http://{server_ip}/readings")
    response.raise_for_status()  # Check for HTTP errors
    readings = response.json()["readings"][0]  # Adjust indexing based on actual response
except Exception as e:
    print("Error fetching data:", e)
    exit()

# Filter sensor data
values = []
for r in readings:
    if r["sensor_id"] == 11:
        values.append(r["value"])

# Plot raw values
plt.figure(figsize=(10, 6))
plt.plot(values, label="Raw Sensor Data")
plt.title("Raw Temperature Readings")
plt.xlabel("Time")
plt.ylabel("Temperature")
plt.legend()
plt.grid()
plt.show()

# Define moving average function
def moving_average(windowSize: int, y: list) -> list:
    y_smoothed = []
    for i in range(0, len(y) - windowSize):
        y_section = y[i : i + windowSize]
        y_average = sum(y_section) / windowSize
        y_smoothed.append(y_average)
    return y_smoothed

# Apply moving average
y = values[600:1600]
temp_y = moving_average(50, y)
x = [i for i in range(0, len(temp_y))]

# Linear fit
m, b = np.polyfit(x, temp_y, deg=1)
x_linear = [min(x), max(x)]
y_linear = [m * x_linear[0] + b, m * x_linear[1] + b]

# Quadratic fit
a, b, c = np.polyfit(x, temp_y, deg=2)
quadratic_model = [a * i**2 + b * i + c for i in x]

# Debugging: Print coefficients
print(f"Quadratic coefficients: a={a}, b={b}, c={c}")

# Rescale x for better visibility of curvature
x_scaled = [i / max(x) for i in x]
a_scaled, b_scaled, c_scaled = np.polyfit(x_scaled, temp_y, deg=2)
quadratic_model_scaled = [a_scaled * i**2 + b_scaled * i + c_scaled for i in x_scaled]

# Plotting
plt.figure(figsize=(12, 8))

# Linear fit plot
plt.subplot(2, 1, 1)
plt.plot(temp_y, color="blue", linewidth=2, label="Smoothed Data")
plt.plot(x_linear, y_linear, label=f"Linear Fit (m={m:.2f}, b={b:.2f})", linestyle="--")
plt.title("Smoothed Temperature Data with Linear Fit")
plt.ylabel("Temperature")
plt.legend()
plt.grid()

# Quadratic fit plot
plt.subplot(2, 1, 2)
plt.plot(temp_y, color="blue", linewidth=2, label="Smoothed Data")
plt.plot(x, quadratic_model, label="Quadratic Fit (Original)", linestyle="--")
plt.plot(x, quadratic_model_scaled, label="Quadratic Fit (Scaled)", linestyle="-.")
plt.title("Smoothed Temperature Data with Quadratic Fit")
plt.xlabel("Time")
plt.ylabel("Temperature")
plt.legend()
plt.grid()

plt.tight_layout()
plt.show()



```
