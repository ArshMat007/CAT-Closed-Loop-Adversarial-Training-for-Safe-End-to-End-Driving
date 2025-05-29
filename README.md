# CAT-Closed-Loop-Adversarial-Training-for-Safe-End-to-End-Driving
The focus is on developing an agent capable of driving autonomously in a simulated environment, MetaDrive, which presents various realistic driving scenarios.
1. Installation and Basic Test:
The initial cell installs the MetaDrive simulator using pip.
It then performs a basic test to confirm the installation, creating a simple environment and interacting with it briefly.
This step ensures that MetaDrive is set up correctly and can be used for further experimentation.

3. Basic Functionality:
The second cell demonstrates the usage of a pre-trained PPO expert policy within MetaDrive.
It sets up an environment, resets it, and uses the expert policy to control the agent.
The code records a top-down view of the simulation as a GIF, illustrating the agent's behavior.
Finally, it prints the episode reward, indicating the agent's performance.

4. SafeMetaDrive:
The next cell focuses on safety-critical scenarios using the SafeMetaDriveEnv.
It applies the same expert policy but also tracks costs related to safety violations.
Again, it records a GIF for visualization and prints episode rewards and costs.

5. Multi-agent Environment Visualization:
This cell showcases multi-agent driving environments within MetaDrive.
It iterates through different types of multi-agent scenarios (roundabout, bottleneck, etc.).
For each scenario, it creates an environment, resets it, and performs random actions.
The code captures frames from the top-down view and combines them into a GIF, illustrating the multi-agent interactions.

6. Real-world Scenario Environment Visualization:
This cell utilizes the Waymo Open Dataset to create real-world-like driving scenarios.
It sets up a DemoEnv with configurations for using Waymo data.
The code then steps through the environment, captures frames, and generates a GIF.

7. Map Generation:
This part demonstrates the map generation capabilities of MetaDrive.
It creates environments with different map configurations (random or fixed block sequences).
For each configuration, it draws the top-down view of the map using matplotlib.
This allows users to visualize and understand the generated maps.

8. 3D Renderer:
The final cell shows how to enable the 3D renderer in MetaDrive.
It configures the environment to use an offscreen renderer and captures frames.
The code saves the captured frame as an image, demonstrating the 3D rendering.
In essence, this Colab file provides:
Introduction: A basic introduction to MetaDrive, its installation, and core functionality.
Examples: Demonstrations of different environments, policies, and rendering settings.
Scenarios: Showcases diverse driving scenarios, including multi-agent and real-world setups.
Map Generation: Explains the capabilities for building custom environments.
3D Rendering: Provides instructions for enabling more immersive visualizations.


Methodology 
1. Environment Setup:
MetaDrive Installation: The Colab starts by installing MetaDrive using pip.
Environment Configuration: Different environments are used throughout the notebook:
MetaDriveEnv: For basic functionalities and PPO expert policy demonstration.
SafeMetaDriveEnv: For safety-critical scenarios.
Multi-agent environments: MultiAgentRoundaboutEnv, MultiAgentBottleneckEnv, MultiAgentIntersectionEnv, MultiAgentParkingLotEnv, MultiAgentTollgateEnv.
Real-world scenario environment: DemoEnv leveraging Waymo Open Dataset.
Environment Parameters: Configurations are used to customize the environments, such as start_seed, num_scenarios, traffic_density, accident_prob, etc.

2. Agent Implementation (TD3):
Replay Buffer: A custom ReplayBuffer class is defined to store experiences for training the agent.
TD3 Agent: The code uses the TD3 (Twin Delayed Deep Deterministic Policy Gradient) algorithm from the stable-baselines3 library to create and train the reinforcement learning agent.
Policy: The agent uses an MLP (Multi-Layer Perceptron) policy with a specified network architecture.
Training Loop: The agent is trained by interacting with the environment, collecting experiences in the replay buffer, and updating its policy using the TD3 algorithm.

3. Evaluation and Visualization:
Evaluation: The trained agent is evaluated over multiple episodes to assess its performance.
Reward Plotting: The episode rewards during evaluation are plotted to visualize the agent's learning progress.
Visualization: MetaDrive provides different rendering modes for visualization:
top_down: A bird's-eye view of the environment.
image_observation: Offscreen rendering for accessing rendered frames.
use_render: Enabling 3D rendering.
GIF Generation: The code generates GIF animations of the simulations using pygame and PIL libraries.

4. Map Generation:
Procedural Generation: MetaDrive's procedural map generation capabilities are demonstrated by generating random maps with different road block sequences.
Visualization: Generated maps are visualized in top-down view using matplotlib.
5. Waymo Open Dataset Integration:
Real-World Scenario: A demo environment (DemoEnv) is created using data from the Waymo Open Dataset to simulate real-world driving scenarios.
Replay Policy: A ReplayEgoCarPolicy is used to control the ego vehicle based on recorded data.
Visualization: The simulation is visualized, and a GIF animation is generated.
