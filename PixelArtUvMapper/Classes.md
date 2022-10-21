
# Classes <!-- omit in toc -->

### Table of Contents <!-- omit in toc -->
- [Engine](#engine)
  - [Methods](#methods)
    - [&#9726; AddLayer](#-addlayer)
    - [&#9726; Apply](#-apply)
    - [&#9726; MapTexture](#-maptexture)
- [MapData](#mapdata)
- [LayerOperator](#layeroperator)
  - [Methods](#methods-1)
    - [&#9726; getPixelAt](#-getpixelat)
- [LayerOperator_REPLACE](#layeroperator_replace)
- [MapBuilder](#mapbuilder)
  - [Methods](#methods-2)
    - [&#9726; BuildMap](#-buildmap)
  - [Static Methods](#static-methods)
    - [&#9726; SaveMap](#-savemap)


---
# Engine
## Description <!-- omit in toc -->
> This class is the main class of the plugin. It is used to create a new instance of the plugin. It is also used to create a new instance of the `PAUM_Mesh` class.

---

## Contructor <!-- omit in toc -->
```csharp
public PAUM_Engine(Texture2D map)
```
__Input__

| Name | Type          | Description                  |
| ---- | ------------- | ---------------------------- |
| map  | ``Texture2D`` | The texture to use as a map. |

---

## Methods

---

### &#9726; AddLayer
> Add a new layer to the engine. The layer will be added to the list of layers.
```csharp
public PAUM_Engine AddLayer(Texture2D layer,PAUM_LayerOperator operation)
```

__Input__

| Parameter | Type                                          | Description                         |
| --------- | --------------------------------------------- | ----------------------------------- |
| layer     | ``Texture2D``                                 | The layer to add                    |
| operation | [``PAUM_LayerOperator``](#paum_layeroperator) | The operation to apply to the layer |

__Output__

| Type            | Description                       |
| --------------- | --------------------------------- |
| ``PAUM_Engine`` | The current instance of the class |

---

### &#9726; Apply
> Apply all current layer to the input map.
```csharp
public PAUM_Engine Apply()
```

__Output__

| Type            | Description                       |
| --------------- | --------------------------------- |
| ``PAUM_Engine`` | The current instance of the class |

---

### &#9726; MapTexture

> Map the input texture according to the map texture and the current skin texture return the mapped texture.

```csharp
public Texture2D MapTexture(Texture2D inputTex)
```

__Input__

| Name     | Type          | Description         |
| -------- | ------------- | ------------------- |
| inputTex | ``Texture2D`` | The texture to map. |

__Output__

| Type          | Description         |
| ------------- | ------------------- |
| ``Texture2D`` | The mapped texture. |

---
# MapData
## Description <!-- omit in toc -->
> This class is used to store the data of a map. It is used by the [Engine](#engine) class to store the data of the map.
# LayerOperator
## Description  <!-- omit in toc -->
> Base interface for creating custom operation on the current texture with a new layer. There are already built-in operators but you can add your own ones to fit your specific needs.  <!-- omit in toc -->
---
## Methods
### &#9726; getPixelAt
```csharp
    public virtual Color getPixelAt(PAUM_MapData data,Texture2D layer, int x, int y)
```
> Return the operation to apply to the pixel at the given position. This method will be call for each pixel of the texture to map when you will build the layer. Don't call this method directly, it is used internally by the plugin.

__Input__

| Name  | Type                    | Description                            |
| ----- | ----------------------- | -------------------------------------- |
| data  | [``MapData``](#mapdata) | The map data.                          |
| layer | ``Texture2D``           | The layer texture                      |
| x     | ``int``                 | The x position of the pixel to process |
| y     | ``int``                 | The y position of the pixel to process |

__Output__

| Type      | Description                                                 |
| --------- | ----------------------------------------------------------- |
| ``Color`` | The color to apply to the given pixel at the output texture |

# LayerOperator_REPLACE 
> Derive from [`LayerOperator`](#layeroperator), it's also an example of how to create your own operator. 

## Description <!-- omit in toc -->
> Replace all pixel on the current texture by none-transparent pixel of the layer 

---

# MapBuilder

## Description <!-- omit in toc -->
> Class to build a map texture from an input texture and custom regions

## Constructor <!-- omit in toc -->

```csharp
public PAUM_MapBuilder(Texture2D input, List<PAUM_RegionPoint> regions)
```

__Input__

| Name    | Type                       | Description                               |
| ------- | -------------------------- | ----------------------------------------- |
| input   | ``Texture2D``              | The input texture to create the map from. |
| regions | ``List<PAUM_RegionPoint>`` | The regions to use to create the map.     |

## Methods

### &#9726; BuildMap

```csharp
public Texture2D BuildMap()
```

> Build the map texture from the input texture and the regions. Return the map texture

__Output__

| Type          | Description     |
| ------------- | --------------- |
| ``Texture2D`` | The map texture |

---

## Static Methods

### &#9726; SaveMap

```csharp
public static bool SaveMap(string path, Texture2D map)
```

>             //SAVE MAP AS TEXTURE TO THE PATH RELATIVE TO APPLICATION.dataPath then add read write permission