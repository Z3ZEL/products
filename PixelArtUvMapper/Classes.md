<!-- 
@TODO: MAKE NAMESPACE
 -->
# Classes <!-- omit in toc --> 🏠 [Home](Home.md)

### Table of Contents <!-- omit in toc -->
- [**Engine**](#engine)
  - [*Methods*](#methods)
    - [**AddLayer**](#addlayer)
    - [**Apply**](#apply)
    - [**MapTexture**](#maptexture)
- [**MapData**](#mapdata)
  - [*Properties*](#properties)
- [**LayerOperator**](#layeroperator)
  - [*Methods*](#methods-1)
    - [**getPixelAt**](#getpixelat)
    - [**Operate**](#operate)
- [**LayerOperator_REPLACE** &rarr; ``PAUM_LayerOperator``](#layeroperator_replace--paum_layeroperator)
- [**MapBuilder**](#mapbuilder)
  - [*Methods*](#methods-2)
    - [**BuildMap**](#buildmap)
  - [*Static Methods*](#static-methods)
    - [**SaveMap**](#savemap)
- [**ComponentValue**](#componentvalue)
  - [*Methods*](#methods-3)
    - [**Subscribe**](#subscribe)
    - [**Unsubscribe**](#unsubscribe)
- [**Layers** &rarr; ``PAUM_ComponentValue``](#layers--paum_componentvalue)
  - [*Methods*](#methods-4)
    - [**CheckValueChanging**](#checkvaluechanging)
    - [**AddLayer**](#addlayer-1)
    - [**ChangeLayerAt**](#changelayerat)
  - [*Properties*](#properties-1)
- [**Texture** &rarr; ``PAUM_ComponentValue``](#texture--paum_componentvalue)
  - [*Methods*](#methods-5)
    - [**CheckValueChanging**](#checkvaluechanging-1)
  - [*Properties*](#properties-2)

 > ⚠️ The title of each class are cut for lisibility reason. Their real name in the package are beggining with `PAUM_`. For example `Engine` is `PAUM_Engine` in the package. 

---
# **Engine**
## *Description* <!-- omit in toc -->
> This class is the main class of the plugin. It is used to create a new instance of the plugin. It is also used to create a new instance of the `PAUM_Mesh` class.


## *Constructor* <!-- omit in toc -->
```csharp
public PAUM_Engine(Texture2D map)
```
__Input__

| Name | Type          | Description                  |
| ---- | ------------- | ---------------------------- |
| map  | ``Texture2D`` | The texture to use as a map. |


## *Methods*

### **AddLayer**
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

### **Apply**
> Apply all current layer to the input map.
```csharp
public PAUM_Engine Apply()
```

__Output__

| Type            | Description                       |
| --------------- | --------------------------------- |
| ``PAUM_Engine`` | The current instance of the class |


### **MapTexture**

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
# **MapData**
## *Description* <!-- omit in toc -->
> This class is used to store the data of a map. It is used by the [Engine](#engine) class to store the data of the map.

## *Constructor* <!-- omit in toc -->
```csharp
public PAUM_MapData(Texture2D map, Vector2 texSize)
```

__Input__

| Name     | Type          | Description                  |
| -------- | ------------- | ---------------------------- |
| map      | ``Texture2D`` | The texture to use as a map. |
| texSize🔨 | ``Vector2``   | The size of the map texture. |



## *Properties*

| Name            | Type                        | Description                                                                                | get | set |
| --------------- | --------------------------- | ------------------------------------------------------------------------------------------ | --- | --- |
| getMap          | ``Texture2D``               | The map texture.                                                                           | ✔️   | ❌   |
| getCurrentTex 🔨 | ``Texture2D``               | The current layer of the map, it's the result of Operation                                 | ✔️   | ✔️   |
| getTexSize      | ``Vector2``                 | The size of the map texture.                                                               | ✔️   | ❌   |
| getPairedColors | ``Dictionary<Color,Color>`` | The unique pixels of the map texture as key referring to the same position pixels as value | ✔️   | ❌   |



---
# **LayerOperator**
## *Description*  <!-- omit in toc -->
> Base interface for creating custom operation on the current texture with a new layer. There are already built-in operators but you can add your own ones to fit your specific needs.  <!-- omit in toc -->
## *Methods*
### **getPixelAt**
```csharp
    public virtual Color getPixelAt(PAUM_MapData data,Texture2D layer, int x, int y)
```
> Return the operation to apply to the pixel at the given position. This method will be call for each pixel of the texture to map when you will build the layer. Don't call this method directly, it is used internally by the plugin. But override it to create your own operation.

__Input__

| Name  | Type                         | Description                            |
| ----- | ---------------------------- | -------------------------------------- |
| data  | [``PAUM_MapData``](#mapdata) | The map data.                          |
| layer | ``Texture2D``                | The layer texture                      |
| x     | ``int``                      | The x position of the pixel to process |
| y     | ``int``                      | The y position of the pixel to process |

__Output__

| Type      | Description                                                 |
| --------- | ----------------------------------------------------------- |
| ``Color`` | The color to apply to the given pixel at the output texture |

### **Operate**

> Apply the operation to the given layer, output the result in of the old layer in map data combined with the new layer. *it doesn't change the current layer of the map data*

```csharp
public virtual Texture2D Operate(PAUM_MapData data, Texture2D layer)
```

__Input__

| Name  | Type                         | Description                 |
| ----- | ---------------------------- | --------------------------- |
| data  | [``PAUM_MapData``](#mapdata) | The map data.               |
| layer | ``Texture2D``                | The layer new layer texture |

__Output__

| Type          | Description                                                     |
| ------------- | --------------------------------------------------------------- |
| ``Texture2D`` | The new layer texture combined with the map data existing layer |

---
# **LayerOperator_REPLACE** &rarr; [``PAUM_LayerOperator``](#layeroperator)
> Derive from [`PAUM_LayerOperator`](#layeroperator), it's also an example of how to create your own operator. 

## *Description* <!-- omit in toc -->
> Replace all pixel on the current texture by none-transparent pixel of the layer 

---
# **MapBuilder**

## *Description* <!-- omit in toc -->
> Class to build a map texture from an input texture and custom regions

## *Constructor* <!-- omit in toc -->

```csharp
public PAUM_MapBuilder(Texture2D input, List<PAUM_RegionPoint> regions)
```

__Input__

| Name    | Type                       | Description                               |
| ------- | -------------------------- | ----------------------------------------- |
| input   | ``Texture2D``              | The input texture to create the map from. |
| regions | ``List<PAUM_RegionPoint>`` | The regions to use to create the map.     |

## *Methods*

### **BuildMap**

```csharp
public Texture2D BuildMap()
```

> Build the map texture from the input texture and the regions. Return the map texture. This class is used by the Map Builder window to build the map texture. You can use it by yourself but it's not recommended.

__Output__

| Type          | Description     |
| ------------- | --------------- |
| ``Texture2D`` | The map texture |

---

## *Static Methods*

### **SaveMap**

```csharp
public static bool SaveMap(string path, Texture2D map)
```

> Save map as texture to the path relative to Application.dataPath then add read and write permission. Use in Map Builder windows. Don't use it outside of the editor.

__Input__

| Name | Type          | Description               |
| ---- | ------------- | ------------------------- |
| path | ``string``    | The path                  |
| map  | ``Texture2D`` | The generated map to save |

__Output__

| Type     | Description                              |
| -------- | ---------------------------------------- |
| ``bool`` | True if the map has been saved correctly |

---
# **ComponentValue**
## *Description* <!-- omit in toc -->
> Abstract class to describe a variable data used by a [Component](#component) all component variable derive from this class

## *Methods*

### **Subscribe**

```csharp
public void Subscribe(PAUM_ComponentEvent listener)
```

> Subscribe a listener to the event of the variable. The listener will be called when the variable value change.

__Input__

| Name     | Type                                                    | Description                                         |
| -------- | ------------------------------------------------------- | --------------------------------------------------- |
| listener | [``PAUM_ComponentEvent``](Interfaces.md#componentevent) | The listener which will subscribe to variable event |

### **Unsubscribe**

```csharp
public void Unsubscribe(PAUM_ComponentEvent listener)
```

> Unsubscribe a listener to the event of the variable. The listener will not be called when the variable value change.

__Input__

| Name     | Type                                       | Description                                           |
| -------- | ------------------------------------------ | ----------------------------------------------------- |
| listener | [``PAUM_ComponentEvent``](#componentevent) | The listener which will unsubscribe to variable event |

---
# **Layers** &rarr; [``PAUM_ComponentValue``](#componentvalue)
## *Description* <!-- omit in toc -->
> This class is used to store the value of a component. It is used by the [Component](Components.md#component) class to store its values

## *Constructor* <!-- omit in toc -->
```csharp
public PAUM_Layers(Texture2D[] value)
```
__Input__

| Name  | Type          | Description                        |
| ----- | ------------- | ---------------------------------- |
| value | ``Texture2D`` | layers to pass as beginning values |


## *Methods*

### **CheckValueChanging**
> Check if the value of the component is changing. This method is used internally by the plugin. You can use it if you're creating your own component.

```csharp
public bool CheckValueChanging(Texture2D[] newTab)
```
__Input__

| Name   | Type          | Description                                                      |
| ------ | ------------- | ---------------------------------------------------------------- |
| newTab | ``Texture2D`` | The new tab which will be compared to the internal current value |

### **AddLayer**
> Add a new layer to the list of layers.

```csharp
public void AddLayer(Texture2D layer, int index)
```

__Input__

| Name  | Type          | Description                                         |
| ----- | ------------- | --------------------------------------------------- |
| layer | ``Texture2D`` | The layer to add                                    |
| index | ``int``       | (Optional) The index where the layer will be added. |

### **ChangeLayerAt**
> Change the layer at the given index.

```csharp
public void ChangeLayerAt(int index, Texture2D layer)
```

__Input__

| Name  | Type          | Description                               |
| ----- | ------------- | ----------------------------------------- |
| index | ``int``       | The index of the layer to change          |
| layer | ``Texture2D`` | The new layer to apply to the given index |

## *Properties*

| Name         | Type            | Description       | Get | Set |
| ------------ | --------------- | ----------------- |--| -- |
| currentValue | ``Texture2D[]`` | The current value | ✔️ | ✔️ |

---
# **Texture** &rarr; [``PAUM_ComponentValue``](#componentvalue) 

## *Description* <!-- omit in toc -->

> This component variable is used to store a texture value by the [Components](Components.md#component). It will be used to store the map and the texture to map.

## *Constructor* <!-- omit in toc -->

```csharp
public PAUM_Texture(Texture2D value)
```

__Input__

| Name  | Type          | Description                        |
| ----- | ------------- | ---------------------------------- |
| value | ``Texture2D`` | texture to pass as beginning value |

## *Methods*

### **CheckValueChanging**

```csharp
public bool CheckValueChanging(Texture2D newTex)
```

> Check if the value of the component is changing if it changed it will remplace the old value. This method is used internally by the plugin. You can use it if you're creating your own component.

__Input__

| Name   | Type          | Description                                                  |
| ------ | ------------- | ------------------------------------------------------------ |
| newTex | ``Texture2D`` | The new texture which will be compared to the internal value |

## *Properties*

| Name         | Type          | Description       | get | set |
| ------------ | ------------- | ----------------- | --- | --- |
| currentValue | ``Texture2D`` | The current value | ✔️  | ✔️  |



