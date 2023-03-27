# Lip-Synchronization
The objective of this work is to enhance the placement of actuators on a physical humanoid robot to enable realistic lip synchronization. 
To achieve this, the algorithm collects vertex position data from an animation of a 3D mesh model of any target humanoid face speaking with synchronized lips.
In our provided assets we include a humanoid 3D mesh model that corresponds to the open-source robot Eva: https://www.creativemachineslab.com/eva.html
<p align="center">
  <img src="https://user-images.githubusercontent.com/105757489/227993954-ea60352b-c5cb-4a96-9e20-b21ddf056aa7.png"/>
</p>
Any 3D model animation of a humanoid face is compatible as long as the vertex locations can be exported, however we used MeshTalk: https://github.com/facebookresearch/meshtalk to generate our animation automatically from just our 3D mesh model and a sound clip of speech.

https://user-images.githubusercontent.com/105757489/228003068-a9cd72eb-71fa-4e16-bff7-41db7ba37f62.mp4


An array of vectors representing the displacement of the vertices from one frame of animation to the next is created.
<p align="center">
  <img src="https://user-images.githubusercontent.com/105757489/227994072-8c9485d8-1c44-43d4-94ab-d91b98150e80.png"/>
 </p>
The algorithm then uses K-means to reduce the dimensionality of the motion vectors to vectors that can represent the optimized placement of actuators for the speech sequence.
<p align="center">
  <img src="https://user-images.githubusercontent.com/105757489/227994147-2540cc7b-b56e-4cad-86f8-b334cbb9e862.png"/>
 </p>
 The motion vectors for each frame of video are grouped based on similarity to the motor vectors, and the amplitude of each motion vector is used to determine how far each motor should be actuated for each animation frame. This data can be used to directly control the motors positions for each 1/30 second interval of animation.
 
 ![Method_algo](https://user-images.githubusercontent.com/105757489/227984066-6640eae9-ab55-491b-9cfc-0b663f321fd6.png)
 
 In future additions, the animation will be reconstructed using the recommended actuator placement and motor angles calculated by the algorithm. The user can then increase or decrease the number of desired actuators based on these physics-informed simulation results.
