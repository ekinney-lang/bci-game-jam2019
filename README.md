# bci-game-jam2019
This is the main code respository for the BCI Game Jam 2019. Currently this only includes the P300_Unity package for the Unity3D game engine. Additional resources will be uploaded as needed.

## P300_Unity

Thanks for joining the BCI Game Jam 2019 and downloading the P300 Unity asset! This tool was created to help game developers rapidly introduce a simple brain-computer interface (BCI) control scheme (the P300) into their games. The P300 Unity asset has been written for integration into a BCI processing pipeline using the LabStreamingLayer (LSL) backbone to synchronize events occuring in the game with specific brain activity.
 
## Getting Started

The P300 Unity project was built around the idea of providing a flexible framework for game developers to integrate in the P300 BCI control scheme. To get started, you simply need to import the P300_Unity package to your game. This includes all of the necessary back-end components requried for including a P300 control scheme. 

### Prerequisites
Unity Game Engine, V. 2019.2.0 or higher. **It is critical to have at least this version of Unity, or else certain parts of the package manager may not work**.

### Setting up the P300 Variables

Here is a step by step set of instructions to help you how get all of the game objects needed for running the P300 tool in your game.

Create the main P300 controller game object.

```
In the Unity editor, create an empty game object and name it P300Controller.
```

Add the required components to the P300Controller object.

```
Right-click on the P300Controller object and add the P300_Flashes script from the P300_Unity package. (Alternatively, drag the P300_Flashes script from the package folder onto your P300Controller object. 
```

Add the required *MarkerStreams* object to the game scene.
```
In the P300_Unity package folder, find the MarkerStreams prefab object located in the Prefabs folder. Add this to the game scene. 
```

Now verify that the added *MarkerStreams* game object has 2 attached components: the *LSL Marker Stream* script and the *Inlet_P300* script. If it does not have those two scripts then you will need to add them.

```
If the MakerStreams prefab does not have the above scripts, they need to be added. The LSL Maker Stream script can be found under P300_Unity/LSL4Unity/Scripts/. The Inlet_P300 is right inside the P300_Unity folder.
```

Add the *cube* prefab into the game. This will be the primary 'object' the P300 will use to populate the scene. You can change this prefab to be any shape/color/sprite you wish for your game.

```
From the P300_Unity/Prefabs folder, drag the cube prefab into the game heirarchy. Feel free to have the cube prefab be inactive in the hiearachy.
```

Add the *cube* game object references to the P300Controller game object and the *P300_Flashes* script.

```
Drag the cube game objects to the P300_Flashes script on the P300Controller object under My Cube.
```

That should be it! You should now be able to hit play, and the P300 tool will populate a set of *cube* game objects based on the options in the *P300_Flashes* component. Hit "S" to try running single flashes, and you should see an output reading in your debug log naming off each cube every time it is highlighted.

## Using the P300 Unity Tool

There are several places for you as the developer to alter the P300 tool to do what you want. 

First, you can alter what type of objects are being highlighted by changing the properties of the *cube* prefab. 
This can include the number of objects you want a user to select from (minimum 2), 
the colors you'd like to highlight, positioning (e.g. where on the screen you'd want the cubes to be) etc. 
Even the number of rows/columns of cubes can be chosen and the distance between the rows and columns can be changed.
The majority of these changes can be done in the *P300_Flashes* component.

If you want to change what happens when the correct object is selected, you will need to edit the *Inlet_P300* script, lines 61, 69, and 78 where it says a variation of:
`cube_list[cubeIndex].GetComponent<Renderer>().material.color = Color.green;`
These 3 lines are what tells Unity what to do with positive findings from the back-end analysis handled in MATLAB or Python. 
(In this case, it simply recolors the cube's material to be green when selected).
 
A demo showing off a potential use for this tool is included in the P300_Unity package under the **Demo** folder. There, you will find variations of the *P300_flashes* and *Inlet_P300* script to showcase how this tool could be used for selecting choices in a HUD system, such as for the Hololens. Note that the 'choice' selected in this demo is just randomly selected (as seen in the *Demo_Inlet_P300* script, and requires the proper set-up seen in the actual *Inlet_P300* script for reading in events.
 
## Built With

* [LabStreamingLayer](https://github.com/sccn/labstreaminglayer) - The synchronization framework used
* [LSL4Unity](https://github.com/xfleckx/LSL4Unity) - The LSL wrapper used for Unity

## Contributing

Please contact [Eli Kinney-Lang](https://github.com/ekinney-lang) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

This is the beta version 0.1 of the P300 Unity asset. Updated October 08, 2019 by EKL.

## Authors

* **Shem Murji** - *Primary Contributor* - [Github Repo](https://github.com/shemmurji/shemmurji.github.io)
* **Eli Kinney-Lang** - *Project Lead* - [Github Repo](https://github.com/ekinney-lang)

## License

This project is licensed under the CC-BY-SA 3.0- see [here](https://creativecommons.org/licenses/by-sa/3.0/) for details

## Acknowledgments

* This project was developed under the support of the Calgary Pediatric Stroke Program (CPSP), Dr. Adam Kirton and Dr. Ephrem Zewdie.
* Original funding for this work provided by: Biomedical Engineering Program at the University of Calgary

