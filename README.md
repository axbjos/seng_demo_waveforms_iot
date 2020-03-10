# waveformsIOT
Sample Industrial IOT Project Using the Digilent Waveforms Analog Discovery 2 Data Acquisition Pod

## Hardware

Linux, Windows, Mac, or RaspberryPi Computer

RaspberryPi (as Industrial IoT Monitoring Endpoint Optional)

Arduino Uno (or other Arduino - assumes you know how to use)

Digilent Analog Discovery 2

## Software
* Digilent Waveforms Software (needed for the SDK)
* Python3 Programming Language
* PIP3 Python Package Manager
* NodeJS JavaScript Runtime
* NPM Node Package Manager
* IBM Node-Red Flow-Based Programming Tool
* Mosquitto MQTT Message Queue
* MongoDB NoSQL Database

## Description
The Digilent Analog Discovery 2 data acquistion pod from Digilent is used to monitor voltage levels being generated by Pin 13 on an Arduino (alternates from 0 to 5V using a varying period).

Python is used to create a Waveforms SDK API client that measures the voltages on the two scope channels.  At every reading Python publishes a reading to the MQTT queue using the paho-mqtt client.

Application logic is in IBM Node-Red. The message queue is subscribed to.  When readings appears on the MQTT queue, they are read and stored in a MongoDB collection.

A webpage is created in Node-Read that allows a user to view the most recent Voltage readings.

![Analog Discovery 2](https://media.digikey.com/Photos/Digilent,%20Inc/410-321.jpg)

## Python Setup
Make sure you are using Python3!

Install the latest version of Python3 in Windows.  Make sure Python is part of your PATH.

On macOS and most Linux Distros Python3 is already installed.  To run Python2 code type python <filename.py> and to run Python3 code type python3 <filename.ph>

Check your version by typing in python or python3 --version

Install the Paho-MQTT module for Python3 using PIP3 (PIP on Windows)

pip3 install paho-mqtt --user

## NodeJS Setup

Recommend to use the installation instructions on the nodejs website: *nodejs.org*

Installing using Ubuntu *sudo apt install* could result in a very very old version of Node being installed.

*node --version* to check that NodeJS was installed.

Type in *npm --version* to check that NPM was installed (The Node Package Manager)

## IBM NodeRed
Node-Red is a very easy to use flow-based (and web-based) programming tool.  Node-Red will implement the data collection and web-interface portions of the project.  Node-Red is a JavaScript app that runs on NodeJS.   Install it using NPM

Make sure you are in your Home directory when installing Node-Red:

*cd ~
sudo npm install -g --unsafe-perm node-red*

Run Node-Red by typing in the following:

*node-red*

Point a browser window to:

*http://127.0.0.1:1880*

Verify that Node-Red is up and running.

Press control-c in the terminal window used to launch Node-Red to quit the application.

## Add MongoDb (and MySQL while we're at it) Modules to Node-Red

First change directory to the newly created *.node-red* directory in the Home directory.

Run:  *npm install node-red-node-mongodb*

Also: *npm install node-red-contrib-mongodb3*

## MQTT Message Broker 

MQTT is an open source protocol that is implemented by several different open source projects.

Popular ones include RabbitMQ, ActiveMQ, and Mosquitto.

Here is the entire list:

https://github.com/mqtt/mqtt.github.io/wiki/brokers

A nice lightweight one is Mosquitto:
http://mosquitto.org/download/

Install for the platform of your choice.

### macOS

*brew install mosquitto*

### Ubuntu

*sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa*
*sudo apt update*

## More to Come

