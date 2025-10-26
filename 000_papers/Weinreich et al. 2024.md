---
title: Real-Time Neural Materials using Block-Compressed Features
authors: Clément Weinreich, Louis de Oliveira, Antoine Houdard, Georges Nader
year: "2024"
journal: Computer Graphics Forum
conference:
doi/url: https://doi.org/10.1111/cgf.15013
tags:
  - neural_network
  - paper
  - texutre_compression
---
##### Abstract 
Neural materials typically consist of a collection of neural featuers along with a decoder network. The main challenge in integrating such models in real-time rendering pipelines lies in the large size required to store their features in GPU memory and the complexity of evaluating the network efficiently. We present a neural material model whose features and decoder are specifically designed to be used in real-time rendering pipelines. Our framework leverages hardware-based block compression (BC) texture formats to store the learned features and trains the model to output the material information continuously in space and scale. To achieve this, we organize the features in a block-based manner and emulate BC6 decompression during tranining, making it possible to export them as regular BC6 textures. This structure allows us to use high resolution features while maintaining a low memory footprint. Consequently, this enhances our model's overall capability, enabling the use of a lightweight and simple decoder architecture that can be evaluated directly in a shader. Furthermore, since the learned features can be decoded continuously, it allows for random uv sampling and smooth transition between scales without needing any subsequent filtering. As a result, our neural material has a small memory footprint, can be decoded extremely fast adding a minimal computational overhead to the rendering pipeline.

##### Takeaways  
- 본 논문은 Nueral Network를 이용하여 Tranditional 한 Block compression (BC6) format에 맞춰 학습, 저장하여, 작은 MLP로도 high-quality PBR materials를 real-time rendering에 적용할 수 있게 만들었음
- Problem
	- Real-time rendering에서는 고품질 PBR materials를 쓰려면, texture resolution과 layer 수가 늘어나서 GPU memory와 computational cost가 급격히 증가.
	- 기존 Neural Materials 접근은
		- Neural features를 uncompressed 상태로 GPU에 저장. 이는 memory footprint가 크게 됨.
		- Decoder network (MLP)가 커서 evaluation이 느림. 이는 real-time 적용이 어려움
- Proposed method 
	- Block-Compressed Features (BCf)
		- Neural features를 BC6 block compression format에 맞춰서 학습
		- Training 시 BC6 decompression을 differentable하게 simulation하게 해서, 학습 후, 그대로 BC6 texture로 export 가능
	- Key-advantages
		- Low memory footprint
		- Lightweight decoder 
		- Shader Integration
		- Continuous decoding 
		- Hardware-compliant filtering 

##### Related works
1. [Vaidyanathan et al. 2023](Vaidyanathan%20et%20al.%202023.md)