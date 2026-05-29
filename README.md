# UR10e SAC HER SB3 GYM MuJoCo Reinforcement Learning

Reinforcement learning for teaching a UR10e arm to learn and complete "reach" task and "pick and place" task. 

This project uses SAC/PPO,curriculum learning, HER, Gymnasium-robotics and Stable-baselines3 within MuJoCo simulator. 

The subject is a UR10e arm with a Robotiq 2F-85 gripper.

The goal of this project is to research the viability of MuJoCo for reinforcement learning and produce a easy to use and replicate example.
## Colaboration

This project was made in colaboration with "Jožef Stefan" Institute.
![Logo of the Institute of "Jožef Stefan"."](https://ctop.ijs.si/wp-content/uploads/2018/06/IJS_logo_2-1024x311.jpg) 
## Workstations

The project used three computers for teaching, using either CPU or CUDA but it's advised to use CUDA.

| computer    | CPU | GPU    | CUDA/CPU | RAM    | OS |
| -------- | ------- | -------- | ------- | -------- | ------- |
| PC 1  | Intel® Core™ i5-7400 × 4   | Intel® HD Graphics 630 | CPU | 8 GiB | Ubuntu 24.04.4 LTS |
| PC 2 | NVIDIA GeForce RTX 4090     | AMD Ryzen Threadripper PRO 5975WX | CUDA | 512 GiB | Ubuntu 24.04.4 LTS |
| PC 3    | intel i5    | rtx 3070 | CUDA | 16GiB| Windows 10|

## Dependencies

* Python 3.12.3
* Numpy 1.26.4
* Mujoco 3.8.1
* gymnasium
* stable-baselines3

## RL System

### Algorithm: SAC (Soft-Actor-Critic)
| Hyperparameter    | Value | Reasoning    |
| -------- | ------- | -------- |
| learning_starts | 32000 |
| buffer_size | 500000 |
| batch_size    | 512 |
| gradient_steps | 1 |
| tau | 0.005 |
| verbose | 1 |
| learning_rate | 1e-3 |
| gamma | 0.99 | 
| ent_coef | auto |

## Teaching results

>success condition will cause the episode to end early and not use up all of its alloted steps, which will cause it to show more episodes than if it ran 1000 timesteps for each episode

Stage 0,1 only: reach
Episodes: 4500
Sucess rate: ~100%
Time elapsed: 1200s
total timesteps: 1_800_000
timesteps per episode: 1000
timesteps to achieve success: ~600
Goal: TCP consistently reaching target
Notes: Model stagnates at 80-90% at under 3000 episodes but reaches 100% after 3000 episodes, sometimes falls to 98-99%

>model oscilates when reaching the target instead of standing still, let run for 2-3mil timesteps for more stable results

## Reward Design
```
Phase 0: (Reach target)

Phase 1: (Reach target fine)

Phase 2: (wait and clamp)


Phase 3: (Lift)
```

