---
title: Update Geometry
permalink: /sphere/Updatematerial/
---


[UpdateMat]: {{site.baseurl}}/sphere/img/UpdateMat.png
[UpdateGeo]: {{site.baseurl}}/sphere/img/UpdateGeo.png



The sound spatialization is made with a pre-computed file based on your scene geometry, so what if you want to make real-time change to your audio environment?

Here we show you two different methods to update it.


## Swap Geometry Asset

We recommend to use this method when a lot of changes happen in your scene.

You can simply swap the geometry asset provided to the ATSphere_settings.cs script for another one during runtime.

{% icon fa-thumb-tack %} Warning  
Currently Geometry asset must be build using the exact same Audio Colliders, only labels and materials used can be different between two swapped geometry asset.

### In Editor Mode

Directly from the main ATSphere_Settings script, select another geometry asset, done.

![hi ...][UpdateGeo]

### Within a Script

You can request the ATSphere_Settings script to change to another geometry asset on runtime using the following method.

```c#
ATSphere_Settings myScript = (ATSphere_Settings)FindObjectOfType(typeof(ATSphere_Settings));

myScript.SetGeometry("audio_2");    // switch to geometry asset named audio_2

myScript.SetGeometry("audio_3");    // switch to geometry asset named audio_3

```

### inconvenient 

Geometry asset need to be build in advance, this mean you must have an aspic geometry asset ready for every possible configuration of your scene. This methods should be used only for major changes in your scene geometry.


## Update Material

Using the ATSphere_Material script you can change the audio characteristics (transmissions/reflections) associated with a given label on runtime.

For instance, if you wish to simulate a door opening/closing, define a label "DOOR1" and use it for a single door in your scene, you should also have multiples AudioMaterials ready like "wood" and "air". During runtime use the ATSphere_Material script to switch the AudioMaterial associated to the label "DOOR1" from "wood" to "air" or vice-versa.

### In Editor Mode

Add ATSphere_Material script to a gameObject, select a label and edit his values(the label list can only be seen during runtime).


![hi ...][UpdateMat]

### Within a Script

If an ATSphere_Material script is on a gameObject, you can call the following methods to update a label.

```c#
ATSphere_Material myScript = (ATSphere_Material)FindObjectOfType(typeof(ATSphere_Material));

//open door
myScript.UpdateMat( "Door_1", 
                    new float[] { 0, 0, 0, 0, 0, 0, 0, 0, 0 },  // reflections => 0% 
                    new float[] { 1, 1, 1, 1, 1, 1, 1, 1, 1 }); // transmissions => 100%

//close door
myScript.UpdateMat( "Door_1",
                    new float[] { 0, 0, 0, 0, 0, 0, 0, 0, 0 },  // reflections => 0% 
                    new float[] { 0, 0, 0, 0, 0, 0, 0, 0, 0 }); // transmissions => 0%
```

### inconvenient 

1. You will need to create an unique label for each element you wish to be able to edit on runtime.

2. The changes mades with ATSphere_Material doesn't impact the sound late reverberation, only the first and early reflections. In short, you should avoid using ATSphere_Material to change the AudioMaterial of surfaces that have too much impact on reverberation like giant walls with high reflections values (prefer the geometry asset swap method in this case).
