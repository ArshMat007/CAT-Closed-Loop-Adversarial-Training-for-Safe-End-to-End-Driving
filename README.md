# CAT: Closed-Loop Adversarial Training for Safe End-to-End Driving

## Project Overview

This project focuses on developing and evaluating an autonomous driving agent within a simulated environment, MetaDrive, designed to handle various realistic and safety-critical driving scenarios. The core objective is to build a robust agent capable of safe, end-to-end autonomous driving through the application of closed-loop adversarial training techniques.

## Table of Contents

- [Introduction](#introduction)
- [Key Features & Demonstrations](#key-features--demonstrations)
- [Methodology](#methodology)
- [Installation](#installation)
- [Usage Examples & Visualizations](#usage-examples--visualizations)

---

## Introduction

This repository provides a comprehensive exploration of MetaDrive, a high-fidelity driving simulator, and its application in developing safe autonomous driving agents. It covers fundamental aspects from environment setup to advanced topics like multi-agent interactions, real-world scenario integration via Waymo Open Dataset, and 3D rendering.

## Key Features & Demonstrations

The Colab notebook (which this README is based on) provides:

* **Basic Introduction:** A foundational understanding of MetaDrive, including its installation and core functionalities.
* **Diverse Examples:** Demonstrations across various MetaDrive environments, policy types (PPO expert), and rendering configurations.
* **Challenging Scenarios:** Showcases a range of driving scenarios, including multi-agent interactions (e.g., roundabout, bottleneck, intersection) and real-world setups derived from the Waymo Open Dataset.
* **Map Generation:** Explains and demonstrates MetaDrive's capabilities for procedurally generating custom environments and visualizing different map configurations.
* **3D Rendering:** Provides instructions and examples for enabling and capturing outputs from MetaDrive's immersive 3D renderer.

## Methodology

The project leverages a robust methodological framework for environment interaction, agent training, and evaluation:

1.  ### Environment Setup
    * **MetaDrive Installation:** Initial setup is handled via `pip` for easy environment preparation.
    * **Environment Configuration:** Utilizes various MetaDrive environments:
        * `MetaDriveEnv`: For basic functionalities and expert policy demonstrations.
        * `SafeMetaDriveEnv`: Specifically for simulating and tracking costs in safety-critical scenarios.
        * **Multi-agent Environments:** Includes `MultiAgentRoundaboutEnv`, `MultiAgentBottleneckEnv`, `MultiAgentIntersectionEnv`, `MultiAgentParkingLotEnv`, and `MultiAgentTollgateEnv` for complex interactions.
        * **Real-World Scenarios:** `DemoEnv` is configured to integrate and leverage data from the Waymo Open Dataset.
    * **Customizable Parameters:** Environments are highly configurable with parameters like `start_seed`, `num_scenarios`, `traffic_density`, and `accident_prob`.

2.  ### Agent Implementation (TD3)
    * **Replay Buffer:** A custom `ReplayBuffer` class is implemented to efficiently store and manage experiences for agent training.
    * **TD3 Agent:** The core reinforcement learning agent is built using the **TD3 (Twin Delayed Deep Deterministic Policy Gradient)** algorithm from the `stable-baselines3` library.
    * **Policy Architecture:** The agent employs an MLP (Multi-Layer Perceptron) policy with a specified network architecture.
    * **Training Loop:** The agent undergoes a training loop where it interacts with the environment, collects experiences into the replay buffer, and iteratively updates its policy using the TD3 algorithm.

3.  ### Evaluation and Visualization
    * **Performance Evaluation:** The trained agent's performance is rigorously assessed over multiple episodes.
    * **Reward Plotting:** Episode rewards are plotted to visually track the agent's learning progress and performance trends.
    * **Rendering Modes:** MetaDrive offers diverse rendering modes for visualization:
        * `top_down`: Provides a bird's-eye view of the simulation.
        * `image_observation`: Enables offscreen rendering for direct access to rendered frames.
        * `use_render`: Activates full 3D rendering for immersive views.
    * **GIF Generation:** High-quality GIF animations of the simulations are generated using `pygame` and `PIL` libraries for dynamic visual demonstrations.

4.  ### Map Generation
    * **Procedural Generation:** MetaDrive's powerful procedural map generation capabilities are showcased, allowing for the creation of diverse and random maps based on configurable road block sequences.
    * **Visualization:** Generated maps are visualized in a top-down view using `matplotlib` for clarity and analysis.

5.  ### Waymo Open Dataset Integration
    * **Real-World Scenario Simulation:** A `DemoEnv` is specifically created to utilize data from the Waymo Open Dataset, enabling the simulation of realistic real-world driving scenarios.
    * **Replay Policy:** A `ReplayEgoCarPolicy` is used to control the ego vehicle, mimicking recorded real-world driving behaviors.
    * **Visualization:** The integrated real-world simulations are visualized, and corresponding GIF animations are generated.

## Usage Examples & Visualizations

<img width="424" alt="image" src="https://github.com/user-attachments/assets/034e42e8-563b-4e63-ba06-aa2ab8f85d16" />
![image](https://github.com/user-attachments/assets/31d07057-ec4e-4b97-a784-41ffaff19869)


---

## Installation

To get started with this project, you'll need to install the MetaDrive simulator.

```bash
pip install metadrive-simulator
