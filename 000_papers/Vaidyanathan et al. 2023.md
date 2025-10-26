---
year: "2023"
title: Random-Access Neural Compression of Material Textures
tags:
  - "#paper"
  - "#neural_network"
  - "#texutre_compression"
journal: ACM Transactions on Graphics (TOG)
conference:
authors: Karthik Vaidyanathan, Marco Salvi, Bartlomiej Wronski, Tomas Akenine-Moller, Pontus Ebelin, and Aaron Lefohn
doi/url: https://doi.org/10.1145/3592407
---
##### Abstract 
The Continuous advancement of photorealism in rendering is accompanied by a growth in the texture data and, consequently, increasing sotrage and memory demands. To address this issue, we propose a novel neural compression technique specifically designed for material textures. We unlock two more levels of detail, i.e., 16$\times$ more texels, using low bitrate compression, with image quality that is better than advanced image compression techniques, such as AVIF and JPEG XL. At the same time, our method allows on-demand, real-time decompression with random access similar to block texture compression on GPUs, enabling compression on disk and memory. The key idea behind our approach is compressing multiple material textures and their mipmap chains together, and using a small neural network, that is optimized for each material, to decompress them. Finally, we use a custom training implementation to achieve practical compression speeds, whose performance surpasses that of general frameworks, like PyTorch, by an order of magnitude.
##### Takeaways 
Real-time rendering demands ever larger texture sets (albedo, normals, roughness, etc.). So, traditional GPU block compression (BC/ASTC) have fast, random-access features, but limited to ~4 channels and modest compression ratio (4~8$\times$). Recently, modern image codecs (AVIF, JPEG XL, neural image compression method) achieve high compression and quality, but lack random-access, multi-channel support, and GPU-friendly decoding.

So they purposed a novel approach to texture compression that exploits redundancies spatially, across mipmap levels, and across different material channels. By optimizing for reduced distortion at a low bitrate, we can compress two more levels of details in he same storage as block-compressed textures. The resulting texture quality at such aggressively low bitrates is better than or comparable to recent image compression standard like AVIF and JPEG XL, which are not designed for real-time decompression with random access.

And they implemented a novel low-cost decoder architecture that is optimizied specifically for each material. This architecture enables real-time performance for random access and can be integrated into material shader functions, such as filtering, to facilitate on-demand decompression.

Consequently, we need to focus on using neural networks for texture compression. Traditional texture compression methods provide random access and real-time decoding, but they are limited in compression efficiency and flexibility. Neural Texture Compression (NTC) achieves these same features while overcoming previous limitations, and I believe it represents a new paradigm in texture compression techniques.
##### Related works
1. [Weinreich et al. 2024](Weinreich%20et%20al.%202024.md)