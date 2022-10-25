# **Interfaces** <!-- omit in toc --> 


- [**ComponentEvent**](#componentevent)
  - [*Abstract methods*](#abstract-methods)
    - [**OnValueChange**](#onvaluechange)

# **ComponentEvent**

## *Description* <!-- omit in toc -->

> Event used to track variable changes in the inspector in play mode

## *Abstract methods*

### **OnValueChange**

```csharp
void OnValueChange(PAUM_ComponentValue value);
```

> Called when a value is changed in the inspector, the components which implement this interface will call the Apply method

__Input__

| Parameter | Type                    | Description                |
| --------- | ----------------------- | -------------------------- |
| value     | [PAUM_ComponentValue](Classes.md#componentvalue) | The value that has changed |
