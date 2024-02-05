---
layout: post
title: Teaching Math to Identify Similar Images
subtitle: Defining a metric for the space of images.
mathjax: true
tags: [metric, images, computer vision]
---

## Introduction
(Find my actual report that I submitted [here](/assets/pdf/image-metric.pdf). It goes into more detail and is more rigorous.)\\
When do we say that two images are similar? The easiest way is to just
look at the images and decide from our experience whether they are similar.
But that leads us nowhere new. One way, which I find straightforward, is to define
the distance between two images; then if the distance between two images is _small_
then they are similar. This way we also get a notion of how similar the two images are.

This is precisely what a metric does, it is function that takes two images and returns the
distance between them. More rigorously:
Let \\(X\\) be a set, a metric on \\(X\\) is a function \\(d:X\times X\rightarrow \mathbb{R}^{\geq 0}\\)
which satisfies the following properties for every \\(x,y,z \in X\\):
- \\(d(x,y)=d(y,x)\\)
- \\(d(x,y)=0 \iff x=y \\)
- \\(d(x,y)+d(y,z) \geq d(x,z)\\)

## What is an image?
In this work, I consider images to be a \\(m\times n\\) matrix with entries from \\(\{0,1\}\\).
When we compare two images, they are assumed to be of equal dimensions.
This means that the image has two kinds of pixels, 'on' or 'off', and nothing in between.
Hence the images are not coloured or even in greyscale. Though there are ways for the metric
I'm going to define to be expanded into greyscale or coloured images, I'll not go into that
here. If you are interested in that, I suggest reading about edge detection algorithms used
in computer vision. The resolution of the image increases as the dimension of the matrix
increases.

## The Chamfer Distance
This is an algorithm used in computer vision to compute how similar two images are.
This algorithm usually uses approximations to reduce the hefty computational costs.
To define a metric, though we do not require approximations. I find that the basic
idea of the Chamfer distance is quite well portrayed in [this YouTube video](https://www.youtube.com/watch?v=P4IyrsWicfs).
The (euclidean) distance of every bright pixel in one image to the nearest pixel in the second image
(think of the two images being superimposed on top of each other) is added up. This is done for the second
image as well. The final metric is the sum of the two numbers we got.

Also before we calculate the chamfer distance, we translate and scale both the images so that
both of them have the same 'center of mass' and 'standard distribution' of pixels.
To identify rotations, we take the angle between the images which correspond to the lowest
chamfer distance after translation and scaling.

To get a more thorough idea, read my [report](/assests/pdf/image-metric.pdf) and feel free to contact me.
