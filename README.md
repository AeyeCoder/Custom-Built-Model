Custom Deep Learning Model with Training Loop in TensorFlow

This repository contains an end-to-end implementation of a deep learning model built from scratch using TensorFlow’s low-level API.
Instead of relying on model.fit(), this project demonstrates how to implement a custom training loop with full control over the forward pass, loss computation, gradient updates, and evaluation.

The goal of this project was to gain a deeper understanding of what happens under the hood when training models with TensorFlow.
Key Features:

Custom Model Architecture: Defined using the subclassing API (tf.keras.Model).
Custom Training Loop: Built with tf.GradientTape to explicitly handle forward and backward passes.
Custom Metric Implementation: Implemented a variant of the Huber loss/metric from scratch for monitoring.
Manual Validation Loop: Explicit validation step per epoch without relying on model.evaluate().
Supports Classic Datasets: Can be easily applied to MNIST, CIFAR-10, or regression datasets.

Why This Project Matters???
Well, Most tutorials stick to high-level Keras training (model.fit, model.evaluate).
While convenient, these abstractions hide the internals of gradient computation and parameter updates.


By implementing the entire pipeline manually, this project provides clarity on:
How losses and metrics are computed.
How optimizers apply gradients.
How to switch between training and evaluation modes.

This level of control is especially important for research, debugging, and experimentation with novel architectures or custom objectives.

The training process follows these steps for each batch: 
Forward pass through the model. Compute loss with SparseCategoricalCrossentropy. Use tf.GradientTape to record operations. 
Compute gradients of loss w.r.t. trainable parameters. Apply gradients with the optimizer. Update metrics manually. Run validation at the end of each epoch.

Training Output:

Epoch 1:
Train Accuracy:  0.82036364
Val_Score:  0.8594

Epoch 2:
Train Accuracy:  0.8609273
Val_Score:  0.8652

Epoch 3:
Train Accuracy:  0.87665457
Val_Score:  0.8688


Epoch 4:
Train Accuracy:  0.88485456
Val_Score:  0.8712

Epoch 5:
Train Accuracy:  0.8924
Val_Score:  0.877


Next Steps

Extend to convolutional or transformer-based architectures.
Add support for regression tasks with Mean Squared Error loss.
Integrate TensorBoard for visualization.
Experiment with regularization and learning rate schedules.
