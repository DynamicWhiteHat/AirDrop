---
title: "AirDrop"
author: "DynamicWhiteHat"
description: "Describe your project in a short sentence!"
created_at: "2025-06-25"
---

# June 25th: Selecting Parts And Starting PCB

## Choosing the flight controller

The goal for my project is to create an autonomous drone that can take an address and go to its coordinates, without any human intervention. To do this, I need a strong flight computer and a companion board
capable of taking sensor data and turning it into commands to send over MavLink to the flight computer so it can avoid obstacles. I've never built a drone before, so I started searching online and found a few videos
where people used flight stacks, which combined both the fc (flight controller) and esc (electronic speed controller) into a small, stackable package. I decided to search for cheap flight stacks, as it would help
reduce wiring and make the drone's overall footprint smaller. Here are a few fc stacks I found after about 90 minutes of searching:

| Stack | SpeedyBee F405 V4 BLS 55A 30×30 FC&ESC Stack                                                                                                                                                                                                      | MAMBA MK4 F722 APP 55A ESC                                                                        | MAMBA MK4 F722 MINI F40 40A ESC                                            |
|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| Price | $84.99                                                                                                                                                                                                                                            | $98.99                                                                                            | $85.99                                                                     |
| Link  | https://www.myfpvstore.com/fpv-electronics/speedybee-f405-v4-bls-55a-30x30-fc-esc-stack-pick-your-esc-or-flight-controller-or-stack/?attribute_config=Flight+Controller&srsltid=AfmBOorgCc-LYhP6BXKjNDUj5Wo4KQOgMTNqw8LecNfK0Dei91qbN8SLbX0&gQT=1 | https://www.diatone.us/collections/mamba-stack/products/mb-mk4-f722-app-fc?variant=39828008337495 | https://www.diatone.us/products/mb-mk4-f722-mini-fc?variant=39800999444567 |

These stacks are all pretty expensive, but for now I've decided to go with the SpeedyBee F405 stack, since it comes with a 55A esc. I will need a strong (high amperage) esc to ensure that I can power a large 
drone with a possibly heavy payload. Choosing a F405 may be problematic when trying to use obstacle avoidance, since it is lower specced than F7 variants like the MAMBA F722, but the companion board should be able to
compute for it.

## Choosing a companion board

Choosing a companion board was pretty straightforward since I already have an RPi 5 laying around at home with no use, so I decided that it would be a good choice. I also have a 64MP camera from ArduCam which I can use
for visual obstacle avoidance. Paired with [this](https://www.amazon.com/MakerFocus-Single-Point-Ranging-Pixhawk-Compatible/dp/B075V5TZRY/) micro lidar for $42.99, the RPi should be able to make good observations about
its environment and react accordingly. After browsing the ArduPilot website (which I plan to use for firmware on the fc), I saw that RPi boards can easily be wired to the fc and can communicate with them using the MavLink
protocol, making the whole setup easier.

## Creating The Transmitter (Controller)

As I started to choose other parts for the drone, such as motors, a vtx, and cameras, I realized that the total price was starting to get high, while I had no estimate of the cost of the PCB. I decided to start making
the PCB first so I could get a good estimate for its cost.

I started with the main MCU, which I chose to be an RPi Zero 2 W, since I have one laying around as well. After searching online, I found that most drones use a protocol called ELRS to communicate. I found the cheapest
(while still reliable) ELRS TX from BetaFPV, their [Nano TX](https://betafpv.com/products/elrs-nano-tx-module?variant=39416993382534). Initially, I spent some time trying to figure out what the connector on the bottom
was, since it seemed to be something that commercial controllers used to connect to the ELRS module. 



However, I was unable to find the connector. I did find a 
