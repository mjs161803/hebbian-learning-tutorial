# Implementation Details

## Overview

This repository contains a complete Docker-based Jupyter Notebook tutorial for Hebbian learning using PyTorch.

## Files Created

### Core Files
- **hebbian_learning_tutorial.ipynb**: Main Jupyter notebook with complete Hebbian learning tutorial
- **Dockerfile**: Docker container configuration for Jupyter server
- **docker-compose.yml**: Docker Compose configuration for easy deployment
- **requirements.txt**: Python dependencies

### Supporting Files
- **.dockerignore**: Files to exclude from Docker build
- **.gitignore**: Files to exclude from Git repository
- **README.md**: Updated with comprehensive usage instructions

## Key Components in the Notebook

### 1. SmallCNN Model
A convolutional neural network with:
- 2 convolutional layers (3→16→32 channels)
- 2 fully connected layers (2048→128→10)
- MaxPooling and Dropout for regularization
- ~77K total parameters

### 2. Reward Function
```python
def reward_function(predictions, labels):
    """Returns 1 for correct cat classification, 0 otherwise."""
```
- Binary reward signal (1 or 0)
- Specifically targets cat classification (class 3 in CIFAR-10)
- Only rewards correct predictions

### 3. Trace Matrix
```python
class TraceMatrix:
    """Maintains eligibility traces for model parameters."""
```
- Tracks parameter activity over time
- Implements eligibility traces with decay factor (λ=0.9)
- Updates based on gradients: `trace = decay * trace + gradient`

### 4. Hebbian Optimizer
```python
class HebbianOptimizer:
    """Custom optimizer implementing Hebbian learning."""
```
- Updates parameters using: `param += learning_rate * reward * trace`
- Combines reward signal with traces
- Implements "neurons that fire together, wire together"

### 5. Training Loop
- Computes forward pass and loss
- Calculates gradients via backpropagation
- Updates traces with current gradients
- Computes reward for batch
- Applies Hebbian update to parameters

## Usage

### Starting the Container
```bash
docker compose up
```

### Accessing Jupyter
1. Open browser to `http://localhost:8888`
2. Open `hebbian_learning_tutorial.ipynb`
3. Run cells sequentially

### What the Notebook Does
1. Loads CIFAR-10 dataset (5000 train, 1000 test samples)
2. Defines and initializes CNN model
3. Implements Hebbian learning components
4. Trains model for 3 epochs
5. Evaluates performance (overall and cat-specific)
6. Visualizes predictions

## Technical Specifications

### Dependencies
- PyTorch 2.1.0
- torchvision 0.16.0
- Jupyter Notebook 7.0.6
- NumPy 1.26.2
- Matplotlib 3.8.2

### Container Configuration
- Base image: Python 3.11-slim
- Port: 8888
- No authentication required (for tutorial purposes)
- Volume-mounted for live editing

### Dataset
- CIFAR-10: 10 classes of 32×32 color images
- Focus on class 3 (cats)
- Subset used for faster tutorial execution

## Educational Value

This tutorial demonstrates:
1. Classical Hebbian learning principles in modern deep learning
2. Custom PyTorch optimizers
3. Eligibility traces in neural networks
4. Reward-modulated learning
5. Integration of reinforcement learning concepts with supervised learning

## Future Extensions

Potential improvements include:
- Multi-class reward functions
- Different trace decay rates
- Comparison with standard backpropagation
- More sophisticated reward shaping
- Longer training runs
- Full dataset usage
