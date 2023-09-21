# SlicingTDUE

This repository enables you to slice objects and then capture the result as a RenderTarget. You can then send this RenderTarget via Spout for use in volumetric LED displays.

## Requirements
- **Unreal Engine (UE)**: Version 5.2 or above.

## Getting Started

### Installation
1. Clone or download the repository.
2. Open the project. *(Note: It may take some time to compile everything.)*

### Usage
![Howtouse](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/d6d79a34-3c84-4166-a7b7-8f228eb905d3)

1. Open level
2. Play the project in the Editor.
3. Click on the "Capture" button.
4. Check if you can receive the Spout feed in TouchDesigner (TD) or any other compatible software.

## Sample Maps

Find the following sample maps in the `Maps` folder:
- `SlicingTest`
- `SlicingLogo` - *A special thanks to CraftTech360 for this sample.*
- `SlicingChase` - Just a fun little sample!

## Core Components
![BP_slicedController](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/59c0ee9a-c6b7-4857-a8f0-766d41641938)

### BP_SlicedController
- **BP Target Actors**: The base actor that will be sliced.
- **Num Slice**: Number of slices.
- **Num Elements X**: Defines the number of columns in the RenderTarget.
- **Box Extent**: Extent of the box.

## Creating Your Own BP_TargetActors
![inheritingbase](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/f0dc0c89-e7a3-4bc4-a362-22ed21113785)

1. Create a new blueprint that inherits from `BP_TargetActorsBase`.
2. Add components that are compatible with either **Static Mesh, Skeletal Mesh, or the Niagara Particle System**.
3. Add your desired assets to the blueprint.
4. If you're using Niagara:
![niagaraextrastep](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/415a79cb-4997-4ce6-8f2d-6a8df1c49944)

   - Override the `SetNiagaraDynamicMaterial` function.
   - Create a Material Dynamic Instance using the material found in the Niagara particle.
   - Set the material, location, and BoxExtent.
     ![niagaramaterial](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/a27e2ea6-2721-4297-b72c-047ac57a4282)

   - Within Niagara, create a Material Instance Parameter. Then, set it as a User Param Binding in the override material section.
  


![particle](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/e72f1622-72b7-4bd1-9074-8339b3d3d67b)

5. Modify all used materials:
   - Drag and drop `MF_InsideBox_Mask` to the Material Editor from the `Materials` folder.
   - Ensure the blend mode is set to "Masked" and connect the MF to the Opacity Mask.
6. You're free to add any other features or components as needed.

*If you're having trouble, refer to the provided sample blueprints for guidance.*

## Adjusting Resolution
![resolution](https://github.com/miwa-maroon/SlicingTDUE/assets/65750938/500eeaec-e6db-4d29-b0aa-1e33e3698ea6)

To change the resolution:
- Update the resolution in `RenderTarget (RT_Slices)`.
- Adjust the resolution in `Spout2MediaOutput (Spout2MediaOutput1)`.



