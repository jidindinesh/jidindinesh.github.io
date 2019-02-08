---
layout: post
title: Broadcasting with Pytorch
subtitle: Demystifying how tensors flow.
---

![](https://i.ibb.co/qNkt1vw/Pytorchv-Tf.jpg)

I heard about **Broadcasting** for the first time in Lesson 9 of Jeremy Howard's [Introduction to Machine Learning for Coders](http://course18.fast.ai/ml). Jeremy went on and on about how important Broadcasting was...

*"The most important programming concept taught in this course and possibly the most important programming concept you will ever need to build machine learning algorithms. "*

*"Very few people in DataScience or Machine Learning community understand broadcasting. "*

*"If you get good at Broadcasting, you will have this super useful skill that very very few people have. "*

These wise words should be enough to pull you through to the end of the article.

Two tensors must have the same shape in order to perform element-wise operations on them and arithmetic operations are element-wise operations. Arithmetic operations on tensors with scalar values can be done in two ways: 

* Using symbolic operations

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/symbolic.PNG)

* Using built in tensor object methods

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/builtintensorobjmethods.PNG)

Both of these options work the same. We can see that in both cases, the scalar 2, is applied to each element with the corresponding arithmetic operation. Math here seems fine but these examples break the rule that **element-wise operations operate on tensors of the same shape.**
Scalars are Rank-0 tensors, which means they have no shape, and our tensor **T** is a rank-2 tensor of shape 2 x 2. So how does this fit in? Let’s break it down.

The first solution that comes intuitively is that the operation is simply using the single scalar value and operating on each element within the tensor. This logic kind of works however, it’s a bit misleading, and it breaks down in more general situations where we’re not using a scalar. To think about these operations differently, we need to introduce the concept of tensor broadcasting or broadcasting.
![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/broadcasting%20microphone%20mic.jpg)

From Numpy documentation:
The term broadcasting describes how numpy treats arrays with different shapes during arithmetic operations. Subject to certain constraints, the smaller array is “broadcast” across the larger array so that they have compatible shapes. Broadcasting provides a means of vectorizing array operations so that looping occurs in C instead of Python. It does this without making needless copies of data and usually leads to efficient algorithm implementations.

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/1..PNG)

We can think of the scalar **b** being stretched during the arithmetic operation into an array with the same shape as **a**. The new elements in **b** are simply copies of the original scalar. The stretching analogy is only conceptual. NumPy is smart enough to use the original scalar value without actually making copies, so that broadcasting operations are as memory and computationally efficient as possible.

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/2,.PNG)

Another example of interaction between a vector and a tensor :

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/3.PNG)

The element wise addition takes place as if **x** was broadcasted as follows to match the dimensions of **y**

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/4.PNG)

Try wrapping your head around this trickier example :

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/tricky%20(2).PNG)

Got your answer??

Is this your answer? 👇

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/tricky.PNG)

Just as before we stretched or broadcasted one tensor to match the shape of the other, here we've stretched both *a* and *b* to match a common shape, and the result is a two-dimensional array! The geometry of these examples is visualized in the following figure (Credits: Jake VanderPlas) :

![](https://github.com/jidindinesh/jidindinesh.github.io/blob/master/assets/broadcasting.png)

*The light boxes represent the broadcasted values: again, this extra memory is not actually allocated in the course of the operation, but it can be useful conceptually to imagine that it is.*
