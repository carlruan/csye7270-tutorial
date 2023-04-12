# Unreal Engine 4 Water Shader Tutorial

Today I’m going to write a tutorial about how to create a water shader in unreal engine 4.  
With this shader, you can control the depth of water, the opacity of the water, the color of the water and the wave of the water.

---

![demo](/screenshot/demo.gif)

---

# Let’s begin!

## Create Water Material

---

Right click the Selected folder and select Add/Import content to add a material inside the folder. Name it M_Water.  
![create-material](/screenshot/create-material.png)  
Double clock the M_Water to edit the material.

---

## Change Mode

---

Since water is translucent, set the blend mode to Translucent. And since we want some metallic, specular and roughness effect, change the Lighting Mode to Surface Translucency Volume.  
![change-mode](/screenshot/change-mode.png)

---

## Set Base Value

---

Create a 3 vector parameter Water Color and connect to Emissive Color. This will set the base color of the water shader.  
Create Metallic, Specular, Roughness parameter and connect them to the M_Water node.  
You can set the default value same as the screenshot or you can change them later in the instance.
![initvalue](/screenshot/initvalue.png)

---

## Water wave

---

Create a Texture Sample node and set the texture to "water_n" under Engine Context folder and crete an Absolute World Position Node.  
Dive the World Position by Water Size Parameter and collect the X and Y panel. So that we can mask the Z panel only.  
Create a Panner node and set the Time to Time Node and Speed by appending two parameters, X panel and Y panel.  
Changing X and Y will change the direction and the speed of the wave.  
Multiply the output by a Parameter and connect to the UVs of the Texture.
![wave](/screenshot/wave.png)  
Duplicate the Panner part to create another wave.  
![TwoWaves](/screenshot/TwoWaves.png)
Add two waves and connect to the Normal.  
![addwave](/screenshot/addwave.png)

---

## Depth Fade

---

Create a Depth Fade node, and create Depth Opacity and Fade Distance parameter to set how much blur you want. Connect it to Opacity.  
![depthfade](/screenshot/depthfade.png)

---

## Refraction Of Light

---

Next, create Lerp Node (right click Linear Interpolate) and Fresnel Node. Fresnel Node is a node can create refractive index. Set A to 1 and B to 1.33 in Lerp according to documentation by Unreal Engine.  
If you are interested in creating ice or other shaders, please check this documentation.  
[Unreal Engine Using refraction](https://docs.unrealengine.com/4.27/en-US/RenderingAndGraphics/Materials/HowTo/Refraction/)  
Connect it to Refraction.  
![refraction](/screenshot/refraction.png)

---

## Overview

---

## ![overview](/screenshot/overview.png)

## Configure Water Instance

---

Create an instance by right click the M_Water and select Create Material Instance.  
![createinstance](/screenshot/createinstance.png)  
Configure the parameters and find out your favorite!  
![configure](/screenshot/configure.png)

---

## Source Code

---

[Source Code on Github](https://github.com/carlruan/csye7270-tutorial)

---

## Reference

---

[Tutorial video on youtube](https://www.youtube.com/watch?v=52RR8jIrDhQ&t=444s)
