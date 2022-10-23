# Pixel Art Uv Mapper
![Pixel Art Uv Mapper](res/PAUMLOGO.svg)
> You can check the roadmap [here](https://woozy-durian-0c5.notion.site/Roadmap-4d4d409b9e0c4a7bb685ba38dfbec057)

- [Pixel Art Uv Mapper](#pixel-art-uv-mapper)
  - [Getting started](#getting-started)
  - [Get used to terminology](#get-used-to-terminology)
  - [Tutorials](#tutorials)
    - [How to create a map texture](#how-to-create-a-map-texture)
    - [How to create a texture to map](#how-to-create-a-texture-to-map)
    - [How to create a skin texture](#how-to-create-a-skin-texture)
    - [How to map a my texture](#how-to-map-a-my-texture)
      - [<h3> Using Shader](#h3-using-shader)
      - [<h3> Using Sprite Component](#h3-using-sprite-component)
      - [<h3> Using Animator Override Component](#h3-using-animator-override-component)
      - [<h3> Using Engine class](#h3-using-engine-class)
      - [<h3> Using Compute Sprite Component](#h3-using-compute-sprite-component)
  - [References](#references)



## Getting started

1. First you need to import the package into your unity project.
2. We recommand you to open the demo scene to get familiar with the package.

## Get used to terminology

- **Map Texture** : The map texture is the texture that contains unique pixels and it's pixel position will  be used by the layer texture to map the texture to map.
- **Texture to map** : The texture to map is the texture that will be mapped in according to the map texture and the layers texture.
- **Layer/Skin** : The layer texture or the skin texture will be used to map the texture to map in according to the map texture. The layer texture is the texture that contains the pixels that will be mapped in the texture to map. So the layer texture is the texture that contains the rendering of the texture to map.

## Tutorials

### How to create a map texture

---
### How to create a texture to map

---
### How to create a skin texture

---

### How to map a my texture
> There is a lot of way to map the texture, PAUM provides a lot of components and shader to achieve this

  #### <h3> Using Shader
  ![Using Shader](res/home/using-shader.PNG)

  PAUM provide a shader to map the texture. You can use it by just creating a new material and assign the shader to it. Then there is three variables in this shader, the first one is the texture to map, the second one is the map texture and the third one is the skin texture. You can assign the textures to these variables in the material inspector.
  Shader is the lightest and quickest way to map your texture. But it presents its limitations : layering is not supported, you can't use custom operators or mutliple layers.
  #### <h3> Using Sprite Component
  #### <h3> Using Animator Override Component
  #### <h3> Using Engine class 
  #### <h3> Using Compute Sprite Component

## References
>All the detailled references of each class and components
* ### [Classes](Classes.md)
* ### [Components](Components.md)
* ### [Shaders](Shader.md)
