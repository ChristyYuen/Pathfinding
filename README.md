# Navmesh Pathfinding with Bidirectional A* Search

## Overview

This project implements a **bidirectional A\*** search algorithm in Python to find optimal paths in navigation meshes (navmeshes) generated from user-provided images. The navmeshes are built using rectangular regions (nodes) extracted from the images, and the goal is to compute a valid path between two points interactively selected on the image.

The provided template includes base code for building navmeshes, displaying images, and user interaction, leaving the implementation of the pathfinding algorithm to complete. This project uses a **bidirectional A\*** search algorithm for efficient pathfinding.

## Features

- **Bidirectional A\*** search for fast and optimal pathfinding.
- Navmeshes generated from any black-and-white image.
- Interactive GUI: click to select source and destination points.
- Customizable for user-provided images.
- Visualization of computed paths directly on the image.

## How It Works

1. **Navmesh Construction**: 
   The `p2_meshbuilder.py` script takes a black-and-white image and generates a navmesh as a pickled binary file. The mesh represents the walkable space in the image as a collection of non-overlapping rectangular regions (nodes) with adjacency data.

2. **Interactive Pathfinding**: 
   Using the `p2_interactive.py` script, users can visualize the image and interactively select source and destination points by clicking. After the second click, the `find_path` function is invoked to calculate and display the optimal path.

3. **Bidirectional A\***: 
   The core of the project is the implementation of the bidirectional A\* algorithm in `p2_pathfinder.py`. This algorithm searches from both the source and destination points simultaneously, meeting in the middle to reduce the search space and improve efficiency.

## Setup and Usage

### Requirements

- Python 3.x
- SciPy (for navmesh generation)

Install dependencies via pip:

```bash
pip install scipy

Running the Pathfinding Program
To generate a navmesh for an image, run the following command:

bash
Copy code
python src/p2_meshbuilder.py <your_image.png>
This will create a .mesh.pickle file that contains the navmesh data.

To run the interactive pathfinding application, use the following command:

```bash
python src/p2_interactive.py <your_image.png> <your_image.png.mesh.pickle> <subsampling_factor>
Example:

```bash
python src/p2_interactive.py input/homer.png input/homer.png.mesh.pickle 2
Image file: The PNG image to display.
Pickled navmesh: The binary file containing the pre-built navmesh.
Subsampling factor: An integer to scale down large images for display.
In the interactive window:

Click once to select the source point (red circle).
Click again to select the destination point (blue circle).
The optimal path will be displayed as a series of connected line segments.

Key Files
p2_interactive.py: Handles image display and user interaction. Calls find_path to compute the path between selected points.

p2_meshbuilder.py: Generates the navmesh from a black-and-white PNG image. The navmesh is saved as a .mesh.pickle file.

p2_pathfinder.py: Contains the find_path function, where the bidirectional A* algorithm is implemented.

Heuristic
The algorithm uses the Euclidean distance between the current node and the destination as a heuristic to prioritize search directions.

