---
title: IR Metering
permalink: /sphere/IR/
---

[IR1]: {{site.baseurl}}/sphere/img/ir1.png
[IR2]: {{site.baseurl}}/sphere/img/ir2.png
[IRMetrics]: {{site.baseurl}}/sphere/img/IRMetrics.png

[link1]: {{site.baseurl}}/sphere/Effects/#environment-based-effects


This page will help you use the optional ATSphere_IR script to visualize impulse responses of AudioSources using Sphere Dynamic Reverberation. 

![hi ...][IR1]

## Setting up

To enable IR Metering simply add an ATSphere_IR script anywhere in your scene before the application start as it can't be added when the application is playing.

{% icon fa-thumb-tack %} Warning   
The presence of an ATSphere_IR script in your scene can impact the performances of the simulation, it is recommended to remove or disable this script when not used.

### AudioSource

Only AudioSource Spatialized using the Sphere Spatializer Plugin and The Dynamic Reverberation Effect (see [Aspic Audio Source][link1]]) can be selected.

### Impulse Response

The Impulse Response is displayed as a Graph that can be customized.

![hi ...][IR2]

##### Graph
Select a graph mode and a channel to display.

##### IR Duration
This slider can be used to keep the focus on the first [x] milliseconds of the impulse response, the default range goes from 100 to 1000 milliseconds.

### Metrics

This second half display common metrics computed from the impulse response.  
Results can be viewed for each channel.

![hi ...][IRMetrics]

##### C50
Speech Clarity 

##### STI
Speech Transmission Index

##### T20
Reverberation Time.  
Time needed (in s) for the reverberation volume to drop 20dB

##### STR
Strength (also called G).  
Comparison (in dB) of the source volume against the same source in an anechoic chamber.