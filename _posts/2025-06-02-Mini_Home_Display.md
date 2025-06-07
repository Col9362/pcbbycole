---
title: '[IN PROGRESS] Building My First Custom PCB: A Mini Home Display'
date: 2025-06-02
categories: [PCB, Programming]
tags: []     # TAG names should always be lowercase
author: <author_id>
description: My first project, a mini home display that utilizes an lcd as a display that takes sensor inputs
---

<!-- ![Desktop View](/assets/lib/Home-Display/Schematic.png){: w="700" h="400"}

{% include embed/youtube.html id='8RjkiRD_ySs' %} 
5687190801612800-proj-->

## Introduction 
  For my first time designing a PCB, I wanted to keep it small and simple - only including components I could solder by hand without a hot plate or special equipment. My goal was to design something that would actually be useful but would also teach me a lot about a variety of PCB design concepts.

  The result is a mini home display that can toggle between showing the time/date and the temperature/humidity of your environment. It utilizes a standard LCD (Liquid-Crystal Display) to easily and cheaply display information. 
  
  For the brain of the project, I selected  the ESP32-S3-Nano microcontroller developed by Waveshare because of its low price, compactness, USB-C power, and surface mount capabilities. For sensors, I went with a DHT11 for temperature/humidity and Adafruit's DS3231 Real-Time Clock Module to ensure accurate time. 
  
  You can find a detailed parts list below with links to the components I used, as well as links to the documentation for components in the Documentation section below. At the bottom of the post, I've also included the full Arduino Code and the PCB design files so you can build or modify this project yourself! 

## Parts List

| Component                  | Description                                    | Link                                                                                        |
| -------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------- |
| **ESP32-S3-Nano**          | Microcontroller; USB-C powered, surface-mount  | <a href="https://a.co/d/j2IUD7o" target="_blank" rel="noopener">Amazon</a>                  |
| **DS3231 RTC Module**      | Real-Time Clock with battery backup            | <a href="https://www.adafruit.com/product/3013" target="_blank" rel="noopener">Adafruit</a> |
| **DHT11 Sensor**           | Temperature and humidity sensor                | <a href="https://a.co/d/80NInRv" target="_blank" rel="noopener">Amazon</a>                  |
| **16x02 LCD (I2C)**        | Display for sensor data                        | <a href="https://a.co/d/eogehxN" target="_blank" rel="noopener">Amazon</a>                  |
| **Common Cathode RGB LED** | Visual feedback, color changes on button press | <a href="https://a.co/d/8MJoMgh" target="_blank" rel="noopener">Amazon</a>                  |
| **Push Button**            | Toggles display mode                           | <a href="https://a.co/d/bW8v7g3" target="_blank" rel="noopener">Amazon</a>                  |
| **10k Potentiometer**      | Adjusts LCD contrast                           | <a href="https://a.co/d/anGid44" target="_blank" rel="noopener">Amazon</a>                  |
| **Resistors**              | R1: 220Ω, R2-R4: 470Ω                          | <a href="https://a.co/d/9Tn8IR9" target="_blank" rel="noopener">Amazon</a>                  |
| **Custom PCB**             | Designed by me and fabricated via JLCPCB       | See download section                                                                        |


>The CR1220 Coin Cell Battery for the DS3231 RTC Module is not included and must be bought separately
{: .prompt-info}

## How it Works
This project combines a few key components to function.
- ESP32-S3 Nano Microcontroller: Acts as the brain of the project. This is the part that runs the firmware to read sensor data, control the LCD, and manages user input.
- DS3231 RTC: Keeps track of the current time/date accurately even when the device isn't connected to power because of its onboard coin cell battery.
- DHT11 Temperature and Humidity Sensor: Measures the sensor's surrounding temperature and humidity.
- 16x02 LCD: A backlit display that has 2 lines of 16 characters (letters, numbers, spaces,etc); Contrast is adjustable.
- Push Button: Allows the user to toggle the display. When the button is pushed down, a circuit is completed and the microcontroller gets sent an input, which is then recorded in code.
- Common Cathode RGB LED: Provides visual feedback. Green for successful operation, Blue for button presses, and Red for errors.
- 10kΩ Potentiometer: A variable resistor; Turning the knob changes the resistance, which allows for the contrast of the LCD to be adjusted.

