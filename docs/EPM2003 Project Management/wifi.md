# Wifi
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

**A. Includes the ESP8266 Wi-Fi library, which provides functions to connect to Wi-Fi networks**

```cpp
#include <ESP8266WiFi.h>
```

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

**C. The ```setup()``` function runs once when the board starts. It initializes settings**

```cpp
void setup(){

```

**D. Starts serial communication at 9600 baud rate for debugging**

```cpp
Serial.begin(9600);
```

!!! Tip 

    You can also use ```Serial.begin(115200)``` for faster communication (common in ESP8266).

**E. Attempts to connect to the Wi-Fi network using the provided ```ssid``` and ```password```**

```cpp
WiFi.begin(ssid, password);
```

!!! Notes 

    This is non-blocking (the code continues while connecting in the background).

**F. Prints ```"Connecting"``` to the Serial Monitor to indicate the connection attempt**

```cpp
Serial.print("Connecting");
```

**G. Waits until the Wi-Fi connection is established**

```cpp
while (WiFi.status() != WL_CONNECTED) {
  delay(500);
  Serial.print(".");
}
```

  - ```WiFi.status()```: checks the connection status
  - ```WL_CONNECTED```: successfully connected
  - The loop prints dots (```...```) every 500ms while waiting. 

!!! Notes 

    This is a blocking loop (code pauses here until connected).

**H. Prints ```"Connected!"``` on a new line (```\n```) once the Wi-Fi is connected**

```cpp
Serial.println("\nConnected!");
```

**I. Prints the local IP address assigned to the ESP8266 by the router**

```cpp
Serial.println(WiFi.localIP());
```

!!! Example 

    ```192.168.1.100``` (your IP will vary)

**J. The ```loop()``` function runs repeatedly after ```setup()```**

```cpp
void loop() {}
```

## Key points 

!!! Info 

    - Make sure to double-check ssid / password
    - Ensure the Wi-Fi is 2.4 GHz (ESP8266 doesn't support 5 GHz)
