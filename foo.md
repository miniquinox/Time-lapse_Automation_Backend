# Blender Automation guide

To run this script, using cmd go to your Blender Automation folder and type the following command:

```
"C:\Program Files\Blender Foundation\Blender 3.0\blender.exe" foo.blend --background --python "Blender_automation_V2.py"
```

Blender 3.1.2 an up MUST BE INSTALLED

Blender_Automation_V2.py:

- device_list.json : Contains the list of devices to be automated along with their corresponding scenes and the location of each camera (this location is specific to the product and scene). This list is used as a reference and should only be edited when a new product is added to our collection.

- parameters.json : This is your input file.

# Examples:

## device_list.json
```json
{
    "Sunglasses V1":{
        "Desktop Setup":{
            "Camera 1": {
                "Location x": 0.065321,
                "Location y": -0.460942,
                "Location z": 0.701089,
                "Rotation x": -270,
                "Rotation y": -360,
                "Rotation z": 0,
                "Frustum size": 0.05},
            "Camera 2": {
                "Location x": -0.065321,
                "Location y": -0.460942,
                "Location z": 0.701089,
                "Rotation x": -270,
                "Rotation y": -360,
                "Rotation z": 0,
                "Frustum size": 0.05
            }
        }
    },
}
```

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 26
}
```
