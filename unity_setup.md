---
title: Setup a project
permalink: /sphere/Setup a project/
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



Sphere is available as an audio spatializer for [Unity][Unity] version 5.2+.
(to use Sphere in Unity through Wwise integration see the Wwise integration chapter)

## AppLauncher

The Installation of the Sphere plugin into a Unity project can be done from the dedicated page of the AppLauncher after validating a License key, if you don't have the AppLauncher nor a validated License key, go check the [first chapter](/Doc/sphere/installation).

* Select the latest plugin version of Sphere and choose the Unity installer(.unitypackage) to start the installation.

* Choose a valid License in the list and click "To Unity" to copy the License file at the root of your Unity project


## Unity Project

At this point you should have a folder named AspicTechnologies and a License file(.bytes) at the root of your Unity project, if it's the case you can start using Sphere.

### Sphere Spatializer

Sphere use Unity spatializer feature available since Unity 5.2.
Inform unity to use the freshly installed Sphere plugin as spatializer, for this go to Edit -> Project Settings -> Audio
and select "Aspic Sphere" entry as Spatializer Plugin.

The Unity Audio Settings as seen in the Inspector.
![hi ...][AspicSpatializer]


### Aspic Settings script

The script ATSphere_Settings.cs can be found in the Asset/Aspic/AspicPlugin directory, 
it must be added to the scene on any gameObject of your choice.  
This script manages settings shared ammong all spatialized AudioSources, additional settings can be found within each AudioSource scripts (see [Aspic Audio Source](/doc/sphere/Effects/)). 


The ATSphere_Settings script.
![hi ...][AspicConfig]


##### License Key
You should have generated a license file (.bytes) to put here, if not, go back to the [first chapter](/Doc/sphere/installation) you may have missed something.

##### Master gain
A simple gain affecting all the Spatialized Audio Sources

##### Reverberation 
You will find 2 sliders under this panel.
Dry and Wet sliders allow you to control the sound volume comming directly from the audio sources (Dry) and the volume of the reverbered sound (Wet).    
This can be used to artificially enhance the reverberation or simply has a control tool.

#####  Weather (Atmospheric Settings)
2 more sliders for temperature (in Celsius) and Humidity (%).    
Atmospheric settings will affect the sound propagation through the air.

##### Geometry Asset
If you wish to use environment based effects, you will need to provide a file describing your audio environment to the plugin.
If you already have files describing your environment you can import them from here and ignore the next chapter, if you don't you can create some using Meshforge, a tool designed to build those geometry Asset.








