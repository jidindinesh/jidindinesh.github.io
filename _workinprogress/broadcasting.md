---
layout: post
title: Broadcasting with Pytorch
subtitle: Demystifying how tensors flow.
---

![](https://i.ibb.co/qNkt1vw/Pytorchv-Tf.jpg)

I heard about *Broadcasting* for the first time in Lesson 9 of Jeremy Howard's [Introduction to Machine Learning for Coders](http://course18.fast.ai/ml). Jeremy went on and on about how important Broadcasting was...

"The most important programming concept taught in this course and possibly the most important programming concept you will ever need to build machine learning algorithms. "

"Very few people in DataScience or Machine Learning community understand broadcasting. "

"If you get good at Broadcasting, you will have this super useful skill that very very few people have. "

Two tensors must have the same shape in order to perform element-wise operations on them and arithmetic operations are element-wise operations. Arithmetic operations on tensors with scalar values can be done in two ways: 

* Using symbolic operations

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/symbolic.PNG)
