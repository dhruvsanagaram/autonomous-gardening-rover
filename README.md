# Autonomous Gardening Rover

Team Members:
- dhruvs7
- tmyadam2
- rct4

# Problem

Our group would like to focus on gardening and agriculture. Many people like to maintain home gardens for the fresh produce. However, it is tedious to monitor a home garden, namely the soil quality and irrigation and set up a home garden by planting seeds manually. 

# Solution

Our project is a small autonomous rover that can plant seeds and monitor soil quality. The rover can be operated in two steps. The first involves the rover traversing across the plot and creating a soil quality profile that summarizes the pH, humidity, and temperature, amongst other characteristics. This profile will be shown on a mobile application. The gardener can read the profile and determine how they want to load a detachable supply wheel, which will have a number of compartments storing a variety of seeds, pesticides, and other gardening materials. Then, through the app, the user can configure the plot size and intervals and start the rover’s autonomous movement across the plot.

# Solution Components

## User Input Subsystem

This system will allow users to input the following parameters (assuming the field is a perfect rectangle) using a React Native client accessible through their phone. 

Field length, width (m)
Seed drop interval (m)
Rover starting point (m,m)

Our code will use the field to create a movement plan, which will be uploaded to a BLE server on the ESP32 microcontroller. The rover will execute the movement plan once a button is pressed on the PCB. 

The movement plan will consist of splitting the field up into rows according to the seed drop interval. The rover will traverse across each row in a snake pattern, turning towards the next row once it reaches the end of a row. Our seed dropping mechanism will ensure that the seeds are spread out according to the interval input across each row.

Components:
ESP32 Microcontroller
Button

## Autonomous Movement Subsystem

Explain what the subsystem does.  Explicitly list what sensors/components you will use in this subsystem.  Include part numbers.

Given a predetermined path, the rover would need to use a GPS to track its location and traverse the terrain accordingly. An electronic compass would track the direction of the rover and allow the motors to make corrections as needed. Additionally, we will most likely need a gyroscope and accelerometer to calibrate the movements of the rover, ensuring it traverses and turns at the correct amounts. These sensors will provide feedback to our algorithm, adjusting control to the motors.

3D Printed Chassis

Ultimate GPS Module - 66 channel w/10 Hz updates - PA1616S - MTK3339 Chipset

SEN-12916 Compass

Wheels and motor dc-geared-motor-and-wheel-kit-3-9v-77rpm 

Adafruit 9-DOF Absolute Orientation IMU Fusion Breakout - BNO055

## Dispensing Subsystem

The rover will stop periodically to dispense materials through a supply paddle wheel operated by a servo. The paddle wheel’s compartments can be filled with seeds, pesticides, water, or other gardening materials. When the rover stops, the paddle wheel will turn, and the wheel's bottom will be an open compartment so the material can drop. When the compartments are empty, the car will dock on a mechanical switch that opens a hatch for a dispenser. The dispenser will unload its contents into an angled funnel on the rover, which will feed into the paddle wheel. When the compartments are empty, the rover will autonomously drive to the mechanical switch, and the gardener will fill the dispenser with the required materials.

Components:
3D printed wheel
SG90 9g Micro Servo Motor
Materials Storage Dispenser 

## Soil Monitoring Subsystem

Another subsystem of the smart gardening rover will focus on soil monitoring. This subsystem will use a combination of moisture, pH, and temperature sensors to assess soil conditions in real time. The data collected will help guide the rover’s decisions on when to dispense seeds and water plants or apply treatments such as weed killer solution (plant or fruit based vinegar) to ensure optimal soil quality and conditions for plant growth and weed prevention.

Components:

Moisture Sensor: Adafruit STEMMA Soil Sensor - I2C Capacitive Moisture Sensor

pH Sensor: Atlas Scientific GRAVITY ANALOG ISOLATOR

Temperature Sensor: MCP9808 High Accuracy I2C Temperature Sensor 


## Power Subsystem

The power subsystem for the smart gardening rover will utilize a rechargeable lithium-ion battery pack that can provide consistent energy to the microcontroller, sensors, motors, and dispensing mechanisms. The battery pack will help ensure that the system lasts for a long period and can be recharged as needed, minimizing the cost and need for frequent battery replacements. 

Additionally, to protect the components and manage power distribution effectively, we will create a comprehensive BMS system containing a Battery Management IC to monitor the battery’s health, ensuring that it doesn’t discharge or overcurrent too quickly. A voltage regulator and step-down converters will also be needed to help distribute appropriate battery voltage levels for different components, such as sensors and ESP 32 microcontrollers. Additionally, power from these lithium-ion batteries will be stepped down to a specific voltage for the actuators and motors we plan to implement.

Components:

Rechargeable Lithium-Ion Battery Pack: 10.8V (11.1V) 3500 mAH 10A Lithium Ion Battery with Wire Leads 3S1P from Liion Wholesale
Battery Management IC: TI BQ769X0
Voltage Regulator/Step down: TI MC34063ADR
Power Switch: Standard 2N2222 NPN TO-92 Plastic-Encapsulate Power Transistors

# Criterion For Success

We will place the rover in a dirt field and set the field size to a small rectangular region. Then, we will set our seed interval to a reasonable amount so that the rover will be able to plant multiple times per row for multiple rows.

We will then run the rover and measure how close the seeds are planted to our desired interval. 

For soil analysis, we will check whether our computer receives the data and whether the data is within a reasonable range.




