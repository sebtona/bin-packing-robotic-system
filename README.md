# Bin Packing Robotic System
My graduate research aims at creating an accessible robotic system that can be used to test various 3D bin packing algorithms. An arm robot was integrated with a depth sensing camera so that given a random set of objects, each object can be grasped, 3D scanned, and packed into a container in a pose based on chosen criteria.

<img src="https://github.com/sebtona/bin-packing-robotic-system/blob/main/thumbnail.jpg" alt="Sawyer" width="400"/>

## Challenges
- Repurposing hand-eye calibration code to work with Sawyer robot
- Repurposing GR-ConvNet and pick-and-place code to work with Sawyer robot
- Automating the creation of 3D models of objects held by Sawyer
- Creating a bin and set of objects that can be used to test the effectiveness of a given bin packing algorithm

## Implementation
### Hardware
- Sawyer arm robot positioned in front of table workspace
- Intel RealSense Depth Camera D435 mounted to an overhead apparatus
- Created hand-eye calibration object
- Wooden bin created for bin pack testing
- Set of objects designed and 3D printed for bin pack testing

<img src="https://github.com/sebtona/bin-packing-robotic-system/blob/main/blocks.png" alt="Object Set and Bin" width="400"/>

### Software
#### Hand-Eye Calibration
- Set of coordinates adjusted for Sawyer's workspace
- Joint angle constraints determined and enforced to ensure the calibration object is fully visible at all times
#### Object Grasping
- GR-ConvNet neural network by Sulabh Kumra used to generate grasps for objects
- Grasping code originally created for Baxter robot adapted for use with Sawyer robot

<img src="https://github.com/sebtona/bin-packing-robotic-system/blob/main/grasps.png" alt="Generated Grasps for Objects Alone and In Clutter" width="400"/>

#### Object Modeling
- Intel RealSense SDK used to capture point clouds of object from all sides
- Intera SDK used to tell Sawyer to rotate the object as the depth camera captures point clouds
- Point clouds of the object from all six angles filtered and segmented using Point Cloud Library (PCL), then stitched together into a full object model
- Model of object converted to PointCloud2 ROS message and displayed in RViz

<img src="https://github.com/sebtona/bin-packing-robotic-system/blob/main/block_and_model.png" alt="Block and Point Cloud Model" width="400"/>

### Object Packing
- Code written to pack objects in bin with desired location and orientation

## Deliverables
- Operation Demonstration
- IEEE Conference Paper
- User Guide
- Code

## Future Work
- Allow robot the option to approach object from sides when grasping
- Have robot pack bins from the side (similar to packing a truck)
- Adapt project to other end of arm tooling (EOAT) options, such as a vacuum gripper
- Add code to automatically extract a set of geometric features from an object model
- Test novel 3D bin packing algorithms