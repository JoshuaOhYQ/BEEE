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














