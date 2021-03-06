# NDK_Engine

## Synopsis
This project is a simple, android mobile-oriented, 3D OpenGL ES 2.0 based game engine developed inside of the Android Native Development kit, written primarily  in C++

This engine was written specifically for a game
 * This is why no general 3D physics engine is included, and why other common game engine features are missing (i.e. a particle system, lighting/shadow rendering)

## Graphical Features
* Skeletal 3D Animations
* Parenting objects to skeletal animation bones 
 * (i.e. parenting the camera to a head bone for first person animations)
* Custom GLSL shader/material support
* Skybox rendering support

## Sound Features
* Supports 3D stereo R/L volume panning
 * (i.e. sounds playing from a source nearby on the camera's left hand side will be played through the left speaker)
* Supports 3D audio falloff
 * (i.e. sounds playing further away are quieter than nearby sounds)


## Mobile Specific Features
* Includes JNI (Java Native Interface) support
 * This allows you to create Java code snippets and execute them from within the C++ game code
  * Meant for implementing in-app purchases
* Mobile banner ad support
 * Achieved through JNI, this allows a banner ad to be overlayed on top of the opengl game view
  * Banner ad can be made visible / hidden from within the engine C++ code

## Technical Details
* Utilizes OpenGL ES 2
* Utilizes OpenSL for sound engine

* Custom Skeletal animation format (*.skaf)
* Custom Skeleton structure format (*.sksf)
* Custom Skeletal Model Format (*.skmf)
 * Allows each vertex to have:
  * up to 3 bone weight influences
  * 1 set of UV coordinates
  * vertex normals, tangents, and binormals
* Custom Static Model Format (*.stmf)
 * Allows each vertex to have:
  * 2 sets of UV coordinates
   * One meant for a diffuse texture, the other meant for a lightmap texture atlas
  * vertex normals, tangents, and binormals

* Utilizes ETC1 Compressed texture format (*.pkm)
 * This allows me to simply pass along the image data directly to the GPU without the need for modification
 * The tradeoff is that this format only supports RGB channels, and has some (slight) compression artifacts
* Utilizes raw headerless Sound format (*.raw)
 * 16-bit depth stereo files, at 44100 Hz
