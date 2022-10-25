# Components <!-- omit in toc --> 

- [Component , PAUM_ComponentEvent](#component--paum_componentevent)
  - [Methods](#methods)
    - [&#9726; Apply](#-apply)
    - [&#9726; OnValueChanged](#-onvaluechanged)
  - [Properties](#properties)
- [Animator Overlay &rarr; Component](#animator-overlay--component)
- [Sprite &rarr; Component](#sprite--component)
- [Compute Sprite &rarr; Component](#compute-sprite--component)

# Component , [PAUM_ComponentEvent](Classes.md#componentevent)
> Abstract class common to all components. You can derive from this class to create your own component. All its properties can be accessed in the other components. All methods can be overrided to create your own component.

---

## Methods

### &#9726; Apply
> Apply to the sprite renderer the current texture to map in according to the map and layers cames from the [PAUM_ComponentEvent](Classes.md#componentevent) 

```csharp
public abstract void Apply();
```

### &#9726; OnValueChanged
> Called when a value is changed in the inspector, by default it calls the `Apply` method

```csharp
public void OnValueChange(PAUM_ComponentValue value)
```

__Input__

| Parameter | Type                    | Description                |
| --------- | ----------------------- | -------------------------- |
| value     | ``PAUM_ComponentValue`` | The value that has changed |

---
## Properties

| Name              | Type               | Description                                                                                                                                    | get | set |
| ----------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | --- | --- |
| autoApply         | ``bool``           | If true, the component will auto apply whenever a properties in the component changed. Set True by default, can be set only from the inspector | O   | O   |
| mapInput          | ``Texture2D``      | The field use in inspector to assign a map texture can be set only from the inspector                                                                                             | O   | O   |
| textureToMapInput | ``Texture2D``      | The field use in inspector to assign a texture to map can be set only from the inspector                                                                                          | O   | O   |
| layersInput       | ``Texture2D[]``    | The field use in inspector to assign a list of layers can be set only from the inspector                                                                                          | O   | O   |
| sr                | ``SpriteRenderer`` | The sprite renderer of the game object.                                                                                            | X   | X   |
| layers            | ```PAUM_Layers```  | The layers object, use this by script to change layers value                                                                                   | X |O|
| map               | ``PAUM_Texture``   | The map object, use this by script to change map value                                                                                         | X |O|
| textureToMap      | ``PAUM_Texture``   | The texture to map object, use this by script to change texture to map value                                                                   | X |O|

---
# Animator Overlay &rarr; [Component](#component)
> The Animator Overlay component is used to overlay a texture on top of the animated texture. This is useful for adding things like blood, dirt, or other effects to the animated texture.
# Sprite &rarr; [Component](#component)
> The Sprite component is a basic mapper, it will map the sprite in the SpriteRenderer component in according to the map texture and the skin texture.
# Compute Sprite &rarr; [Component](#component)
> The compute sprite component do the same as sprite component but way much faster and lighter because it's calculated on the GPU but for now multi-layering is not supported by this component.










