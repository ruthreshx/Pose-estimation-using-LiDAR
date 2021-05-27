# Pose_estimation


The repo is all about implementing hprel paper. 

The Hperl paper has two archtecture 

  AVOD(https://arxiv.org/pdf/1712.02294.pdf) followed by 
  LCRNET++ (https://arxiv.org/pdf/1803.00455.pdf).
  
In this repo used dope(https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123710375.pdf) which make use of LCRNET++ as a part.

First the AVOD (Aggregate View of Object Detection) architecture is cloned from the git https://github.com/kujason/avod. Here we are mainly concern about pedistrain. So by taking the pedistrain config file the data is trained.
 
AVOD is trained with AVOD_People_example config for 70 epoch and time taken is 10 Hours

After finished of the training phase the testing phase is started. 

For testing it taken 16 Hours for 110 epoch

      EASY(%)  MODERATE(%)   HARD(%)  VIEW MODE
      60.80      52.81       40.88    AP - 3D
      58.75      51.05       47.54    AP -BEV
