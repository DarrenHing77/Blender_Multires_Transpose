# Multires Transpose
An addon inspired by ZBrush's Transpose Master Plugin. It aims to mimic its functionality by allowing the user to edit an arbitrary number of multiresolution modifier-enabled meshes at once through a single lower subdivision level mesh, with support for objects with different subdivison levels, as well as meshes without the multires modifier.

Requires Blender 4.4 or later. **Tested and working in Blender 4.5**.

## How to use:
UI Panel located in the sidebar of the 3D viewport under `Edit > Multires Transpose`
1. Select meshes to create a Transpose Target proxy mesh for
2. Click `Create Transpose Target` to create a proxy mesh
3. Make changes to the proxy mesh
4. Click `Apply Transpose Target` to apply the changes to the original meshes

https://github.com/19829984/Blender_Multires_Transpose/assets/57331630/7cfed5dc-f0de-46e2-a534-f9e1a5b3fcf5

## Features:
Multires Transpose Version 1.1.0:
* **Blender 4.4+ Compatibility**: Fixed API compatibility issues for modern Blender versions
* Allows editing an arbitrary number of multiresolution modifier-enabled meshes at once through creating a single lower subdivision level proxy mesh.
    * This proxy mesh can be created through the Create Transpose Target operator
    * Supports using objects with different subdivision levels, or the same level for all objects
    * Can optionally include meshes not using the multires modifier
        * The proxy mesh for this will use the original mesh without any modifiers applied
* Changes to the proxy mesh can be propagated back to the original meshes with the Apply Transpose Target operator
    * Modifiers can be used on the proxy mesh, this allows you to rig the proxy mesh or use other modifiers.
    * The makes use of the multires modifier's reshape operator, which may not propagate the changes with 100% accuracy.
    * Therefore you can specify the number of iterations to apply the reshape operator to improve the accuracy of the changes
        * Use auto iteration to automatically reshape the mesh until the changes are within a specified threshold, or until the specified number of iterations have been reached
* **New in 1.1.0**: Apply Base option to apply base mesh changes to the multires modifier after reshaping
* **New in 1.1.0**: Delete Transpose Target option (enabled by default) to automatically clean up the proxy mesh after applying changes
* **Improved**: Better error handling when no valid objects are selected
* **Improved**: Enhanced faceset preservation during transpose operations
* Multiple Transpose Targets can be created to store different poses.
  
https://github.com/19829984/Blender_Multires_Transpose/assets/57331630/0889b592-a5b5-4d20-a5f2-81b7202f1303

## Settings:

### Create Transpose Target:
- **Use Multires Level As Is**: Use the current multires level of selected objects
- **Include Non-Multires Objects**: Include objects without multires modifiers
- **Hide Original Objects**: Hide original objects after creating transpose target
- **Multires Level To Use**: Specific subdivision level to use (when not using "as is")

### Apply Transpose Target:
- **Auto Iterations**: Automatically apply reshape until threshold is reached
- **Delete Transpose Target**: Remove the transpose target after applying (default: ON)
- **Hide Transpose Target**: Hide the transpose target after applying (disabled when delete is enabled)
- **Apply Base**: Apply base mesh changes to multires modifier after reshaping
- **Threshold**: Accuracy threshold for auto iterations
- **Max Auto Iterations**: Maximum iterations for auto mode
- **Reshape Iterations**: Number of reshape iterations for manual mode

### Known Limitations
- Does not work with multiuser data (instancing)
- Some complex faceset configurations may not preserve perfectly across all operations

## Changelog

### Version 1.1.0
- **Fixed**: Blender 4.4+ compatibility issues
- **Added**: Apply Base checkbox option for multires modifier
- **Added**: Delete Transpose Target option (default: enabled)
- **Improved**: Better error handling and user feedback
- **Improved**: Enhanced faceset preservation
- **Tested**: Confirmed working in Blender 4.5

### Version 1.0.3
- Initial stable release
- Basic transpose functionality
- Support for multiple subdivision levels
