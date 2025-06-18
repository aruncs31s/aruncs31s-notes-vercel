---
{"dg-publish":true,"permalink":"/01-projects/ai-robot/servos/","tags":["python","sub_module"]}
---

# Servos
This will provide all supporting function for the servo's data manipulations

#### `dict_to_list` 
```python
def dict_to_list(the_dict):
    if len(the_dict) != 16:
        raise ValueError("The dictionary must contain exactly 16 elements.")
    return [the_dict[i] for i in range(16)]
```

#### `list_to_dict`

```python
def list_to_dict(the_list):
    if len(the_list) != 16:
        raise ValueError("The list must contain exactly 16 elements.")
    return {id: angle for id, angle in enumerate(the_list)}
```

#example 
```
```