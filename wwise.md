---
title: Wwise
permalink: /sphere/Wwise/
---

[GeometryAsset0]: {{site.baseurl}}/sphere/img/GeometryAsset0.png
[GeometryAsset2]: {{site.baseurl}}/sphere/img/GeometryAsset2.png
[AspicConfig]: {{site.baseurl}}/sphere/img/AspicConfig.png
[AspicSpatializer]: {{site.baseurl}}/sphere/img/AspicSpatializer.png
[AspicAudioSource]: {{site.baseurl}}/sphere/img/AspicAudioSource.png
[AspicMaterial]: {{site.baseurl}}/sphere/img/AspicMaterial.png
[WwiseMixerPlugin1]: {{site.baseurl}}/sphere/img/WwiseMixerPlugin1.png
[WwiseMixerPlugin2]: {{site.baseurl}}/sphere/img/WwiseMixerPlugin2.png
[InstallerWwise]: {{site.baseurl}}/sphere/img/InstallerWwise.png
[UnrealInstall0]: {{site.baseurl}}/sphere/img/UnrealInstall0.png
[UnrealInstall]: {{site.baseurl}}/sphere/img/UnrealInstall.png


[LaMeilleureStartUpDuMonde]: http://www.aspictechnologies.com/
[Wwise]: https://www.audiokinetic.com/products/wwise/
[WwiseUnityIntegration]: https://www.audiokinetic.com/fr/library/edge/?source=Unity&id=main.html
[WwiseUnrealIntegration]: https://www.audiokinetic.com/library/edge/?source=UE4&id=using.html
[Unity]: https://unity3d.com
[Unreal]: https://www.unrealengine.com
[VisualStudio]: https://www.visualstudio.com


This guide assume you know how to use [Wwise][Wwise].

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

