# Unit 2 Distributed Weather Station for ISAK
___
### Criteria A: Planning


## Problem Definition

In the R2-14 house, members tend to sleep late around 1 or 2 AM, even when they are not studying or engaged in any particular activity. This late sleep pattern often leads to waking up late in the morning, causing some to miss breakfast or even classes. As a result, their overall productivity and focus during the day are negatively affected.

After discussing the problem with the residents, it became clear that the root cause might not only be related to personal habits but could also be influenced by environmental factors such as temperature, humidity, and air pressure. Although these factors are not always physically noticeable, they might have an impact on sleep quality, leading to the late bedtimes and poor morning routines observed.

The residents need a way to monitor and track these environmental conditions to determine if they are affecting their sleep and, if so, how they can improve their environment to ensure better sleep quality.

---

## Proposed Solution
Considering the client requirements, an adequate solution includes a low-cost sensing device for humidity and temperature, as well as a custom data script to process and analyze the samples acquired. For a low-cost sensing device, the DHT11 sensor is an ideal alternative. It is offered online for less than ¥336 USD and provides adequate precision and range for the client’s needs (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as the DHT22,  BME280 or SHT35 have higher specifications, but the DHT11 uses a simple serial communication (SPI) rather than more elaborate protocols like I2C used by the alternatives. Given the range, precision, and accuracy required for this application, the DHT11 provides the best compromise.

To connect the DHT11 sensor to a computer, we will use a device that provides serial communication. A common and cost-effective solution for prototyping is the Arduino UNO microcontroller. Arduino is an open-source electronics platform known for its easy-to-use hardware and software. In addition to its low cost (<¥4300 USD), this device is programmable and expandable. While alternatives, such as different versions of Arduino, are available, their size and price make them less adequate for this project.

Considering the budgetary constraints and hardware requirements, the proposed software tool for this solution is Python. Python's open-source nature and platform independence contribute to the long-term viability of the system. Python simplifies potential future enhancements or modifications, enabling seamless scalability without extensive redevelopment. Compared to alternatives like C or C++, Python is a high-level programming language (HLL) with high abstraction. For example, memory management is automatic in Python, while in C/C++, it is the responsibility of the developer to allocate and free memory, which can lead to potential memory issues. Using a high-level language allows both current and future developers to extend the solution or resolve issues promptly.


<h5> Design Statement</h5>

Design Statement
To investigate the environmental factors impacting the sleep quality of residents in Room R2-14, we will deploy an Arduino-based distributed weather station that monitors temperature, humidity, and air pressure. The DHT11 sensor will be used to measure temperature and humidity, while a BMP180 or similar sensor will measure air pressure. The data will be collected over a 48-hour period to identify patterns that might correlate with the residents' sleep behaviors.

The collected data will be processed using Python in PyCharm, where we will create visualizations using the matplotlib library to analyze the environmental conditions and their potential effects on sleep quality. The goal of this project is to provide insights into how temperature, humidity, and pressure may be influencing sleep patterns and to suggest possible adjustments that could improve the residents' sleep environment, helping them achieve better sleep quality, productivity, and focus throughout the day.

---
## Success Criteria
1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours. 
2. ```[HL]``` The local variables will be measure using a set of 3 sensors around the dormitory.
3. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)``` 
4. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
5. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server as a backup.
6. The solution provides a prediction for the subsequent 12 hours for both temperature and humidity.
7. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.
