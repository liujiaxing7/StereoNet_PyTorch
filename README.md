# StereoNet implemented in PyTorch

**Currently training (2021-09-04) (~20hrs per epoch on my 1070)**

Implementation of the StereoNet network to compute a disparity map using stereo RGB images.

Currently training, early results are ok.  Validation EPE $\approx20$ pixels.  Still need to implement the left/right disparity training vs just using the left disparity.

Epoch 10:

<img src="./readme_images/Epoch_10_Val.JPG" alt="Validation image" style="width:1000px;"/>

Implemented using PyTorch Lightning as a learning exercise to learn about stereo networks, PyTorch, and PyTorch lightning.  Feel free to make any comments or recommendations for better coding practice.

Currently implemented

* Downsampling feature network with `k_downsampling_layers`
* Cost volume filtering
* Hierarchical refinement with cascading `k_refinement_layers`
* Robust loss function [A General and Adaptive Robust Loss Function, Barron (2019)](https://arxiv.org/abs/1701.03077)

Currently unclear

* "We found that, intuitively, training with the left and right disparity maps for an image pair at the same time significantly sped up the training time." Page 9.  Does that mean for each left/right RGB image pair, they compute the loss for the left disparity and the loss for the right disparity and then sum?  I need to investigate.

    * I think maybe I need to compute 2 cost volumes and then have 2 passes through the cascading refiner.  I'll think.