# 🎮 Deep Q-Learning on Atari Pong (CNN-Based Agent)

This project implements a **Deep Q-Network (DQN)** using a **Convolutional Neural Network (CNN)** to train an agent to play Atari Pong. The implementation follows core reinforcement learning principles and includes experiments with different exploration strategies and hyperparameters.

---

## 🧠 Overview

Deep Q-Learning (DQN) extends traditional Q-learning by using a neural network to approximate the action-value function:

\[
Q(s, a) = \mathbb{E}\left[\sum_{t=0}^{\infty} \gamma^t r_t\right]
\]

Key components implemented:
- Experience Replay
- Target Network
- Frame Preprocessing & Stacking
- ε-greedy and Softmax Exploration

---

## 🌍 Environment

- **Environment:** Atari Pong (`ALE/Pong-v5`)
- **Observation:** Preprocessed frames (grayscale, resized, stacked)
- **Action Space:** Discrete actions (move paddle up/down, etc.)

---

## ⚙️ Model Architecture

- CNN-based DQN:
  - Convolutional layers extract spatial features
  - Fully connected layers estimate Q-values
- Target network used for stable training

---

## 🚀 Training Pipeline

The agent is trained using:
- Replay buffer for sampling past experiences
- ε-greedy exploration (decaying ε)
- Periodic target network updates

### Hyperparameters
- Learning rate: 2.5e-4  
- Discount factor (γ): 0.99  
- Batch size: 32  
- Epsilon decay: 1.0 → 0.05  

At the end of training, epsilon reaches approximately **0.05** and remains constant.

---

## 🧪 Experiments

We evaluated multiple strategies:

| Model | Description |
|------|------------|
| Random | Baseline random policy |
| CNN DQN (Greedy) | Deterministic policy |
| CNN DQN (Softmax) | Probabilistic exploration |
| Alt Alpha/Gamma | Modified learning rate & discount |
| Alt Epsilon/Decay | Different exploration schedule |

---

## 📊 Results

| Model | Mean Reward |
|------|------------|
| Random | ~ -20.4 |
| CNN DQN (Greedy) | ~ -21.0 |
| CNN DQN (Softmax) | ~ -20.0 |

👉 Softmax exploration showed better performance due to improved action exploration.

---

## 📈 Key Insights

- Limited training time prevented full convergence
- Exploration strategy significantly impacts performance
- Softmax policy outperformed greedy in early training
- Hyperparameter tuning affects stability and learning speed

---

## 🤖 DQN vs LLM Agents

| Aspect | DQN (RL) | LLM Agents |
|-------|---------|-----------|
| Learning Signal | Numeric rewards | Human feedback |
| Policy | Value-based | Generative reasoning |
| Interaction | Environment states | Text + tools |
| Goal | Maximize reward | Alignment & reasoning |

---

## 🛠️ Requirements

Install dependencies:


pip install -r requirements.txt
---

## ▶️ Run the Project

Open the notebook:

jupyter notebook Atari_Pong_Deep_Q_Learning_CNN.ipynb

Or run on Google Colab.
---

## 🏁 Conclusion

This project demonstrates a complete Deep Reinforcement Learning pipeline using DQN. While the agent did not fully converge due to limited training time, the implementation successfully captures the core principles of RL and highlights the importance of exploration strategies in learning.
