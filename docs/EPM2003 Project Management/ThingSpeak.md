# ThingSpeak

## Introduction
ThingSpeak is an IoT (Internet of Things) platform that allows users to collect, store, analyze, and visualize sensor data in the cloud. Developed by MathWorks, it is widely used for IoT projects, including environmental monitoring, smart agriculture, industrial automation, and home automation. We will be using in our irrigation control system, where the temperature of the water will be detected and uploaded to the platform, as this will give farm users an easier way to check their temperature of their irrigation system. 

## How to start
To begin using ThingSpeak, we need to first create a new channel. In here, we put in the name of the system, in this case **Test Temperature Monitoring**, description, which is the general about for the system and fields, where you can put as many as you like, but since we are only doing it for temperature, we have only picked one, which is **Temperature**. 

## Code for ThingSpeak Testing
In this part, we will not be using the sensor, as I will be randomly generating some values to replicate the process of temperature sensor reciveing information (water temperature).

```cpp
#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ThingSpeak.h>

const char* ssid = "Your_SSID";       // Your Network SSID
const char* password = "Your_PASSWORD";     // Your Network Password

WiFiClient client;

unsigned long myChannelNumber = 2975330; 
const char * myWriteAPIKey = "P7N4N8GGXILVWY9P"; 

int val;

void setup()
{
  Serial.begin(9600);
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("\nWiFi connected");
  
  // Seed random number generator using analog noise
  randomSeed(analogRead(A0));

  ThingSpeak.begin(client);
}

void loop()
{
  val = random(0, 101);  // Random number between 0 and 100
  Serial.print("Temperature: ");
  Serial.print(val);
  Serial.println("*C");

  ThingSpeak.writeField(myChannelNumber, 1, val, myWriteAPIKey);

  delay(15000);  // ThingSpeak requires at least 15s delay between writes
}
```

## Explanation 

**A. Includes all the necessary libraries for ESP8266 and ThingSpeak**

```cpp
#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ThingSpeak.h>
```

  - ```ESP8266WiFi.h```: Enables Wi-Fi connectivity for ESP8266
  - ```WiFiClient.h```: Allows the ESP8266 to act as a network client
  - ```ThingSpeak.h```: Provides functions to interact with ThingSpeak IoT platform

**B. Defining Wi-Fi network credantials**

```cpp
const char* ssid = "Your_SSID";
const char* password = "Your_PASSWORD";
```

  - ```ssid```: Name of your Wi-Fi network (case sensitive)
  - ```password```: Password for the network
  - Replace ```Your_SSID``` and ```Your_PASSWORD``` with your actual credentials

!!! Danger 

    For your SSID and passwork, try not to use special character such as ' or ` 

**C. ThingSpeak Configuration**

```cpp
WiFiClient client;
unsigned long myChannelNumber = 2975330; 
const char * myWriteAPIKey = "P7N4N8GGXILVWY9P";
```

  - ```client```: Creates a Wi-Fi client object to handle connections
  - ```myChannelNumber```: Your ThingSpeak channel ID (replace with your own)
  - ```myWriteAPIKey```: Your ThingSpeak Write API Key (keep this private)

**D. Global Variables**

```cpp
int val;
```

  - ```val```: Stores the random "temperature" value to be sent to ThingSpeak

**E. ```setup()``` Function**

```cpp
void setup()
{
  Serial.begin(9600);
  WiFi.begin(ssid, password);
```

  - ```Serial.begin(9600)```: Starts serial communication for debugging (baud rate = 9600)
  - ```WiFi.begin(ssid, password)```: Attempts to connect to the specified Wi-Fi network

**F. Wi-Fi Connection Loop**

```cpp
while (WiFi.status() != WL_CONNECTED) {
  delay(500);
  Serial.print(".");
}
Serial.println("\nWiFi connected");
```

  - ```while``` loop: Waits until Wi-Fi is connected, printing dots (```...```) every 500ms
  - ```WiFi.status()```: Checks the connection status (```WL_CONNECTED``` means success)
  - Prints "```WiFi connected```" once linked

**G. Random Seed Initialization**

```cpp
randomSeed(analogRead(A0));
```

  - ```randomSeed()```: Seeds the random number generator using noise from analog pin ```A0``` (unconnected pin = floating voltage for randomness)

**H. ThingSpeak Initialization**

```cpp
ThingSpeak.begin(client);
```

  - Starts the ThingSpeak client using the ```WiFiClient``` object

**I. ```loop()``` Function**

```cpp
void loop()
{
  val = random(0, 101);  // Random number between 0 and 100
```

  - ```random(0, 101)```: Generates a pseudo-random integer between 0 and 100 (simulates temperature)

**J. Serial Monitor Output**

```cpp
Serial.print("Temperature: ");
Serial.print(val);
Serial.println("*C");
```

  - Prints the random value as a "temperature" (e.g., ```Temperature: 42*C```)

**K. Send Data to ThingSpeak**

```cpp
ThingSpeak.writeField(myChannelNumber, 1, val, myWriteAPIKey);
```

  - ```writeField()```: Sends ```val``` to Field 1 of your ThingSpeak channel
  - The arguments are ```(channelNumber, fieldNumber, data, APIKey)```

**L. Delay Between Writes**

```cpp
delay(15000);  // ThingSpeak requires at least 15s delay between writes
```

  - We need this line, as ThingSpeak only accepts data every 15 seconds due to free account limitation 

## Expected Output

**So, the serial monitor will show:**

```
....
WiFi connected
Temperature: 64*C
Temperature: 12*C
...
```

**In your ThingSpeak Channel, it will show:**
A graph of random values (0–100) updating every 15 seconds

## Demo

To review the demo, please click this link:  
[View ThingSpeak Channel](https://thingspeak.mathworks.com/channels/2975330)
  












