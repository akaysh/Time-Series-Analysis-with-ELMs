# Time-Series-Analysis-with-ELMs

## Extreme Learning Machine
Extreme learning machine (ELM) is a modification of single layer feedforward network (SLFN) where learning is quite similar to the reservoir computing where the input are connected randomly to higher level of abstraction (see it as a hidden layer of higher level) and output can be tapped from those nodes and the training problem reduces to calculating the connection (weights) of tapping nodes to output.

## Learning Algorithm

![ELM]({{site.baseurl}}/ELM.jpg)


After performing the tedious backpropagation ritual, we are left with the following equation that predicts output from inputs

![EQ2]({{site.baseurl}}/eq1.jpg)

Where **h<sup>i</sup>** is the activation of ith hidden neuron computed using

![EQ1]({{site.baseurl}}/eq2.jpg)

Here, **f** is the activation function like **sigmoid, tanh** etc., **x<sub>j</sub>** is the **j<sup>th</sup>** input, **w<sub>i/<sub>**, j is the connection weight from **j<sup>th</sup>** input to **i<sup>th</sup>** hidden neuron and **b<sub>i</sub>** is the bias term.

In matrix notation, the process can be represented in the following form

**Y = W’ . H**

Where **W’** is the matrix of weights from hidden to output layer while **H** is the activation matrix computed using

**H = f(W . X + B)**
with **W** (without the “ **‘** ”) is matrix of weights from input to hidden layer.

Now, being different from usual SLFN, the ELM doesn’t tune **W** using backprop or any other iterative method, instead **W** is randomly generated. This gives us a pool of higher level input abstractions in the hidden layer, out of which, ones fitting to training data can be found by adjusting hidden to output weights by solving a simple matrix equation.

**Y = W’ . H**
Now, given a training data with X as input and Y as output, the ELM training process takes the following steps

Generate **W**
Find **H**
Solve **Y = W’ . H for W’**
The value of **W’** can be calculated simply using psuedo (Moore-Penrose) inverse which is usually available as a function that goes by the name pinv most of the scientific computation environment including Matlab and Python’s numpy.linalg.

**W’ = Y . pinv(H)**

This inverse can also be computed using regularized inverse for better generalization.

## About this project
How to use ELM (Extreme Learning Machines) for time series forecasting. This example demonstrates TS forecasting with ELMs. It uses Python-ELM for implementation of ELMs and sklearn, pandas and matplotlib for data processing and visualization.

ELM is used to predict point estimates while Nearest Neighbour approach is used to predict prediction intervals for the test data values.
link to paper: https://www.ncbi.nlm.nih.gov/pubmed/25910257
This gist is only based on 2nd approach of the paper.


