# LADY: Linear Attention for Autonomous Driving Efficiency without Transformers

[![arXiv](https://img.shields.io/badge/arXiv-2512.15038-b31b1b.svg)](https://arxiv.org/pdf/2512.15038)
[![RAL2026](https://img.shields.io/badge/RAL-2026-blue.svg)](https://arxiv.org/pdf/2512.15038)

## What This Work Does

LADY is the first fully linear attention-based generative model for end-to-end autonomous driving. This work addresses the quadratic computational complexity problem faced by existing Transformer-based autonomous driving methods when processing long spatiotemporal sequences, particularly the real-time performance limitations on resource-constrained edge platforms.

Key contributions include:

1. **Constant Time and Memory Complexity**: LADY enables fusion of long-range temporal context from camera and LiDAR features at inference, with constant computational and memory costs regardless of history length.

2. **Linear Cross-Attention (LICA) Mechanism**: Proposes a lightweight linear cross-attention mechanism that enables effective cross-modal information exchange.

3. **Edge Device Deployment**: The model has been deployed and validated on edge devices (NVIDIA Orin), demonstrating its practicality in resource-limited scenarios.

## Methods

### Core Technologies

1. **Fully Linear Attention Architecture**
   - Completely eliminates traditional Transformer's quadratic attention mechanism
   - Built upon RWKV-7 linear attention blocks
   - Achieves O(n) spatiotemporal complexity instead of Transformer's O(n²)

2. **Linear Cross-Attention (LICA) Module**
   - Encodes queries via linear attention blocks to capture positional dependencies
   - Concatenates context features and encoded queries into a unified sequence
   - Uses state-based conditioning mechanism to accumulate context semantics
   - Maintains fully linear computational complexity

3. **Multi-modal Feature Fusion**
   - Supports camera and LiDAR multi-modal inputs
   - Generates BEV (Bird's Eye View) feature representations
   - Decodes trajectories through learnable queries

## Evaluation Benchmarks

### Main Benchmarks

#### 1. NAVSIM-v1
- Achieves state-of-the-art performance on the NAVSIM-v1 benchmark
- Primary evaluation metric: PDMS (Planning Driving Mixed Score)
- Compared with SOTA methods including DiffusionDrive, Transfuser, etc.

#### 2. Bench2Drive
- Comprehensive evaluation on the Bench2Drive benchmark
- Test scenarios include:
  - Long Path scenarios
  - Intersection scenarios
- Comparison with multiple Transformer-based baseline methods

### Performance Evaluation

1. **Planning Accuracy**
   - PDMS score improved from 88.1 to 89.3 with multi-frame inputs
   - After training with 10 frames, using longer sequences at inference further boosts performance

2. **Computational Efficiency** (NVIDIA Orin Platform)
   - **Inference Latency**: ~187ms (constant, regardless of frame count)
   - **Memory Usage**: ~400MB (constant)
   - Comparison: Transformer methods scale with history length, leading to rapidly increasing latency and memory

3. **Ablation Studies**
   - Effectiveness validation of historical frame count
   - LICA module vs. standard Transformer cross-attention comparison
   - Impact analysis of different training history lengths

### Real-world Deployment

- Successfully deployed on NVIDIA Orin edge computing platform
- Validated practicality in resource-constrained scenarios
- Demonstrated feasibility for real-time autonomous driving applications


## Citation

```bibtex
@article{huang2025lady,
  title={LADY: Linear Attention for Autonomous Driving Efficiency without Transformers},
  author={Huang, Jihao and Xia, Xi and Li, Zhiyuan and Liu, Tianle and Wang, Jingke and Chen, Junbo and Ye, Tengju},
  journal={arXiv preprint arXiv:2512.15038},
  year={2025}
}
```

## Project Page

This repository contains the webpage for the LADY project, including:
- Method overview and architecture diagrams
- Experimental results on NAVSIM and Bench2Drive
- Inference efficiency comparison analysis
- Ablation study results
- Video demonstrations

## Acknowledgments

We would like to thank the following repositories for their excellent work and open-source contributions:

- [NAVSIM](https://github.com/autonomousvision/navsim) - Data-Driven Non-Reactive Autonomous Vehicle Simulation and Benchmarking
- [Bench2Drive](https://github.com/Thinklab-SJTU/Bench2Drive) - Closed-Loop E2E-AD Benchmark Enhanced by World Model RL Expert

## More Works

For more works from our lab, please visit:
- [LLM2AD](https://github.com/UDEER-AI/LLM2AD) - CoRL 2025

## License

This website is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
