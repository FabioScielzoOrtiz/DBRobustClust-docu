# `plots`

## `clustering_MDS_plot_one_method`

```
Computes and display the MDS plot for a considered clustering configuration, 
differentiating the cluster labels and the real groups, if they are known.

Parameters (inputs)
----------
X_mds: a numpy array with the MDS matrix for the distance matrix used in the considered clustering configuration.
y_pred: a numpy array with the predictions of the response.
y_true: a numpy array with the true values of the response.
title: the title of the plot.
accuracy: the accuracy of the clustering algorithm, if computed.
time: the execution time of the clustering algorithm, if computed.
figsize: the size of the plot.
bbox_to_anchor: the size of the legend box.
title_fontsize: the size of the font of the title.
title_weight: the weight of the title.
points_size: the size of the points of the plot.
title_height: the height of the tile of the plot.

Returns (outputs)
-------
The described plot.
   
```


## `clustering_MDS_plot_multiple_methods`

```
Computes and display the MDS plot for a considered clustering configuration, 
differentiating the cluster labels and the real groups, if they are known.

Parameters (inputs)
----------
X_mds: a numpy array with the MDS matrix for the distance matrix used in the considered clustering configuration.
y_pred: a numpy array with the predictions of the response.
y_true: a numpy array with the true values of the response.
title: the title of the plot.
accuracy: the accuracy of the clustering algorithm, if computed.
time: the execution time of the clustering algorithm, if computed.
figsize: the size of the plot.
bbox_to_anchor: the size of the legend box.
title_fontsize: the size of the font of the title.
title_weight: the weight of the title.
points_size: the size of the points of the plot.
title_height: the height of the tile of the plot.

Returns (outputs)
-------
The described plot.
```