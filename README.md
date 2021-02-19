# Gradient Centralization TensorFlow [![Twitter](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fgithub.com%2FRishit-dagli%2FGradient-Centralization-TensorFlow)](https://twitter.com/intent/tweet?text=Wow:&url=https%3A%2F%2Fgithub.com%2FRishit-dagli%2FGradient-Centralization-TensorFlow)

TODO: Add Pypi badge

[![Upload Python Package](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/actions/workflows/python-publish.yml/badge.svg)](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/actions/workflows/python-publish.yml)
[![Flake8 Lint](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/actions/workflows/flake8-lint.yml/badge.svg)](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/actions/workflows/flake8-lint.yml)
![Python Version](https://img.shields.io/badge/python-3.7%20%7C%203.8%20%7C%203.9-blue)

[![GitHub license](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![PEP8](https://img.shields.io/badge/code%20style-pep8-orange.svg)](https://www.python.org/dev/peps/pep-0008/)
[![GitHub stars](https://img.shields.io/github/stars/Rishit-dagli/Gradient-Centralization-TensorFlow?style=social)](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Rishit-dagli/Gradient-Centralization-TensorFlow?style=social)](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/network)
[![GitHub watchers](https://img.shields.io/github/watchers/Rishit-dagli/Gradient-Centralization-TensorFlow?style=social)](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/watchers)

This Python package implements Gradient Centralization in TensorFlow, a simple and effective optimization technique for 
Deep Neural Networks as suggested by Yong et al. in the paper 
[Gradient Centralization: A New Optimization Technique for Deep Neural Networks](https://arxiv.org/abs/2004.01461). It can both speedup training 
 process and improve the final generalization performance of DNNs.
 
![](images/gctf.png)

## Installation

Run the following to install:

```bash
pip install gradient-centralization-tf
```

## Usage

### [`gctf.centralized_gradients_for_optimizer`](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/blob/main/gctf/centralized_gradients.py#L45-L55)

Create a centralized gradients functions for a specified optimizer.

#### Arguments:
- optimizer: a `tf.keras.optimizers.Optimizer object`. The optimizer you are using.

#### Example:

```py
>>> opt = tf.keras.optimizers.Adam(learning_rate=0.1)
>>> optimizer.get_gradients = gctf.centralized_gradients_for_optimizer(opt)
>>> model.compile(optimizer = opt, ...)
```
    
### [`gctf.get_centralized_gradients`](https://github.com/Rishit-dagli/Gradient-Centralization-TensorFlow/blob/a7c5226dad86ca42341061e3fafc8c8d1ec3f51f/gctf/centralized_gradients.py#L5-L42)

Computes the centralized gradients.

This function is ideally not meant to be used directly unless you are building a custom optimizer, in which case you
could point `get_gradients` to this function. This is a modified version of
`tf.keras.optimizers.Optimizer.get_gradients`.

#### Arguments:
- optimizer: a `tf.keras.optimizers.Optimizer object`. The optimizer you are using.
- loss: Scalar tensor to minimize.
- params: List of variables.

#### Returns:
A gradients tensor.

#### Reference:
- [Yong et al., 2020](https://arxiv.org/abs/2004.01461)

## Developing `gctf`

To install `gradient-centralization-tf`, along with tools you need to develop and test, run the following in your 
virtualenv:

```bash
git clone git@github.com:Rishit-dagli/Gradient-Centralization-TensorFlow
# or clone your own fork

pip install -e .[dev]
```

