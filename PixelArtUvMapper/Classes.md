
# Classes <!-- omit in toc -->

### Table of Contents <!-- omit in toc -->
- [PAUM_Engine](#paum_engine)
  - [Methods](#methods)
    - [&#9726; AddLayer](#-addlayer)
    - [&#9726; Apply](#-apply)
    - [&#9726; MapTexture](#-maptexture)
- [PAUM_LayerOperator](#paum_layeroperator)
  - [Methods](#methods-1)
    - [getPixelAt](#getpixelat)
- [PAUM_LayerOperator_REPLACE](#paum_layeroperator_replace)
- [PAUM_MapBuilder](#paum_mapbuilder)


---
# PAUM_Engine
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

| Type          | Description                       |
| ------------- | --------------------------------- |
| ``Texture2D`` | The mapped texture.               |

---


# PAUM_LayerOperator
## Description  <!-- omit in toc -->
> Base interface for creating custom operation on the current texture with a new layer. There are already built-in operators but you can add your own ones to fit your specific needs.  <!-- omit in toc -->
---
## Methods
### getPixelAt
```csharp
    public virtual Color getPixelAt(PAUM_MapData data,Texture2D layer, int x, int y)
```
> Return the operation to apply to the pixel at the given position

# PAUM_LayerOperator_REPLACE 
> Derive from [`PAUM_LayerOperator`](#paum_layeroperator)

## Description <!-- omit in toc -->
> Replace all pixel on the current texture by none-transparent pixel of the layer 

---

# PAUM_MapBuilder

## Description <!-- omit in toc -->
> Class to build a map texture from an input texture and custom regions

## Constructor <!-- omit in toc -->

```csharp
public PAUM_MapBuilder(Texture2D input, List<PAUM_RegionPoint> regions)
```

__Input__

| 
