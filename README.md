General matrix multiplication (GEMM) plays a paramount role in a broad range of domains such as deep learning, scientific computing, and image processing. Many researchers have spent large amounts of efforts on optimizing GEMM to exploit the enormous computing power of GPUs. The primary optimization method is to partition the matrix into many tiles and exploit the parallelism between and within each tile, which closely mirrors the thread hierarchy on GPUs. In practice, GPUs can fully unleash its computing power when the matrix size is large and there are a sufficient number of tiles and enough workload within each tile. However, in many real-world applications especially deep learning domains, the matrix size is small. Besides, in many other fields, such as astrophysics, metabolic networks, high-order FEM schemes and deep learning, the matrix size is also not large enough to fully drive the GPU hardware resource. To this end, batched GEMMs has been proposed to process a group of small independent GEMMs together. However, prior works only optimize either from the tiling or from the batching perspective.
In this paper, we propose a coordinated tiling and batching framework for accelerating GEMM on GPUs. Our solution exploits the synergistic interaction between the two optimization knobs. It is composed of two engines: tiling engine and batching engine. In the tiling engine, we first design a series of tiling strategies dedicated for the batched GEMM scenario. Then, we design an algorithm to select the tiling strategy for each GEMM. After tiling engine, it generates multiple tiles from the GEMMs. In the batching engine, it is responsible to assign the tiles into thread blocks. We design a series of batching algorithms to determine the assignment from tiles to thread blocks. Then, we propose a general programming style to describe the coordinated tiling and batching solution. Finally, experiment evaluation results show that our framework can achieve about 40% performance speedup over the state-of-the-art work.
