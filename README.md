 # EXPERIMENT-04-INTERFACING-DIGITAL-SENSOR-BH1750-LUX-Light-Intensity-SENSOR-ADXL335-Accelerometer-sensor--WITH-EDGE-DEVELOPMENT-BOARD-

---

### NAME:HARIHARAN A
### DEPARTMENT: CSE-IOT
### ROLL NO: 212223110013  
### DATE OF EXPERIMENT:13.05.2026

---

## **AIM:**  
To interface an **Light-Intensity sensor (BH1750) Accelerometer sensor (ADXL335)** with the **Raspberry Pi 4** and display the sensor readings using Thingzmate cloud.

---

## **APPARATUS REQUIRED:**  
1. Raspberry Pi 4  
2. Light-Intensity sensor (BH1750) and Accelerometer sensor (ADXL335)  
3. Jumper Wires  
4. Breadboard  
5. USB Cable  
6. Computer with Thonny IDE  

---

## **THEORY:**  
<img width="1293" height="744" alt="image" src="https://github.com/user-attachments/assets/3c04afa6-1517-45d2-88f1-e671d9ed1ffb" />

 ### FIGURE-01 RASPI PI 4 PINOUT DIAGRAM: 

The Raspberry Pi 4 Model B is built around a Broadcom BCM2711 system-on-chip that integrates a quad-core ARM Cortex-A72 (64-bit) CPU, VideoCore VI GPU, memory controller, and peripheral interfaces, forming a compact yet complete computer architecture where the SoC connects internally to RAM, USB 3.0 controller, Gigabit Ethernet, HDMI display, and wireless modules. Its 40-pin GPIO header provides a flexible pin configuration consisting of power pins (5 V and 3.3 V), multiple ground pins, and general-purpose input/output pins that operate at 3.3 V logic and can be programmed for digital I/O or alternate functions. Key alternate functions include I²C (SDA, SCL) for sensor communication, SPI (MOSI, MISO, SCLK, CS) for high-speed peripheral interfacing, UART (TX, RX) for serial communication, and PWM for control applications.  For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.This architecture and pin multiplexing allow the Raspberry Pi 4 to act as both a general-purpose computing platform and an embedded controller, supporting rapid prototyping, hardware interfacing, and IoT applications.
## Light-Intensity sensor (BH1750):
BH1750 is a digital ambient light sensor that is used commonly used in mobile phones to manipulate the screen brightness based on the environment lighting. This sensor can accurately measure the LUX value of light up to 65535lx. The BH1750 is a light intensity sensor that can be used to adjust the brightness of display in mobiles and LCD displays. It can also be used to turn the headlights of cars on/off based on the outdoor lighting. The sensor uses I2C communication protocol so that makes it super easy to use with microcontrollers. The SCL and SDA pins are for I2C. There is no calculation needed to measure the LUX value because the sensor directly gives the lux value. Actually, it measures the intensity according to the amount of light hitting on it. It operates on voltage range of 2.4V-3.6V and consumes really small current of 0.12mA. The results of the sensor does not depends upon the light source used and the influence of IR radiation is very less. There are very less chances of any error because the variation in measurement is as low as +/-20%. 

<img width="700" height="303" alt="image" src="https://github.com/user-attachments/assets/8fd74c78-2f6a-4201-aafd-693439b77aad" />

<img width="696" height="404" alt="image" src="https://github.com/user-attachments/assets/8854550e-ba79-457e-aa78-83fb56755964" />

<img width="486" height="118" alt="image" src="https://github.com/user-attachments/assets/120ee6bc-2ef6-467c-91bd-2ffd264cc5ee" />



### FIGURE-02 Light-Intensity sensor (BH1750) BH1750 Sensor Module & BH1750 connection diagram

## Accelerometer sensor (ADXL335):
The ADXL335 is a small, thin, low power, complete 3-axis accelerometer with signal conditioned voltage outputs. The product measures acceleration with a minimum full- scale range of ±3 g. It can measure the static acceleration of gravity in tilt-sensing applications, as well as dynamic acceleration resulting from motion, shock, or vibration. The user selects the bandwidth of the accelerometer using the CX, CY, and CZ capacitors at the XOUT, YOUT, and ZOUT pins. Bandwidths can be selected to suit the application, with a range of 0.5 Hz to 1600 Hz for the X and Y axes, and a range of 0.5 Hz to 550 Hz for the Z axis.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/1fd81121-70aa-4b28-9d54-6b5cf92791f4" />

<img width="435" height="330" alt="image" src="https://github.com/user-attachments/assets/63490620-cc1a-4172-bd55-3a90941e0f99" />

<img width="493" height="103" alt="image" src="https://github.com/user-attachments/assets/26014264-621b-4ca7-9fb8-4c5ffccbee75" />


 ### FIGURE-03 Accelerometer sensor (ADXL335) ADXL335 module & ADXL connection WITH ETS IoT Kit

## Working Principle:
Experiment 4A
The Light-Intensity sensor (BH1750) SDA is connected to one of the GPIO pins of the Raspberry Pi 4.
The Light-Intensity sensor (BH1750) SCL is connected to one of the GPIO pins of the Raspberry Pi 4.
The Python script sets the measure the real time Intensity of light output and shown in Thingzmate cloud with current status and Console.
CIRCUIT DIAGRAM
Connect the Vcc of the Light-Intensity sensor (BH1750) is connected to +5V in Raspberrry Pi4.
Connect the Gnd of the Light-Intensity sensor (BH1750) is connected to Gnd in Raspberrry Pi4.
Connect the OUT to any one GPIO.


Experiment 4B
The Accelerometer sensor (ADXL335) D0 is connected one of the GPIO pins in Raspberry Pi 4.
The Accelerometer sensor (ADXL335) A0 is connected one of the GPIO pins in Raspberry Pi 4.
The Python script sets the Accelerometer sensor (ADXL335) value based on the variation in the acceleration and shown in Thingzmate Cloud and console.
CIRCUIT DIAGRAM
Connect the Accelerometer sensor (ADXL335) Vcc to any +5V.
Connect the Accelerometer sensor (ADXL335) GND to any GND.
Connect the Accelerometer sensor (ADXL335) X_OUT to any one GPIO. 
Connect the Accelerometer sensor (ADXL335) Y_OUT to any one GPIO. 
Connect the Accelerometer sensor (ADXL335) Z_OUT to any one GPIO. 

Experiment 4A
## PROGRAM (Python)
```

from urllib import request
import json
import time
import smbus2
import ssl

# =====================================================
# SSL FIX
# =====================================================

ssl._create_default_https_context = ssl._create_unverified_context

# =====================================================
# BH1750 SENSOR CONFIGURATION
# =====================================================

DEVICE = 0x23
ONE_TIME_HIGH_RES_MODE = 0x20

bus = smbus2.SMBus(1)

# =====================================================
# THINGZMATE CLOUD CONFIGURATION
# =====================================================

API_KEY = "cae825cbe99a4f0ce400d8431c3d5fd3"

URL = "https://iot.saveetha.in:4433/api/v1/device-types/9360/devices/936016/uplink"

# =====================================================
# BH1750 READ FUNCTION
# =====================================================

def read_light():

    data = bus.read_i2c_block_data(
        DEVICE,
        ONE_TIME_HIGH_RES_MODE,
        2
    )

    lux = (data[0] << 8 | data[1]) / 1.2

    return round(lux, 2)

# =====================================================
# START MESSAGE
# =====================================================

print("======================================")
print("BH1750 + ThingzMate Cloud Started")
print("======================================")

time.sleep(2)

# =====================================================
# MAIN LOOP
# =====================================================

while True:

    try:

        # ==========================================
        # READ SENSOR
        # ==========================================

        lux = read_light()

        print("Light Intensity (Lux):", lux)

        # ==========================================
        # CREATE JSON PAYLOAD
        # ==========================================

        payload = {
            "lux": lux
        }

        data = json.dumps(payload).encode()

        print("Payload:", payload)

        # ==========================================
        # HTTP REQUEST
        # ==========================================

        req = request.Request(
            URL,
            method="POST"
        )

        req.add_header(
            "Content-Type",
            "application/json"
        )

        req.add_header(
            "Authorization",
            "Bearer " + API_KEY
        )

        # ==========================================
        # SEND DATA TO THINGZMATE
        # ==========================================

        response = request.urlopen(
            req,
            data=data,
            timeout=10
        )

        # ==========================================
        # RESPONSE
        # ==========================================

        print("======================================")
        print("Cloud Upload Success")
        print("Server Response:", response.read().decode())
        print("======================================")

        time.sleep(5)

    except KeyboardInterrupt:

        print("======================================")
        print("Program Stopped")
        print("======================================")

        break

    except Exception as e:

        print("======================================")
        print("Error:", e)
        print("======================================")

        time.sleep(2)
````

### OUTPUT:
<img width="591" height="1280" alt="image" src="https://github.com/user-attachments/assets/6f23668c-abe3-42fd-a1f0-39ebe1730a41" />


# FIGURE -04 PROGRAM OUTPUT:
<img width="1918" height="1078" alt="Screenshot 2026-05-13 112808" src="https://github.com/user-attachments/assets/16907612-c67b-4288-a933-2501d4cbd180" />



#  FIGURE -05 CONSOLE OUTPUT:
<img width="1918" height="1075" alt="Screenshot 2026-05-13 112839" src="https://github.com/user-attachments/assets/4ea5e21e-2200-4506-8b8e-f928432c3d7b" />


# FIGURE -06 VIsualization:

<img width="1918" height="1075" alt="Screenshot 2026-05-13 113116" src="https://github.com/user-attachments/assets/a4e2b263-ed78-4fbd-9b87-c98339ce5409" />


Experiment 4B
## PROGRAM (Python)
```
from urllib import request
import json
import time
import smbus2
import math
import ssl

# =====================================================
# SSL FIX
# =====================================================

ssl._create_default_https_context = ssl._create_unverified_context

# =====================================================
# MPU9250 / MPU6500 CONFIGURATION
# =====================================================

# Change to 0x69 if your sensor address is 69
MPU_ADDR = 0x68

# MPU Registers
PWR_MGMT_1 = 0x6B

ACCEL_XOUT_H = 0x3B
ACCEL_YOUT_H = 0x3D
ACCEL_ZOUT_H = 0x3F

GYRO_XOUT_H = 0x43
GYRO_YOUT_H = 0x45
GYRO_ZOUT_H = 0x47

# =====================================================
# I2C SETUP
# =====================================================

bus = smbus2.SMBus(1)

# Wake up MPU Sensor
try:

    bus.write_byte_data(
        MPU_ADDR,
        PWR_MGMT_1,
        0
    )

    print("======================================")
    print("MPU Sensor Initialized Successfully")
    print("======================================")

except Exception as e:

    print("======================================")
    print("MPU Sensor Connection Failed")
    print("Check:")
    print("1. Wiring")
    print("2. I2C Enabled")
    print("3. Sensor Address")
    print("4. Power Supply")
    print("--------------------------------------")
    print("Error :", e)
    print("======================================")

    exit()

# =====================================================
# THINGZMATE CLOUD CONFIGURATION
# =====================================================

API_KEY = "01eccef7cad94a15fb2b40e909522d22"

URL = "https://iot.saveetha.in:4433/api/v1/device-types/936016/devices/936016/uplink"

# =====================================================
# READ RAW SENSOR DATA
# =====================================================

def read_raw_data(addr):

    high = bus.read_byte_data(
        MPU_ADDR,
        addr
    )

    low = bus.read_byte_data(
        MPU_ADDR,
        addr + 1
    )

    value = ((high << 8) | low)

    if value > 32768:
        value = value - 65536

    return value

# =====================================================
# START MESSAGE
# =====================================================

print("======================================")
print("MPU9250 / MPU6500 + ThingzMate Started")
print("======================================")

time.sleep(2)

# =====================================================
# MAIN LOOP
# =====================================================

while True:

    try:

        # ==========================================
        # READ ACCELEROMETER
        # ==========================================

        acc_x = read_raw_data(ACCEL_XOUT_H)
        acc_y = read_raw_data(ACCEL_YOUT_H)
        acc_z = read_raw_data(ACCEL_ZOUT_H)

        Ax = acc_x / 16384.0
        Ay = acc_y / 16384.0
        Az = acc_z / 16384.0

        # ==========================================
        # READ GYROSCOPE
        # ==========================================

        gyro_x = read_raw_data(GYRO_XOUT_H)
        gyro_y = read_raw_data(GYRO_YOUT_H)
        gyro_z = read_raw_data(GYRO_ZOUT_H)

        Gx = gyro_x / 131.0
        Gy = gyro_y / 131.0
        Gz = gyro_z / 131.0

        # ==========================================
        # MOTION STATUS
        # ==========================================

        motion = math.sqrt(
            (Ax * Ax) +
            (Ay * Ay) +
            (Az * Az)
        )

        if motion > 1.2:

            status = "MOVING"

        else:

            status = "STABLE"

        # ==========================================
        # DISPLAY VALUES
        # ==========================================

        print("======================================")

        print("Accelerometer")

        print("Ax :", round(Ax, 2))
        print("Ay :", round(Ay, 2))
        print("Az :", round(Az, 2))

        print("--------------------------------------")

        print("Gyroscope")

        print("Gx :", round(Gx, 2))
        print("Gy :", round(Gy, 2))
        print("Gz :", round(Gz, 2))

        print("--------------------------------------")

        print("Status :", status)

        # ==========================================
        # JSON PAYLOAD
        # ==========================================

        payload = {

            "Ax": round(Ax, 2),
            "Ay": round(Ay, 2),
            "Az": round(Az, 2),

            "Gx": round(Gx, 2),
            "Gy": round(Gy, 2),
            "Gz": round(Gz, 2),

            "status": status
        }

        data = json.dumps(payload).encode()

        print("--------------------------------------")
        print("Payload :", payload)

        # ==========================================
        # HTTP REQUEST
        # ==========================================

        req = request.Request(
            URL,
            method="POST"
        )

        req.add_header(
            "Content-Type",
            "application/json"
        )

        req.add_header(
            "Authorization",
            "Bearer " + API_KEY
        )

        # ==========================================
        # SEND DATA TO THINGZMATE
        # ==========================================

        response = request.urlopen(
            req,
            data=data,
            timeout=10
        )

        # ==========================================
        # CLOUD RESPONSE
        # ==========================================

        print("--------------------------------------")
        print("Cloud Upload Success")
        print("Response :", response.read().decode())

        time.sleep(5)

    except KeyboardInterrupt: 

        print("======================================")
        print("Program Stopped")
        print("======================================")

        break

    except Exception as e:

        print("======================================")
        print("Runtime Error :", e)
        print("======================================")

        time.sleep(2)

 



 
````

### OUTPUT:
<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/9f66121c-77c8-45f8-b8e0-e51d3e3584f0" />

<img width="1730" height="973" alt="172 17 159 32 (WayVNC) - RealVNC Viewer 19-05-2026 14_55_08" src="https://github.com/user-attachments/assets/536fc264-b12a-4010-8a12-a9029bbe402a" />

<img width="1920" height="1020" alt="Recent Events _ thingZmate - Personal - Microsoft​ Edge 19-05-2026 14_48_05" src="https://github.com/user-attachments/assets/1cb37150-d957-436b-8728-9c076bf22607" />

<img width="1920" height="1020" alt="Recent Events _ thingZmate - Personal - Microsoft​ Edge 19-05-2026 14_53_53" src="https://github.com/user-attachments/assets/19f5411f-104e-4a3e-b76d-d7e8b5592643" />

<img width="1920" height="1020" alt="Recent Events _ thingZmate - Personal - Microsoft​ Edge 19-05-2026 14_53_59" src="https://github.com/user-attachments/assets/50efc70d-83cb-4730-b7b1-b50d0a9ed071" />

## **RESULT:**  
The **Light-Intensity sensor (BH1750) Accelerometer sensor (ADXL335)** was successfully interfaced with the **Raspberry Pi 4**, and real-time **Intensity of Light and acceleration level in ax,ay,az,gx,gy & gz** were read and displayed in Console and Thingzmate Cloud. 

---

