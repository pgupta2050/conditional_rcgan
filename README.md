**Authors**: [Prakhar Gupta](https://www.linkedin.com/in/prakharkalyangupta/), [Mayuresh Bhosale](https://www.linkedin.com/in/mayuresh-bhosale-b6b935136/)

This work is the capstone project for the graduate course CPSC8810: ML for Image Synthesis by Dr. Siyu Huang at Clemson University. 

<!-- [About Me](/_pages/about/) -->


### Motivation & Key Idea

We build upon the ideas from [Retrospective Cycle GAN (Kwon et al)](https://openaccess.thecvf.com/content_CVPR_2019/papers/Kwon_Predicting_Future_Frames_Using_Retrospective_Cycle_GAN_CVPR_2019_paper.pdf). They established great performance compared to the SOTA with their forward and backward temporal consistency idea for training the generator. However, they do not consider any conditionong on physics or restrict the movement of pixels expicitly
<!-- ![kitti_paper](assets/kitti_paper.png) -->
<p align="center">
  <img src="assets/images/kitti_paper.png" alt="kitti_paper" width="450"/>
  <br />
  <em>Figure 1: This image from Kwon et al (2019) shows the blurring in longer term predicitons and distortions. Even though they outperform PredNet, it has room for improvement.</em>
</p>

We ask the following quesiton: **"Can we improve blurring in longer term predictions through the use of physics constraints?"**

#### RCGAN baseline model
They use two discriminators - one for image frame reconstruction and one for image sequence temporal consistency. The loss function in the baseline model is given by :
<p align="center">
  <img src="assets/images/rcgan_loss.png" alt="loss" width="250"/>
</p>

<h2 class="custom-heading">RCGAN baseline model</h2>

#### Optical Flow Conditioned RCGAN
To restrict pixel movement to realistic areas indirectly, we exploit [RAFT, Teed et al](https://arxiv.org/abs/2003.12039) pre-trained optical flow model to condition generations on optical flow loss. 
<p align="center">
  <img src="assets/images/raft_flow.png" alt="kitti_paper" width="500"/>
  <br />
  <em>Optical flow detection perormance on KITTI dataset has been well estbalished by the Teed et al.</em>
</p>


The new loss function is designed as:
<p align="center">
  <img src="assets/images/rcgan_flow_loss.png" alt="loss" width="350"/>
</p>


#### Kinematics Constraint Flow Conditioned RCGAN

The new loss function is designed as:
<p align="center">
  <img src="assets/images/rcgan_kine_loss1.png" alt="loss" width="450"/>
</p>


#### Combined Contstraints Conditioned RCGAN



### Project Results

We trained the conditional GAN on KITTI dataset city driving frame sequences of length 5. The models were evaluated on ~70 test sequences. Results belows show the performance of 3 models at different training epoch numbers for 2 chosen test sequences

Epoch 10:

<p align="center">
  <img src="assets/images/result_0.png" alt="loss"/>
</p>

<p align="center">
  <img src="assets/images/results_e10.png" alt="loss"/>
</p>

<p align="center">
  <img src="assets/images/results_e10_tab.png" alt="loss" width="400"/>
</p>

Epoch 30:

<p align="center">
  <img src="assets/images/results_e30.png" alt="loss"/>
</p>

Epoch 50:

<p align="center">
  <img src="assets/images/results_e50.png" alt="loss"/>
</p>


Epoch 100:

<p align="center">
  <img src="assets/images/results_e99.png" alt="loss"/>
</p>

<p align="center">
  <img src="assets/images/results_e99_tab.png" alt="loss"  width="400"/>
</p>

### Project Insights and Conclusions

<p align="center">
  <img src="assets/images/results_kineExtra.png" alt="loss"/>
</p>