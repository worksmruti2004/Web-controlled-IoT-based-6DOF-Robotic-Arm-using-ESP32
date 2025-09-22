# 6DOF-Robotic-Arm-using-ESP32






### Web-controlled-IoT-based-6DOF-Robotic-Arm-using-ESP32
Here is an elaborated version of the theoretical explanation, aligned with your IoT-Based Wi-Fi Controlled 6 DOF Robotic Arm project. This expanded version includes deeper insights into control theory, servo operation, system architecture, and practical implications.

Robotics combines mechanical systems, electronics, and control logic to replicate or augment human tasks through automation. Among the most versatile robotic mechanisms is the robotic arm, inspired by the biomechanics of the human arm. It finds wide usage in manufacturing, medical operations, hazardous environment handling, and educational purposes. This project focuses on the design and implementation of a 6 Degrees of Freedom (DOF) robotic arm, controlled wirelessly via an ESP32 microcontroller using Wi-Fi and a web-based interface.

The 6 DOF robotic arm is designed to move in six independent axes: base rotation, shoulder movement, elbow movement, wrist pitch, wrist rotation, and gripper control. These joints enable the arm to reach any point in a 3D space with high precision. Each joint is actuated using servo motors (MG90S and MG99R), which are ideal for their compact size, torque efficiency, and easy control using PWM (Pulse Width Modulation).
The angular position of each servo motor is governed by the PWM signal it receives:
•	A typical servo motor interprets pulse widths between 1 ms to 2 ms, corresponding to 0° to 180° of rotation.
•	For example, a 1.5 ms pulse usually centers the servo at 90°.
•	The ESP32 generates these PWM signals using its GPIO pins, mapped individually to each servo motor.


Control System Architecture
At the heart of this system is the ESP32, a low-cost, high-performance microcontroller with integrated Wi-Fi and Bluetooth capabilities. The ESP32 serves a dual function:
1.	Web Server Hosting: It creates and hosts an HTML-based user interface accessible via any device on the same network. The interface includes sliders for each joint, allowing the user to send desired angles in real-time.
2.	Signal Processing and Actuation: It processes incoming HTTP requests from the interface and generates corresponding PWM signals to control each servo motor accurately.
This closed-loop system allows for real-time control without the need for external applications, Bluetooth pairing, or cloud dependency. The latency is minimal, and feedback is immediate, creating an interactive and intuitive robotic experience.


Principle of Operation
The fundamental operating principle of this robotic system revolves around translating user inputs into motion, following these steps:
1.	User Input: The user adjusts sliders on the web interface hosted by the ESP32.
2.	Data Transmission: Each slider change sends an HTTP GET request to the ESP32 with updated servo parameters.
3.	PWM Generation: The ESP32 interprets the request and adjusts the PWM signal on the corresponding GPIO pin.
4.	Servo Movement: The servo motor responds to the new PWM signal by rotating to the specified angle, changing the posture of the robotic arm.
5.	Real-Time Feedback: The change is reflected immediately in the physical position of the arm, creating an interactive control loop.
Stability and Safety Considerations
•	Dual Power Supply: The project uses separate 5V power supplies for high-torque and standard servos, preventing voltage drops and ensuring consistent operation.
•	Ground Reference Sharing: All components share a common ground to maintain signal integrity.
•	Mode Selection: A "Control Mode" enables servo activation, while a "Standby Mode" deactivates all motors to save power and prevent wear.
•	Web Security: Optional user authentication can restrict unauthorized access to the robotic control interface


## Components Required 📋

Component	Quantity	Description
<img width="922" height="312" alt="image" src="https://github.com/user-attachments/assets/36251ce8-d6fb-4440-8922-74b61ed39df4" />

## Getting 3D Printed Robo Arm & Assembly
Assembling the Robo Arm is a straightforward process as it is entirely 3D printed in small parts. With a few components and simple instructions, the entire arm can be easily put together. The required components are:

3* MG995 Servos (180-degree rotation)
Few Nuts and Bolts of different Sizes.
The screws and horns for installing Servos are available in the servos kit, and the rest part can be assembled easily by Nuts and Bolts, which you will get easily inside the whole Robotic Arm Kit from your vendor.

The Assembly process requires a little bit more attention for the perfect fitting of the servo’s arms with their correct rotational angle of 180 degrees. You can refer to the blog and YouTube videos of How To Mechatronics by using the Link.

You will find the easy and simplest way to assemble the whole Arm there. Also, you will get the link for the STL files for your 3d design model, if you wish to design it from Scratch.

The below image gives an idea about the looks of the final assembled product.
<img width="516" height="505" alt="image" src="https://github.com/user-attachments/assets/50857f4e-3db8-43f4-9725-ebd66469e4c9" />

## Block Diagram
The proposed system “IoT-Based Robotic Arm Control using ESP32” enables real-time wireless control of a robotic arm through a locally hosted web interface. The core component is an ESP32 microcontroller that acts as both the Wi-Fi server and the controller for the servo motors of the arm. Here’s how it works:
•	When powered, the ESP32 creates a Wi-Fi hotspot or connects to an existing Wi-Fi network.
•	A webpage hosted on the ESP32 contains sliders for each servo motor representing the arm’s degrees of freedom (typically 5 or 6 DOF).
•	When a user adjusts a slider on the page, a JavaScript function sends the new angle via HTTP request to the ESP32.
•	The ESP32 receives these values and updates the respective PWM signal to the servo motor, adjusting the arm's position in real-time.
•	As the entire system operates over a local network, there is no latency from cloud-based services, ensuring fast and accurate movements.


<img width="789" height="724" alt="image" src="https://github.com/user-attachments/assets/e982df02-9a5c-4e69-a82a-f8cc85f891f6" />

## Flow Chart
The flowchart outlines the operation of the IoT-based Robotic Arm using ESP32. The system starts by initializing the ESP32 and servo motors, then connects to a Wi-Fi network and launches a web server. Users control the arm via a web interface, where slider inputs send HTTP requests to the ESP32. It processes these commands and generates PWM signals to move the respective servos in real time. This cycle continues until the system is powered off or enters standby mode.


<img width="923" height="1049" alt="image" src="https://github.com/user-attachments/assets/2790dbfa-0f87-4543-a16d-0f1718ab6d66" />


## Circuit Diagram for ESP32 based Robotic Arm
The circuit connections are pretty simple, just connect each servo +ve & -ve terminal to the power supply. For powering our Servos, I am using a Micro-USB female connector which works on 5 volts and can able to draw the sufficient current required for servos. Micro-Usb female jack can be connected to any USB generic Adaptor.

We are using the same outer power source to power the ESP32, in which the +ve is connected to Vin and the -ve terminal to the GND of the ESP32.
USE 2 SMPS for power supply
5V-2Amps for SG90 Servo Motor and Esp 32
5V-10Amps for MG995 Servo Motor

<img width="1024" height="497" alt="image" src="https://github.com/user-attachments/assets/0df44617-cfa4-40ad-af03-a7a9a0887fe9" />

Each control Signal pin of the Servo is connected to the Digital PWM pins of the ESP32. We are using Six Servos of which three of them are MG995 high torque and rest three are SG90 servos. I have connected signal pins to 14,27,26,25,33,32 digital pins of the board. You can also use other pins, but make sure that it supports PWM (Pulse width Modulation) and that it is properly assigned inside the code.

Note: Do not power the Servos directly from ESP32, doing so will results in damaging the board.

Make All the connections to the perf board by using Male/Female headers for attaching separately Microcontroller board & jumper wires without direct soldering. Also, be careful about short-circuiting while soldering.

ESP32 was connected to a vero board
<img width="435" height="364" alt="image" src="https://github.com/user-attachments/assets/cf55ccd2-4ea9-4c1e-a0c3-be5a57a4c081" />

ESP32 was connected to a vero board
<img width="468" height="373" alt="image" src="https://github.com/user-attachments/assets/eb78a6c2-cbbc-4474-a3aa-ce38a5731190" />

Power supply unit
<img width="447" height="363" alt="image" src="https://github.com/user-attachments/assets/a0de0077-32a4-4e61-96a1-299f07623167" />

Power supply back side
<img width="468" height="350" alt="image" src="https://github.com/user-attachments/assets/d7fca3c6-edb1-46ff-8e49-2d867d45129a" />

Connector unit for servo motor
<img width="486" height="400" alt="image" src="https://github.com/user-attachments/assets/7af5c811-c37f-4b0c-bd6c-d31bf7a876d0" />

Servo connection
<img width="469" height="404" alt="image" src="https://github.com/user-attachments/assets/353c5710-b2a6-49d6-9605-7d68cc7046fa" />

Final Assembly
<img width="461" height="398" alt="image" src="https://github.com/user-attachments/assets/ccdec079-7645-4b2d-b139-fe3177119819" />

Arm function
<img width="454" height="388" alt="image" src="https://github.com/user-attachments/assets/19248729-d6ae-4a5d-8cd2-4db99fff811d" />


After all the setup and connections of the servos to the controller board, the final RoboArm is ready to proceed with the programming section.


## Programming the ESP32 for Robotic Arm

The program uses the WiFi capabilities of the Esp to connect with a WIFI connection through which we can further able to control the RoboArm using our webpage. We will also learn about creating the webpage and controlling all the motions of the Arm.
To ensure successful program execution, we first include the necessary libraries: Servo.h and WiFi.h. The Servo.h library is utilized to control servo motors by providing the appropriate PWM signal based on the desired angle.
We create six different objects of the Servo class, each with a unique name, as we are using six distinct servos.
Furthermore, we define six additional variables to assign the control pins of the microcontroller. It is essential to verify the hardware connections before assigning PINs to avoid incorrect servo functionality.
The Wi-Fi credentials are defined using a pointer variable named "ssid" and “password”. These credentials are necessary for establishing a successful connection to a wireless network.
Following that, an instance of the WiFiServer object is created, named "server", with the HTTP port number 80 passed as an argument.


### <> Additionally, the code declares variables to store the positions of sliders, which will be utilized for controlling the servo motors.

motors.

#include <WiFi.h>
#include <Servo.h>
Servo ObjServo1; // Make object of Servo motor from Servo library
Servo ObjServo2;
Servo ObjServo3;
Servo ObjServo4;
Servo ObjServo5;
Servo ObjServo6;
// Objects are made for every servo motor we want to control through this library
static const int ServoGPIO1 = 33; // define the GPIO pin with which servo 1 is connected
static const int ServoGPIO2 = 25;
static const int ServoGPIO3 = 26;
static const int ServoGPIO4 = 27;
static const int ServoGPIO5 = 14;
static const int ServoGPIO6 = 12;
// Variables to store network name and password
const char* ssid = "IN1b"; // Enter your network name
const char* password = "in@india"; // Enter your network password
// Set the server port number to default 80
WiFiServer server(80);
// Variables to store slider positions
String valueString1 = String(0);
String valueString2 = String(0);
String valueString3 = String(0);
String valueString4 = String(0);
String valueString5 = String(0);
String valueString6 = String(0);
Inside Setup() function, we initialize the serial communication with a baud rate of 115200. Then, we attached each servo motor with the respective digital PWM pins of the Esp32 board. This sets up the communication between the servo motors and the microcontroller, allowing you to control the servo motors' positions.  

We initiate the WiFi connection using the function WiFi.begin() by providing SSID and Password as an Argument. After a Successful connection, it will print the IP Address on the Serial Monitor. Consequently, the WiFi server started using the command server.begin().

void setup() {
  Serial.begin(115200); // Define serial communication with baud rate of 115200
  ObjServo1.attach(ServoGPIO1); // Attach ObjServo1 to ServoGPIO1 pin
  ObjServo2.attach(ServoGPIO2);
  ObjServo3.attach(ServoGPIO3);
  ObjServo4.attach(ServoGPIO4);
  ObjServo5.attach(ServoGPIO5);
  ObjServo6.attach(ServoGPIO6);
  Serial.print("Making connection to "); // Display message on serial monitor
  Serial.println(ssid);
  WiFi.begin(ssid, password);
    while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  // Print the IP address value on serial monitor
  Serial.println("");
  Serial.println("WiFi connected.");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
  server.begin(); // Start the server
}
Inside Loop() function, the code listens for incoming client connections by calling server.available(). If a client connects, a WiFiClient object named “client” is created to handle the communication with that client.

Inside the if (client) block, the code sets up the HTTP response headers and starts constructing the HTML web page to be sent to the client.

void loop() {
  WiFiClient client = server.available();                                    // Listen for incoming clients
  if (client) {                                                                                    // If a new client connects
    String header = client.readStringUntil('\r');
    client.println("HTTP/1.1 200 OK");
    client.println("Content-type:text/html");
    client.println("Connection: close");
    client.println();
    // Display the HTML web page
    client.println("<!DOCTYPE html><html>");
    client.println("<head><meta name=\"viewport\" content=\"width=device-width, initial-scale=1\">");
    client.println("<link rel=\"icon\" href=\"data:,\">");
    client.println("<style>body { text-align: center; font-family: \"Trebuchet MS\", Arial; margin-left:auto; margin-right:auto;}");
    client.println(".slider { width: 300px; }");
    client.println(".button { font-size: 24px; padding: 10px 20px; }</style>");
    client.println("<script src=\"https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js\"></script>");
    client.println("</head><body>");
The HTML web page includes six sets of elements: a heading (‘h1’), a position display (‘span’), a range input (‘input’), and two buttons (‘button’). Each set corresponds to one servo motor. The position display shows the current position of the servo motor, and the range input allows the user to adjust the position. The buttons allow the user to increment or decrement the position by 5 units.

    // Slider 1
    client.println("<h1>ESP32 RoboArm Conrol</h1>");
    client.println("<p>Position 1: <span id=\"servoPos1\"></span></p>");
    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider1\" onchange=\"servo(this.value, 1)\" value=\"" + valueString1 + "\"/>");
    client.println("<button class=\"button\" onclick=\"decrementValue(1)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");
    client.println("<button class=\"button\" onclick=\"incrementValue(1)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");
    // Slider 2
    client.println("<p>Position 2: <span id=\"servoPos2\"></span></p>");
    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider2\" onchange=\"servo(this.value, 2)\" value=\"" + valueString2 + "\"/>");
    client.println("<button class=\"button\" onclick=\"decrementValue(2)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");
    client.println("<button class=\"button\" onclick=\"incrementValue(2)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");
    // Slider 3
    client.println("<p>Position 3: <span id=\"servoPos3\"></span></p>");
    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider3\" onchange=\"servo(this.value, 3)\" value=\"" + valueString3 + "\"/>");
    client.println("<button class=\"button\" onclick=\"incrementValue(3)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");
    client.println("<button class=\"button\" onclick=\"decrementValue(3)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");
    // Slider 4
    client.println("<p>Position 4: <span id=\"servoPos4\"></span></p>");
    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider4\" onchange=\"servo(this.value, 4)\" value=\"" + valueString4 + "\"/>");
    client.println("<button class=\"button\" onclick=\"incrementValue(4)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");
    client.println("<button class=\"button\" onclick=\"decrementValue(4)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");
    // Slider 5
    client.println("<p>Position 5: <span id=\"servoPos5\"></span></p>");
    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider5\" onchange=\"servo(this.value, 5)\" value=\"" + valueString5 + "\"/>");
    client.println("<button class=\"button\" onclick=\"decrementValue(5)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");
    client.println("<button class=\"button\" onclick=\"incrementValue(5)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");
    // Slider 6
    client.println("<p>Position 6: <span id=\"servoPos6\"></span></p>");
    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider6\" onchange=\"servo(this.value, 6)\" value=\"" + valueString6 + "\"/>");
    client.println("<button class=\"button\" onclick=\"decrementValue(6)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");
    client.println("<button class=\"button\" onclick=\"incrementValue(6)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");
JavaScript code is included within the HTML to handle the user interactions with the sliders and buttons. It updates the position display when the slider value changes and makes AJAX requests to the server when the sliders or buttons are interacted with.

    client.println("<script>");
    client.println("var slider1 = document.getElementById(\"servoSlider1\");");
    client.println("var servoP1 = document.getElementById(\"servoPos1\");");
    client.println("slider1.oninput = function() { servoP1.innerHTML = this.value; }");
    client.println("var slider2 = document.getElementById(\"servoSlider2\");");
    client.println("var servoP2 = document.getElementById(\"servoPos2\");");
    client.println("slider2.oninput = function() { servoP2.innerHTML = this.value; }");
    client.println("var slider3 = document.getElementById(\"servoSlider3\");");
    client.println("var servoP3 = document.getElementById(\"servoPos3\");");
    client.println("slider3.oninput = function() { servoP3.innerHTML = this.value; }");
    client.println("var slider4 = document.getElementById(\"servoSlider4\");");
    client.println("var servoP4 = document.getElementById(\"servoPos4\");");
    client.println("slider4.oninput = function() { servoP4.innerHTML = this.value; }");
    client.println("var slider5 = document.getElementById(\"servoSlider5\");");
    client.println("var servoP5 = document.getElementById(\"servoPos5\");");
    client.println("slider5.oninput = function() { servoP5.innerHTML = this.value; }");
    client.println("var slider6 = document.getElementById(\"servoSlider6\");");
    client.println("var servoP6 = document.getElementById(\"servoPos6\");");
    client.println("slider6.oninput = function() { servoP6.innerHTML = this.value; }");
    client.println("$.ajaxSetup({timeout: 1000});");
    client.println("function servo(pos, servoNum) {");
    client.println("$.get(\"/?servo=\" + servoNum + \"&value=\" + pos + \"&\");");
    client.println("}");
    client.println("function incrementValue(servoNum) {");
    client.println("var slider = document.getElementById(\"servoSlider\" + servoNum);");
    client.println("slider.value = parseInt(slider.value) + 5;");
    client.println("servo(slider.value, servoNum);");
    client.println("}");
    client.println("function decrementValue(servoNum) {");
    client.println("var slider = document.getElementById(\"servoSlider\" + servoNum);");
    client.println("slider.value = parseInt(slider.value) - 5;");
    client.println("servo(slider.value, servoNum);");
    client.println("}");  
    client.println("</script>");
    client.println("</body></html>");
If the HTTP request received from the client contains the string "GET /?servo=", it means that the client is sending a request to change the position of a servo motor. The code extracts the servo number and value from the request headers, converts them to integers, and calls the setServoPosition() function to set the corresponding servo motor to the specified value.

After processing the client request, the code disconnects the client using client.stop() and prints a message on the serial monitor to indicate that the client has been disconnected.

    if (header.indexOf("GET /?servo=") >= 0) {
      int servoPosition = header.indexOf("servo=") + 6;
      int valuePosition = header.indexOf("&value=");
      int servoNum = header.substring(servoPosition, valuePosition).toInt();
      int value = header.substring(valuePosition + 7).toInt();
      // Set the servo position
      setServoPosition(servoNum, value);
    }
    client.stop(); // Disconnect the client
    Serial.println("Client disconnected.");
    Serial.println("");
  }
}
The setServoPosition() function is a helper function that takes in the servo number and value as parameters. It uses a switch statement to identify the servo number and sets the corresponding servo motor to the specified value. It also updates the corresponding valueString variable to keep track of the current position of each servo motor.

void setServoPosition(int servoNum, int value) {
  switch (servoNum) {
    case 1:
      ObjServo1.write(value);
      valueString1 = String(value);
      break;
    case 2:
      ObjServo2.write(value);
      valueString2 = String(value);
      break;
    case 3:
      ObjServo3.write(value);
      valueString3 = String(value);
      break;
    case 4:
      ObjServo4.write(value);
      valueString4 = String(value);
      break;
    case 5:
      ObjServo5.write(value);
      valueString5 = String(value);
      break;
    case 6:
      ObjServo6.write(value);
      valueString6 = String(value);
      break;
  }
}
Working of Web-based controlled Robotic Arm
The maximum voltage to withstand both types of Servos (MG995 & SG90) is about 7.2 volts. And by using Micro-USB, you can use any generic 5-volt adaptor with a minimum output current of 2 Amps which is enough to provide sufficient power to all servos.

Once Check the sorting between External +ve and -ve power terminals before powering the board.

Also, check for WiFi credentials SSID, and Password for establishing a successful connection with a network.

Upload the code by selecting the correct board and COM port. Open the Serial monitor in Arduino IDE and set the baud rate as 115200. An IP address will get printed if it is successfully connected to a network.

<img width="750" height="449" alt="image" src="https://github.com/user-attachments/assets/a3bb8bcf-e351-44ca-92d4-242fa2ac8ac3" />

Go to that IP Address in any browser either in Windows or Android by searching the IP Address in Search Bar. You will see an attractive web-interface with sliders and buttons for controlling the Arm.

Note: Make sure the browser device is also connected to the same WiFi Network else no page will be open.

UI Interface for controlling
<img width="620" height="512" alt="image" src="https://github.com/user-attachments/assets/cd4e9512-a2ce-4987-b7a9-4cbb5890aa2d" />

Now, the users can adjust the servo positions using sliders and buttons on the web page, and the changes will be reflected in the physical servo motors.

 

Hope you enjoyed the Project and learned something useful from it. If you have any questions, you can leave them in the comment section below.

## Code

#include <WiFi.h>
#include <Servo.h>

Servo ObjServo1; // Make object of Servo motor from Servo library

Servo ObjServo2;

Servo ObjServo3;

Servo ObjServo4;

Servo ObjServo5;

Servo ObjServo6;

 

// Objects are made for every servo motor we want to control through this library

 

static const int ServoGPIO1 = 33; // define the GPIO pin with which servo 1 is connected

static const int ServoGPIO2 = 25;

static const int ServoGPIO3 = 26;

static const int ServoGPIO4 = 27;

static const int ServoGPIO5 = 14;

static const int ServoGPIO6 = 12;

 

// Variables to store network name and password

const char* ssid = "IN1b"; // Enter your network name

const char* password = "in@india"; // Enter your network password

 

// Set the server port number to default 80

WiFiServer server(80);

 

// Variables to store slider positions

String valueString1 = String(0);

String valueString2 = String(0);

String valueString3 = String(0);

String valueString4 = String(0);

String valueString5 = String(0);

String valueString6 = String(0);

 

void setup() {

  Serial.begin(115200); // Define serial communication with baud rate of 115200

 

  ObjServo1.attach(ServoGPIO1); // Attach ObjServo1 to ServoGPIO1 pin

  ObjServo2.attach(ServoGPIO2);

  ObjServo3.attach(ServoGPIO3);

  ObjServo4.attach(ServoGPIO4);

  ObjServo5.attach(ServoGPIO5);

  ObjServo6.attach(ServoGPIO6);

 

  Serial.print("Making connection to "); // Display message on serial monitor

  Serial.println(ssid);

  WiFi.begin(ssid, password);

 

  while (WiFi.status() != WL_CONNECTED) {

    delay(500);

    Serial.print(".");

  }

 

  // Print the IP address value on serial monitor

  Serial.println("");

  Serial.println("WiFi connected.");

  Serial.println("IP address: ");

  Serial.println(WiFi.localIP());

 

  server.begin(); // Start the server

}

 

void loop() {

  WiFiClient client = server.available(); // Listen for incoming clients

 

  if (client) { // If a new client connects

    String header = client.readStringUntil('\r');

    client.println("HTTP/1.1 200 OK");

    client.println("Content-type:text/html");

    client.println("Connection: close");

    client.println();

 

    // Display the HTML web page

    client.println("<!DOCTYPE html><html>");

    client.println("<head><meta name=\"viewport\" content=\"width=device-width, initial-scale=1\">");

    client.println("<link rel=\"icon\" href=\"data:,\">");

    client.println("<style>body { text-align: center; font-family: \"Trebuchet MS\", Arial; margin-left:auto; margin-right:auto;}");

    client.println(".slider { width: 300px; }");

    client.println(".button { font-size: 24px; padding: 10px 20px; }</style>");

    client.println("<script src=\"https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js\"></script>");

    client.println("</head><body>");

 

    // Slider 1

    client.println("<h1>ESP32 RoboArm Conrol</h1>");

    client.println("<p>Position 1: <span id=\"servoPos1\"></span></p>");

    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider1\" onchange=\"servo(this.value, 1)\" value=\"" + valueString1 + "\"/>");

    client.println("<button class=\"button\" onclick=\"decrementValue(1)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");

    client.println("<button class=\"button\" onclick=\"incrementValue(1)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");

 

    // Slider 2

    client.println("<p>Position 2: <span id=\"servoPos2\"></span></p>");

    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider2\" onchange=\"servo(this.value, 2)\" value=\"" + valueString2 + "\"/>");

    client.println("<button class=\"button\" onclick=\"decrementValue(2)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");

    client.println("<button class=\"button\" onclick=\"incrementValue(2)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");

 

    // Slider 3

    client.println("<p>Position 3: <span id=\"servoPos3\"></span></p>");

    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider3\" onchange=\"servo(this.value, 3)\" value=\"" + valueString3 + "\"/>");

    client.println("<button class=\"button\" onclick=\"incrementValue(3)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");

    client.println("<button class=\"button\" onclick=\"decrementValue(3)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");

 

    // Slider 4

    client.println("<p>Position 4: <span id=\"servoPos4\"></span></p>");

    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider4\" onchange=\"servo(this.value, 4)\" value=\"" + valueString4 + "\"/>");

    client.println("<button class=\"button\" onclick=\"incrementValue(4)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");

    client.println("<button class=\"button\" onclick=\"decrementValue(4)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");

 

    // Slider 5

    client.println("<p>Position 5: <span id=\"servoPos5\"></span></p>");

    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider5\" onchange=\"servo(this.value, 5)\" value=\"" + valueString5 + "\"/>");

    client.println("<button class=\"button\" onclick=\"decrementValue(5)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");

    client.println("<button class=\"button\" onclick=\"incrementValue(5)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");

 

    // Slider 6

    client.println("<p>Position 6: <span id=\"servoPos6\"></span></p>");

    client.println("<input type=\"range\" min=\"0\" max=\"180\" class=\"slider\" id=\"servoSlider6\" onchange=\"servo(this.value, 6)\" value=\"" + valueString6 + "\"/>");

    client.println("<button class=\"button\" onclick=\"decrementValue(6)\"style=\"font-size: 24px; padding: 10px 20px;\">-</button>");

    client.println("<button class=\"button\" onclick=\"incrementValue(6)\"style=\"font-size: 24px; padding: 10px 20px;\">+</button>");

 

    client.println("<script>");

    client.println("var slider1 = document.getElementById(\"servoSlider1\");");

    client.println("var servoP1 = document.getElementById(\"servoPos1\");");

    client.println("slider1.oninput = function() { servoP1.innerHTML = this.value; }");

 

    client.println("var slider2 = document.getElementById(\"servoSlider2\");");

    client.println("var servoP2 = document.getElementById(\"servoPos2\");");

    client.println("slider2.oninput = function() { servoP2.innerHTML = this.value; }");

 

    client.println("var slider3 = document.getElementById(\"servoSlider3\");");

    client.println("var servoP3 = document.getElementById(\"servoPos3\");");

    client.println("slider3.oninput = function() { servoP3.innerHTML = this.value; }");

 

    client.println("var slider4 = document.getElementById(\"servoSlider4\");");

    client.println("var servoP4 = document.getElementById(\"servoPos4\");");

    client.println("slider4.oninput = function() { servoP4.innerHTML = this.value; }");

 

    client.println("var slider5 = document.getElementById(\"servoSlider5\");");

    client.println("var servoP5 = document.getElementById(\"servoPos5\");");

    client.println("slider5.oninput = function() { servoP5.innerHTML = this.value; }");

 

    client.println("var slider6 = document.getElementById(\"servoSlider6\");");

    client.println("var servoP6 = document.getElementById(\"servoPos6\");");

    client.println("slider6.oninput = function() { servoP6.innerHTML = this.value; }");

 

    client.println("$.ajaxSetup({timeout: 1000});");

    client.println("function servo(pos, servoNum) {");

    client.println("$.get(\"/?servo=\" + servoNum + \"&value=\" + pos + \"&\");");

    client.println("}");

 

    client.println("function incrementValue(servoNum) {");

    client.println("var slider = document.getElementById(\"servoSlider\" + servoNum);");

    client.println("slider.value = parseInt(slider.value) + 5;");

    client.println("servo(slider.value, servoNum);");

    client.println("}");

 

    client.println("function decrementValue(servoNum) {");

    client.println("var slider = document.getElementById(\"servoSlider\" + servoNum);");

    client.println("slider.value = parseInt(slider.value) - 5;");

    client.println("servo(slider.value, servoNum);");

    client.println("}");

   

    client.println("</script>");

    client.println("</body></html>");

 

    if (header.indexOf("GET /?servo=") >= 0) {

      int servoPosition = header.indexOf("servo=") + 6;

      int valuePosition = header.indexOf("&value=");

 

      int servoNum = header.substring(servoPosition, valuePosition).toInt();

      int value = header.substring(valuePosition + 7).toInt();

 

      // Set the servo position

      setServoPosition(servoNum, value);

    }

 

    client.stop(); // Disconnect the client

    Serial.println("Client disconnected.");

    Serial.println("");

  }

}

 

void setServoPosition(int servoNum, int value) {

  switch (servoNum) {

    case 1:

      ObjServo1.write(value);

      valueString1 = String(value);

      break;

    case 2:

      ObjServo2.write(value);

      valueString2 = String(value);

      break;

    case 3:

      ObjServo3.write(value);

      valueString3 = String(value);

      break;

    case 4:

      ObjServo4.write(value);

      valueString4 = String(value);

      break;

    case 5:

      ObjServo5.write(value);

      valueString5 = String(value);

      break;

    case 6:

      ObjServo6.write(value);

      valueString6 = String(value);

      break;

  }

}

### ATTACHED FILE
[ROBOTIC ARM (1).docx](https://github.com/user-attachments/files/22452282/ROBOTIC.ARM.1.docx)
[ROBOTIC_ARM_B2( GROUP 5 )_SMRUTI_RANJAN_ROUT (1).pptx](https://github.com/user-attachments/files/22452285/ROBOTIC_ARM_B2.GROUP.5._SMRUTI_RANJAN_ROUT.1.pptx)

