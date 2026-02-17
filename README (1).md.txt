# IoT Based Fall Detection System Using ESP8266 and MPU6050

## 1. Introduction

This project presents the design and implementation of an IoT-based Fall
Detection System using the Wemos D1 Mini (ESP8266) and the MPU6050
accelerometer and gyroscope sensor. The system is capable of detecting
sudden falls based on motion analysis and transmitting real-time data to
a web-based dashboard for remote monitoring.

The objective of this project is to develop a reliable and
cost-effective fall detection mechanism suitable for elderly monitoring,
patient safety systems, and wearable health applications.

------------------------------------------------------------------------

## 2. System Overview

The system continuously monitors acceleration and angular velocity using
the MPU6050 sensor. A fall event is detected by analyzing:

1.  A sudden drop in acceleration (free fall condition).
2.  A sharp acceleration spike indicating impact.
3.  High angular velocity indicating abrupt rotation.

When a fall is detected:

-   A buzzer is activated locally.
-   Angular velocity data is transmitted to the IoT server.
-   The system remains accessible for remote monitoring via a web
    dashboard.

The IoT dashboard also allows remote control of a digital output pin
(D7) through a web interface.

------------------------------------------------------------------------

## 3. Hardware Components

-   Wemos D1 Mini (ESP8266)
-   MPU6050 Accelerometer and Gyroscope Module
-   Buzzer
-   Breadboard
-   Jumper Wires
-   3.3V Power Supply

------------------------------------------------------------------------

## 4. Circuit Connections

### MPU6050 to Wemos D1 Mini

  MPU6050 Pin   Wemos D1 Mini Pin
  ------------- -------------------
  VCC           3.3V
  GND           GND
  SDA           D2
  SCL           D1

### Additional Components

  Component                      Wemos Pin
  ------------------------------ -----------
  Buzzer                         D5
  Digital Output (IoT Control)   D7

------------------------------------------------------------------------

## 5. Software and Libraries

The following libraries are required:

-   ESP8266WiFi
-   ESP8266HTTPClient
-   MPU6050_tockn
-   Wire

The system is programmed using the Arduino IDE. The board selection
should be: LOLIN (Wemos) D1 R2 & Mini.

------------------------------------------------------------------------

## 6. IoT Communication

The system communicates with a web server using HTTP requests.

### Write Angular Velocity Data

http://iot.roboninja.in/index.php?action=write&UID=DS07&Angular_Velocity=value

### Read Digital Pin State (D7)

http://iot.roboninja.in/index.php?action=read&UID=DS07&D7

The dashboard updates angular velocity every second and allows remote
toggling of the D7 pin.

------------------------------------------------------------------------

## 7. Fall Detection Algorithm

The fall detection logic is based on magnitude calculations:

1.  Acceleration Magnitude = sqrt(ax\^2 + ay\^2 + az\^2)
2.  Gyroscope Magnitude = sqrt(gx\^2 + gy\^2 + gz\^2)

A fall is detected when:

-   Acceleration magnitude falls below 0.5g (free fall stage), and
-   Followed by either:
    -   Acceleration magnitude greater than 2.5g (impact), or
    -   Gyroscope magnitude greater than 250 degrees/second (sudden
        rotation).

This combined approach reduces false positives compared to
single-threshold detection.

------------------------------------------------------------------------

## 8. System Operation

1.  Power on the device.
2.  The MPU6050 performs gyro calibration (sensor must remain still).
3.  The ESP8266 connects to the configured WiFi network.
4.  Sensor data is continuously monitored.
5.  In case of a fall event, the buzzer is activated and data is updated
    to the server.
6.  The web dashboard displays live angular velocity and allows digital
    output control.

------------------------------------------------------------------------

## 9. Applications

-   Elderly fall monitoring
-   Hospital patient monitoring
-   Smart wearable safety devices
-   Industrial worker safety systems

------------------------------------------------------------------------

## 10. Future Enhancements

-   Integration with GSM module for SMS alerts
-   GPS module for location tracking
-   Cloud database logging
-   Mobile application integration
-   Advanced filtering and machine learning-based fall detection

------------------------------------------------------------------------

## 11. Conclusion

The implemented IoT-based Fall Detection System successfully
demonstrates real-time motion monitoring and remote data transmission
using ESP8266. The system combines acceleration and gyroscope data to
improve detection accuracy and provides a scalable foundation for
wearable healthcare and safety monitoring applications.

------------------------------------------------------------------------

## BY DELEENA SARAS FOR LODHA GENIUS PROGRAMME, CONTINUED LEARNING

