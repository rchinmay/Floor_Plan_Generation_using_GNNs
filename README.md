# Residential Floor Plan Generation Using Deep Learning Techniques

> Our project provides a user-friendly software solution that minimizes the gap between the complexity of designing residential floor plans and the capabilities of non-technical users. users can input the boundary of their piece of ground and their preferences which are then seamlessly processed by our advanced AI model to generate customized floor plans. 

## Dataset
- The source dataset is [Rplan Dataset](http://staff.ustc.edu.cn/~fuxm/projects/DeepLayout/index.html), it is a dataset consists of about 80k floor plans as images.
- First, we converted the image-based RPlan dataset to a geometry-based dataset, this conversion helped us with some benefits:
  - Accurate Representation.
  - Geometric Operations such as buffers, and intersections.
- Then, we created a customized dataset as **Graphs** to be a new version of the Rplan floor plans. This conversion helped us train the **GAT-Net** model.

## Our full architecture consists of 2 stages:
1. Predicting room centroids. Using CNN model.
2. Best room size estimation Using GNN model **[Our work in this repo]**

![image](https://github.com/mo7amed7assan1911/Floor_Plan_Generation_using_GNNs/assets/55090589/c0448e53-fdc6-471a-9e0c-8b1aee185363)

> * User inputs:
>   * The boundary of his piece of ground and the position of the front door.
>   * His preferences such as the number of rooms, bathrooms, and kitchens.
> * User gets:
>    * Final layout for his floor plan.
>    * 3D model for his floor plan.
>
> **We will focus in this repository on the second stage to get the best room size estimations using the GNN model.**

## Stage 2: Using Graph Neural Networks (GNNs) for floor plan analysis and get best room size estimation.

### How do we use Graphs in our task:
* For each floor plan two types of graphs were created: one representing the floor plan itself and another representing the boundary of the floor plan.
* The process of creating the graphs involved the following steps:
	* **Polygon-to-Node Conversion:** The nodes were assigned features such as the type of polygon (e.g., room, bathroom), the centroid's X and Y coordinates, the room size (expressed as the ratio of the room's area to the total floor plan area), and the width and height of the square bounding the polygon. Also, the boundary graph was created.
	* **Connections - Edges - between the nodes:** Real connections, Living to all connections, and All-to-All connections.

> Below, is a floor plan from the dataset and the corresponding generated graphs.

![image](https://github.com/mo7amed7assan1911/Floor_Plan_Generation_using_GNNs/assets/55090589/3e49c78e-f1e5-49a6-8dd3-23b1ce8151f1)

