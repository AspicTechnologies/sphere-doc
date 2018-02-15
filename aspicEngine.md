---
title: AspicEngine
permalink: /sphere/aspicengine/
---

[GeometryAsset0]: GeometryAsset0.png
[GeometryAsset2]: GeometryAsset2.png
[AspicConfig]: AspicConfig.png
[AspicSpatializer]: AspicSpatializer.png
[AspicAudioSource]: AspicAudioSource.png
[AspicMaterial]: AspicMaterial.png
[WwiseMixerPlugin1]: WwiseMixerPlugin1.png
[WwiseMixerPlugin2]: WwiseMixerPlugin2.png
[InstallerWwise]: InstallerWwise.png
[UnrealInstall0]: UnrealInstall0.png
[UnrealInstall]: UnrealInstall.png


[LaMeilleureStartUpDuMonde]: http://www.aspictechnologies.com/
[Wwise]: https://www.audiokinetic.com/products/wwise/
[WwiseUnityIntegration]: https://www.audiokinetic.com/fr/library/edge/?source=Unity&id=main.html
[WwiseUnrealIntegration]: https://www.audiokinetic.com/library/edge/?source=UE4&id=using.html
[Unity]: https://unity3d.com
[Unreal]: https://www.unrealengine.com
[VisualStudio]: https://www.visualstudio.com



# [Aspic Engine][LaMeilleureStartUpDuMonde] (version 0.1)

You are currently reading a quick install guide for Aspic Engine, 
a real time audio spatialization solution made by [Aspic technologies][LaMeilleureStartUpDuMonde].

## Table of contents

I. [Aspic Engine](#aspic-engine)
  1. [Table of contents](#table-of-contents)
  2. [Content](#content)
  3. [Prerequisites](#prerequisites)
  
II. [Aspic Engine for Unity](#aspic-engine-for-unity)
  1. [Install Unity Package](#install-unity-package)
  2. [Setup Unity Project](#setup-unity-project)
  3. [Usage with Unity](#unity-usage)  
 
III. [Aspic Engine for Wwise](#aspic-engine-for-wwise)
  1. [Install Aspic Plug-In](#install-aspic-plug-in)
  2. [Usage with Wwise](#usage-with-wwise)
  3. [Unity integration](#unity-integration)
  4. [Unreal integration](#unreal-integration)



## Content 

This is the install package content you should have received,

* [Unity package 1]
* [Unity package 2] (demo scene)
* [AspicForWwise installer]


## Prerequisites

At least one of the following combination of softwares (64 bits version only),
* [Unity 5.3+][Unity]
* [Wwise 2016.X][Wwise]
* [Wwise 2016.X][Wwise] + [Unity 5.3+][Unity]
* [Wwise 2016.X][Wwise] + [Unreal 4.X][Unreal] and a compatible [Visual Studio] version [VisualStudio]

a license key,
* [License Key].bytes a valid Aspic license key

and 3 files describing your 3d scene *
* [.asmp2 file] geometry file of your scene 
* [.asmat file] material properties 
* [.aslrx file] precomputed data 

*More information will be provided on how to generate those files in the future [TODO V2]





# Aspic Engine for [Unity][Unity]

Aspic Engine is available as a native audio plugin for [Unity][Unity].
(to use Aspic engine in Unity through Wwise integration see Wwise integration chapter)



## Install Unity Package

Simply deploy the [unity package 2] in an empty Unity project to get a demo scene ready to use scene with Aspic Engine.

Or use the [unity package 1] to add Aspic Engine into an existing project.



## Setup Unity Project

At this point you should have a folder named AspicPlugin in your project.


### 1. Create a Geometry Asset

If you want to use Aspic Engine advanced features, you will need to build a Geometry Asset describing the audio properties of your scene.


menu Assets -> create -> Aspic Geometry (or directly in the Project tab (right click -> create)).  
name this geometry and feed it the 3 files describing your scene
([.asmp2 file], [.asmat file] and [.aslrx file]) => hit "Ok".


![hi ...][GeometryAsset2]
 
### 2. Add an Aspic Config script to the scene

The script AspicConfig.cs can be found in the AspicPlugin directory of your project, 
it must be added to the scene on whichever object you want.  
This script manages global variables and required files for Aspic Engine.  
You must provide it your [License Key] and the Geometry asset file you have build previously.  

![hi ...][AspicConfig]

### 3. Set up Aspic spatializer

Inform unity to use the Aspic spatializer, for this go to Edit -> Project Settings -> Audio
and select the newly appeared "Aspic engine" entry as Spatializer Plugin.

![hi ...][AspicSpatializer]


> [unity package 2] already contain an AspicConfig script set on the camera but missing a valid license key and Geometry asset.


## Usage with Unity
 
### 1. Aspic Audio Source

Add an audio source and the AspicAudioSource.cs script to a same object and enable 
the Spatialize option for the audio source.
You will now be able to use the Aspic audio effects on your source,
 4 effects are available for now and should be self explanatory enough.
* Binaural
* Attenuation
* Dynamic Reverberation (require Geometry Asset file)
* Occlusion (require Geometry Asset file)

![hi ...][AspicAudioSource]

### 2. Aspic Material

This script allow you to change materials properties defined in the .asmat file on the fly, 
it can be added anywhere in the scene. 
Materials have basicaly 2 properties called "transmission" and "reflection".   
* Transmission is the ability of a given material to let pass the sound (air=1 // perfect wall=0).  
* Reflection is the amount of sound reflected by the material (glass=0.95 // curtains=0.05). 
    
Those values can be set for up to 9 differents frequency bands(depends of the Aspic Engine version).

![hi ...][AspicMaterial]





# Aspic Engine for [Wwise][Wwise]

Aspic engine can also be used through [Wwise][Wwise] and later be integrated into game engines, 
we provide instructions on how to do it for [Unity][Unity] and [Unreal][Unreal].

This guide assume you know how to use [Wwise][Wwise]

## Install Aspic Plug-In

* launch the [AspicForWwise installer]
* select Wwise at the plugin selection screen and follow the installer instructions

![hi ...][InstallWwise]

* Done

## Usage with Wwise

Aspic Engine is now available in Wwise as a Mixer Plug-in.

### Add an Aspic Engine Mixer Plug-in to a Bus

First you must add the Aspic Engine Mixer Plug-in to an existing Bus or create a new Bus to receive it.

1. Open the audio bus property editor and select the Mixer Plug-in panel
2. Select Aspic Engine -> Default (Custom) as Mixer
3. Open Mixer Plug-in settings

![hi ...][WwiseMixerPlugin1]

then add in the newly opened window the paths to the required files.

![hi ...][WwiseMixerPlugin2]


### Apply effects to your audio source

1. Select an audio source 
2. make sure your source use 3d positioning (positioning panel -> 3d)
2. make it go through your customized audio bus (General Settings Panel -> Output Bus)
3. Select the desired effects in the Mixer Plug-in Panel of your audio source


## Unity integration

### Install
 
1. You must already have installed Aspic Engine plugin in the version of Wwise you wish to use for the integration
2. Use Wwise launcher to integrate Wwise into your Unity project
3. launch the [AspicForWwise installer]
4. select Unity at the plugin selection screen and follow the installer instructions

### Usage

You should be able to generate sounbanks including Aspic Engine effects in Wwise and use them in unity through the 
Wwise unity integration.  
More materials on how to use the Wwise Unity integration on the [Wwise documentation][WwiseUnityIntegration].

## Unreal integration

### Install

#### I. Create a recompilable Unreal project

You will need to recompile your Unreal project,
for this it's preferable to start with a new C++ templates based project or use an existing one.  
1. launch Unreal-> new project -> C++ based

Or  

If you want to use an existing Blueprint based project.
Generate the C++ code, Right click on your .uproject file and run "Generate Visual Studio Project Files", you may have to add an empty C++ file to your project if the "Generate Visual Studio Project Files" entry is missing.

![hi ...][UnrealInstall0]

#### II. Do the Wwise/Aspic integration

1. You must already have installed Aspic Engine plugin in the version of Wwise you wish to use for the integration
2. Use Wwise launcher to integrate Wwise into your Unity project

![hi ...][UnrealInstall]

3. launch the [AspicForWwise installer]
4. select Unity at the plugin selection screen and follow the installer instructions

#### III. Recompile 

Finaly to recompile your Unreal project.

1. Open the Unreal Project root folder in your file explorer
2. Open [Unreal Project name].sln with Visual Studio
3. Build -> Rebuild Solution

yeah!

### Usage

You should be able to generate events and sounbanks including Aspic Engine effects in Wwise and use them in Unreal using the Wwise Unreal integration.  
More materials on how to use the Wwise Unreal integration on the [Wwise documentation][WwiseUnrealIntegration].


## Error

You may be displayed error codes in Unity or Wwise. Please contact us and provide us error codes so
that we can understand what’s going on.
If you see more than one error code, the first one is linked to the real error that occurred.
For your information:
* Error code 14 means that your license is not valid anymore.
* Error code 15 means that engine could not start, it may happen (for instance) if you
have no audio source or no listener.
* Error code 7 means that Audio Geometry was not found.
* Error code 13 means that audio material update failed.


