# Pong DQN — Rubric Answers (Auto)

## Baseline Performance
Random policy (10 eps, max_steps=1000): avg_return=-20.4, avg_steps=1000.8  
DQN (40 eps): avg_return≈-20.5 (early-stage), best≈-19.0  

## Environment Analysis
Observations: RGB frames (210×160×3) → grayscale 84×84 × stack 4 frames  
Actions: Discrete (pong paddle actions)  
Q-table size: infeasible (|S|≈256^(210×160×3), |A| small) → requires function approximation  

## Reward Structure
+1 for scoring, -1 for opponent scoring  
Optional reward clipping [-1, 1] used for stability  

## Bellman Parameters
α≈2.5e-4, γ=0.99  
Alternative experiments: γ=0.95, lower learning rate  

## Policy Exploration
Baseline: ε-greedy  
Alternative: Softmax (Boltzmann) exploration  

## Exploration Parameters
ε decayed from 1.0 → 0.05  
At max steps, ε ≈ 0.05 (minimum and stable)  

## Performance Metrics
Average reward per episode  
Average steps per episode (~1000 early stage)  
Training reward curve (moving average)  

## Q-Learning Classification
Value-based method: learns Q(s,a) and selects actions via greedy or ε-greedy policy  

## Q-Learning vs. LLM Agents
DQN: dense reward signal, environment interaction  
LLM agents: sparse/preference-based rewards, reasoning via language  

## Expected Lifetime Value
E[Σ γ^t r_t] — expected discounted future reward from (s,a), estimated via Bellman updates  

## RL → LLM Agents
Concepts like exploration, reward optimization, and value estimation inspire LLM agent planning  

## Planning (RL vs LLM)
RL: value iteration, rollouts  
LLM: chain-of-thought reasoning + tool usage  

## Algorithm
Q ← Q + α [r + γ max_a' Q_target(s',a') − Q(s,a)]  
Loss: Huber loss  
Target network: periodic or soft updates  

## LLM Integration
LLM as planner + RL as executor  
Hybrid systems: LLM defines goals, RL agent executes actions in environment  
