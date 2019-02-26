---
title: Ambisonic Recording
permalink: /sphere/Ambisonic/
---

[Ambisonic1]: {{site.baseurl}}/sphere/img/ambisonic1.png
[Ambisonic2]: {{site.baseurl}}/sphere/img/ambisonic2.png


[Ambisonic_wiki]: https://en.wikipedia.org/wiki/Ambisonics



Follow this guide if you want to save Sphere sound simulation in [Ambisonic format][Ambisonic_wiki] of order 3.


## Setting up

Ambisonic features can be found at the bottom of the ATSphere_Settings main script.

Ambisonic must be set on enabled before playing and cannot be changed during play.

{% icon fa-thumb-tack %} Warning   
When Ambisonic Recording is enabled the sound that can be heard in Unity is the main ambisonic channel. If you wish to listen the produced ambisonic file you must use an ambisonic player.

![hi ...][Ambisonic1]

##### Output path
Select an output path for the Ambisonic file.

##### IR Display
Optional Settings when using IR Metering with Ambisonic.

{% icon fa-thumb-tack %} Warning   
This setting does not change the the Ambisonic Order for the record, only the IR Metering one.
Ambisonic Order Record is always 3 (16 channels).

##### Record on Awake
Auto-Start Ambisonic Record on play.

## Use In Editor Mode
In Editor Mode you can directly use the 3 recorder buttons like a tape recorder to start, pause or stop the ambisonic record.

![hi ...][Ambisonic2]

##### {% icon fa-play-circle-o %} Start 
Create a new ambisonic file at the designated path and start recording.

##### {% icon fa-pause %} Pause 
Pause or resume current record.

##### {% icon fa-stop %} Stop 
Stop recording and close the current ambisonic file.

## Use With Script

##### Start, Pause, Stop
```c#
//Start Recording
ATSphere_Settings.getConfig().AmbisonicStart();

//Pause Recording
ATSphere_Settings.getConfig().AmbisonicPause();

//Resume Recording
ATSphere_Settings.getConfig().AmbisonicPause();

//Stop Recording
ATSphere_Settings.getConfig().AmbisonicStop();     
```

##### Set Output
```c#
//Set ambisonic file to be saved at "C:/ambisonics/myFirstAmbisonicRecord.wav"
ATSphere_Settings.getConfig().SetAmbisonicSavePath("C:/ambisonics", "myFirstAmbisonicRecord");
```


## Multiple Record

Pressing {% icon fa-play-circle-o %} Start again after {% icon fa-stop %} Stop will overwrite the previous recording, you can avoid that by setting a new output path in between allowing you to produce multiple records in a row.

```c#
ATSphere_Settings.getConfig().SetAmbisonicSavePath("C:/ambisonics", "myFirstAmbisonicRecord");
ATSphere_Settings.getConfig().AmbisonicStart();     
ATSphere_Settings.getConfig().AmbisonicStop();      

ATSphere_Settings.getConfig().SetAmbisonicSavePath("C:/ambisonics", "mySecondAmbisonicRecord");
ATSphere_Settings.getConfig().AmbisonicStart();     
ATSphere_Settings.getConfig().AmbisonicStop();      
```










