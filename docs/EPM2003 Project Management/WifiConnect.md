## Introduction
Since we are using the NodeMCU ESP8266 which is widely used for IoT (Internet of Things projects), it has built-in Wi-Fi, hence making it ideal for connecting devices to the internet. 

## Code for Wifi Testing
To use the built-in Wi-Fi, we first wrote some codes and uploaded the codes to the NodeMCU ESP8266 to test out the built in wifi. 

```cpp
#include <ESP8266WiFi.h>

const char* ssid = "Your_SSID";
const char* password = "Your_PASSWORD";

void setup() {
  Serial.begin(9600);
  WiFi.begin(ssid, password);
  Serial.print("Connecting");

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("\nConnected!");
  Serial.println(WiFi.localIP());
}

void loop() {}

```

## Explanation 
