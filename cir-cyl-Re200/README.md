# Laminar flow over a circular cylinder simulation with OpenFOAM v7
​
This is a part of our undergraduate project titled 'Aeroelastic modelling of insect flight' carried out in the school of Mechanical sciences, Indian Institute of Technology Goa.

* Authors: Nithin Adidela, Revanth Sharma, Y. Sudhakar

* email: {nithin.adiela.16003,revanth.sharma.16003,sudhakar}@iitgoa.ac.in

The  simulation is tested with OpenFOAM v7 in serial as well as parallel modes in a machine running Ubuntu 18.04.

## Highlights 

Reynold's number 200
Inlet Velocity Ux = 1 m/s
Diameter of the cylinder =1 m
Kinematice Viscosity = 0.005 m2/s

## Domain Description

The domain is a rectangle of length of 33 m, height of 16 m and a width of 1 m. The boundingBox is (-8 -8 -0.5) (25 8 0.5). The diameter of the circular cylinder is 1 m which is taken as the characteristic length. The cylinder is fixed, and its center is located at (0,0,0). From the center of the cylinder the domain expands for  25 characteristic lengths (25D = 25 m) to the right, 8 characteristic lengths (8D = 8 m)  to the left, 8 characteristic lengths to the top (8D = 8 m) and 8 characteristic lengths to the bottom (8D = 8 m). The domain for fixed flow over circular cylinder can be seen in figure.

A fine mesh is required near the periphery of the cylinder of the cylinder as well as the wake region and a gradual mesh grading is done to get a coarse mesh at the boundaries. The meshing is achieved with the help of blockMesh. The number of mesh points is 1,27,912. The number of mesh cells produced is 63,420. The mesh over the whole domain as well as a close-up view of the mesh around the cylinder for fixed flow over circular cylinder can be seen in figure.

## Boundary Conditions

Velocity boundary conditions applied are, at the inlet, uniform fixed velocity is applied. Ux is 1 m/s; Uy is 0 1 m/s; Uz is 0 1 m/s. At the outlet a Newman condition is applied with zeroGradient. 

Pressure boundary conditions applied are, at the inlet a Neumann condition is applied with zeroGradient. At the outlet a uniform fixed value of 0 is applied. 

At the top and the bottom patches, a slip condition is applied using symmetryPlane. On the surface of the cylinder a no-slip condition is applied.

## Running the case
​
To mesh

> $ blockMesh

To check the quality of the mesh

> $ checkMesh

To run the simulation in serial
> $ icoFoam

To run the simulation in parallel:

First decompose the mesh, edit the file *system/decomposeparDict* and run

> $ decomposePar

> $ mpirun -np 6 icoFoam -parallel > log & 

Reconstruct the case before viewing the results by running 

> $ reconstructPar


## Outputs

Results can be viewed in paraFoam by typing 

> $ paraFoam

Additionally the Coefficient of Forces are found in *postProcessing/forces/0* directory



