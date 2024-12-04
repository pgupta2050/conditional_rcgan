**Authors**: [Prakhar Gupta](https://www.linkedin.com/in/prakharkalyangupta/), [Mayuresh Bhosale](https://www.linkedin.com/in/mayuresh-bhosale-b6b935136/)

**Institution**: Clemson University

**Project Report PDF**: [Report](/assets/files/report.pdf)

**Course Name**: CPSC8810 ML for Image Synthesis, Dr. Siyu Huang

<!-- [About Me](/_pages/about/) -->

<h2 style="color: brown; text-align: center;">Motivation & Key Idea</h2>

We build upon the ideas from [Retrospective Cycle GAN (Kwon et al)](https://openaccess.thecvf.com/content_CVPR_2019/papers/Kwon_Predicting_Future_Frames_Using_Retrospective_Cycle_GAN_CVPR_2019_paper.pdf). They established great performance compared to the SOTA with their forward and backward temporal consistency idea for training the generator. However, they do not consider any conditionong on physics or restrict the movement of pixels expicitly
<!-- ![kitti_paper](assets/kitti_paper.png) -->
<p align="center">
  <img src="assets/images/kitti_paper.png" alt="kitti_paper" width="450"/>
  <br />
  <em>Figure 1: This image from Kwon et al (2019) shows the blurring in longer term predicitons and distortions. Even though they outperform PredNet, it has room for improvement.</em>
</p>

We ask the following quesiton: **"Can we improve blurring in longer term predictions through the use of physics constraints?"**

<h2 style="color: brown; text-align: center;">Formulation</h2>

<h3 style="color: blue;">RCGAN baseline model</h3>

They use two discriminators - one for image frame reconstruction and one for image sequence temporal consistency. The loss function in the baseline model is given by :
<p align="center">
  <img src="assets/images/rcgan_loss.png" alt="loss" width="350"/>
</p>


<h3 style="color: blue;"> Optical Flow Conditioned RCGAN</h3>

To restrict pixel movement to realistic areas indirectly, we exploit [RAFT, Teed et al](https://arxiv.org/abs/2003.12039) pre-trained optical flow model to condition generations on optical flow loss. 
<p align="center">
  <img src="assets/images/raft_flow.png" alt="kitti_paper" width="550"/>
  <br />
  <em>Figure 2: Optical flow detection perormance on KITTI dataset has been well estbalished by the Teed et al.</em>
</p>


The new loss function is designed as:
<p align="center">
  <img src="assets/images/rcgan_flow_loss.png" alt="loss" width="450"/>
</p>


<h3 style="color: blue;"> Kinematics Constraint Flow Conditioned RCGAN</h3>


The new loss function is designed as:
<p align="center">
  <img src="assets/images/rcgan_kine_loss1.png" alt="loss" width="580"/>
</p>


<h3 style="color: blue;"> Combined Contstraints Conditioned RCGAN</h3>



<h2 style="color: brown; text-align: center;"> Project Results</h2>

We trained the conditional GAN on KITTI dataset city driving frame sequences of length 5. The models were evaluated on ~70 test sequences. Results belows show the performance of 3 models at different training epoch numbers for 2 chosen test sequences

<h3 style="color: blue;">Epoch 10</h3>

<p align="center">
  <img src="assets/images/result_0.png" alt="loss"/>
</p>

<p align="center">
  <img src="assets/images/results_e10.png" alt="loss"/>
</p>

<p align="center">
  <img src="assets/images/results_e10_tab.png" alt="loss" width="350"/>
</p>

<h3 style="color: blue;">Epoch 30</h3>

<p align="center">
  <img src="assets/images/results_e30.png" alt="loss"/>
</p>

<h3 style="color: blue;">Epoch 50</h3>
[ .... ] ...

<p align="center">
  <img src="assets/images/results_e50.png" alt="loss"/>
</p>


<h3 style="color: blue;">Epoch 100</h3>

[ .... ] ...

<p align="center">
  <img src="assets/images/results_e99.png" alt="loss"/>
</p>

<p align="center">
  <img src="assets/images/results_e99_tab.png" alt="loss"  width="350"/>
</p>



<h2 style="color: brown; text-align: center;">Project Insights and Conclusions</h2>

[ .... ] ...

<p align="center">
  <img src="assets/images/results_kineExtra.png" alt="loss"/>
</p>