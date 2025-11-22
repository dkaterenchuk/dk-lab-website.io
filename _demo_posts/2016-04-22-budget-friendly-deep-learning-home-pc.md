---
id: 410
title: Budget Friendly Deep Learning Home PC
date: 2016-04-22T15:18:44-04:00
author: Den
layout: post
guid: http://www.dk-lab.com/?p=410
permalink: /budget-friendly-deep-learning-home-pc/
categories:
  - Deep Learning
  - Fun Science
  - Neural Networks
---
For over ten years my main work tool has been a laptop. For most tasks, whether it is software development or research, laptops deliver good performance with an advantage of working from anywhere. More demanding work is done on remote servers or cloud computing. In my lab, I set up Sun Grid Engine cluster of six servers that brings together the power of 36 Xeon CPUs. This system was used to build Automatic Speech Recognition (ASR) models (which took over a month to train) and to run many other extensive experiments. My laptop could not compete with it. However, in recent years with the development of Deep Learning, GPUs became very powerful tools in research. For example, when I needed to run the same ASR training, a single GPU brought training time from over 30 days to around 6. 

Having to work with deep learning on a daily basis, I needed to find an efficient work setup with an accessible GPU. Some possible options were: 1) use lab GPU, 2) rent an AWS instance, 3) buy a home PC. Each option has its drawbacks: 1) it was hard to manage (no root access), constant problems with libraries and dependencies, could not run personal projects on shared resources; 2) the price, running on a virtual machine; 3) buying, storing, managing, etc. With no real intentions to buy a PC, I was surprised to find many deals and promotions on computers and parts including $170 sale on Lenovo TS140. I could not resist getting it and trying to turn it into a deep learning work machine. This is the configuration that ended up being my deep learning build: Lenovo TS140 ThinkServer i3 CPU, 4Gb ECC RAM, NO HHDs, NO OS. 

<a href="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.13.28-e1457933691187.jpg" rel="attachment wp-att-420"><img src="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.13.28-1024x768.jpg" alt="2016-03-12 16.13.281" width="500" height="375" class="alignleft size-large wp-image-420" /></a>

The advantages of this server were the price, size, and the fact that it is sold with the minimum components inside. This lets you decide what is important in your build. I had a couple of hard drives around and ordered an additional 4TB drive to use as a data drive. This server can fit four drives and a CD/DVD drive. In addition to 4Gb ECC RAM that server came with, I ordered 3x8Gb of non-ECC RAM that brings a total of 28Gb of RAM. It is recommended to use ECC memory with this server, but the price was too high for a feature that is excessive for my intend. Having extra RAM memory, on the other hand, makes work more comfortable and saves you from playing the Big Data game when it is not necessary. 

<a href="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.17.02-e1457933771824.jpg" rel="attachment wp-att-422"><img src="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.17.02-1024x768.jpg" alt="2016-03-12 16.17.02" width="500" height="375" class="alignleft size-large wp-image-422" /></a>

Now is it the time to decide on a GPU. Most deep learning libraries support only CUDA. This means that we are limited to Nvidia GPUs. The current generation is 9xxx series. There were some very good and powerful options from the previous generations, but my concern was the power consumption and future support. GeForce GTX TITAN X or GTX 980 TI are the best consumer GPUs at this time. However, these are a bit expensive. For a budget friendly build, GTX 970 could have been a good choice, but because of the specifics of memory architecture, it is not recommended to use for some deep learning. As a result, I was left with its cheaper version GTX 960 4Gb. This GPU is rated as one of the best for it&#8217;s  [price/performance value](http://www.videocardbenchmark.net/gpu_value.html). This particular version is from Asus and is it a bit shorter, which fits perfectly inside Lenovo&#8217;s micro ITX case. Longer GPUs might not fit or will require modifications. Overall, this seems to be a good choice.

<a href="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174.jpg" rel="attachment wp-att-442"><img src="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174-1024x768.jpg" alt="2016-03-12 16.40" width="500" height="375" class="alignleft size-large wp-image-442" srcset="http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174-1024x768.jpg 1024w, http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174-300x225.jpg 300w, http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174-768x576.jpg 768w, http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174-350x263.jpg 350w, http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174-700x525.jpg 700w, http://www.dk-lab.com/wp-content/uploads/2016/03/2016-03-12-16.40-e1457933805174.jpg 1500w" sizes="(max-width: 500px) 100vw, 500px" /></a>

One additional detail is that I had to upgrade the power supply unit. The one that comes with the server was only 280W and would have struggled to power all the parts. 500W upgrade, on the other hand, will be sufficient for possible future additions.

At this point, we are ready to play with deep learning and run tests. TensorFlow currently attracts a lot of attention, so I will use it to assess the performance. I will run standard CNN training recipe from [Tensorflow website](https://www.tensorflow.org/versions/r0.7/tutorials/deep_cnn/index.html) and measure the time it takes to build an image recognition model. I use Linux&#8217;s built-in &#8220;time&#8221; command to capture the time of cifar10\_train.py script (&#8220;time python cifar10\_train.py&#8221;). The training is limited to 100k steps. The experiments are run on different platforms and GPUs and I will try to extend this comparison as I get access to different systems. For now we have the following experiments: 1) Xeon E5450 &#8211; 3.0GHz (8 cores), 2) NVidia Tesla K20c 5Gb, 3) NVidia GeForce GTX 960 4Gb (this build) and 4) NVidia Tesla K80 12Gb. <!--In the future, I will add NVidia Tesla K20c 5Gb scientific GPU to this comparison. -->

<!-- 
<table border="1" width="60%"  cellpadding="5" cellspacing="5" align="center">
<tr align="center" >
<th width="30%">Xeon E5450</th>
<th width="30%">NVidia Tesla K20</th>
<th width="30%">NVidia GeForce GTX 960</th>
</tr>
<tr align="center" width="30%">
<td>2243 minutes</td>
<td>820 minutes</td>
<td>366 minutes</td>
</tr>
</table>
-->

<iframe width="100%" height="400" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/752.embed"></iframe>

The results show that this budget build is quite competitive. From the very beginning, it was obvious that training a CNN model on a CPU is not a good idea and it would take very long time. Even this entry level GPU performed over 6x better that Xeon CPU based training. The comparison GTX 960 to Tesla K20 is very surprising. Keeping in mind that Tesla K20 cost more than 10x the price of GTX 960, but was 2.25 times slower! Tesla K80 was only 23% faster considering that it is over 20-30 times more expensive. I would imagine that the difference with K80 would be way more significant when running big jobs since it can fit more data into its memory. On the other hand, all Tesla line GPUs features double precision floating point that slows down computations without adding any values according to (<a href="https://arxiv.org/pdf/1412.7024.pdf" target="_blank">this paper</a>) and have lower core clock frequencies (GTX960-1127MHz V.S. K80-562MHz). I honestly did not expect to see this outcome. This small project turned out to be a solid build. Anyone who is curious about deep learning should be able to do it on their own for the price of a monthly subscription to AWS GPU instance.

One last note on AWS GPU instance. It seems that AWS does not support TensorFlow 0.7 (or newer). TensorFlow requires NVIDIA compute capabilities of 3.5 or higher, but amazon&#8217;s GPUs provide only 3.0. There is a way to get around this, but it wasn&#8217;t trivial. After playing with it, I decided not to invest more time into figuring it out. Nvidia-docker might be a solution to end all these incompatibility issues.

Update 1: I updated the GPU unit to NVidia GTX 1070. This looks like the best card in terms of price to performance ratio and it has 8GB VRAM to fit larger models. Because Lenovo case is so small, I was limited to blower style GPUs to keep the internal temperature lower. The results were quite impressive. Updated time is in the table above.

<!-- In the future, I will try to get NVidia GTX 1070. Very excited to test it's performance.-->

<!-- The speed isn't not good either -->

<!--
CPU
2243

GTX960 - 6xCPU
real	366m22.332s
user	1064m47.120s
sys	86m2.804s


GTX 1070

real	119m17.320s
user	325m34.060s
sys	47m41.020s

GTX 1080

real	103m21.079s
user	363m32.788s
sys	50m51.872s
-->