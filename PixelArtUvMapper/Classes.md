
# Classes <!-- omit in toc -->

### Table of Contents <!-- omit in toc -->
- [PAUM_Engine](#paum_engine)
  - [Methods](#methods)
    - [&#9726;AddLayer](#addlayer)
  - [Static Methods](#static-methods)
- [PAUM_LayerOperator](#paum_layeroperator)
  - [Methods](#methods-1)
    - [getPixelAt](#getpixelat)


---
# PAUM_Engine
## Description <!-- omit in toc -->
> This class is the main class of the plugin. It is used to create a new instance of the plugin. It is also used to create a new instance of the `PAUM_Mesh` class.

---
## Contructor <!-- omit in toc -->
```csharp
public PAUM_Engine(Texture2D map)
```
---

## Methods

---

### &#9726;AddLayer
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


## Static Methods

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
