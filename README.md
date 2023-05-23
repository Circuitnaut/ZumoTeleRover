# ZumoTeleRover

Description: A electric tank track rover that provides a video feed and tank control over a reverse TCP connection allowing anyone in the world with the right URL and credentials to tap into the connection and control the rover. The tank chassis and controls are based off Pololu's Zumo platform, the motor controller Arduino Uno, and the server for the connection as well as the website provided by raspberry pi.

![20210217_224053](https://user-images.githubusercontent.com/3383005/163281605-4ddbc04a-5d8b-4b1b-841a-f43a97b21da4.jpg)


<br>

# Zumo Tele-Rover Instructions

The following document should provide you with everything you need to know to get the Zumo Tele-Rover up and running with a control system that can be accessed from anywhere around the world as long as you have an internet connection and a hunger to explore! 

---

<br>

## <u>Table Of Contents</u>

- [Prep](#prep)
- [Inventory](#inventory-your-parts)
- [BOM](#bom)
- [Set up the Raspberry Pi](#set-up-the-raspberry-pi)
- [Setup the Arduino](#setup-the-arduino)
- [3D Print the Parts](#3d-print-the-parts)
- [Prep the Rover for Assembly](#prep-the-rover-for-assembly)
- [Assemble the Rover](#assemble-the-rover)
- [Setup the Rover Software](#setup-the-rover-software)
- [Operation](#operation)

<br>

## Prep

Before you get started, make sure you have the following ready...

- Computer with ability to plug in an SD card

- Monitor for Raspberry Pi

- Mouse and keyboard for Raspberry Pi

- Phillips or Hex (depending on your fasteners) screw driver

- Soldering iron and solder (or hammer)

--- 

## Inventory your parts

<br>

### Hardware

<u> **Raspberry Pi Computer** </u>
    

<img src="https://user-images.githubusercontent.com/3383005/163280242-ff1b55ea-3cee-4776-bcc1-21e342e2cf6a.png" width="400">


<u> **Micro SD Card with SD card adapter** </u>
 
<img src="https://user-images.githubusercontent.com/3383005/163280266-2af33058-9803-4ae9-b575-decd9d04d155.jpg" width="400">


<u> **Arduino Uno R3 micro controller** </u>
  
<img src="https://user-images.githubusercontent.com/3383005/163280280-83fa904a-190e-41c8-acad-9b4f1d5a4378.jpg" width="400">



<u> **Zumo Robot for Arduino, v1.2** </u>
  
<img src="https://user-images.githubusercontent.com/3383005/163280290-7a48b495-3bdc-4a67-bc80-4f95b9f9b582.jpg" width="400">



<u> **Raspberry Pi Fish-eye Camera** </u>
  
<img src="https://user-images.githubusercontent.com/3383005/163280310-1535243c-cceb-4d2b-a808-ddf15caa0386.jpg" width="400">


<u> **SG90 Servo Motor** </u>
  

<img src="https://user-images.githubusercontent.com/3383005/163280314-c9d543e4-d9e8-44b5-aa2f-c44931bb0c50.jpg" width="400">


<u> **POWERADD Energy Cell Portable USB Charger** </u>
  
<img src="https://user-images.githubusercontent.com/3383005/163280321-bd9ab8c4-c213-4b51-bf47-e2be202650f1.jpg" width="400">



<u>**USB-A to USB-C male to male cable**</u>
  
<img src="https://user-images.githubusercontent.com/3383005/163280341-9804eeeb-99ba-4a13-8261-f2125683fb90.jpg" width="400">



<u>**USB-A to USB-B male to male cable**</u>
  
<img src="https://user-images.githubusercontent.com/3383005/163280355-44c1c8a7-8791-4914-9b6d-0fb46b25b74f.jpg" width="400">



**Header pins**
  
<img src="https://user-images.githubusercontent.com/3383005/163280362-3b61ad12-b006-4a4e-ac0d-ed775540c209.jpg" width="400">



  
  **BOM**

| Item                                      | Where to buy                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Raspberry Pi 4                            | https://www.microcenter.com/product/621439/raspberry-pi-4-model-b---2gb-ddr4                                                                                                                                                                                                                                                                                                                                                                                                     |
| Micro SD Card with SD Card Adapter        | https://www.microcenter.com/product/486146/micro-center-16gb-microsdhc-class-10-flash-memory-card                                                                                                                                                                                                                                                                                                                                                                                |
| Arduino Uno R3                            | https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/ref=sr_1_4?dchild=1&keywords=Arduino+uno+r3&qid=1613677083&sr=8-4                                                                                                                                                                                                                                                                                                                                            |
| Zumo Robot for Arduino, v1.2              | https://www.pololu.com/product/2510                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Raspberry Pi Fish-eye Camera              | https://www.microcenter.com/product/615100/inland-fish-eye-1080p-camera-for-raspberry-pi                                                                                                                                                                                                                                                                                                                                                                                         |
| SG90 Servo Motor                          | https://www.amazon.com/Tower-Pro-SG90-Analog-Servo/dp/B07B8SJQJD/ref=sr_1_2?dchild=1&keywords=tower+pro+sg90+servo&qid=1613677273&sr=8-2                                                                                                                                                                                                                                                                                                                                         |
| POWERADD Energy Cell Portable USB Charger | https://www.amazon.com/POWERADD-EnergyCell-Portable-Smallest-Compatible/dp/B07MS1B8KQ/ref=sr_1_3?dchild=1&keywords=Poweradd+energycell&qid=1613677326&sr=8-3                                                                                                                                                                                                                                                                                                                     |
| USB-A to USB-C male to male cable         | https://www.amazon.com/dp/B085SBKFJR/ref=twister_B085SGW4KK?_encoding=UTF8&psc=1
| USB-A to USB-B male to male cable         | https://www.amazon.com/YCS-Basics-Black-Printer-Scanner/dp/B00B5HS7TI/ref=sr_1_9?dchild=1&keywords=usb-a+to+right+angle+usb-b&qid=1613677849&s=electronics&sr=1-9                                                                                                                                                                                                                                                                                                                |
| Header Pins                               | https://www.amazon.com/Breakaway-Header-Straight-Connector-Prototype/dp/B07BXDYTBP/ref=sr_1_8?dchild=1&keywords=header+pins&qid=1613675782&sr=8-8                                                                                                                                                                                                                                                                                                                                |

### Software

GIthub is a wonderful cloud storage like tool for software that allows you to store, share, and even collaborate on troves of software, programs and files. It's where most of the software for this project is stored and has everything necessary to turn all this gear you now have into a rover you can access over the internet. The following link has software for the Raspberry Pi, Arduino, and even STL files for 3D printing. We will download this on the computer being used to set up and on the Raspberry Pi itself.

- [GitHub - MalcolmD/ZumoTeleRover](https://github.com/MalcolmD/ZumoTeleRover)

---

## Set up the Raspberry Pi

First thing we need to do is setup the Raspberry Pi for operation. It's going to run the standard Raspberry Pi Operating System or Raspberry Pi OS. Lucky enough the fine folks at the Raspberry Pi foundation made it easy for us to get the OS loaded up.

1. Go to [Official Rasperry Pi Software Website](https://www.raspberrypi.org/software/)
   
   1. Go to the *Raspberry Pi OS using Rasperry Pi Imager* and download the program to your computer. 
   
   
![DownloadRPiImager](https://user-images.githubusercontent.com/3383005/163280733-efcd4b73-37de-4bca-812b-b79e65cac7a2.png)


   
   This program is useful for downloading and imaging SD cards with Raspberry pi OS and other operating systems.

2. Once downloaded, install the application, and then run it. You should see the options below.
   
![RPiImagerpng](https://user-images.githubusercontent.com/3383005/163280768-5885abf8-602a-4760-acad-985193dfab69.png)




3. Insert your SD card into the your computer and hit the **CHOOSE SD CARD** button in Raspberry Pi Imager. You should see it in the menu.
   

![ChooseSDCard](https://user-images.githubusercontent.com/3383005/163280792-e7fa9d9d-2421-483c-a28a-d62b4c608022.png)



4. Now hit the **CHOOSE OS** button and hit the top option that should say *Raspberry Pi OS (32-bit)*![](C:\Personal%20Development\Professional%20Work\Zumo\Instructions\RPiImageSelection.png)

![RPiImageSelection](https://user-images.githubusercontent.com/3383005/163280808-e6c80875-5369-4fdd-a699-db0085a4db93.png)


Hit **Yes** to erase everything on the SD card (Assuming you're not using it for anything else.) Then sit back and relax as it bakes a scrumptious Raspberry Pi operating sysem right into your SD card. XD

5. At this point, you are ready to plug the micro SD-card into the Raspberry pi and boot it up!

Raspberry Pi is all baked and ready! 🥧

---

## Setup the Arduino

The Arduino is directly connected to the motors and the arm. We just need to load it up with the software (sketch) that allows it to talk correctly to the raspberry pi when they're connected with the USB cable.

1. FIrst things first, you need to get the Arduino IDE setup on your computer. You can find it here https://www.arduino.cc/en/software

2. Once installed and running, get the Arduino sketch from the [github archive]([GitHub - MalcolmD/ZumoTeleRover](https://github.com/MalcolmD/ZumoTeleRover)) we downloaded from earlier.

3. Unzip the file and you'll find the Arduino sketch at  
   
   `ZumoTeleRover-main\ZumoTeleRover-main\RPi-Arduino Communication\Arduino Side\ZumoMotorControl\`
   
 ![ArduinoSketchPath](https://user-images.githubusercontent.com/3383005/163280968-6d59784d-d6ec-420a-a401-d608755e2a4c.png)



4. Open **ZumoMotorControl.ino** in the Arduino IDE.

5. Plug the Arduino Uno R3 into your computer with the USB-A to USB-B cable.

6. In the Arduino IDE you want to make sure the settings are all set to upload the code to the Arduino. We want to go into **Tools** and check that board is set to *Arduino Uno*. 
   
   - **Note** if you're on Windows you need to make sure that the **COM** is selected for the Arduino Uno. Usually this isn't set by default.
   
   ![ArduinoSetup](https://user-images.githubusercontent.com/3383005/163281060-40926503-3adf-413e-a9c9-a85a2cd1f787.png)

   



7. With any luck you'll now be ready to upload the sketch to your Arduino Uno. Go ahead and hit the **Check** button to first make sure the code compiles without any errors. Then hit the **Arrow** button to upload the board.
   
   ![ArduinoUpload](https://user-images.githubusercontent.com/3383005/163281084-cc1be597-7293-4420-a1f3-599fa78a4a4f.png)




Arduino is now all set! ✔

---

## 3D Print the Parts

There are some parts that we need to 3D print in order to assemble the rover.  You can grab these files from the repository we downloaded for the Arduino at..

`\ZumoTeleRover-main\3D-Print files\`

- You can print all the parts separately, or print the `Complete_Assembly.gcode` to print everything all at once.

| file                    | quantity |
| ----------------------- | -------- |
| top_mount               | 1        |
| bottom_mount            | 1        |
| battery_anchor_cradle   | 1        |
| battery_cradle          | 2        |
| cam_pod_housing         | 1        |
| cam_pod_bulb            | 1        |
| cam_pod_back_cover      | 1        |
| clamped_servo_seat      | 1        |
| double_arm_tslot_insert | 1        |
| full_bisected_rail      | 1        |

---

## Prep the Rover for Assembly

There are only a couple things we need to do to prepare the Rover for Assembly. 

- If you look at the Zumo Robot for Arduino, you'll notice it's already all put together for you. It should look like this...
  
  
![ZumoRobot](https://user-images.githubusercontent.com/3383005/163281101-7f451857-fa61-4f0e-b512-8696b7f75bc4.jpg)



- The first thing we'll want to do is remove the metal bumper. We won't need this. If your Zumo has the line following sensor behind the bumper, we can unplug this at this time as well.

- The next thing we'll need to do is solder some headers at this location. We need to have at least three headers soldered in for **A3**, **5V** and **GND**. This is where we'll plug in our servo arm.
  
  
  ![ZumoExpansionPorts](https://user-images.githubusercontent.com/3383005/163281109-0b03ca09-b4fd-48cb-bdcd-784155008fa1.jpg)




- As the Zumo Robot is right now, you can actually almost start using it. All it needs are some batteries and an Arduino and it can start zipping around on it's own.

- If you install the Arduino, just take note that it plugs in upside down onto the Zumo and the USB and power jack are pointed **away** from where the metal shield was. Be careful to make sure the pins are all lined up when you press down.
  

![ZumoRobotWithArduino](https://user-images.githubusercontent.com/3383005/163281172-73dc6be5-2a8f-46a2-ab17-50fd98e3d61f.jpg)




If you want to mess around with the Zumo right now, feel free to check out some of the stuff it can do. You should be able to search for the Zumo Libraries in the *Manage Libraries* option under *Tools*. We want the **ZumoShield** library.

![ArduinoLibrariesMenu](https://user-images.githubusercontent.com/3383005/163281203-63de043c-03ad-49fe-9e6f-d7c98775f7cb.jpg)


![ZumoLibraries](https://user-images.githubusercontent.com/3383005/163281228-c0d21ecb-192d-431f-9f33-03544ab63e3a.jpg)





---

## Assemble the Rover

Once all of the parts are 3D printed, we're ready to begin assembly of the rover. The end goal is to have something that looks like this...


![20210217_224101](https://user-images.githubusercontent.com/3383005/163281461-fafa1825-7940-4b75-90bf-341836b8088d.jpg)


![20210217_224053](https://user-images.githubusercontent.com/3383005/163281605-4ddbc04a-5d8b-4b1b-841a-f43a97b21da4.jpg)


![20210217_224033](https://user-images.githubusercontent.com/3383005/163281674-07dd43ad-b4cf-4a94-aa69-929de46f9868.jpg)


3D printed parts are *italicized*

1. To start, fasten the Arduino to the *bottom_mount* 3D printed part using the M2x8mm bolts and M2 nuts.
   
![20210217_232549](https://user-images.githubusercontent.com/3383005/163281772-8231c5e3-ec33-4669-88d0-c5de7edf8fd7.jpg)

2. Let's put the camera in *cam_pod_housing*. To do this, we'll actually have to unscrew the fish-eye lens on the camera because the lens won't fit through the opening...
   
   ![IMG_0299](https://user-images.githubusercontent.com/3383005/163281817-3e20f9c8-3a29-4498-82e9-82df219278d5.jpg)
   
   
   ![IMG_0300](https://user-images.githubusercontent.com/3383005/163281820-c8f03372-6008-444f-90b5-f4d54b774e9f.jpg)
   

   
   Put the camera PCB body into the housing and then screw the lens back on. You can then take the *cam_pod_back_cover* and snap it into the back. Then snap the *cam_pod_bulb* into the bottom of the camera.

3. Next take the *battery_anchor_cradle* and screw it in place on the underside of the *top_mount*.
   
   ![20210217_232604](https://user-images.githubusercontent.com/3383005/163281897-52094276-98ba-4d20-8aef-a67d795be83e.jpg)


4. Next it's probably easiest to attach the camera and Raspberry pi at the same time to the *top_mount*. Go ahead and fasten the Raspberry Pi to the *top_mount* with 4 bolts and nuts. Find a spot of your choice around the mounting rim of the *top_mount* and fasten the camera into place. 
   
   **Remember the camera should face away from the USB port on the Raspberry Pi, as that will be the back of the rover.**
   
   ![20210217_232901](https://user-images.githubusercontent.com/3383005/163281917-a9a0c82e-4aa1-4ef4-8cc5-84079594003e.jpg)
   

5. Next we're going to put together the moving arm.
   
   - First, take the servo arm arm attachment that has just the two sides, and we want to focus on the holes that are one away from the tip on both sides.
      
    ![servoattachments](https://user-images.githubusercontent.com/3383005/163281969-bb3ca33d-aebd-4680-acdc-ac146c6f8f6e.jpg)
     
   
   - We will take one of the two pointy screws that the servo came with and thread  into the holes. Drive the screws in and make sure they really widen the holes. 
   
   - Next try to fit two M2 bolts into the holes. If they do, secure the arm into the servo with the smaller screw that came with the servo.
          
     ![20210217_235537](https://user-images.githubusercontent.com/3383005/163282015-0c0ff654-db10-44dc-951d-f8bfd0f6af10.jpg)
     
   
   - Now we can attach the *full_bisected_rail* onto the servo arm. To do this we'll use the *double_arm_tslot_insert*. We need to put two nuts into the recess in the back of this insert like so...
         
     ![0210217_235544a](https://user-images.githubusercontent.com/3383005/163282060-c0b02ed1-7892-4384-ba7f-0c3c585c4ade.jpg)
     
   
   - We can then screw it onto the servo double arm, but not too far! Just enough to where the bolts thread into the nuts.
     
     
     ![20210217_235606a](https://user-images.githubusercontent.com/3383005/163282139-4e389912-9d08-4e3d-aed6-5930cb8652f8.jpg)

   
   - We don't want to screw them in too far, because we will now slide the *full_bisected_rail* onto the the servo assembly.
     
     ![20210217_235800](https://user-images.githubusercontent.com/3383005/163282177-6bc87c8c-d063-4cf2-9d92-a148a1fbc879.jpg)

     
     - Now we can screw in the bolts further until they "bite" into the rail keeping it in place.
- Finally, we can slot the servo into the *clamped_servo_seat* so that the cable comes out of the opening.  At this point we can take the two pointy scews that came with the servo and screw the servo body into the *clamped_servo_seat*. They might be a little tough, but they should be biting into the plastic part pretty good.
  
  <img title="" src="file:///C:/Personal%20Development/Professional%20Work/Zumo/Instructions/Camera%20Pictures/20210218_001614.jpg" alt="" width="258" data-align="inline">
  
  ![20210218_001614](https://user-images.githubusercontent.com/3383005/163283429-ba2a4c07-3327-4109-8288-bfd2194f0855.jpg)


  
  - You also will have to turn the arm around to get a clear shot at screwing those in. One side will definitely have an awkward angle. 😅

- Find a spot on the mount rim of *top_mount* where the arm has full clearance and screw it in.
6. The last step is putting all the pieces together.
   
   - Press the Arduino attached to the *bottom_mount* onto the Zumo Robot.
     
   ![20210217_232946](https://user-images.githubusercontent.com/3383005/163282333-ce66db32-01f5-467c-a832-3eb95ed9594f.jpg)
      
   
   - Place the two *battery_cradle* parts and press them into their mounting position on the *bottom_mount*, leaving the one closest to the USB and power jack of the Arduino open.
          
     ![20210217_233025](https://user-images.githubusercontent.com/3383005/163282362-2095b1a1-a262-439f-827c-e9d1c31a796f.jpg)               
          
   
   - Take the Raspberry Pi top mount assembly and press that into the last *battery_cradle* mounting position so that the USB ports on the Raspberry Pi are pointed the same direction1 as the USB ports on the Arduino. 
   
   - You can now slide the battery into the space between the top and bottom mounts.
     
     ![20210217_224053](https://user-images.githubusercontent.com/3383005/163282456-e85db1c3-c1bd-4d77-8856-4b8d15d3ac8b.jpg)

   
   - The last step is to plug in the camera and the servo arm.
     
     - To see how to plug in the camera go here we want to plug into this connector with the blue tape facing the USB ports. Go [here](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/2) for a better explanation.
       
      ![PiCameraConnector](https://user-images.githubusercontent.com/3383005/163282509-42100ece-9f78-46df-be86-620e99613c49.png)

     
     - As for the servo arm, we want to plug into those headers we soldered (or hammered) earlier. **Yellow -> A3**, **Orange -> 5V**, and **Brown -> GND**.
              
     ![20210218_094824a](https://user-images.githubusercontent.com/3383005/163282521-a54b7f91-2624-410f-ad1a-c9892fa2c7a2.jpg)

   ✨Huzzah!✨The rover is now fully assembled. You can plug in the USB-A to USB-B cable from one of the USB ports on the Raspberry Pi into the Arduino. Now we're ready to put the Rover Software on the Raspberry Pi.      
   
   ![20210218_115919b](https://user-images.githubusercontent.com/3383005/163282578-2498603c-e727-4eb7-b7de-2210d33bdf4f.jpg)

   ![20210218_115615](https://user-images.githubusercontent.com/3383005/163282611-d31aad51-963e-414f-862a-472ae6528681.jpg)

   ---

## Setup the Rover Software

When you bootup Raspberry Pi OS for the first time you'll probably go some initialization settings, but eventually you should end up at the plain old Raspberry Pi desktop...

![RPiDesktop](https://user-images.githubusercontent.com/3383005/163282714-8959f2da-4bf0-484d-adc1-34b12cec8c8f.png)


The first thing we want to do in here is **enable the camera**. To do this...

1. Click on the raspberry icon at the very top left of the screen, and then Go to **Preferences**  and then to  **Raspberry Pi Configuration**.
   
   ![RPIConfiguration](https://user-images.githubusercontent.com/3383005/163282740-3c117084-4a93-438a-86b4-792aafa74756.png)

   
2. The Raspberry Pi Configuration menu should pop up. From here go to the **interfaces** tab and check enable on the Camera.
   
   ![RPIConfigurationCamEnable](https://user-images.githubusercontent.com/3383005/163282756-38832465-dfa3-488a-b4cd-653572385d2a.png)


Next, we need to grab the code from github [repo](https://github.com/MalcolmD/ZumoTeleRover) again, but **this time we need to pull it down onto the Raspberry Pi.**

Let's do this through the terminal using `git`. *Which comes pre-installed :)*

1. Go to the Terminal program that's at the top of the desktop bar.
   
   ![RPITerminal](https://user-images.githubusercontent.com/3383005/163282793-9960fca8-a160-4a22-9313-0d8a0e40e5bf.png)


2. We can use a simple command that basically goes up to the Github repository online and says, "Hey give me a copy of that". Once the terminal is open, immediately type this in.
   
   ```bash
   $ git clone --recurse-submodules https://github.com/MalcolmD/ZumoTeleRover.git 
   ```
   
   **Note**: If you're curious about `--recurse-submodules`, I have a little repo-ception going on, so that just makes sure to also download all the repos I have in my repo.

3. Once the repo downloads, we want to go to the top level of it.
   
   ```bash
   $ cd ZumoTeleRover
   ```

4. If you use `ls` should see a file called `install.sh`. This script will do everything needed to setup the rover for operation.
   
   ```bash
   $ ls
                       
   3D-Print files  install.sh  mjpg-streamer  ngrok  RPi-Arduino Communication  Scripts
   ```
   
   **But Wait!**
   
   Before we run the script we need to give it one argument. There is a unique authentication token that lets us to use the services of **ngrok**  (The company that allows us to host our robot over the internet). We get this from our ngrok account.
   
   <br>
   
	 ![ngrok_token](https://user-images.githubusercontent.com/3383005/163284026-85678ea9-d933-4003-a1ea-99e98411b59b.png)

   
   <br>
   
   
   If at all possible try to copy and paste the code right after the script name before you hit *enter* to run it.  If you can't copy and paste, then you'll have to type it in and well...happy landing. 😅
   
   Regardless it should look like this...
   
   ```bash
   $ ./install.sh <auth_token_here>
   ```

5. ##### Security
   
   Because we're setting up access over the internet, anyone that can get to our URLs (probably by brute forcing guesses) can potentially get inside the Raspberry Pi on the Rover and mess around with our operation. Like with hosting anything over the web we want to put some security measures in place. You'll setup your own username and password to access the Zumo Controls web page.
   
   
   
   During installation process you will  be asked to this *username* and *password*. Type these in for yourself and remember them, as you'll be asked for them at the Zumo controls page.
   
   ```bash
   ...
   Please provide a username to access Zumo Control: <user>
   Please provide a password to access Zumo Control: <pass>
   
   Your user:pass credentials to access the controls page are...
   user: <user>
   password: <pass>
   ...
   ```
   
   

6. Alright! If everything went right, go ahead and reboot the Pi!
   
   ```bash
   $ reboot now
   ```



After it boots back up again, open the terminal again and we should be ready for operation!

---

## Operation

🎉🎊If you got up to this point, congratulations you're on the precipice of Rover exploration! Before we start though we need to make sure we do the following.

- Make sure the switch on the back at the base of the rover is turned **on**

- Make sure the USB-A to USB-B cable is plugged in from the Pi to the Arduino.

- Power the Raspberry Pi with the USB-A to USB-C cable from the Pi to the battery or just power the Pi with the included power supply for now.

To start the rover and expose it to the web go to the terminal and type the following command.

```bash
$ ZumoStart
```

The Output you should see should spit out a bunch of stuff, but then it will repeatedly output the `running zumo...` along with some cryptic looking URLs. These are what exposed to the World Wide Web and can be accessed from anywhere.

URLs Example...
```bash
Running Zumo...
camera: url=https://<bunch of characters>.ngrok.io
control: url=https://<bunch of characters>.ngrok.io
```
<br>


```bash
Running Zumo...
camera: url=https://23fhf4hfsa4.ngrok.io
control: url=https://23fhf4hfsa4.ngrok.io
```

In particular we are interested in the URL for the ***control*** system. You can copy  this URL into your browser, enter your username and password, and then you can access the rover. 

    If you're curious , you can also go to the ***camera*** system URL to see an example webserver that is streaming the camera feed, but we do have that feed running in the control page, as well.



##### *Note*

**Everytime we run `zumostart`, the URLs will change to some other assortment of random characters.**

- For now this will be enough to mess around and test out the rover. For competition time, you'll be provided an actual consistent URL to use.



##### Go Forth!

As long as it outputs `Running Zumo...` and those URLs, the Rover is "live". 

```bash
Running Zumo...
camera: url=https://23fhf4hfsa4.ngrok.io
control: url=https://fe234fga044.ngrok.io

Running Zumo...
camera: url=https://23fhf4hfsa4.ngrok.io
control: url=https://fe234fga044.ngrok.io

Running Zumo...
camera: url=https://23fhf4hfsa4.ngrok.io
control: url=https://fe234fga044.ngrok.io

...
```

To stop the software from runnning and disconnect functionality from the internet we can hit **CTRL-C** on the terminal at any point.



## Resources

- https://github.com/Circuitnaut/ZumoTeleRover
