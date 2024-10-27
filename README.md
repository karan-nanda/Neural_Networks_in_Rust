# Neural Networks in Rust

A simple neural network implementation in Rust, featuring customizable layers, backpropagation, and save/load functionality for trained weights and biases. This project demonstrates core concepts of neural networks and matrix operations from scratch, using Rust's robust type system and safety features.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview
This project implements a feedforward neural network from scratch, with support for configurable layers, activation functions, and training via backpropagation. The library allows for saving and loading trained network weights and biases, making it easy to reuse and test the network with various datasets.

## Features
- Configurable network layers and activation functions
- Feedforward propagation and backpropagation for training
- Save/load functionality using JSON serialization
- Example XOR dataset training included
- Basic matrix operations implemented (addition, multiplication, transposition)

## Installation
1. **Clone the Repository:**
    ```bash
    git clone https://github.com/karan-nanda/Neural_Networks_in_Rust.git
    cd Neural_Networks_in_Rust
    ```

2. **Build the Project:**
    This project requires the Rust toolchain, which you can install from [Rust's official site](https://www.rust-lang.org/).
    ```bash
    cargo build --release
    ```

3. **Run the Example Code:**
    ```bash
    cargo run
    ```

## Usage
The neural network can be configured by specifying the layers, learning rate, and activation function. This library includes an example that trains the network on the XOR dataset, demonstrating the network's ability to learn non-linear relationships.

### Example: XOR Training
```rust
use activations::SIGMOID;
use network::Network;

fn main() {
    let inputs = vec![
        vec![0.0, 0.0],
        vec![0.0, 1.0],
        vec![1.0, 0.0],
        vec![1.0, 1.0],
    ];
    let targets = vec![vec![0.0], vec![1.0], vec![1.0], vec![0.0]];

    let mut network = Network::new(vec![2, 3, 1], 0.5, SIGMOID);
    network.train(inputs, targets, 10000);

    println!("0 and 0: {:?}", network.feed_forward(vec![0.0, 0.0]));
    println!("0 and 1: {:?}", network.feed_forward(vec![0.0, 1.0]));
    println!("1 and 0: {:?}", network.feed_forward(vec![1.0, 0.0]));
    println!("1 and 1: {:?}", network.feed_forward(vec![1.0, 1.0]));
}
```

### Saving and Loading a Trained Model
After training, you can save the model to a JSON file:
```rust
network.save("network.json".to_string());
```

To load a saved model:
```rust
network.load("network.json".to_string());
```

## Documentation
- **Matrix Operations:** Implements basic operations such as addition, dot product, transposition, and element-wise functions.
- **Activation Functions:** Provides sigmoid activation for non-linear transformations.
- **Network Structure:** Defines layers, weights, and biases with support for forward and backward propagation.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for bug fixes or new features.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
