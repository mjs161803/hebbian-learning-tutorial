# Hebbian Learning Tutorial

A Jupyter Notebook tutorial demonstrating Hebbian learning implementation using PyTorch, CIFAR-10 dataset, and a small CNN model.

## Overview

This tutorial implements a Hebbian learning approach that:
- Uses a reward function (returns 1 for correct cat classification, 0 otherwise)
- Maintains trace matrices for model parameters
- Uses a custom optimizer combining reward and trace values to implement Hebbian learning

## Prerequisites

- Docker and Docker Compose installed on your system
- At least 2GB of free disk space

## Quick Start

### Using Docker Compose (Recommended)

1. Clone this repository:
   ```bash
   git clone https://github.com/mjs161803/hebbian-learning-tutorial.git
   cd hebbian-learning-tutorial
   ```

2. Build and run the container:
   ```bash
   docker compose up
   ```
   
   Note: If you have Docker Compose v1, use `docker-compose up` instead.

3. Open your browser and navigate to:
   ```
   http://localhost:8888
   ```

4. Open the `hebbian_learning_tutorial.ipynb` notebook and run the cells

5. To stop the container, press `Ctrl+C` in the terminal

### Using Docker Directly

1. Build the Docker image:
   ```bash
   docker build -t hebbian-tutorial .
   ```

2. Run the container:
   ```bash
   docker run -p 8888:8888 -v $(pwd):/workspace hebbian-tutorial
   ```

3. Access the notebook at `http://localhost:8888`

## What You'll Learn

- **Hebbian Learning Principles**: Understanding "neurons that fire together, wire together"
- **PyTorch Implementation**: Building a custom Hebbian optimizer
- **Trace Matrices**: Maintaining eligibility traces for parameters
- **Reward Functions**: Implementing selective learning based on rewards
- **CNN Architecture**: Working with convolutional neural networks
- **CIFAR-10 Dataset**: Image classification tasks

## Tutorial Contents

The notebook includes:
1. Introduction to Hebbian learning
2. Loading and preparing CIFAR-10 dataset
3. Defining a small CNN model
4. Implementing a reward function for cat classification
5. Creating trace matrices for parameters
6. Building a custom Hebbian optimizer
7. Training loop with Hebbian learning
8. Model evaluation and visualization

## Technical Details

- **Model**: Small CNN with ~77K parameters
- **Dataset**: CIFAR-10 (subset of 5000 training, 1000 test samples)
- **Framework**: PyTorch
- **Optimizer**: Custom Hebbian optimizer
- **Reward**: Binary reward for correct cat classification

## Requirements

See `requirements.txt` for Python package dependencies:
- PyTorch 2.1.0
- torchvision 0.16.0
- Jupyter Notebook
- NumPy
- Matplotlib

## License

This project is open source and available for educational purposes.
