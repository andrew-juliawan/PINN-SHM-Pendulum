# Physics-Informed Neural Network (PINN) for Simple Harmonic Motion
This project demonstrates the application of Physics-Informed Neural Networks (PINNs) to solve the differential equations governing the Simple Harmonic Motion (SHM) of a pendulum. Unlike traditional neural networks that rely solely on data, this model incorporates the underlying physical laws directly into its loss function, allowing it to predict the system's behavior with high accuracy even in the absence of extensive labeled datasets.
## Project Overview
The objective of this project is to model the displacement ($\theta$) of a simple pendulum over time ($t$). The system is governed by a second-order ordinary differential equation (ODE) representing SHM:

$$\frac{d^2\theta}{dt^2} + \frac{g}{L}\theta = 0$$

Key Parameters:
* Gravity ($g$): 9.81 m/s²
* Length ($L$): 1.0 m
* Initial Angle ($\theta_0$): 0.2 rad
* Initial Velocity ($\theta'_0$): 0.0 rad/s
* Time Domain: 0.0 to 10.0 seconds
## Model Architecture
he neural network is built using PyTorch and consists of a fully connected architecture:
* Input Layer: 1 node (time $t$)
* Hidden Layers: 2 layers with 32 neurons each
* Activation Function: Hyperbolic Tangent (Tanh)
* Output Layer: 1 node (predicted angle $\theta$)
## Loss Function
The model is trained by minimizing a multi-part loss function:
1. Physics Loss: Calculates the residual of the SHM differential equation using automatic differentiation (torch.autograd.grad) to compute $\theta_{tt}$.
2. Initial Condition (IC) Loss: Ensures the model honors the starting position ($\theta_0 = 0.2$) and starting velocity ($\theta'_0 = 0$).
## Requirements
To run this project, you will need the following Python libraries:
* `torch`
* `numpy`
* `matplotlib`
## How to Use
1. Open the Notebook: Launch PINN_project.ipynb in your Jupyter environment.
2. Train the Model: Execute the cells to initialize the PINN class and start the training loop. The model is configured to run for 100,000 epochs using the Adam optimizer.
3. View Results: The notebook includes a training log showing the loss decrease over time.
## Results
After training, the neural network effectively learns to approximate the sinusoidal motion of the pendulum by satisfying both the initial conditions and the governing physical laws of gravity and length.
