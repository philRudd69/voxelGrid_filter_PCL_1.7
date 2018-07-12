# voxelGrid_filter_PCL_1.7

Installation:

1. create your 'catkin_workspace' folder at a convenient location

2. place a 'src' folder in this catkin workspace, such that it looks like this: .../catkin_workspace/src/

3. cd to the catkin_workspace and call 'catkin_make' from there. DONE.


Use like this:

0. follow the steps from my repository 'voxelGrid_filter_PCL_1.8'

1. assuming you did step 1. of the other (...PCL_1.8) repo, continue with:
   to apply voxel grid filter to a point cloud, specify its load path and saving path:

	./downsampling_compare -downsample /path/to/point/cloud/ /saving/path/for/downsampled/cloud/

then you have one downsampled version of the point cloud filtered with voxelGrid filter of PCL 1.7 and another one filtered with voxelGrid filter of PCL 1.8

3. now you can compare the two downsampled point clouds with (use same paths as in step 1)
   you can use the following command with the executable of both repos (1.7. and 1.8), they are exactly the same.

	./downsampling_compare -compare /path/to/point/cloud/ /saving/path/for/downsampled/cloud/

Expected result: The filter should produce different results for both PCL versions.
