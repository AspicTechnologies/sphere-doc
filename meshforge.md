---
title: Build a Geometry (Meshforge)
permalink: /sphere/Meshforge/
---


[screenshot mui]: {{site.baseurl}}/sphere/img/m_mui.png
[screenshot merging]: {{site.baseurl}}/sphere/img/m_merge123.png
[screenshot merging2]: {{site.baseurl}}/sphere/img/m_merge.png
[screenshot settings]: {{site.baseurl}}/sphere/img/m_settings.png
[screenshot material factory]: {{site.baseurl}}/sphere/img/m_materialf.png
[screenshot material picker]: {{site.baseurl}}/sphere/img/m_materialp.png
[screenshot audiocollider]: {{site.baseurl}}/sphere/img/m_audiocollider.png
[screenshot exporter]: {{site.baseurl}}/sphere/img/m_exporter.png


[LaMeilleureStartUpDuMonde]: http://www.aspictechnologies.com/
[Wwise]: https://www.audiokinetic.com/products/wwise/
[WwiseUnityIntegration]: https://www.audiokinetic.com/fr/library/edge/?source=Unity&id=main.html
[WwiseUnrealIntegration]: https://www.audiokinetic.com/library/edge/?source=UE4&id=using.html
[Unity]: https://unity3d.com
[Unreal]: https://www.unrealengine.com
[VisualStudio]: https://www.visualstudio.com




Audio geometry assets are a core component of Sphere, they contains the environment audio characteristics and pre-processed data used to speed up the real time audio spatialization.

The creation of an audio geometry asset can be done with Meshforge, a tool included with the Sphere plugin for Unity.
The process to build them should be really simple and require only two components.

+ AudioMaterial : This is a set of audio characteristics (transmissions/reflections/absorbtions).  
+ AudioCollider : Like any other Unity's colliders they can be moved and reshaped to match your environment but in addition an AudioMaterial can be associated to each of their faces.

The Meshforge Unity Interface is here to provide you a wide set of tools to manipulate AudioMaterials and AudioColliders.


## Meshforge Unity Interface

All Meshforge's features are accessible through a single Unity Window Editor  
Window -/> AspicTechnologies -/> Meshforge

![screenshot menu][screenshot mui]

The Window Editor is split in 5 differents parts

* [Settings](#settings): 
Define general Meshforge Settings 
* [Material Picker](#material-picker): 
Used to associate AudioMaterials to your geometry
* [Material Factory](#material-factory): 
Help you create new AudioMaterials
* [AudioCollider Editor](#audioCollider-editor): 
Build your geometry with AudioColliders
* [Geometry Exporter](#geometry-exporter): 
Generate precomputed geometry files to use with Sphere


### A possible workflow example

1. Open Meshforge (Window -/> Meshforge).
2. Prepare your AudioMaterials using [Material Factory](#material-factory).
3. Prepare your Audio label using [Material Picker](#material-picker).
4. Add and place your AudioColliders using [AudioCollider Editor](#audiocollider-editor).
5. Tag them using [Material mapper](#material-picker) [Paint Mode](#paint-mode) tool.
6. Merge all overlapping colliders [audioCollider editor](#audiocollider-editor).
7. Check the labels of faces resulting of colliders merge.
8. Export and set the geometry with the [geometry exporter](#geometry-exporter).


## Settings

![screenshot settings][screenshot settings]

* Meshforge Layer : The layer in which the MeshForge items will be stored
* Layer Visibility : Allow you to simply hide/show or lock for selection the MeshForge Layer and the rest of your scene
* Frequency band : the number of frequency band used to define the characteristics of your audiomaterials
* Shortcut : enable/disable Meshforge shortcuts


## Material Picker

Material Picker help you asociate AudioMaterials with AudioColliders.

![screenshot material mapper][screenshot material picker]

We don't directly associate an AudioMaterial to an AudioCollider face, we use the Material Picker to define a label, and then we associate a label to AudioColliders faces. In practice this allow us to easily change the AudioMaterial on all faces who share the same label.

### Default label

The first label "Default" can't be renamed and must be given an AudioMaterial(transparent), It will be used by default on new colliders and associated on faces created by the merge of multiple AudioColliders (see AudioCollider editor).

### Paint Mode

You can select(highlight) a label in the Material Picker, if 'Paint Mode' is enabled a simple click on an AudioCollider face will change is associated label.

## Material Factory

This Window editor can be used to create new AudioMaterials ([new material] button) or editing existing one, those materials can then be used in the [Material Map](#material-map).

![screenshot material factory][screenshot material factory]

### Transmissions and Reflections

AudioMaterials contains multiples transmissions and reflections coefficients, who define the ability of a given material to transmit or reflect sounds at differents frequencies.  

### Frequency bands

The number of frequency bands can be set to 9, 5 or 3 in [Settings](#settings) and correspond to the following frequencies.

* 9 frequency bands : 62.5 Hz / 125 Hz / 250 Hz / 500 Hz / 1 000 Hz / 2 000 Hz / 4 000 Hz / 8  000 Hz / 16 000 Hz  
* 5 frequency bands : 62.5 Hz / 250 Hz / 1 000 Hz / 4 000 Hz / 16 000 Hz   
* 3 frequency bands : 125  Hz / 1 000 Hz / 8 000 Hz

## AudioCollider Editor

By default this panel allow you to create new primitive AudioColliders (cube, sphere, ...) or build complex one by merging multiple AudioColliders.

![screenshot audiocollider][screenshot audiocollider]

### Positionning

Use the standards Unity object manipulation tools to quickly resize, rotate and move your AudioColliders over your scene, see the [official documentation](https://docs.unity3d.com/Manual/PositioningGameObjects.html). 

##### Editing Colliders 

Enabling "Edit Colliders" will make appear handles that can be grabed on the faces of your AudioColliders allowing you to move a single face at a time. This will replace the default Unity manipulation tool.

##### Snapping

AudioColliders faces will snap when close enough using the same distance Settings has Unity Snapping (Edit -> Snap Settings).

{% icon fa-thumb-tack %} Warning   
If you never set-up or modified the Unity default's snap settings this feature may not work.

### Merging

Two colliders overlaping or touching must be merged, simply because Aspic can't decide which volume choose when 2 colliders overlap or which AudioMaterial must be used when 2 faces are in contact, by merging two colliders you will remove all ambiguity.

The merging process will keep the original labels on the resulting AudioCollider and use the [material picker](#material-picker) "Default" Audio label for newly created faces, you should manually inspect the result to ensure it matchs your expectations.

### Merging order

Order is important and can lead to different results, by default the last selected AudioCollider will overlaps the previous ones. in this example you can see some merge results.

From left to right : 

1. unmerged 
2. order: Red / Blue / Green
3. order: Green / Blue / Red
4. order: Green / Red / Blue
5. order: Blue / green / Red

![screenshot mf][screenshot merging2]


## Geometry Exporter

![screenshot exporter][screenshot exporter]

When you are satisfied with your geometry it's time to export it using this last module. The export process will pre-compute sound path and store them in an AspicGeometry Asset, these pre-computing can take some time but will allow to greatly speed up the real-time audio processing.


### Others

The Geometry asset is also exported as 3 files, (.aslrx, .asmp2, .asmat) they can be used in other aspic products requiring Geometry files or imported in another Unity project using Aspic Sphere.






