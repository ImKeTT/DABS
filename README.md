## What is it ?

2019 Student Reaserch Training Program (SRTP) project: Diagnosis and analysis of bone structure. Supervised by Prof.[Wenxi Liu](http://cmcs.fzu.edu.cn/website/f/teacherDetail?id=212) ,Fuzhou University. Osteocyte images provieded by Dr.[Junning Chen](https://emps.exeter.ac.uk/engineering/staff/jc934) , Biomedical engineering ,University of Exeter.

## What we've done ?

The purpose is to do the segmentation of osteocyte cell images. Since the similar work hasn't been conducted using neural network. We initialy planned to apply [U-net](dataset/unet.pdf) to do the segmentation. After that, we did some modification (add neurals to fill the iconic *U gap* between encoder layers and decoder layers) to the network structure to strengthen the connection and see what may happen to the results. And surprisingly results were not bad consider the number of our mini data set. 

- Stage1:  Label raw osteocyte images using [TINA]() and [Amira]() manually. Since our mini data set only contain 135 images([here](dataset/raw-data/ocn)), it's not hard to draw the labels. Then we started training for 20 epochs (2000 iterations per epoch), thats total 40000 times iterations. And our training loss came to a fair 0.5816 with average error rate 2.635%.
- Stage 2: Continue with the training until the training epochs reached 65. That's total $1.3\times10^5$ times iterations, with average training loss 0.4024. Applying the latest weights and parameters the error rate declined to 2.560% performed on our test dataset. 
- Stage 3: Apply the modification, and continue training.

## What can you see?

Here are some examples of our outcomes, just take a look ! ( use `ImageChops.difference()` to compare)

​              *Label                                                             Prediction                                                            Distinction*

<img src="result/compare-pic/compare_2/0.PNG" alt="0" style="zoom:80%;" />



Want to have a more intuitive look?

<img src="result/loss-error-curve/intuitive.GIF" alt="intuitive" style="zoom:80%;" />

​                                                            Loop (*Label*$\to$*Prediction*$\to$*Distinction*)



## You can always have a try !

- Want to see how the segmentation is generated ? Apply `model.ckpt` from `train-saver/dataresult9` to `src/demo_ratio_data.ipynb` to get the result segmentation immediately .
- Want to train the network on your own ? Change path in `src/network/unet.py` as well as the corresponding ones in `src/demo_ratio_data.ipynb` click the run bottom and have a try !
- What about data visualization and analysis processes ? All in `src/demo_ratio_data.ipynb`.

### What should be improved ?

Much work need to be done. 

- Our dataset is limited in number. 
- We didn't consider how deep the ConNet may be most suitable for the segmentation result.
- The modification is in processing.



**PS: The reporitory has NOT completed for now.**