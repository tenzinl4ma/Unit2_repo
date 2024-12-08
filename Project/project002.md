
![DHT11-Working](https://github.com/user-attachments/assets/2510f28a-fdd3-492f-8eb7-50981413d52f)
<h6>Img by Jobit Joseph</h6>


# Unit 2 Distributed Weather Station for ISAK
___
### Criteria A: Planning


## Problem Definition

In the R2-14 house, members sleep late around 1 or 2 AM, even when they are not studying or engaged in any particular activity. This late sleep pattern often leads to waking up late in the morning, causing some to miss breakfast or even classes. As a result, their overall productivity and focus during the day are negatively affected.

And one member came to me and complained about this situation,(Client) party A.
I try to pinpoint the problem and after 
discussing 
the problem with other residents,
it became clear 
that 
the root cause might not only be related to personal habits but could also be influenced by environmental factors such as temperature, humidity, and air pressure. Although these factors are not always physically noticeable, they might impact sleep quality, leading to late bedtimes and poor morning routines.

My client( Party A) needs a way to monitor and track these environmental 
conditions to 
determine if they are affecting their sleep and, if so, how they can improve their environment to ensure better sleep quality.

---

## Proposed Solution
Considering the client's requirements, an adequate solution includes a 
low-cost sensing device for humidity and temperature and a custom 
data script to process and analyze the samples acquired. For a low-cost 
sensing device, the DHT11 sensor is an ideal alternative. It is offered 
online for less than ¥336 and provides adequate precision and range for 
the client’s needs (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 
90%). Similar devices such as the DHT22,  BME280, or SHT35 have higher specifications, but the DHT11 uses a simple serial communication (SPI) rather than more elaborate protocols like I2C used by the alternatives. 
Also, we can calculate the estimated atmospheric pressure by the ideal gas 
law and the psychrometric law E=(RH/100)*Es(T) from temperature and humidity 
readings 
from 
DHT11. So, given the range, precision, and 
accuracy required for this 
application,
the DHT11 provides the best compromise.

To connect the DHT11 sensor to a computer, we will use a device that provides serial communication. A common and cost-effective solution for prototyping is the Arduino UNO microcontroller. Arduino is an open-source electronics platform known for its easy-to-use hardware and software. In addition to its low cost (<¥4300 USD), this device is programmable and expandable. While alternatives, such as different versions of Arduino, are available, their size and price make them less adequate for this project.

Considering the budgetary constraints and hardware requirements, the proposed software tool for this solution is Python. Python's open-source nature and platform independence contribute to the long-term viability of the system. Python simplifies potential future enhancements or modifications, enabling seamless scalability without extensive redevelopment. Compared to alternatives like C or C++, Python is a high-level programming language (HLL) with high abstraction. For example, memory management is automatic in Python, while in C/C++, it is the responsibility of the developer to allocate and free memory, which can lead to potential memory issues. Using a high-level language allows both current and future developers to extend the solution or resolve issues promptly.


<h5> Design Statement</h5>


To investigate the environmental factors impacting the sleep quality of residents in Room R2-14, we will deploy an Arduino-based distributed weather station that monitors temperature, humidity, and air pressure. The DHT11 sensor will be used to measure temperature and humidity, while a BMP180 or similar sensor will measure air pressure. The data will be collected over a 48-hour period to identify patterns that might correlate with the residents' sleep behaviors.

The collected data will be processed using Python in PyCharm, where we will create visualizations using the matplotlib library to analyze the environmental conditions and their potential effects on sleep quality. The goal of this project is to provide insights into how temperature, humidity, and pressure may be influencing sleep patterns and to suggest possible adjustments that could improve the residents' sleep environment, helping them achieve better sleep quality, productivity, and focus throughout the day.

---
## Success Criteria
1. The solution provides a visual representation of the Humidity and  
   Temperature values inside a dormitory (Local) and outside the house  
   (Remote) for a period of minimum 48 hours. 
 * Issue tackled: By monitoring environmental conditions both inside and 
   outside the dormitory, the project helps identify patterns that  might be 
   affecting the sleep of residents, such as temperature and humidity levels.
   According to research from the National Library of Medicine, exposure to  
   certain heat levels, particularly in humid environments, can negatively  
   affect sleep stages and thermoregulation. By visualizing these factors,  
   this solution could directly contribute to understanding and improving  
   residents' sleep quality.
2. ```[HL]``` The local variables will be measure using a set of 2 sensors 
   around the room.
 * Issue tackled: By using two sensors to measure temperature, humidity, and calculated pressure, and calculating the mean of these readings, the solution ensures reliable data. This approach resolves potential inconsistencies from individual sensors, allowing for a more accurate representation of conditions that may influence sleep. Given that ideal humidity levels are between 30% and 50% (EPA recommendation), and that excessive heat can reduce sleep quality, monitoring these variables is essential.
3. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)``` 
 * Issues tackled: This solution resolves the challenge of understanding how environmental factors interact. Modeling temperature, humidity, and pressure will help identify how different combinations affect sleep quality. Given the recommended temperature ranges of 15.6°C to 19.4°C (for adults) and 18.3°C to 21.1°C (for babies), this modeling will provide actionable insights into how adjustments to these variables can improve sleep.
4. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
 * Issue tackled: By analyzing the variation and extremes of environmental factors like temperature and humidity, this solution addresses the need to evaluate the impact of these factors on sleep. Research shows that humid heat exposure increases wakefulness and decreases quality sleep, so identifying moments of high thermal load through this analysis can guide improvements in the dormitory’s environment.
5. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server as a backup.
* Issue tackled: By saving the data in a CSV file and backing it up remotely, this solution ensures reliable storage and accessibility for further analysis. This is particularly important for tracking long-term trends in environmental conditions, which might help correlate sleep disturbances to specific temperature and humidity levels.
6. The solution provides a prediction for the subsequent 12 hours for both temperature and humidity.
* Issues tackled: Providing predictions for future conditions helps residents plan their routines to optimize sleep quality. Given the temperature range of 15.6°C to 19.4°C for adults, predicting and adjusting room temperature in advance could make it easier to fall and stay asleep.
7. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.
* Issues tackled: The poster provides a clear summary of the findings and 
   recommendations, guiding the residents towards maintaining healthy levels of temperature (15.6°C to 19.4°C) and humidity (30%-50%) to improve sleep quality. Based on the findings from both the project data and medical research, the poster can suggest specific actions to adjust the environment for better sleep.

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

Fig.1 Shows the  System diagram (HL) for the proposed system to visualize and 
analyze temperature and humidity data in R2-14'B'. A remote server provides and API for 
remote monitoring and storage via the ISAK-S network. The two sensor are 
used to determine more precisely the physical values and include measurement 
uncertainty and their indoor variables will be measured inside the room.The 
Local 
values are stored in a CSV database 
locally 
and a 
backup copy will be store in the remote server using the Weather API.


<img width="592" alt="Screenshot 2024-12-07 at 2 38 21 PM" src="https://github.com/user-attachments/assets/c8d7815a-0ea4-4fcf-bb44-e02aa85e162f">


Fig.2 The above diagram shows the hardware architecture of the arduino. The 
Arduino is connected to the computer using a USB cables with type C- Type B 
cable. The DHT11 sensors and the LED indicator are connected to Arduino's 
pins as shown. The 
Arduino is powered by the computer with 5v via the cable.

<img width="860" alt="Screenshot 2024-12-07 at 2 59 52 PM" src="https://github.com/user-attachments/assets/653069a6-51a4-4f02-a09a-35901f3422ba">
 
Fig.3  Above diagram show the location of the DHT11 sensor across the room 
of R2-14. The arduino is center of the room and each sensor is around 
diagonal of the room. These two sensor are going to measure hte temperature 
and the humidity of the room and later we can also calculate the estimate 
the atmospheric pressure from these readings.

--- 

### Flow chart

![Screenshot 2024-12-07 at 3 44 37 PM](https://github.com/user-attachments/assets/e3c6daef-2102-46a5-9e94-ad7e49a48e11)

#### Fig.4    The above flowchart shows the blinking light indicator with an infinite loop with no end. the light will blink 7 times in each loop.



---

## Test Plan
| Test Type        | Test Content                                                                                                         | Input                                                                                                                                                                                                                                                                                                                                                                 | Expected Output                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unit/Performance | Check Arduino Connects to Computer, and that the connection is fast as an indicator that it is functioning correctly | After identifying connected Arduino's id, use the serial.serial() function on PyCharm to establish a serial connection. Set the parameter timeout to 0.1                                                                                                                                                                                                              | Program does not timeout. A message confirming that a connection has been established printed onto PyCharm console.                                                                                                                                                                                                                                                                                                                                                                                                           |
| Unit             | Check that Sensor Retrieves Data and Sends to Computer                                                               | Upload program from Arduino IDE that identifies a sensor connected to the correct pins, and reads from so.                                                                                                                                                                                                                                                            | A serial connection should be established between the arduino and the computer. The recorded temperature and humidity should appear in the console as follows: "Temperature: t1, Humidity: h1"                                                                                                                                                                                                                                                                                                                                |
| Integration      | Check All 3 Sensors Can Retrieve Data and Send Data in the same Circuit                                              | 1. Connect 3 DHT sensors to Arduino at once 2. Upload program from Arduino IDE that a) correctly identifies the 3 sensors in the correct pins and b) returns readings from all 3 sensors 3. Run program in PyCharm which reads and prints lines stored in Arduino                                                                                                     | A serial connection should be established between the arduino and the computer. When running program, a total of 6 different values (a temperature value and humidity value from each of the 3 sensors) should be printed onto the console.                                                                                                                                                                                                                                                                                   |
| Integration      | Check that readings can be saved into a csv file per certain amount of time                                          | Run program in PyCharm which reads the data from the Arduino each second for 10 minutes, and then saves the data into a csv file once per minute.                                                                                                                                                                                                                     | A new csv file called "testcase.csv" should be created. Within it, there should be 10 lines, each looking like the following, with different times (datetime of recording),t1,t2,t3,h1,h2,h3                                                                                                                                                                                                                                                                                                                                  |
| Unit             | Create Test Sensor and Recording on Server                                                                           | 1. Using requests, register user on server, under username MMproject 2. Similarly, get access token through requests 3. Using access token, create a new sensor called "testing" 4. Confirm "testing" exists under user using requests 5. Send a test recording {'sensor_id:{id},'value':6} to "testing" using requests 6. Get recordings on "testing" using requests | 1. answer should be printed, informing the successful creation of a new user 2. answer should be printed, an access token 3. answer should be printed, informing the successful creation of a new sensor "testing", and its id 4. answer should be printed, showing all of the sensors on the server. The most recent sensor added should be "testing" under user MMproject 5. answer should be printed, showing the datetime, value, and sensor id recorded 6. answer should be printed, containing recording of {'value':6} |
| Integration      | Check that readings can be sent to the server per certain amount of time                                             | Run program in PyCharm which reads the data from the Arduino each second for 30 seconds, and then sends the data {'sensor_id:{id}, 'value':{t1}} to the sensor "testing" previously created on the server using a POST request each 10 seconds. Then, using a GET request, retrieve recordings on "testing" to confirm there are 3 recordings.                        | The last 3 recordings in the sensor should contain key and value pairs of {'value':{t1}}. The t1 value should correspond to the t1 value printed on the console at t=10, 20, and 30.                                                                                                                                                                                                                                                                                                                                          |
| Usability        | Check that the graphs are easy to comprehend and meaningful.                                                         | Show the clients (20C) the graphs, and ask them to describe the graph and the data it is representing                                                                                                                                                                                                                                                                 | Ideally, they would be able to answer what kind of data each graph is expressing (e.g. when looking at the average of temperature, they should be able to say that they see the average of the 3 temperature values being plotted). If this test fails for any of the graphs, there is a need to make adjustments, such as adding labels, using different colors, etc.                                                                                                                                                        |



<h3> Record of Tasks</h3>

| Task No 	 |                Planned Action                               	                |                     Planned Outcome                                         	                      |  Time estimate 	  | Target completion date 	 | Criterion 	 |
|:---------:|:----------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------:|:-----------------:|:------------------------:|:-----:|
| 1       	 | write the problem<br>context and design <br>statement                      	 | have concrete problem <br>defination and design <br>design statement.                            	 |  15 min        	  | Nov 22                 	 | A         	 |
| 2       	 | Code and upload code<br>on Arduino with <br>Arduino IDE                    	 | upload program for data<br>collection and the light <br>indicator for the arduino                	 |  45 min        	  | Nov 23                 	 | C         	 |
| 3       	 | Make Arduino Circuit<br>and right connection <br>of all components         	 | have able to read the data<br>of sensors and blink <br>indicators.                               	 |  30 min        	  | Nov 23                 	 | C         	 |
| 4       	 | Connect with python                                                        	 | able to read the data on <br>terminal and control via <br>pyfirmata                              	 |  1 hr          	  | Nov 24                 	 | C         	 |
| 5       	 | Answer TOK questions                                                       	 | drafting and refining the <br>answers                                                            	 |  25 min        	  | Nov 24                 	 | A         	 |
| 6       	 | watch tutorial on how <br>to create new file <br>and store in csv folder   	 | able to store all the <br>reading from sensor into csv<br>file.                                  	 |  30 min        	  | Nov 25                 	 | C         	 |
| 7       	 | create function for <br>keyboard interruption<br>and sensor error.         	 | make a library that is able<br>to pause, resume with threshold<br>module to tackle, interuption. 	 |  1 hr          	  | Nov 26                 	 | C         	 |
| 8       	 | Create an Id on server <br>and push the csv                                	 | able to store the data on server<br>for backup                                                   	 |  2 hrs         	  | Nov 28                 	 | C         	 |
| 9       	 | Construct Graphs using <br>matplotlib.pyplot                               	 | Have graph of data and average <br>using pyplot                                                  	 |  3 hrs         	  | Nov 29                 	 | C/D       	 |
| 10      	 | Conduct usability <br>testing to check if graphs<br>represent data clearly 	 | Have a finalized graphs that <br>which is understable to everyone                                	 |  45 min        	  | Nov 30                 	 | D         	 |
|    11	    |            make a poster to illustrate <br/>your<br/>overall project 	            |                                      Have a finalize poster 	                                      | 1.5 hrs         	 |      De1          	      |  C/D  |

---

# Criteria C: Development
## List of techniques used
- For Loop
- While Loop
- If/Else Statements
- Try/Except statements
- Functions
- Lists and Dictionaries
- Libraries
  - Comma Separated Values (CSV) Files
  - Serial Communication 
  - Application Programming Interface (API)
  - Data Visualization
  

## List of libraries used
PyCharm: csv, time, datetime, requests, matplotlib, numpy, serial, math, 
interruption_handler.py(custom-created lib)

Arduino IDE: Adafruit DHT Sensor Library

## Development
### Code from Arduino IDE
In order to be able to read data from the sensors, there is a need to compile and upload a program to the arduino. This is done using the Arduino IDE. The code we wrote as follows.

From file ```arduino.ino```:
```.C++
#include <DHT.h>

// Pin definitions for the DHT sensors and LED
#define DHT1_PIN 2
#define DHT2_PIN 3
#define LED_PIN 7

DHT dht1(DHT1_PIN, DHT11);  // Sensor 1 
DHT dht2(DHT2_PIN, DHT11);  // Sensor 2 
```
**(Success Criteria 2)** In the first line, we include the `DHT.h` class from the Adafruit Unified Sensor Library. This library is necessary in our program as it allows the arduino to identify and communicate with the DHT sensors connected to it. In the second line, we define the type of sensor we are using. For our solution, we are using the DHT11 sensor.

The third and fourth line defines the pin of the arduino that the sensor is 
connected to, and creates the sensor's identity so that it can be used in 
later programs. This is done both sensors, changing the number of the 
pin in the arduino (defining `DHTPIN2`, `DHTPIN3`,`LED_PIN7`), and then the 
corresponding id of the sensor (`dht2`, `dht3`,). The pins that the sensors are connected to can be seen in fig. 2.

```.C++
void setup() {
  Serial.begin(9600);
  dht1.begin();
  dht2.begin();
  pinMode(LED_PIN, OUTPUT);  // Initialize the LED pin as an output
  digitalWrite(LED_PIN, LOW);  // Initially turn off the LED
}

```

The `setup()` function initializes the necessary components for the Arduino program. It begins by starting serial communication at a baud rate of 9600 with `Serial.begin(9600)`. The `dht1.begin()` and `dht2.begin()` initialize the DHT sensors connected to the Arduino, making them ready to read temperature and humidity. The `pinMode(LED_PIN, OUTPUT)` configures pin 7 as an output to control the LED, and `digitalWrite(LED_PIN, LOW)` ensures the LED is initially turned off by setting the pin to a LOW voltage.
```.C
// Reading Sensor 1
  float temp1 = dht1.readTemperature();  // Temperature in Celsius
  float hum1 = dht1.readHumidity();     // Humidity in percentage
  
  // Reading Sensor 2
  float temp2 = dht2.readTemperature();  // Temperature in Celsius
  float hum2 = dht2.readHumidity();     // Humidity in percentage
  } else {
    // Print only the numerical values in a single line, separated by commas
    Serial.print(temp1);
    Serial.print(", ");
    Serial.print(hum1);
    Serial.print(", ");
    Serial.print(temp2);
    Serial.print(", ");
    Serial.println(hum2);

```
The program reads data from the DHT sensors every 60 seconds, using the `millis()` function to track the time elapsed since the last reading. Once 60 seconds have passed, it reads the temperature and humidity values from both sensors. These values are stored in separate variables (`temp1`, `hum1`, `temp2`, `hum2`). If the readings fail (i.e., if the data returned is NaN), an error message is printed. Otherwise, the successful readings are displayed in the Serial Monitor in a comma-separated format.

### Code from Pycharm
**(Success Criteria 5)** Initially, we recognized the critical need for a reliable communication link with our remote server to ensure the safety and accessibility of our data. We made the decision to store our collected data remotely, creating a backup on the server. This approach ensures that if the local backup encounters issues, such as malfunctioning or becoming inaccessible, we can easily retrieve the same data by accessing the server's backup. This redundancy provides an added layer of security and reliability, ensuring that our data remains intact and retrievable under any circumstances.

From file server-handshakr.py:
 
```.py
import requests
# Server details
server_ip = 'http://XXX.XX.X.XXX' # For security reaseon and DdoS 
register_url = f'{server_ip}/register'
login_url = f'{server_ip}/login'
sensor_url = f'{server_ip}/sensor/new'
sensor_data_url = f'{server_ip}/sensor/data'

```
 requests: This library is used to send HTTP requests to a web server. In 
 this code, it handles POST requests to register users, log in, create 
 sensors, and send data. After slash the server ip/ these are the endpoints 
 where HTTP request will be sent to perform set function.
 ```.py
 
# New user details mean to run once
new_user = {
    "username": "**********",  # set username 
    "password": "**********"    # set password
}
```
This is the data for the new user you're creating on the server. The username and password are used for registration and logging in.
```.python
# Register User [ONLY RUN ONCE]
answer = requests.post(f'http://{ip}/register', json=user)  # Register user, save result in answer
print(answer.json())  # Print answer to check if it worked

```
Purpose: This line sends a POST request to the server to register the user. The server will receive the username and password in JSON format. If uncommented, this would initiate the registration process.
```.python
answer = requests.post(f"http://{server_ip}/login", json=user)
print(answer.json())
cookie = answer.json()['access_token']
print(cookie)

```
This sends a POST request to the servers /login endpoint with the provided 
username and password. This server responds with an access token
(asscess_token) that is used to authorize future requests. The third line 
code is to extracts the access token from the JSON response and stores it in 
the cookie variable. This token is printed out, which is needed for 
authenticating further requests.
 
```.python
# step 3: create a sensor
# auth = {"Authorization": f'Bearer {cookie}'}
sensor = {
    'type': 'temperature',
    'location': 'R2-14',
    'name': 'Dragonsensor',
    'unit': 'C'
}
# answer = requests.post(f'http://{server_ip}/sensor/new', json=sensor, headers=auth)
# print(answer.json())

```
Here the sensor object is created with different attributes.
```.python
# Part 1
def process_and_push_data(csv_file, auth_header):
    with open(csv_file, mode='r') as file:
        csv_reader = csv.reader(file)
        next(csv_reader)  # Skip header row
# Part 2
 for row in csv_reader:
        temp = float(row[1])  # Mean Temperature (°C)
        humidity = float(row[2])  # Mean Humidity (%)
        pressure = float(row[3])  # Estimated Pressure (hPa)

        temperature_data.append(temp)
        humidity_data.append(humidity)
        pressure_data.append(pressure)
```
In commented part 1 it open a CSV file in read mode and initialize the 
reading and skip the first line as its heading row. From part 2 its the 
looping throug each row in the CSV file it and the respecting value are 
converted in time string and temperature, humidity, pressure into floats. 

---

**(Success Criteria 2)** This section we will be reading the data from the 
sensors send by the arduino in live time with pyserial and then calculate 
the exstimate pressure. These data are then save in local csv file and then 
later send to the server for the backup. Lets walk through the code.
```.python
import serial
import math
def estimate_pressure(temp, humidity):# Function to estimate the atmospheric pressure using temperature and humidity
    E_s = 6.112 * math.exp((17.67 * temp) / (temp + 243.5))    # This is the Ideal gas and psychometric formula that I talk about in problem definition
    E_a = E_s * (humidity / 100)    # Calculate the actual vapor pressure
    pressure = 1013.25 * (1 + (temp / 44330)) ** 5.255
    return round(pressure, 2)  # Return the pressure rounded to 2 decimal places
arduino_port = "/dev/cu.usbserial-110"  # This is my mac port
baud_rate = 9600  # this is to match the arduino
csv_file = "dht11_data.csv"  # this is my file name where sensor data is stored
```
First we import the math for calculating the estimate pressure applyig the 
psychometric formula and serial for the live interaction with the arduino to 
read the data. we calculate and round the data into 2 decimal point and 
these data were saved to the csv file called dht11_data.csv file. 
```.python
# send temperature data
for temp in temperature_data:
    sensor_data = {'data': [temp]}  # Wrap the data in a list
    response = requests.post(f"http://{server_ip}/sensor/{temperature_sensor_name}/data", json=sensor_data,
                             headers=auth)
    if response.status_code == 200:
        print("Temperature data sent successfully.")
    else:
        print(f"Failed to send temperature data: {response.status_code}, {response.text}")
# Send pressure data
for pressure in pressure_data:
    sensor_data = {'data': [pressure]}  # Wrap the data in a list
    response = requests.post(f"http://{server_ip}/sensor/{pressure_sensor_name}/data", json=sensor_data, headers=auth)
    if response.status_code == 200:
        print("Pressure data sent successfully.")
    else:
        print(f"Failed to send pressure data: {response.status_code}, {response.text}")
# send the humidity data
for hum in humidity_data:
    sensor_data = {'data': [hum]}  # Wrap the data in a list
    response = requests.post(f"http://{server_ip}/sensor/{humidity_sensor_name}
    /data", json=sensor_data,
                             headers=auth)
    if response.status_code == 200:
        print("Humididty  data sent successfully.")
    else:
        print(f"Failed to send Humidity data: {response.status_code}, {response.
        text}")
```
 Then we loop through each data which is appended in temp, hum and press 
 variable which is then send these  data to the sever for the remote for the 
 backup.
**Success Criteria 1**
 The data from the dht11_data.csv file are open in read mode. 
 ```.python
times, temperature, humidity, pressure = [],[],[],[]
with open('dht11_data.csv', mode='r') as file:# Open and read the CSV file
    reader = csv.reader(file)
    next(reader)  # Skip the header row
    for row in reader:         # Check if the row has the expected number of columns
        if len(row) >= 4:  # Ensure there are at least 4 columns (Time, Temp, Humidity, Pressure)
            time_str = row[0]  # Assuming Time is the first column
            temperature_value = float(row[1])  # Assuming Temperature (°C) is the second column
            humidity_value = float(row[2])  # Assuming Humidity (%) is the third column
            pressure_value = float(row[3])  # Assuming Pressure (hPa) is the fourth column
            time_obj = datetime.strptime(time_str, '%m-%d %H:%M')  # Adjust the format as needed
            times.append(time_obj)            # Append the data to the lists
            temperature.append(temperature_value),humidity.append(humidity_value),pressure.append(pressure_value)
```
we made the empty list to store the respective data later after open opening 
the csv file we loop through every row and extract the value in float and 
append to the empyty list that variable which was declared above. Now we 
have a set of data in respective list with name assign.
```.python
times_np = np.array([np.datetime64(t) for t in times])# Convert times to numpy array
temperature_np = np.array(temperature)
humidity_np = np.array(humidity)
pressure_np = np.array(pressure)
fig, axs = plt.subplots(3, 1, figsize=(10, 12))# Create subplots (3 rows and 1 column)
axs[0].plot(times_np, temperature_np, label='Temperature (°C)\n R2-14(B)', color='r')
axs[1].plot(times_np, humidity_np, label='Humidity (%)\n R2-14(B)', color='g')
axs[2].plot(times_np, pressure_np, label='Pressure (hPa)\n R2-14(B)', color='b')
plt.show()
```
![weather_data_plot](https://github.com/user-attachments/assets/7d11b154-45aa-4c23-824b-2d30a16060bb)


<h6 align='center'>Fig5. trend on time and other objects</h6>

we convert the datetime into he numpy array(numpy built in function) and other 
objects too, so that we can plot in the graph. The above graph is the full 
graph on the raw data on humidity, temperature, pressure trend on time which 
was record for more than 49 hours. 

![weather_data_extra_smoothed_plot](https://github.com/user-attachments/assets/b106ddea-b46a-4c62-b5c5-999b131ca428)


<h6 align='center'>Fig5. Smoothen data graph</h6>

```.python
def moving_average(windowSize:int, x:list)->list:
    x_smoothed = []
    for i in range(0, len(x)-windowSize):
        x_section = x[i:i+windowSize]
        x_average = sum(x_section)/windowSize
        x_smoothed += [x_average]
    return x_smoothed
```
I decided to use the moving average function to smooth out the data because the 
raw data was too noisy and fluctuating too much. When working with things like 
temperature or humidity measurements, the values can jump up and down rapidly, 
making it hard to see any real patterns. By using a moving average, I can take
a group of data points, calculate their average, and create a smoother line that
makes the underlying trend much clearer. This will helps us to better 
understand how the temperature or humidity is changing over time without 
getting distracted by the random fluctuations. 

**Success Criteria 4**
```.python
import numpy as np

def standardization(data: list):
    data_array = np.array(data)  # Convert the data list to a NumPy array
    data_reshaped = data_array.reshape(-1, 1)  # Reshape data for StandardScaler
    scaler = StandardScaler()  # Initialize the StandardScaler
    sc_data = scaler.fit_transform(data_reshaped)  # Standardize the data
    
    time = np.arange(sc_data.shape[0])  # Generate time indices for the data
    return time, sc_data  # Return the time and standardized data

```

![standardized_pressure_comparison_plot](https://github.com/user-attachments/assets/203e99f0-7d41-47ae-ba0a-fff038721ba6)

<h6 align='center' > Graph of standardized pressure</h6>

I decided to use the standardization technique because I needed to ensure that both the remote and local sensor data could be compared on a common scale. The data collected from both sources may have different ranges or units, and this could cause misinterpretation when visualizing or analyzing them.

By standardizing the data, I can transform the data to have a mean of 0 and a standard deviation of 1, regardless of the original units or scale. This ensures that the pressure data from the CSV file and the server are directly comparable, even if they originally had different ranges.

The goal of this technique is to remove any bias from the scale or units of the data so that I can analyze and visualize the relative patterns and trends between the two sources. This helps in understanding how the pressure values from both sources fluctuate over time and allows me to accurately compare and visualize the two datasets on a single graph.

![hourly_analysis.png](../project2-p/hourly_analysis.png)
above is the linear model

![hourly_quadratic_analysis_with_smaller_grid.png](../project2-p/hourly_quadratic_analysis_with_smaller_grid.png)

this is the quadratic model