# IoTMotionSensor

This is my first attempt with IoT and I created IoT enabled motion sensor. So I am going to briefly explain how I went about it.
The goal was to detect an object near a sensor, change LED status to indicate that some object has come in the vicinity of sensor and also send a push notification to android mobile phone.

It requires both hardware and software components. In hardware, I have used a PIR motion sensor, ESP8266 WiFi board, A breadboard, Red and Green LED strips and 1k ohm resistors, a laptop, USB cable, 5V/2A DC power adapter. These components will be available at any online shopping portal (like amazon) or at your local electronics hobby shop. In Software, I had installed Arduino IDE, ESP8266 library and Android Studio on my Windows 7 32-bit laptop. I have also used IBM Bluemix and Google Firebase cloud platforms for sending communication from sensor to mobile.

**The Circuit**
Connect ESP 8266 board to laptop via USB and Select WeMos board in Arduino IDE. The board should lit up a blue LED on it.
Connect PIR VIN — ESP8266 5V, PIR GND — ESP 8266 GND, PIR Digital Out — ESP 8266 D3.
Connect +ve leg of external Red LED to resistor and resistor to ESP 8266 D5 and -ve leg to GND of ESP 8266. Connect +ve leg of external Green LED to resistor and resistor to ESP 8266 D6 and -ve leg to GND of ESP 8266. Utilize breadboard to do these connections.

**Programming**
Once the circuit is complete, programming part starts. Open Arduino IDE and create new sketch. Write a program to interface with PIR sensor and light up the Red LED when no object is near the sensor. Add a condition to light up Green LED when any object is near to sensor and switch off the Red LED. You will get plenty of code examples on google to do this. [Here is one example](https://playground.arduino.cc/Code/PIRsense/).

Create a IBM Bluemix account and create an IoT platform starter app. Note down the keys and add these keys in the Arduino sketch where you are calling the Bluemix service.

We also create push notification service on Bluemix and provide Firebase cloud messaging project details in it. The push notification app guid and client secret needs to be part of your android app. Open android studio and create a simple app with one imageview and buttons for registering the device and resetting app. You will get examples of this code as well in various free e.g. [github repositories](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush).

Once the app is created, you need to install it on your android phone. Thats it. With this I was able to send PIR sensor data to my android phone and also indicate LED changes based on sensor data changes.

Hope this will give you an idea on how to proceed with your IoT journey. Thanks for reading this.
