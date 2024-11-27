# Unit 2 Distributed Weather Station for ISAK

## Problem Definition

In the R2-14 house, members tend to sleep late around 1 or 2 AM, even when they are not studying or engaged in any particular activity. This late sleep pattern often leads to waking up late in the morning, causing some to miss breakfast or even classes. As a result, their overall productivity and focus during the day are negatively affected.

After discussing the problem with the residents, it became clear that the root cause might not only be related to personal habits but could also be influenced by environmental factors such as temperature, humidity, and air pressure. Although these factors are not always physically noticeable, they might have an impact on sleep quality, leading to the late bedtimes and poor morning routines observed.

The residents need a way to monitor and track these environmental conditions to determine if they are affecting their sleep and, if so, how they can improve their environment to ensure better sleep quality.

---

## Proposed Solution

The primary goal is to monitor the **temperature**, **humidity**, and **pressure** within the R2-14 house, particularly the rooms where the residents sleep. These environmental factors can have a significant impact on sleep quality, which is essential for maintaining overall well-being and productivity throughout the day. The proposed solution will collect data on these factors during the night and analyze the trends to identify if a correlation exists between environmental conditions and poor sleep.
### Hardware Components
To implement this system, two sensors will be used:

- **DHT11 Sensor**: This is a widely used, low-cost sensor that measures temperature and humidity. It is sufficient for the intended application, offering a temperature range of **0°C to 50°C** and a humidity range of **20% to 90%**, which is appropriate for indoor environments like bedrooms. The DHT11 provides a simple and cost-effective way to monitor these two critical environmental variables. Though other more accurate sensors (like the DHT22) exist, the DHT11 offers the best balance between cost and precision for this project.
  
- **BMP180 Sensor**: This sensor measures atmospheric pressure and provides valuable data regarding air pressure variations in the room. Fluctuations in atmospheric pressure can impact the quality of sleep by affecting the overall comfort of the sleeping environment. The BMP180 is compact and reliable, offering a pressure measurement range of 300 to 1100 hPa, which is ideal for indoor monitoring.

The sensors will be interfaced with an **Arduino UNO microcontroller**. The Arduino UNO is a cost-effective, open-source microcontroller that provides sufficient processing power for the task. It offers serial communication capabilities, which are compatible with both the DHT11 and BMP180 sensors, making it an ideal choice for data collection.

### Software Implementation

The software solution involves using **Python**, a versatile programming language that is well-suited for data collection, processing, and analysis. The Python IDE **PyCharm** will be used for writing and testing the scripts. The **Arduino IDE** will be used for programming the microcontroller to interface with the sensors.

The steps for data collection and analysis are as follows:
1. **Data Collection**: The Arduino will collect data from the DHT11 and BMP180 sensors at regular intervals (e.g., every 30 minutes or hourly) over a period of 48 hours. The data will include temperature, humidity, and pressure readings.
  
2. **Data Storage**: The collected data will be stored temporarily in a **CSV file**. CSV format is simple and widely used, making it easy to handle, visualize, and upload later.

3. **Data Analysis and Visualization**: Once the data is collected, **Python’s matplotlib** library will be used to visualize the temperature, humidity, and pressure trends over time. Various plots will be generated, such as line graphs showing how these variables fluctuate during the night.

4. **Correlational Analysis**: The collected data will be analyzed to check if there are significant correlations between the environmental factors (temperature, humidity, pressure) and the residents' sleep patterns. If these factors are found to affect sleep, the residents will be able to adjust their environment accordingly.

### Benefits and Outcome

By continuously monitoring and analyzing the room’s environmental conditions, the residents will be able to understand if temperature, humidity, or pressure is affecting their sleep. If the data shows that the temperature is too high or low, they can adjust the thermostat to optimize the sleep environment. Similarly, if the humidity is too high or low, they can invest in a humidifier or dehumidifier to maintain the optimal humidity levels for a good night’s rest.

If pressure fluctuations are found to be a factor, the residents can explore other solutions, such as improving ventilation or sealing the room to prevent external air pressure variations. The data will empower the residents to make informed decisions about their sleep environment, leading to improved sleep quality and better overall health.

This system will not only help in identifying sleep-related issues but can also be a useful tool for future residents of Room 20C or other rooms in the house, as they can benefit from the environmental data to ensure their own sleep quality and comfort.