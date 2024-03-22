# Scanner Bot
## Senior Capstone Project: AmazonRobotics Group 2 
## Peter Gansallo, Melidem Nwokolo, Ayomide Okeshola, Sarim Faruque, Darius Tollett


## Project description

Our problem statement: 
- In package warehouses, one of the more strenuous positions is that of package handlers moving numerous boxes out of trucks.
  - This important and fast-paced role in the process of bringing the product to the customer has many points of error between strain and injury on the employee as well as damage to products. 

Our solution would be to:
- We are designing a robot that will have the perception & motion capabilities necessary to record and process objects between locations.
- The robot will be capable of entering package trucks
- Scanning packages for inventory
- Reporting their location and product information for further processing throughout the warehouse


## Technical details

We are using a university-owned Turtlebot 4 for our project; the Raspi 4B in it runs Ubuntu 22.04 w/ ROS2 Humble pre-installed. Communication was designed between it and laptops running native desktop versions of Ubuntu 22.04 LTS.
The Turtlebot 4 User Manual was quinnessential for us: https://turtlebot.github.io/turtlebot4-user-manual
Currently we are using zbar_ros for the barcode scanning functionality: https://github.com/ros-drivers/zbar_ros/tree/humble

The IP as of typing this is 10.42.0.1. Once you connect to the Turtlebot's WiFi access point w/ username/password 12345678, connect to the Create 3 by typing the IP + localhost in the browser. 

The Create 3 is connected physically to the Raspi 4B with a large ribbon cable & USB. It only supports 2.4GHz WiFi and we've struggled due to that fact for a long time now, as the Raspi 4B doesn't easily connect to 2.4GHz networks either. 

Extensive research was done and it may be possible this is due to what channels/wifi networks the Raspi can reach; efforts were made to make either 1. a 2.4GHz hotspot that works on the proper WiFi channels the Raspi can connect to, or 2. buying and using an external wifi adapter for the Raspi. We sometimes had the Raspi connect properly to a phone hotspot, and then our laptops were able to access the robot's sensors that way, but the bandwidth was really poor and we were still relying on someone to have their phone hotspot on at all times. 

Our tentative solution ended up being a Simple Discovery connection using the Turtlebot's Access Point mode, as the Raspi & Create 3 can be configured to be visible on the Raspi's dual-band network. We're using Simple Discovery & rmw_fastrtps_cpp
