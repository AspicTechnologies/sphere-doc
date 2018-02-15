---
title: Aspic Audio Source
permalink: /sphere/Effects/
---

[AspicConfig]: {{site.baseurl}}/sphere/img/AspicConfig.png
[AspicAudioSource]: {{site.baseurl}}/sphere/img/AspicAudioSource.png

[LaMeilleureStartUpDuMonde]: http://www.aspictechnologies.com/
[Wwise]: https://www.audiokinetic.com/products/wwise/
[WwiseUnityIntegration]: https://www.audiokinetic.com/fr/library/edge/?source=Unity&id=main.html
[WwiseUnrealIntegration]: https://www.audiokinetic.com/library/edge/?source=UE4&id=using.html
[Unity]: https://unity3d.com
[Unreal]: https://www.unrealengine.com
[VisualStudio]: https://www.visualstudio.com


## Source Component

Enabling Spatialize on any Unity AudioSource components will add an ATSphere_Source component to it.    
The Spatialize option will make this AudioSource use the Sphere Spatializer and the ATSphere_Source component will allow us to choose the desired effects to apply. 

![hi ...][AspicAudioSource]

{% icon fa-thumb-tack %} Warning  
Be sure to keep spatialblend set to 2D.


Each spatialized Audio Source can use one or a combination of effects depending on your objective, sound can be simply oriented with just a Binaural effect or fully spatialized using all availables effects.

## Simple Effects

### Binaural

Enable spatialization using HRTF functions, reproducing how the sound coming from a specific point in space will be heared at the ears of a listener, allowing him to detect the sound direction.

### Attenuation

A simple attenuation effect is provided with customizables settings to provide add a distance sensation to the sound.

Attenuation settings are disabled when using an environment based effect since those effects already handle attenuation on their own.

## Environment Based Effects

{% icon fa-thumb-tack %} Environment based Effects require a valid geometry asset to be set.  

### Occlusion

Occlusion effect will use the environment described in the geometry asset to reproduce how surrounding obstacles affect the sound propagation, using atmospheric attenuation, material transmissions of traversed sufaces and sound diffraction.

### Dynamic Reverberation

This last effect will make use of material reflections coefficients to produce the sound of early reflections (from close reflective surfaces) and late reverberations(residual sound from successive reflections).



