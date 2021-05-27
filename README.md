# Pose_estimation


The repo is all about implementing hprel paper. 

The current state-of-the-art is focused only
on RGB and RGB-D approaches for predicting the 3D human
pose. However, not using precise LiDAR depth information limits
the performance and leads to very inaccurate absolute pose
estimation. With LiDAR sensors becoming more affordable and
common on robots and autonomous vehicle setups, we propose
an end-to-end architecture using RGB and LiDAR to predict
the absolute 3D human pose with unprecedented precision.

The Hperl paper has two architecture 

  AVOD(https://arxiv.org/pdf/1712.02294.pdf) followed by 
  LCRNET++ (https://arxiv.org/pdf/1803.00455.pdf).
  
  Avod is used for predicting the pedestrain in the real time followed by the LCRNET++ which derives the poses from the detected pedestrain with 13 keypoints
  
  
In this repo used dope
(https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123710375.pdf) 
which make use of LCRNET++ as a part.

**Getting Started**

First the AVOD (Aggregate View of Object Detection) 
Architecture is cloned from the git 

    git clone https://github.com/kujason/avod. 
    
Here we are mainly concern about pedestrain.We have trained by the various epoch So by taking the pedistrain config file the data is trained.
 
AVOD is trained with AVOD_People_example config for 70 epoch and time taken is 10 Hours

After finished of the training phase the testing phase is started. 

For testing it taken 16 Hours for 110 epoch

      EASY(%)  MODERATE(%)   HARD(%)  VIEW MODE
      60.80      52.81       40.88    AP - 3D
      58.75      51.05       47.54    AP -BEV

![pose_estimation](https://user-images.githubusercontent.com/84854222/119814972-a8f1e200-bf08-11eb-9a83-0035ff2f8df3.png)


Once we done the pedestrian detection move to the LCRNET++ part which contains pose estimation from detected the pedestrian.

LCRNET++(Localization, Classfication & Regression )

Architecture is cloned from the git 

    git clone https://github.com/naver/dope
    
   
post-processing with a modified version of LCR-Net++

Our post-processing relies on a modified version of the pose proposals integration proposed in the LCR-Net++ code. To get this code, once in the DOPE folder, please clone our modified LCR-Net++ repository:

    git clone https://github.com/naver/lcrnet-v2-improved-ppi.git
    
    
 To use our code on an image, use the following command:

      python dope.py --model <modelname> --image <imagename>
      
      For ex:
      python dope.py  --model DOPErealtime_v1_0_0 --image post_estimation.jpg
      
 
 Note that DOPE predicts 3D poses for each body part in their relative coordinate systems, eg, centered on body center for bodies. For better visualization, we approximate 3D    scene coordinates by finding the offsets that minimize the reprojection error based on a scaled orthographic projection model.
 
 
 **Final Output:**
 ![pose_estimation_13keypoints](https://user-images.githubusercontent.com/84854222/119815862-a6dc5300-bf09-11eb-8992-e7744d731ee7.png)

