---
layout: default
---

Hello! I'm Nicholas Karr.
* Embedded Systems + Software Engineer
* Computer Engineering Sophomore at the University of Texas at Dallas
* Member of the Hobson Wildenthal Honors College

## Portfolio

### [<u>ChessBots Hardware Team Lead</u> (F23-Present)](https://github.com/Comet-Robotics/chessBot)
<div id="chessbots"></div>
- We are building a fleet of 32 waist-height robots that mirror games of chess on a massive board
- I am responsible for hardware programming and part selections. Each robot has a custom PCB, an ESP32, brushed motor controllers, and a variety of basic components to allow them to interact with the field.
- Over-the-air updates, sensor feeds, and motor control have been implemented

### [<u>Screen Rotation Utility</u> (F24)](https://github.com/nicholas-karr/MonitorRotationMemory)
- Applies monitor rotations programmatically to correct an oversight in the Windows 11 multiple monitor implementation where rotations are not automatically managed in the same way as resolution and location
- Through heavy use of Win32, collects lists of monitor names and imposes a state onto them from a config file generated at the user's request
- Suitable for daily use: I use it as a service to let me dock my laptop vertically

### [<u>Compiler</u> (S24)](https://github.com/nicholas-karr/Compiler)
- Compiles a subset of C to LLVM IR, a single static assignment virtual machine language
- Project for the semester long [<u>UTD Compiler Club</u>](https://charlesaverill.github.io/teaching/ICD/)
- Interesting exception-based flow control that provided an excellent case for why exceptions should not be used to handle regular flow control. Custom optional objects like Rust, combined with some macros, are much better.
- Earned [<u>this cool certificate</u>](https://karrmedia.com/assets/Nicholas-Karr-Compiler-Certification.pdf) from it

### [<u>Roomie</u> (F24)](https://devpost.com/software/roomie-vp4m6t)
- Won 1st place at HackUTD for hardware and 2nd overall out of 250 teams
- NodeJS server collected information from a distributed array of Arduinos attached to motion sensors to monitor whether study rooms had life in them
- Presented that information on a status page to allow students to find unoccupied rooms

### FIRST Tech Challenge (F19-S23)
- [<u>Robocol Wii</u>](https://github.com/nicholas-karr/ftc-robocol)
    - I implemented an unpacked binary protocol without documentation to drive robots used at thousands of high schools
    - This time, I used Unix socket pooling and CRTP with an array of handler functions 
    - The Nintendo Wii is not a viable server development platform, it turns out. The Unix sockets implementation is inefficient (DevKitPro put memory allocation on every send) and is emulated with considerable latency on desktop. I've since moved on to embedded platforms that offer actual advantages in exchange for low speeds, and still let you use Wiimotes.

- [<u>Hotpatch</u>](https://github.com/nicholas-karr/ftc-hotpatch) 
    - Significantly accelerates the development lifecycle of FTC robots by allowing live code replacement without rebooting
    - A Java program generates a new APK through Android Studio, then extracts the pertinent class files and drops them onto a robot's remotely mounted filesystem through wireless ADB
    - A service running in the program to be patched watches a file to see when an update is available, then loads it as a set of Java classes
    - All program state is copied through reflection to make the experience seamless - no rerun required!
    - This made it easier to quickly iterate and debug code

- [<u>Sargon Robotics 20181</u>](https://github.com/nicholas-karr/Sargon-FTC-Energize)
    - The actual robot I made all those programs for won the regional ARM Control Award [<u>(see winning presentation)</u>](https://karrmedia.com/assets/Nicholas-Karr-Control-Award-Submission.pdf), and is shown driving itself on the left. That award is dedicated to excellence in sensor use and automation.
    - I designed and 3d printed two "odometry wheels" that tension to the ground and collect detailed positional information to locate the robot on the field at any time
    - Uses spline paths to navigate without human intervention, while moving extending arms (also position tracked) to manipulate field elements
    - When a human (me) is driving it, the algorithms offset some of the active work of play by automating claw and arm alignment
    - It also used a bit of OpenCV to recognize game elements, which was nontrivial to implement using the limited resources of Android and Java
    - I did most of the work on this robot, so I'm glad 
<div id="sargon"></div>

### Garage Door Server (F21)
- Combined hardware-software project that let an authenticated PHP page open my houses' garage door
- It consisted of a PHP script that made HTTP calls to a C++ backend, which did authentication and dispatch to local addresses
- This was my second attempt at a client-server packet protocol. I went with UDP for it's discrete packets, and a simple fixed width header and contents. I didn't have any problems with it, but UDP without a retransmit protocol was not the right choice for essential packets sent over WiFi. The next time I got to implement my own protocol, I moved to TCP for its guaranteed transmission and order.
- The hardware itself was an ESP8266 running a simple Arduino packet parsing loop with a heartbeat
- In my home, this has since been replaced by the Home Assistant-compatible ESPHome (writing Home Assistant extensions is not fun)
- The connection with the garage door opener was originally a relay that simulated the simple closing of the button circuit, but in order to defeat new radio encryption it instead powers and simulates a button press on a code generator remote.

## Experience

### Full Stack Intern at The University of Kansas Medical Center (Summer 23, 24)
- One of my apps has been published on app stores! Check it out on [<u>Android</u>](https://play.google.com/store/apps/details?id=edu.kumc.alzheimersinfo) or [<u>iOS</u>](https://apps.apple.com/us/app/dementia-careassist/id6463645164).


### Oracle Health / Cerner (Spring 22)

### SMSD Farm Hand (Summer 21, 22)
