---
title: "Budget Friendly Deep Learning Home PC"
date: 2016-04-22T00:00:00-04:00
draft: false
author: "Denys Katerenchuk"
image: "images/blog/2016/03/2016-03-12-16.13.02.jpg"
description: "A guide to building an affordable yet powerful deep learning workstation for home use."
categories:
  - "Deep Learning"
  - "Hardware"
  - "Neural Networks"
tags: ["Deep Learning", "GPU", "Hardware", "TensorFlow", "Budget Build"]
---

For over ten years, my main work tool has been a laptop. For most tasks — whether it is software development or research — laptops deliver good performance with the advantage of working from anywhere. More demanding work gets done on remote servers or cloud computing platforms. In my lab, I set up a Sun Grid Engine cluster of six servers that brings together the power of 36 Xeon CPUs. This system was used to build Automatic Speech Recognition (ASR) models (which took over a month to train) and to run many other extensive experiments. My laptop simply couldn't compete with it. However, in recent years with the development of deep learning, GPUs have become incredibly powerful tools in research. For example, when I needed to run the same ASR training, a single GPU reduced training time from over 30 days to around 6.

## The Challenge

Working with deep learning on a daily basis, I needed to find an efficient setup with accessible GPU power. I considered several options: 1) use our lab GPUs, 2) rent an AWS instance, or 3) buy a home PC. Each option had its drawbacks: 1) the lab GPUs were hard to manage (no root access), had constant problems with libraries and dependencies, and I couldn't run personal projects on shared resources; 2) AWS was expensive and required working on a virtual machine; 3) buying a personal server meant dealing with purchasing, storage, management, etc. With no real intention to buy a PC, I was surprised to find many deals and promotions on computers and parts, including a $170 sale on the Lenovo TS140 - a workstation. This was a great opportunity to build a deep learning PC for under $600. Here's how I did it.

![Lenovo TS140 ThinkServer](images/blog/2016/03/2016-03-12-16.13.28.jpg)


## The Build

After researching various options, I decided to go with a Lenovo TS140 ThinkServer. This server is designed for small businesses and workgroups, making it a cost-effective choice. It supports up to 32GB of ECC RAM and has a micro-ITX motherboard, which is compact and fits well in small spaces. The server can run a Xeon E3-1225 v3 CPU, which is powerful enough for most deep learning tasks. However, my starting configuration was quite modest. The base Lenovo TS140 ThinkServer came with i3 CPU, 4GB ECC RAM, no HDDs, and no OS.

The advantages of this server were its price, compact size, and the fact that it ships with minimal components. This allows you to decide what's important for your specific build. I had a couple of hard drives lying around and ordered an additional 4TB drive to use for data storage. This server can accommodate four drives plus a CD/DVD drive. In addition to the 4GB ECC RAM that came with the server, I ordered 4×8GB of non-ECC RAM, bringing the total to 32GB of RAM. While ECC memory is recommended for this server, the price was too high for an ECC feature that seemed excessive for my intended use. Having extra RAM, on the other hand, makes work more comfortable and saves you from playing the "big data optimization game" when it's not necessary.

![Server internals with RAM installed](images/blog/2016/03/2016-03-12-16.17.02.jpg)

## GPU Selection

Now it was time to decide on a GPU. Most deep learning libraries support only CUDA, which means we're limited to Nvidia GPUs. At the time, the current generation was the 9xx series. There were some very good and powerful options from previous generations, but my concerns were power consumption and future support. The GeForce GTX TITAN X and GTX 980 TI were the best consumer GPUs available, but they were quite expensive. For a budget-friendly build, the GTX 970 could have been a good choice, but due to the specifics of its memory architecture, it's not recommended for some deep learning applications. As a result, I settled on its more affordable sibling, the GTX 960 4GB. This GPU is rated as one of the best for its price-to-performance ratio. This particular version from Asus is slightly shorter, which fits perfectly inside Lenovo's micro ITX case.

![Asus GTX 960 GPU installed](images/blog/2016/03/2016-03-12-16.40.jpg)

## Performance Testing

At this point, we were ready to experiment with deep learning and run performance tests. TensorFlow was attracting a lot of attention at the time, so I used it to assess the performance. I ran the standard CNN training recipe from the TensorFlow website and measured the time it took to build an image recognition model. The training was limited to 100,000 steps. The experiments were conducted on different platforms and GPUs:

1. Xeon E5450 – 3.0GHz (8 cores)
2. NVidia Tesla K20c 5GB
3. NVidia GeForce GTX 960 4GB (this build)
4. NVidia Tesla K80 12GB

## Surprising Results

The results showed that this budget build was quite competitive. From the beginning, it was obvious that training a CNN model on a CPU wasn't a good idea and would take an extremely long time. Even this entry-level GPU performed over 6× better than Xeon CPU-based training. The comparison between the GTX 960 and Tesla K20 was very surprising. Considering that the Tesla K20 costs more than 10× the price of the GTX 960, it was actually 2.25 times slower! The Tesla K80 was only 23% faster, despite being 20-30 times more expensive.

<div align="center">
<iframe width="100%" height="400" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/752.embed"></iframe>
</div>

I would imagine that the difference with the K80 would be much more significant when running large jobs since it can fit more data into its memory. On the other hand, all Tesla line GPUs feature double precision floating point that slows down computations without adding any value (according to <a href="https://arxiv.org/pdf/1412.7024.pdf" target="_blank">this paper</a>) and have lower core clock frequencies (GTX960: 1127MHz vs. K80: 562MHz). I honestly didn't expect to see this outcome. This small project turned out to be a solid build. Anyone curious about deep learning should be able to create their own setup for the price of a monthly subscription to an AWS GPU instance.

### Update 1

I later updated the GPU to an NVidia GTX 1070. This appeared to be the best card in terms of price-to-performance ratio, and it has 8GB VRAM to accommodate larger models. Because the Lenovo case is so compact, I was limited to blower-style GPUs to keep internal temperatures lower. The results were quite impressive, with significant performance improvements over the GTX 960.

### Update 2

Eventually, this little machine outlived the ever growing deep learning models and datasets. I upgraded to a more powerful setup with a full-sized case, better cooling, and better GPUs. Lenovo is still my manufacturer of choice; I went with a ThinkStation P520 tower with 20 core Xeon CPU that can fit the latest GPUs and up to 128GB of RAM. After **upgrading the power supply**, I installed a single NVidia GTX 3090 card, which is currently the best consumer GPU available. This setup is still very affordable compared to enterprise solutions, and it performs extremely well for my research needs.

![Lenovo ThinkStation P520 with RTX 3090](images/blog/2016/03/lenovo_p520.jpeg)