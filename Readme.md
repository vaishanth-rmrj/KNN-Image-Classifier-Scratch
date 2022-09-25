## What is image classification?

Imagine the classical example: You are given a set of images each of which either depicts a cat or a dog. Instead of labeling the pictures all on your own, you want to use an algorithm to do the work for you: It "looks" at the whole picture and outputs probabilities for each of the classes it was trained on.

This is usually made possible through training neural networks, which we describe in more detail in other articles. (Note: There are other techniques but they do not play a role in practice due to performance.) As in other applications of supervised learning, the network is fed with a sufficient training data – namely labeled images of cats and dogs.

What happens in between the image and output is somewhat obscure and we are going into greater detail in other posts. But in simple terms, most networks break down the image into abstract shapes and colors, which are used to form a hypothesis regarding the image's content.


### Image Classification Techniques

1. K Nearest Neighbor
2. Support Vector Machines
3. Artificial Neural Networks
4. Convolutional Neural Networks

### Image Classification with K Nearest Neighbours

K-Nearest Neighbours (k-NN) is a supervised machine learning algorithm i.e. it learns from a labelled training set by taking in the training data X along with it’s labels y and learns to map the input X to it’s desired output y.

The k-NN algorithm is arguably the simplest of the machine learning algorithms. The model only consists of the training data, that is, the model simply learns the entire training set and for prediction gives the output as the class with the majority in the ‘k’ nearest neighbours calculated according to some distance metric.


#### The working in a little more detail is as follows

After the model has stored the training set for prediction, it takes a test image to be predicted, calculates the distance to every image in the training set and obtains the ‘k’ training images closest to the test image. It then outputs the class according to some voting procedure from the labels of these ‘k’ neighbours , generally a majority vote.

The distance metric used to calculate distances may differ, such as either a L1 distance function which is the summation of the differences between the pixels of the images.


L1 distance metric

An example of how the L1 distance works.
An alternative distance metric may be the L2 distance or more commonly called the Euclidean distance.


L2 distance metric
In other words we would be computing the pixel-wise difference as before, but this time we square all of them, add them up and finally take the square root.

It is interesting to note that due to the squared differences in the L2 distance, it is much more strict when the pixel difference is too large.

Now, we move onto the practical considerations: Hyperparameters in k-NN and how they affect the performance.

As k-NN is a very simple algorithm it doesn’t really have a lot of hyperparameters to tweak, just the two: the distance metric and the value of ‘k’. So what we can do is, run our model for various values of ‘k’ and get the model with the best validation accuracy, which will be used as our final model on the test set.