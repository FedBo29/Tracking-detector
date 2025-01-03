# Reconstruction
This is the reconstruction algorithm.
The aim is reconstruct the Z-vertex position of the collition from the hit points of the layers.

Starting from the layer 1, the algorithm matches every hit with the ones of the layer 2 forming a line. The tracklet, i.e. the lines that likes the hit point of the two layer, are done if the angle between the line and the X-axes is smaller than 6mRadiant. Each event can have multiple tracklets along the z-axes. An histogram is filled with all the z coordinates of the Z-axes. What we get is a distribution of trackets for each event.

Now, in order to reconstruct the event, there are three main posisbilities:

1. No tracklets in the histogram: the event is not reconstructed.
2. Only one tracklet: the event is reconstructed with that position.
3. multiple tracklets.

The multiple trackelts represents the most difficult case, here we must create an algorithm to select the vertex position.
We find the bins with the highest number of entries and we save the index in a vector. With this list, we run those bins and we count the number of entries until we find a hole in the bin. The, the weighted average has been calculated for the group of bins. Here, we find a centroid and, from this position, the calculate the average of point next to 1.5 mm from it.
The value will represent the z vertex position.

![immagine](https://github.com/user-attachments/assets/0e38faaf-00f9-46cf-963a-3398ad33a166)
