
![DHT11-Working](https://github.com/user-attachments/assets/2510f28a-fdd3-492f-8eb7-50981413d52f)
<h6>Img by Jobit Joseph</h6>


# Unit 2 Distributed Weather Station for ISAK
___
### Criteria A: Planning


## Problem Definition

In the R2-14 house, members tend to sleep late around 1 or 2 AM, even when they are not studying or engaged in any particular activity. This late sleep pattern often leads to waking up late in the morning, causing some to miss breakfast or even classes. As a result, their overall productivity and focus during the day are negatively affected.

After discussing the problem with the residents, it became clear that the root cause might not only be related to personal habits but could also be influenced by environmental factors such as temperature, humidity, and air pressure. Although these factors are not always physically noticeable, they might have an impact on sleep quality, leading to the late bedtimes and poor morning routines observed.

My client need a way to monitor and track these environmental conditions to determine if they are affecting their sleep and, if so, how they can improve their environment to ensure better sleep quality.

---

## Proposed Solution
Considering the client requirements, an adequate solution includes a low-cost sensing device for humidity and temperature, as well as a custom data script to process and analyze the samples acquired. For a low-cost sensing device, the DHT11 sensor is an ideal alternative. It is offered online for less than ¥336 USD and provides adequate precision and range for the client’s needs (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as the DHT22,  BME280 or SHT35 have higher specifications, but the DHT11 uses a simple serial communication (SPI) rather than more elaborate protocols like I2C used by the alternatives. Given the range, precision, and accuracy required for this application, the DHT11 provides the best compromise.

To connect the DHT11 sensor to a computer, we will use a device that provides serial communication. A common and cost-effective solution for prototyping is the Arduino UNO microcontroller. Arduino is an open-source electronics platform known for its easy-to-use hardware and software. In addition to its low cost (<¥4300 USD), this device is programmable and expandable. While alternatives, such as different versions of Arduino, are available, their size and price make them less adequate for this project.

Considering the budgetary constraints and hardware requirements, the proposed software tool for this solution is Python. Python's open-source nature and platform independence contribute to the long-term viability of the system. Python simplifies potential future enhancements or modifications, enabling seamless scalability without extensive redevelopment. Compared to alternatives like C or C++, Python is a high-level programming language (HLL) with high abstraction. For example, memory management is automatic in Python, while in C/C++, it is the responsibility of the developer to allocate and free memory, which can lead to potential memory issues. Using a high-level language allows both current and future developers to extend the solution or resolve issues promptly.


<h5> Design Statement</h5>


To investigate the environmental factors impacting the sleep quality of residents in Room R2-14, we will deploy an Arduino-based distributed weather station that monitors temperature, humidity, and air pressure. The DHT11 sensor will be used to measure temperature and humidity, while a BMP180 or similar sensor will measure air pressure. The data will be collected over a 48-hour period to identify patterns that might correlate with the residents' sleep behaviors.

The collected data will be processed using Python in PyCharm, where we will create visualizations using the matplotlib library to analyze the environmental conditions and their potential effects on sleep quality. The goal of this project is to provide insights into how temperature, humidity, and pressure may be influencing sleep patterns and to suggest possible adjustments that could improve the residents' sleep environment, helping them achieve better sleep quality, productivity, and focus throughout the day.

---
## Success Criteria
1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours. 
 * Issue tackled: monitor and track these environmental conditions
2. ```[HL]``` The local variables will be measure using a set of 3 sensors around the dormitory.
 * Issue tackled: 
3. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)``` 
 * Issue tackled:
4. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
 * Issue tackled:
5. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server as a backup.
* Issue tackled:
6. The solution provides a prediction for the subsequent 12 hours for both temperature and humidity.
* Issue tackled:
7. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.
## TOK Connection for the Sleep Quality Project

### To what extent does the use of data science in climate research influence our understanding of environmental issues, and what knowledge questions arise regarding the reliability, interpretation, and ethical implications of data-driven approaches in addressing climate change?

Data science plays a crucial role in climate research, as it allows for the collection and analysis of large amounts of data from different regions, periods, and environmental conditions. This data-driven approach helps us gain a deeper understanding of climate change patterns and trends that would be difficult to observe through simple observation. By using sensors and monitoring technologies to collect data on temperature, humidity, and air pressure, we can accurately analyze how these variables influence various aspects of our environment, including sleep quality.

However, challenges arise regarding the reliability of the data and the interpretation of results. For example, if data is not collected from a broad enough sample size or if sensor accuracy is questionable, the conclusions we draw could be misleading. There is also an ethical dilemma when collecting and analyzing data related to people's personal environments—ensuring that the data is collected and used responsibly and with consent is paramount. Ultimately, data science provides valuable insights into environmental issues, but the quality and ethical handling of the data must be carefully considered.

## 1. How does our use of technology shape our understanding of the environment?

Technology enhances our ability to understand the environment by allowing us to gather objective, precise data that goes beyond our natural sensory perception. In the case of this project, sensors like the DHT11 and BMP180 provide quantitative measurements of temperature, humidity, and air pressure, which are difficult to assess accurately without such technology. By collecting and analyzing this data, we can understand environmental factors that influence sleep quality, such as room temperature and humidity.

Technology helps us move beyond subjective perceptions and gain a more accurate, data-driven understanding of our surroundings. Unlike relying on personal judgment, which can be biased or influenced by prior experiences, technology offers consistency and reliability, improving our ability to identify trends and correlations. For example, while we may feel a room is warm or cold based on intuition, the sensor data offers a much clearer picture, leading to better decisions about how to adjust our living conditions for better sleep.

## 2. What responsibilities do we have as technologists when it comes to handling personal data related to our living spaces?

As technologists, we have a responsibility to respect privacy and handle personal data with transparency and care. In this project, the residents of Room R2-14 have consented to having their environmental data collected and analyzed to determine the potential impact on their sleep quality. Technologists must ensure that the data is used for its intended purpose and that it is kept secure. This includes informing individuals about the nature of the data being collected, how it will be used, who will have access to it, and how long it will be retained.

Additionally, technologists must uphold the trust that is placed in them when collecting such data. In this project, all participants have given informed consent, and the data will only be used for improving the residents' sleep environment. Technologists must take appropriate steps to protect the data and ensure that it is not exploited for malicious purposes or shared without consent.

## 3. What cultural and contextual factors might impact our interpretation of the results, especially when comparing our local readings with those from other rooms or locations on campus?

Cultural and contextual factors play an important role in how we interpret environmental data. People from different cultural backgrounds may have varying perceptions of what constitutes "comfortable" or "uncomfortable" environmental conditions. For example, students who are used to warmer climates may find 20°C chilly, while those from colder regions may feel it is quite comfortable. This cultural perception can impact how the data is interpreted—what one person considers a "good" temperature for sleep might be seen as too cold or too warm by someone else.

Contextually, the interpretation of data can also be influenced by personal biases. If a resident believes their room is too cold based on their own experiences, they might be inclined to ignore or discount data that suggests otherwise. This is known as cognitive bias, and it can affect how data is analyzed and acted upon. For instance, even if the sensors show that the room temperature is ideal for sleep, residents may not believe the data if it contradicts their personal feelings. Therefore, it’s crucial to balance both objective data and subjective experiences, acknowledging that personal observations can offer valuable insights into interpreting the results.
___
# Criteria B: Design
<img width="660" alt="Screenshot 2024-12-03 at 3 54 27 PM" src="https://github.com/user-attachments/assets/4759e89d-af73-4a04-ae82-94cc48f88006">


| Task No 	|                               Planned Action                               	|                                          Planned Outcome                                         	| Time estimate 	| Target completion date 	| Criterion 	|
|:-------:	|:--------------------------------------------------------------------------:	|:------------------------------------------------------------------------------------------------:	|:-------------:	|:----------------------:	|:---------:	|
| 1       	| write the problem<br>context and design <br>statement                      	| have concrete problem <br>defination and design <br>design statement.                            	| 15 min        	| Nov 22                 	| A         	|
| 2       	| Code and upload code<br>on Arduino with <br>Arduino IDE                    	| upload program for data<br>collection and the light <br>indicator for the arduino                	| 45 min        	| Nov 23                 	| C         	|
| 3       	| Make Arduino Circuit<br>and right connection <br>of all components         	| have able to read the data<br>of sensors and blink <br>indicators.                               	| 30 min        	| Nov 23                 	| C         	|
| 4       	| Connect with python                                                        	| able to read the data on <br>terminal and control via <br>pyfirmata                              	| 1 hr          	| Nov 24                 	| C         	|
| 5       	| Answer TOK questions                                                       	| drafting and refining the <br>answers                                                            	| 25 min        	| Nov 24                 	| A         	|
| 6       	| watch tutorial on how <br>to create new file <br>and store in csv folder   	| able to store all the <br>reading from sensor into csv<br>file.                                  	| 30 min        	| Nov 25                 	| C         	|
| 7       	| create function for <br>keyboard interruption<br>and sensor error.         	| make a library that is able<br>to pause, resume with threshold<br>module to tackle, interuption. 	| 1 hr          	| Nov 26                 	| C         	|
| 8       	| Create an Id on server <br>and push the csv                                	| able to store the data on server<br>for backup                                                   	| 2 hrs         	| Nov 28                 	| C         	|
| 9       	| Construct Graphs using <br>matplotlib.pyplot                               	| Have graph of data and average <br>using pyplot                                                  	| 3 hrs         	| Nov 29                 	| C/D       	|
| 10      	| Conduct usability <br>testing to check if graphs<br>represent data clearly 	| Have a finalized graphs that <br>which is understable to everyone                                	| 45 min        	| Nov 30                 	| D         	|
|         	|                                                                            	|                                                                                                  	|               	|                        	|           	|
|         	|                                                                            	|                                                                                                  	|               	|                        	|           	|
|         	|                                                                            	|                                                                                                  	|               	|                        	|           	|
|         	|                                                                            	|                                                                                                  	|               	|                        	|           	|
|         	|                                                                            	|                                                                                                  	|               	|                        	|           	|



