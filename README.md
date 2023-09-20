# SlicingTDUE

This repo is to make sliced objects and capture it as RenderTarget to send it via Spout for volumetric LED

### requirement
- UE5.2

# How to use
1. Open the project (takes a long time to compile all)
2. Play in Editor
3. Press Capture button
4. See if you can get spout in TD or any software

# Samples
in Maps folder
- SlicingTest
- SlicingLogo -> Special thanks to CraftTech360
- SlicingChase -> cute one haha

# Explanation

### BP_SlicedController
- BP Target Actors
- - Base Actor that is sliced
- Num Slice
- Num Elements X
- - number of column of RenderTarget
- Box Extent

# Make own BP_TargetActors
1. Create YOUR blueprint inheriting BP_TargetActorsBase
2. Add components that are only supported by Static Mesh, Skeltal Mesh, Niagara Particle 
3. Add your assets
4. if you use Niagara, you need extra steps
   - 
5. Modify all used Material
   - Drag and Drop MF_InsideBox_Mask to Material Editor from Materials folder
   - Blend mode has to be Masked and connect the MF to Opacity Mask


