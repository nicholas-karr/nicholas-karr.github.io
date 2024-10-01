---
layout: default
---

<div id="main-name">Hello! I'm Nicholas Karr.</div>
- Embedded Systems + Software Engineer
- Computer Engineering Sophomore at the University of Texas at Dallas
- Member of the Hobson Wildenthal Honors College

## Projects

### [<u>ChessBots Hardware Team Lead</u> (Fall 2023-Present)](https://github.com/Comet-Robotics/chessBot)
- We are building a fleet of 32 waist-height robots that mirror games of chess on a massive board
- I am responsible for hardware programming and part selections. Each robot has a custom PCB, an ESP32, brushed motor controllers, and a variety of basic components to allow them to interact with the field
- Over-the-air updates, sensor feeds, and motor control have been implemented. Robots discover updates through HTTP, and each other through DNS and MDNS
- During this project, I have experienced the full spectrum of bringing up hardware. I've had to investigate failures of digital and analog components with an oscilloscope, measure power usage with a programmable supply, trace faulty connections with a multimeter, and observe WiFi characteristics with a spectrum monitor
- I have simulated multiple subassemblies using LTSpice to understand their behavior better, then verified them on breadboards in the lab with an oscilloscope
- To communicate with a central computer, the robots use the network protocol I finally settled on: newline-separated JSON over TCP. It just can't be beaten for interoperability between disparate teams or reliability

<div id="chessbots-detector"></div>

### [<u>Screen Rotation Utility</u> (Fall 2024)](https://github.com/nicholas-karr/MonitorRotationMemory)
- Applies monitor rotations programmatically to correct an oversight in the Windows 11 multiscreen implementation where rotations are not automatically managed in the same way as resolution and location
- Through heavy use of Win32, it collects lists of monitor names and imposes a state onto them from a config file generated at the user's request
- Suitable for daily use: I rely on it as a service to let me dock my laptop vertically

### [<u>Compiler</u> (Fall 2023)](https://github.com/nicholas-karr/Compiler)
- Compiles a subset of C to LLVM IR, a single static assignment virtual machine language
- Project for the semester-long [<u>UTD Compiler Club</u>](https://charlesaverill.github.io/teaching/ICD)
- Interesting exception-based flow control provided an excellent case for why exceptions should not be used to handle regular flow control. Custom optional objects like Rust, combined with some macros, are much better
- Earned [<u>this cool certificate</u>](https://karrmedia.com/assets/Nicholas-Karr-Compiler-Certification.pdf) from it

### [<u>Roomie</u> (Fall 2024)](https://devpost.com/software/roomie-vp4m6t)
- Won 1st place at HackUTD for hardware and 2nd overall out of 250 teams (It's not AI!)
- NodeJS server collected information from a distributed array of Arduinos attached to motion sensors to monitor whether study rooms had life in them
- This time, I sent single-byte messages over TCP: great for low latency but exceedingly simple use cases. It does make you encode all possible information that a packet could convey as part of its type
- Presented that condensed information on a status page to allow students to find unoccupied rooms
- Taught me the significant value of keeping hardware on hand and knowing how to use it - many hours would have been saved if I had a screen and knew it *worked*. Now, I keep a couple of boxes at all times

<div id="sargon-detector" class="inline-asset">
    <video autoplay loop muted controls class="videoInsert">
    <source src="https://karrmedia.com/assets/sargon-1.mp4" type="video/mp4">
    </video>
</div>

### FIRST Tech Challenge (Fall 2019-Spring 2023)
- [<u>Robocol Wii</u>](https://github.com/nicholas-karr/ftc-robocol)
    - Lets you switch your robot control machine from a boring cell phone to a Nintendo Wii
    - I reverse-engineered an unpacked protocol with no documentation used to drive FTC bots used at thousands of high schools
    - This time, I used Unix socket pooling and an array of handler functions, with each sharing behavior through CRTP
    - The Nintendo Wii is not a viable server development platform, as it turns out. The Unix sockets implementation is inefficient (DevKitPro put memory allocation on every send) and is emulated with considerable annoying latency on desktop. I've since moved on to embedded platforms that offer actual advantages in exchange for lower clock speeds, and still let you use Wiimotes

- [<u>Hotpatch</u>](https://github.com/nicholas-karr/ftc-hotpatch) 
    - Significantly accelerates the development lifecycle of FTC robots by allowing live code replacement without rebooting
    - A Java program generates a new APK through Android Studio, then extracts the pertinent class files and drops them onto a robot's remotely mounted filesystem through wireless ADB
    - A service running in the program to be patched watches a file to see when an update is available, then loads it as a set of Java classes
    - All program state is copied through reflection to make the experience seamless - no rerun required!
    - This made it easier to quickly iterate and debug code, which made my life much easier for the next bullet

- [<u>Sargon Robotics 20181</u>](https://github.com/nicholas-karr/Sargon-FTC-Energize)
    - The actual robot I made all those programs for won the regional ARM Control Award [<u>(see winning presentation)</u>](https://karrmedia.com/assets/Nicholas-Karr-Control-Award-Submission.pdf), and is shown driving itself on the side. That award is dedicated to excellence in sensor use and automation
    - I designed and manufactured two "odometry wheels" that tension to the ground and collect detailed positional information to locate the robot on the field at any time
    - Uses spline paths to navigate without human intervention, while moving extending arms (also position tracked) to manipulate field elements
    - When a human (me) is driving it, the algorithms offset some of the active work by automating claw and arm alignment, which let me focus on navigation
    - It also used a bit of OpenCV to recognize game elements, which was nontrivial to implement using the limited resources of Android and Java.

### Garage Door Server (Fall 2021)
- Combined hardware-software project that let an authenticated PHP page open my house's garage door
- It consisted of a PHP script that made HTTP calls to a C++ backend, which did authentication and dispatched requests to local microcontrollers
- This was my second attempt at a client-server packet protocol. I went with UDP for its discrete packets, and a simple fixed width header and contents. I didn't have any problems with it (from UDP anyway, systemd is another story), but UDP without a retransmit protocol was not the right choice for essential packets sent over WiFi. The next time I got to implement my own protocol, I moved to TCP for its guaranteed transmission and ordering
- The hardware itself was an ESP8266 running a simple Arduino packet parsing loop with a periodic heartbeat
- In my home, this has since been replaced by the Home Assistant-compatible ESPHome (writing Home Assistant extensions is not fun)
- The connection with the garage door opener was originally a relay that simulated the simple closing of the button circuit, but in order to defeat new radio encryption it instead powers and simulates a button press on a code generator remote

## Experience

### Full Stack Intern at The University of Kansas Medical Center (Summer 2023, 2024)
- One of my apps has been published in app stores! Check it out on [<u>Android</u>](https://play.google.com/store/apps/details?id=edu.kumc.alzheimersinfo) or [<u>iOS</u>](https://apps.apple.com/us/app/dementia-careassist/id6463645164)
- Summer 2024:
    - I made an app to collect information from cancer patients over time for statistical analysis
    - It also integrates an analysis backend suitable for applying everything from sorts to custom queries to a database
    - Since it's in Ionic, it is easily available on every major platform. For example, adding an installable web app version took under a day
    - I learned that C# is easily the best backend language ever created. Static typing combined with a rich library ecosystem made it much faster to prototype - a rarity with the embedded or JavaScript based systems I'm usually on
- Summer 2023:
    - I made an app to better inform caretakers about dementia.
    - Initially, the app was specified to use a backend server. I recognized that there are many ways to present information, especially when it is highly static. I moved to a multi-layer caching approach that supported document versioning from both the app store and remote updates. This also made offline use possible, which is something I wish a lot of wikis could do.
    - I have used, and will continue to use, the approaches I prototyped there. Hashed ZIP files synced over HTTP are a very comfortable format for updating applications in the field
    - I also prototyped simplifying configuration through YAML, which I have used on every project possible afterwards. You start with an easy to read and edit config file, then translate it into importable JSON at compile time

### Intern at Oracle Health / Cerner (Spring 2022)
- I prototyped how they could introduce Terraform infrastructure-as-code to their servers to simplify service management
- Additionally, I wrote Sentinel rules to restrict how infrastructure scripts stored in GitHub could be changed by developers, to make multiple perspectives mandatory
- If I ever get a chance to work with infrastructure again, I would try to use Terraform or an equivalent software. The potential of not having to do significant work if a server goes down is appealing to me. Also, it gave me ideas about immutability that I'm still applying today. The commands required to make code work should be auditable and testable wherever possible

This page looks better on the desktop. Thanks for reading!