# Embodied Language-Guided Waypoint Planning for Shape-Following Navigation via Reinforcement Learning from Environment Feedback
## Abstract
Precise shape-following with a Deep Deterministic Policy Gradient (DDPG) controller is challenging when the policy is imperfectly trained. Errors such as overshoot, drift, and corner-cutting accumulate across waypoints, causing the robot to deviate from the target shape. 

We address this by introducing a hierarchical framework where a Large Language Model (LLM) acts as a high-level planner, decomposing shape goals into adaptive waypoint sequences that account for the DDPG's error profile. 
The LLM is not prompted with fixed rules — instead, it is trained using Reinforcement Learning from Environment Feedback (RLEF). 
The LLM generates candidate waypoint sequences, the DDPG executes them in simulation, and the resulting trajectory is scored using a composite reward based on Fréchet distance, path smoothness, and waypoint parsimony. 
Group Relative Policy Optimization (GRPO) is used to update the LLM policy without requiring a critic network, keeping memory usage feasible. 
To avoid cold-start failure, a supervised warm-up phase on classical planner outputs precedes RLEF. 

Training follows a curriculum from simple lines to complex shapes. The entire pipeline runs on open-source models (Qwen2.5/Llama, 3B–7B) using 4-bit QLoRA, fitting within 8–16 GB GPU memory. Results show the RLEF-trained planner significantly reduces shape deviation compared to fixed waypoint strategies, without modifying the underlying DDPG.

## Index Terms
- Large Language Models
- DDPG
- Reinforcement Learning from Environment Feedback
- Waypoint Planning
- Shape Following
- Hierarchical Control
- GRPO
- QLoRA
