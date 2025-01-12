# Paper List for Machine Learning Systems

![Awesome](https://awesome.re/badge.svg)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/byungsoo-oh/ml-systems-papers/pulls)

Paper list for broad topics in machine learning systems 
> NOTE: Survey papers are annotated with [Survey 🔍] prefix.

## Table of Contents
<!-- TOC -->

- [Paper List for Machine Learning Systems](#paper-list-for-machine-learning-systems)
  - [Table of Contents](#table-of-contents)
  - [1. Data Processing](#1-data-processing)
    - [1.1 Data pipeline optimization](#11-data-pipeline-optimization)
      - [1.1.1 General](#111-general)
      - [1.1.2 Prep stalls](#112-prep-stalls)
      - [1.1.3 Fetch stalls (I/O)](#113-fetch-stalls-io)
      - [1.1.4 Specific workloads (GNN, DLRM)](#114-specific-workloads-gnn-dlrm)
    - [1.2 Caching and Distributed storage for ML training](#12-caching-and-distributed-storage-for-ml-training)
    - [1.3 Data formats](#13-data-formats)
    - [1.4 Data pipeline fairness and correctness](#14-data-pipeline-fairness-and-correctness)
    - [1.5 Data labeling automation](#15-data-labeling-automation)
  - [2. Training System](#2-training-system)
    - [2.1 Empirical study on ML Jobs](#21-empirical-study-on-ml-jobs)
    - [2.2 DNN job scheduling](#22-dnn-job-scheduling)
    - [2.3 GPU sharing](#23-gpu-sharing)
    - [2.4 GPU memory management and optimization](#24-gpu-memory-management-and-optimization)
    - [2.5 GPU memory usage estimate](#25-gpu-memory-usage-estimate)
    - [2.6 Distributed training (Parallelism)](#26-distributed-training-parallelism)
    - [2.7 DL job failures / Fault tolerance (resilient training)](#27-dl-job-failures--fault-tolerance-resilient-training)
    - [2.8 AutoML](#28-automl)
    - [2.9 Communication optimization \& Network Infrastructure for ML](#29-communication-optimization--network-infrastructure-for-ml)
    - [2.10 DNN compiler](#210-dnn-compiler)
    - [2.11 Model pruning and compression](#211-model-pruning-and-compression)
    - [2.12 GNN training system](#212-gnn-training-system)
    - [2.13 Congestion control for DNN training](#213-congestion-control-for-dnn-training)
    - [2.14 Others](#214-others)
  - [3. Inference System](#3-inference-system)
  - [4. Mixture of Experts (MoE)](#4-mixture-of-experts-moe)
  - [5. LLM Long Context](#5-llm-long-context)
  - [6. Federated Learning](#6-federated-learning)
  - [7. Privacy-Preserving ML](#7-privacy-preserving-ml)
  - [8. ML APIs \& Application-side Optimization](#8-ml-apis--application-side-optimization)
  - [9. ML (LLM) for Systems](#9-ml-llm-for-systems)
  - [10. GPU kernel scheduling](#10-gpu-kernel-scheduling)
  - [11 Energy-efficiency for LLM (carbon-aware)](#11-energy-efficiency-for-llm-carbon-aware)
  - [Others](#others)
- [References](#references)

<!-- /TOC -->

## 1. Data Processing

### 1.1 Data pipeline optimization
#### 1.1.1 General
- [HotInfra'24] [Lotus: Characterize Architecture Level CPU-based Preprocessing in Machine Learning Pipelines](https://kexinrong.github.io/lab/files/lotus-hotinfra24.pdf)
- [arxiv'24] [TensorSocket: Shared Data Loading for Deep Learning Training](https://arxiv.org/abs/2409.18749)
- [arxiv'24] [Efficient Tabular Data Preprocessing of ML Pipelines](https://arxiv.org/abs/2409.14912)
- [arxiv'24] [cedar: Composable and Optimized Machine Learning Input Data Pipelines](https://arxiv.org/abs/2401.08895)
- [MLSys'22] Plumber: Diagnosing and Removing Performance Bottlenecks in Machine Learning Data Pipelines
- [ISCA'22] Understanding Data Storage and Ingestion for Large-Scale Deep Recommendation Model Training
- [SIGMOD'22] Where Is My Training Bottleneck? Hidden Trade-Offs in Deep Learning Preprocessing Pipelines
- [VLDB'21] Analyzing and Mitigating Data Stalls in DNN Training
- [VLDB'21] tf.data: A Machine Learning Data Processing Framework


#### 1.1.2 Prep stalls
- [ATC'24] [Pecan: Cost-Efficient ML Data Preprocessing with Automatic Transformation Ordering and Hybrid Placement](https://www.usenix.org/conference/atc24/presentation/graur)
- [HotStorage'24] [A Selective Preprocessing Offloading Framework for Reducing Data Traffic in DL Training](https://dl.acm.org/doi/abs/10.1145/3655038.3665947)
- [VLDB'24] [FusionFlow: Accelerating Data Preprocessing for Machine Learning with CPU-GPU Cooperation](https://www.vldb.org/pvldb/vol17/p863-kim.pdf)
- [arxiv'23] [Rinas: Training with Dataset Shuffling Can Be General and Fast](https://arxiv.org/abs/2312.02368)
- [CVPR'23] [FFCV: Accelerating Training by Removing Data Bottlenecks](https://openaccess.thecvf.com/content/CVPR2023/papers/Leclerc_FFCV_Accelerating_Training_by_Removing_Data_Bottlenecks_CVPR_2023_paper.pdf)
- [RecSys'23] [InTune: Reinforcement Learning-based Data Pipeline Optimization for Deep Recommendation Models](https://arxiv.org/abs/2308.08500)
- [SIGMOD'23] GoldMiner: Elastic Scaling of Training Data Pre-Processing Pipelines for Deep Learning
- [VLDB'23] [FastFlow: Accelerating Deep Learning Model Training with Smart Offloading of Input Data Pipeline](https://www.vldb.org/pvldb/vol16/p1086-um.pdf)
- [SoCC'23] [tf.data service: A Case for Disaggregating ML Input Data Processing](https://anakli.inf.ethz.ch/papers/tfdata_service_SoCC23.pdf)
  - [arxiv version](https://arxiv.org/abs/2210.14826)
- [ATC'22] Cachew: Machine Learning Input Data Processing as a Service
- [OSDI'22] Looking Beyond GPUs for DNN Scheduling on Multi-Tenant Clusters
- [ICPP'19] DLBooster: Boosting End-to-End Deep Learning Workflows with Offloading Data Preprocessing Pipelines


#### 1.1.3 Fetch stalls (I/O)
- [TACO'23] [Fastensor: Optimise the Tensor I/O Path from SSD to GPU for Deep Learning Training](https://dl.acm.org/doi/pdf/10.1145/3630108)
- [ICPP'22] Lobster: Load Balance-Aware I/O for Distributed DNN Training
- [SC'21] Clairvoyant Prefetching for Distributed Machine Learning I/O


#### 1.1.4 Specific workloads (GNN, DLRM)
- [VLDB'25] [Eliminating Data Processing Bottlenecks in GNN Training over Large Graphs via Two-level Feature Compression](https://dl.acm.org/doi/abs/10.14778/3681954.3681968)
- [ISCA'24] [PreSto: An In-Storage Data Preprocessing System for Training Recommendation Models](https://arxiv.org/abs/2406.14571)
- [arxiv'23] [Towards Data-centric Graph Machine Learning: Review and Outlook](https://arxiv.org/abs/2309.10979)
- [arxiv'23] [FlexShard: Flexible Sharding for Industry-Scale Sequence Recommendation Models](https://arxiv.org/abs/2301.02959)
- [MLSys'23] [RecD: Deduplication for End-to-End Deep Learning Recommendation Model Training Infrastructure](https://proceedings.mlsys.org/paper_files/paper/2023/hash/a1126573153ad7e9f44ba80e99316482-Abstract-mlsys2023.html)
- [ASPLOS'22] [RecShard: statistical feature-based memory optimization for industry-scale neural recommendation](https://www-cs.stanford.edu/people/trippel/pubs/RecShard-Sethi-ASPLOS-22.pdf)
- [RecSys'23] [InTune: Reinforcement Learning-based Data Pipeline Optimization for Deep Recommendation Models
](https://arxiv.org/abs/2308.08500)
- [arxiv'23] MTrainS: Improving DLRM training efficiency using heterogeneous memories
- [SOSP'23] [Bagpipe: Accelerating Deep Recommendation Model Training](https://arxiv.org/abs/2202.12429)
- [SOSP'23] gSampler: General and Efficient GPU-based Graph Sampling for Graph Learning
- [NSDI'23] BGL: GPU-Efficient GNN Training by Optimizing Graph Data I/O and Preprocessing
- [DAC'22] A Joint Management Middleware to Improve Training Performance of Deep Recommendation Systems with SSDs
- [VLDB'22] Accelerating Recommendation System Training by Leveraging Popular Choices


### 1.2 Caching and Distributed storage for ML training
- [TPDS'23] High-Level Data Abstraction and Elastic Data Caching for Data-Intensive AI Applications on Cloud-Native Platforms
- [SOSP'23] UGACHE: A Unified GPU Cache for Embedding-based Deep Learning
- [ATC'23] Tectonic-Shift: A Composite Storage Fabric for Large-Scale ML Training
- [EuroSys'23] SiloD: A Co-design of Caching and Scheduling for Deep Learning Clusters [also in [2.1](#21-dl-scheduling)]
- [FAST'23] [SHADE: Enable Fundamental Cacheability for Distributed Deep Learning Training](https://www.usenix.org/conference/fast23/presentation/khan)
- [HPCA'23]  iCACHE: An Importance-Sampling-Informed Cache for Accelerating I/O-Bound DNN Model Training 
- [NeurIPS'22] [A Deep Learning Dataloader with Shared Data Preparation](https://proceedings.neurips.cc/paper_files/paper/2022/hash/6d538a6e667960b168d3d947eb6207a6-Abstract-Conference.html)
- [CLUSTER'22] [Hvac: Removing I/O Bottleneck for Large-Scale Deep Learning Applications](https://www.osti.gov/servlets/purl/1902810)
- [ICDE'22] Fluid: Dataset Abstraction and Elastic Acceleration for Cloud-native Deep Learning Training Jobs
- [ATC'21] [Refurbish Your Training Data: Reusing Partially Augmented Samples for Faster Deep Neural Network Training](https://www.usenix.org/conference/atc21/presentation/lee)
- [FAST'20] [Quiver: An Informed Storage Cache for Deep Learning](https://www.usenix.org/conference/fast20/presentation/kumar)
- [ICPP'20] [DIESEL: A Dataset-Based Distributed Storage and Caching System for Large-Scale Deep Learning Training](https://dl.acm.org/doi/pdf/10.1145/3404397.3404472)
- [arXiv'19] [Faster Neural Network Training with Data Echoing](https://arxiv.org/abs/1907.05550)
- [HotCloud'19] [The Case for Unifying Data Loading in Machine Learning Clusters](https://www.usenix.org/conference/hotcloud19/presentation/kakaraparthy)


### 1.3 Data formats
- [ECCV'22] L3: Accelerator-Friendly Lossless Image Format for High-Resolution, High-Throughput DNN Training
- [VLDB'21] Progressive compressed records: Taking a byte out of deep learning data

### 1.4 Data pipeline fairness and correctness
- [CIDR'21] Lightweight Inspection of Data Preprocessing in Native Machine Learning Pipelines

### 1.5 Data labeling automation
- [VLDB'18] Snorkel: Rapid Training Data Creation with Weak Supervision

## 2. Training System
### 2.1 Empirical study on ML Jobs
- [ICSE'24] [An Empirical Study on Low GPU Utilization of Deep Learning Jobs](https://www.computer.org/csdl/proceedings-article/icse/2024/021700a880/1V5BksrVgsg)
- [NSDI'24] Characterization of Large Language Model Development in the Datacenter
- [NSDI'22] MLaaS in the wild: workload analysis and scheduling in large-scale heterogeneous GPU clusters (`PAI`)
- [ATC'19] Analysis of Large-Scale Multi-Tenant GPU Clusters for DNN Training Workloads (`Philly`)

### 2.2 DNN job scheduling
- [SoCC'24] [Kale: Elastic GPU Scheduling for Online DL Model Training](https://dl.acm.org/doi/abs/10.1145/3698038.3698532)
- [arxiv'24] [Rubick: Exploiting Job Reconfigurability for Deep Learning Cluster Scheduling](https://arxiv.org/abs/2408.08586)
- [SC'24] [PAL: A Variability-Aware Policy for Scheduling ML Workloads in GPU Clusters](https://arxiv.org/abs/2408.11919)
- [OSDI'24] [MAST: Global Scheduling of ML Training across Geo-Distributed Datacenters at Hyperscale](https://www.usenix.org/conference/osdi24/presentation/choudhury)
- [ASPLOS'24] [Heet: Accelerating Elastic Training in Heterogeneous Deep Learning Clusters](https://dl.acm.org/doi/abs/10.1145/3620665.3640375)
- [Middleware'24] [Optimal Resource Efficiency with Fairness in Heterogeneous GPU Clusters](https://arxiv.org/abs/2403.18545)
- [IPDPS'24] Hadar: Heterogeneity-Aware Optimization-Based Online Scheduling for Deep Learning Cluster
- [EuroSys'24] [Blox: A Modular Toolkit for Deep Learning Schedulers](https://arxiv.org/abs/2312.12621)
- [NSDI'24] Swing: Short-cutting Rings for Higher Bandwidth Allreduce
- [NSDI'24] Towards Domain-Specific Network Transport for Distributed DNN Training
- [NSDI'24] Vulcan: Automatic Query Planning for Live ML Analytics
- [NSDI'24] [CASSINI: Network-Aware Job Scheduling in Machine Learning Clusters](https://arxiv.org/abs/2308.00852)

- [Survey :mag:] [ACM CSUR'23] [Deep Learning Workload Scheduling in GPU Datacenters: A Survey](https://dl.acm.org/doi/10.1145/3638757)
- [arxiv'23] Energy-Efficient GPU Clusters Scheduling for Deep Learning
- [SC'23] [EasyScale: Accuracy-consistent Elastic Training for Deep Learning](https://dl.acm.org/doi/abs/10.1145/3581784.3607054)
- [ICPP'23] CoTrain: Efficient Scheduling for Large-Model Training upon GPU and CPU in Parallel
- [ICPP'23] Embracing Uncertainty for Equity in Resource Allocation in ML Training
- [SOSP'23] [Sia: Heterogeneity-aware, goodput-optimized ML-cluster scheduling](https://www.pdl.cmu.edu/PDL-FTP/BigLearning/sia_sosp23-final.pdf)
- [NSDI'23] Shockwave: Proactive, Fair, and Efficient Cluster Scheduling for Dynamic Adaptation in Machine Learning
- [EuroSys'23] SiloD: A Co-design of Caching and Scheduling for Deep Learning Clusters [also in [1.2](#12-caching)]
- [EuroSys'23] Lyra: Elastic Scheduling for Deep Learning Clusters
- [EuroSys'23] [ElasticFlow: An Elastic Serverless Training Platform for Distributed Deep Learning](https://gudiandian.github.io/attaches/asplos23/asplosb23main-p360.pdf)
- [ASPLOS'23] Lucid: A Non-intrusive, Scalable and Interpretable Scheduler for Deep Learning Training Jobs

- [arxiv'22] [Singularity: Planet-Scale, Preemptive and Elastic Scheduling of AI Workloads](https://arxiv.org/abs/2202.07848)
- [Survey :mag:] [arxiv, 2022] [Deep Learning Workload Scheduling in GPU Datacenters: Taxonomy, Challenges and Vision](https://arxiv.org/abs/2205.11913)
- [SoCC'22] [ESCHER: Expressive Scheduling with Ephemeral Resources](https://dl.acm.org/doi/pdf/10.1145/3542929.3563498)
- [NSDI'22] MLaaS in the wild: workload analysis and scheduling in large-scale heterogeneous GPU clusters (`PAI`)
- [OSDI'22] Looking Beyond GPUs for DNN Scheduling on Multi-Tenant Clusters (`Synergy`)
- [SIGCOMM'22] Multi-resource interleaving for deep learning training (`Muri`)

- [MLSys'21] Wavelet: Efficient DNN Training with Tick-Tock Scheduling
- [SoCC'21] Chronus: A Novel Deadline-aware Scheduler for Deep Learning Training Jobs
- [SC'21] [Characterization and Prediction of Deep Learning Workloads in Large-Scale GPU Datacenters](https://arxiv.org/abs/2109.01313) (`Helios`)
- [OSDI'21] Privacy Budget Scheduling (`DPF`)
- [NSDI'21] Elastic Resource Sharing for Distributed Deep Learning (`AFS`)
- [OSDI'21] Pollux: Co-adaptive Cluster Scheduling for Goodput-Optimized Deep Learning

- [EuroSys'20] Balancing efficiency and fairness in heterogeneous GPU clusters for deep learning (`GandivaFair`)
- [NSDI'20] Themis: Fair and Efficient GPU Cluster Scheduling
- [OSDI'20] HiveD: Sharing a GPU Cluster for Deep Learning with Guarantees
- [OSDI'20] Heterogeneity-Aware Cluster Scheduling Policies for Deep Learning Workloads (`Gavel`)
- [EuroSys'20] AlloX: Compute Allocation in Hybrid Clusters
- [MLSys'20] Resource Elasticity in Distributed Deep Learning

- [NSDI'19] Tiresias: A GPU Cluster Manager for Distributed Deep Learning
- [ATC'19] Analysis of Large-Scale Multi-Tenant GPU Clusters for DNN Training Workloads (`Philly`)

- [EuroSys'18] Optimus: an efficient dynamic resource scheduler for deep learning clusters
- [OSDI'18] Gandiva: Introspective Cluster Scheduling for Deep Learning

### 2.3 GPU sharing
- [SC'24] [ParvaGPU: Efficient Spatial GPU Sharing for Large-Scale DNN Inference in Cloud Environments](https://arxiv.org/abs/2409.14447)
- [arxiv'24] [Tally: Non-Intrusive Performance Isolation for Concurrent Deep Learning Workloads](https://arxiv.org/abs/2410.07381)
- [arxiv'24] [Missile: Fine-Grained, Hardware-Level GPU Resource Isolation for Multi-Tenant DNN Inference](https://arxiv.org/abs/2407.13996)
- [ICPP'24] [MIGER: Integrating Multi-Instance GPU and Multi-Process Service for Deep Learning Clusters](https://dl.acm.org/doi/abs/10.1145/3673038.3673089)
- [ASPLOS'24] [RAP: Resource-aware Automated GPU Sharing for Multi-GPU Recommendation Model Training and Input Preprocessing](https://dl.acm.org/doi/abs/10.1145/3620665.3640406)
- [EuroSys'24] [Orion: Interference-aware, Fine-grained GPU Sharing for ML Applications](https://dl.acm.org/doi/10.1145/3627703.3629578)
- [ATC'23] [Beware of Fragmentation: Scheduling GPU-Sharing Workloads with Fragmentation Gradient Descent](https://www.usenix.org/conference/atc23/presentation/weng)
- [NSDI'23] [Transparent GPU Sharing in Container Clouds for Deep Learning Workloads](https://www.usenix.org/conference/nsdi23/presentation/wu)
- [ICPP'23] FaST-GShare: Enabling Efficient Spatio-Temporal GPU Sharing in Serverless Computing for Deep Learning Inference
- [arxiv'23] [GACER: Granularity-Aware ConcurrEncy Regulation for Multi-Tenant Deep Learning](https://arxiv.org/abs/2304.11745)
- [arxiv'23] MuxFlow: Efficient and Safe GPU Sharing in Large-Scale Production Deep Learning Clusters
- [SoCC'22] MISO: exploiting multi-instance GPU capability on multi-tenant GPU clusters
- [PACT'22] GPUPool: A Holistic Approach to Fine-Grained GPU Sharing in the Cloud
- [ATC'21] Zico: Efficient GPU Memory Sharing for Concurrent DNN Training
- [MLSys'20] Salus: Fine-Grained GPU Sharing Primitives for Deep Learning Applications
- [OSDI'20] AntMan: Dynamic Scaling on GPU Clusters for Deep Learning
- [OSDI'20] PipeSwitch: Fast Pipelined Context Switching for Deep Learning Applications
- [RTAS'19] [Fractional GPUs: Software-Based Compute and Memory Bandwidth Reservation for GPUs](https://ieeexplore.ieee.org/abstract/document/8743200)

### 2.4 GPU memory management and optimization
- [arxiv'24] [Accelerating Large Language Model Training with 4D Parallelism and Memory Consumption Estimator](https://arxiv.org/abs/2411.06465)
- [TACO'24] [ATP: Achieving Throughput Peak for DNN Training via Smart GPU Memory Management](https://dl.acm.org/doi/abs/10.1145/3701996)
- [arxiv'24] [GaLore: Memory-Efficient LLM Training by Gradient Low-Rank Projection](https://arxiv.org/abs/2403.03507)
- [ASPLOS'24] [GMLake: Efficient and Transparent GPU Memory Defragmentation for Large-scale DNN Training with Virtual Memory Stitching](https://arxiv.org/abs/2401.08156)
- [arxiv'23] [Rethinking Memory and Communication Cost for Efficient Large Language Model Training](https://arxiv.org/abs/2310.06003)
- [arxiv'23] Quantized Distributed Training of Large Models with Convergence Guarantees (`QSDP`)
- [arxiv'23] Does compressing activations help model parallel training?
- [SoCC'23] Towards GPU Memory Efficiency for Distributed Training at Scale
- [VLDB'23] [PyTorch FSDP: Experiences on Scaling Fully Sharded Data Parallel](https://www.vldb.org/pvldb/vol16/p3848-huang.pdf)
- [SOSP'23] Efficient Memory Management for Large Language Model Serving with PagedAttention
- [HPCA'23] MPress: Democratizing Billion-Scale Model Training on Multi-GPU Servers via Memory-Saving Inter-Operator Parallelism
- [HPCA'23] Tensor Movement Orchestration in Multi-GPU Training Systems
- [IJCAI'23] [OSDP: Optimal Sharded Data Parallel for Distributed Deep Learning](https://www.ijcai.org/proceedings/2023/0238.pdf)
- [ICLR'22] [LoRA: Low-Rank Adaptation of Large Language Models](https://openreview.net/forum?id=nZeVKeeFYf9)
  - algorithmic method for memory efficiency
- [VLDB'22] Harmony: Overcoming the Hurdles of GPU Memory Capacity to Train Massive DNN Models on Commodity Servers
- [ATC'21] ZeRO-Offload: Democratizing Billion-Scale Model Training
- [ICLR'21] ActNN: Reducing Training Memory Footprint via 2-Bit Activation Compressed Training
- [ICLR'21] Dynamic Tensor Rematerialization
- [SC'21] ZeRO-infinity: breaking the GPU memory wall for extreme scale deep learning
- [HPCA'21] [Sentinel: Efficient Tensor Migration and Allocation on Heterogeneous Memory Systems for Deep Learning](https://ieeexplore.ieee.org/abstract/document/9407112)
- [MLSys'20] Checkmate: Breaking the Memory Wall with Optimal Tensor Rematerialization
- [ASPLOS'20] Capuchin: Tensor-based GPU Memory Management for Deep Learning
- [ASPLOS'20] SwapAdvisor: Pushing Deep Learning Beyond the GPU Memory Limit via Smart Swapping
- [SC'20] ZeRO: memory optimizations toward training trillion parameter models
- [ISCA'18] Gist: Efficient Data Encoding for Deep Neural Network Training
- [PPoPP'18] Superneurons: dynamic GPU memory management for training deep neural networks
- [MICRO'16] vDNN: Virtualized deep neural networks for scalable, memory-efficient neural network design
- [arxiv'16] Training Deep Nets with Sublinear Memory Cost

### 2.5 GPU memory usage estimate
- [ESEC/FSE'20] Estimating GPU memory consumption of deep learning models

### 2.6 Distributed training (Parallelism)
- [ASPLOS'25 (to appear)] [GraphPipe: Improving Performance and Scalability of DNN Training with Graph Pipeline Parallelism](https://arxiv.org/abs/2406.17145)

- [SOSP'24] [Uncovering Nested Data Parallelism and Data Reuse in DNN Computation with FractalTensor](https://dl.acm.org/doi/abs/10.1145/3694715.3695961)
- [SOSP'24] [Enabling Parallelism Hot Switching for Efficient Training of Large Language Models](https://dl.acm.org/doi/10.1145/3694715.3695969)
- [arxiv'24] [Accelerating Large Language Model Training with 4D Parallelism and Memory Consumption Estimator](https://arxiv.org/abs/2411.06465)
- [TACO'24] [ATP: Achieving Throughput Peak for DNN Training via Smart GPU Memory Management](https://dl.acm.org/doi/abs/10.1145/3701996)
- [NeurIPS'24] [Rethinking Memory and Communication Costs for Efficient Data Parallel Training of Large Language Models](https://openreview.net/forum?id=4Un2TD9bNe)
- [NeurIPS'24] [SpeedLoader: An I/O efficient scheme for heterogeneous and distributed LLM operation](https://openreview.net/forum?id=Y2I0Fy4sm7)
- [SC'24] [Accelerating Distributed DLRM Training with Optimized TT Decomposition and Micro-Batching](https://www.computer.org/csdl/proceedings-article/sc/2024/529100a776/21HUVYHhG1O)
- [SC'24] [Democratizing AI: Open-source Scalable LLM Training on GPU-based Supercomputers](https://www.computer.org/csdl/proceedings-article/sc/2024/529100a036/21HUV5yQsyQ)
- [arxiv'24] [BitPipe: Bidirectional Interleaved Pipeline Parallelism for Accelerating Large Models Training](https://arxiv.org/abs/2410.19367)
- [arxiv'24] [Cephalo: Harnessing Heterogeneous GPU Clusters for Training Transformer Models](https://arxiv.org/abs/2411.01075)
- [SoCC'24] [Distributed training of large language models on AWS Trainium](https://www.amazon.science/publications/distributed-training-of-large-language-models-on-aws-trainium)
- [arxiv'24] [SimpleFSDP: Simpler Fully Sharded Data Parallel with torch.compile](https://arxiv.org/abs/2411.00284)
- [TPDS'24] [AutoDDL: Automatic Distributed Deep Learning With Near-Optimal Bandwidth Cost](https://arxiv.org/abs/2301.06813)
- [arxiv'24] [Malleus: Straggler-Resilient Hybrid Parallel Training of Large-scale Models via Malleable Data and Model Parallelization](https://arxiv.org/abs/2410.13333)
- [SOSP'24] Enabling Parallelism Hot Switching for Efficient Training of Large Language Models
- [arxiv'24] [FusionLLM: A Decentralized LLM Training System on Geo-distributed GPUs with Adaptive Compression](https://arxiv.org/abs/2410.12707)
- [arxiv'24] [FALCON: Pinpointing and Mitigating Stragglers for Large-Scale Hybrid-Parallel Training](https://arxiv.org/abs/2410.12588)
- [arxiv'24] [TorchTitan: One-stop PyTorch native solution for production ready LLM pre-training](https://arxiv.org/abs/2410.06511)
- [arxiv'24] [PipeFill: Using GPUs During Bubbles in Pipeline-parallel LLM Training](https://arxiv.org/abs/2410.07192)
- [arxiv'24] [Poplar: Efficient Scaling of Distributed DNN Training on Heterogeneous GPU Clusters](https://arxiv.org/pdf/2408.12596)
- [arxiv'24] [DistTrain: Addressing Model and Data Heterogeneity with Disaggregated Training for Multimodal Large Language Models](https://arxiv.org/abs/2408.04275)
- [SOSP'24] [TENPLEX: Changing Resources of Deep Learning Jobs using Parallelizable Tensor Collections](https://arxiv.org/abs/2312.05181)
- [arxiv'24] [Efficient Multi-Task Large Model Training via Data Heterogeneity-aware Model Management](https://arxiv.org/abs/2409.03365)
- [arxiv'24] [FlashFlex: Accommodating Large Language Model Training over Heterogeneous Environment](https://arxiv.org/abs/2409.01143v1)
- [arxiv'24] [PARALLELGPUOS: A Concurrent OS-level GPU Checkpoint and Restore System using Validated Speculation](https://arxiv.org/abs/2405.12079)
- [arxiv'24] [Unicron: Economizing Self-Healing LLM Training at Scale](https://arxiv.org/abs/2401.00134)
- [arxiv'24] [TBA: Faster Large Language Model Training Using SSD-Based Activation Offloading](https://arxiv.org/abs/2408.10013)
- [ICPP'24] [AutoPipe: Automatic Configuration of Pipeline Parallelism in Shared GPU Cluster](https://dl.acm.org/doi/abs/10.1145/3673038.3673047)
- [arxiv'24] [Optimus: Accelerating Large-Scale Multi-Modal LLM Training by Bubble Exploitation](https://www.arxiv.org/abs/2408.03505)
- [Survey :mag:] [arxiv'24] [Efficient Training of Large Language Models on Distributed Infrastructures: A Survey](https://arxiv.org/abs/2407.20018)
- [COLM'24] [LightSeq: Sequence Level Parallelism for Distributed Training of Long Context Transformers](https://arxiv.org/abs/2310.03294)
- [OSDI'24] [nnScaler: Constraint-Guided Parallelization Plan Generation for Deep Learning Training](https://www.usenix.org/conference/osdi24/presentation/lin-zhiqi)
  - [arxiv'23] [SuperScaler: Supporting Flexible DNN Parallelization via a Unified Abstraction](https://arxiv.org/abs/2301.08984)
- [ATC'24] [Accelerating the Training of Large Language Models using Efficient Activation Rematerialization and Optimal Hybrid Parallelism](https://www.usenix.org/conference/atc24/presentation/yuan)
- [ATC'24] [Metis: Fast Automatic Distributed Training on Heterogeneous GPUs](https://www.usenix.org/conference/atc24/presentation/um)
- [ATC'24] [FwdLLM: Efficient Federated Finetuning of Large Language Models with Perturbed Inferences](https://www.usenix.org/conference/atc24/presentation/xu-mengwei)
- [ATC'24] [OPER: Optimality-Guided Embedding Table Parallelization for Large-scale Recommendation Model](https://www.usenix.org/conference/atc24/presentation/wang)
- [arxiv'24] [LoongTrain: Efficient Training of Long-Sequence LLMs with Head-Context Parallelism](https://arxiv.org/abs/2406.18485)
- [arxiv'24] [PAFT: A Parallel Training Paradigm for Effective LLM Fine-Tuning](https://arxiv.org/abs/2406.17923)
- [HPDC'24] [DataStates-LLM: Lazy Asynchronous Checkpointing for Large Language Models](https://arxiv.org/abs/2406.10707v1)
- [ICML'24] [Scaling Beyond the GPU Memory Limit for Large Mixture-of-Experts Model Training](https://openreview.net/forum?id=uLpyWQPyF9)
- [ICML'24] [Integrated Hardware Architecture and Device Placement Search](https://openreview.net/pdf?id=ucl3B05EsX)
- [MLSys'24] [Lancet: Accelerating Mixture-of-Experts Training via Whole Graph Computation-Communication Overlapping](https://proceedings.mlsys.org/paper_files/paper/2024/file/339caf45a6fa281cae8adc6465343464-Paper-Conference.pdf)
- [MobiCom'24] [Asteroid: Resource-Efficient Hybrid Pipeline Parallelism for Collaborative DNN Training on Heterogeneous Edge Devices](https://dl.acm.org/doi/abs/10.1145/3636534.3649363)
- [EuroSys'24] [ScheMoE: An Extensible Mixture-of-Experts Distributed Training System with Tasks Scheduling](https://dl.acm.org/doi/abs/10.1145/3627703.3650083)
- [EuroMLSys@EuroSys'24] [ML Training with Cloud GPU Shortages: Is Cross-Region the Answer?](https://dl.acm.org/doi/pdf/10.1145/3642970.3655843)
- [ASPLOS'24] [AdaPipe: Optimizing Pipeline Parallelism with Adaptive Recomputation and Partitioning](https://dl.acm.org/doi/abs/10.1145/3620666.3651359)
- [ASPLOS'24] [PrimePar: Efficient Spatial-temporal Tensor Partitioning for Large Transformer Model Training](https://dl.acm.org/doi/abs/10.1145/3620666.3651357)
- [EuroSys'24] [Aceso: Efficient Parallel DNN Training through Iterative Bottleneck Alleviation](https://dl.acm.org/doi/abs/10.1145/3627703.3629554)
- [arxiv'24] [BurstAttention: An Efficient Distributed Attention Framework for Extremely Long Sequences](https://arxiv.org/abs/2403.09347)
- [arxiv'24] [Branch-Train-MiX: Mixing Expert LLMs into a Mixture-of-Experts LLM](https://arxiv.org/abs/2403.07816)
- [arxiv'24] [Accelerating Heterogeneous Tensor Parallelism via Flexible Workload Control](https://arxiv.org/abs/2401.11469)
- [arxiv'24] [GRAWA: Gradient-based Weighted Averaging for Distributed Training of Deep Learning Models](https://arxiv.org/abs/2403.04206)
- [ICLR'24] [Zero Bubble (Almost) Pipeline Parallelism](https://openreview.net/forum?id=tuzTN0eIO5)
- [arxiv'24] [BitDelta: Your Fine-Tune May Only Be Worth One Bit](https://arxiv.org/abs/2402.10193)
- [arxiv'24] [NutePrune: Efficient Progressive Pruning with Numerous Teachers for Large Language Models](https://arxiv.org/abs/2402.09773)
- [arxiv'24] [Accelerating Parallel Sampling of Diffusion Models](https://arxiv.org/abs/2402.09970)
- [arxiv'24] [Training DNN Models over Heterogeneous Clusters with Optimal Performance](https://arxiv.org/abs/2402.05302)
- [TKDE'24] [Improving Automatic Parallel Training via Balanced Memory Workload Optimization](https://ieeexplore.ieee.org/abstract/document/10449463)
  - extended version of Galvatron (VLDB'23)
  - arxiv version (2023): [link](https://arxiv.org/abs/2307.02031)
- [NSDI'24] DISTMM: Accelerating Distributed Multi-modal Model Training
- [NSDI'24] Accelerating Neural Recommendation Training with Embedding Scheduling
- [NSDI'24] Resiliency at Scale: Managing Google’s TPUv4 Machine Learning Supercomputer
- [NSDI'24] QuickUpdate: a Real-Time Personalization System for Large-Scale Recommendation Models
- [NSDI'24] [Scaling Large Language Model Training to More Than 10,000 GPUs](https://arxiv.org/abs/2402.15627)
- [arxiv'24] [Breaking MLPerf Training: A Case Study on Optimizing BERT](https://arxiv.org/abs/2402.02447)
- [ICLR'24] CO2: Efficient Distributed Training with Full Communication-Computation Overlap
  - [arxiv](https://arxiv.org/abs/2401.16265) [openreview](https://openreview.net/forum?id=ZO5cn4IfaN)
- [arxiv'24] [LocMoE: A Low-overhead MoE for Large Language Model Training](https://arxiv.org/abs/2401.13920)
- [arxiv'24] [Re-evaluating the Memory-balanced Pipeline Parallelism: BPipe](https://arxiv.org/abs/2401.02088)
- [AAMAS'24] [Holonic Learning: A Flexible Agent-based Distributed Machine Learning Framework](https://arxiv.org/abs/2401.10839)
- [arxiv'24] [InternEvo: Efficient Long-sequence Large Language Model Training via Hybrid Parallelism and Redundant Sharding](https://arxiv.org/abs/2401.09149)
- [VLDB'24] [Saturn: An Optimized Data System for Multi-Large-Model Deep Learning Workloads](https://arxiv.org/abs/2309.01226)
- [HPCA'24] [Tessel: Boosting Distributed Execution of Large DNN Models via Flexible Schedule Search](https://arxiv.org/abs/2311.15269)
- [NSDI'24] Parcae: Proactive, Liveput-Optimized DNN Training on Preemptible Instances
- [EuroSys'24] [HAP: SPMD DNN Training on Heterogeneous GPU Clusters with Automated Program Synthesis](https://i.cs.hku.hk/~cwu/papers/swzhang-eurosys24.pdf)

- [ICPP'23] Mercury: Fast and Optimal Device Placement for Large Deep Learning Models
- [arxiv'23] [vTrain: A Simulation Framework for Evaluating Cost-effective and Compute-optimal Large Language Model Training](https://arxiv.org/abs/2312.12391)
- [arxiv'23] [ASPEN: High-Throughput LoRA Fine-Tuning of Large Language Models with a Single GPU](https://arxiv.org/abs/2312.02515)
- [arxiv'23] [FlexModel: A Framework for Interpretability of Distributed Large Language Models](https://arxiv.org/abs/2312.03140)
- [arxiv'23] [Holmes: Towards Distributed Training Across Clusters with Heterogeneous NIC Environment](https://arxiv.org/abs/2312.03549)
- [arxiv'23] [RTP: Rethinking Tensor Parallelism with Memory Deduplication](https://arxiv.org/abs/2311.01635)
- [arxiv'23] [FP8-LM: Training FP8 Large Language Models](https://arxiv.org/abs/2310.18313)
- [arxiv'23] [Redco: A Lightweight Tool to Automate Distributed Training of LLMs on Any GPU/TPUs](https://arxiv.org/abs/2310.16355)
- [arxiv'23] [DeepSpeed Ulysses: System Optimizations for Enabling Training of Extreme Long Sequence Transformer Models](https://arxiv.org/abs/2309.14509)
- [arxiv'23] [A Distributed Data-Parallel PyTorch Implementation of the Distributed Shampoo Optimizer for Training Neural Networks At-Scale](https://arxiv.org/abs/2309.06497)
- [arxiv'23] [FLM-101B: An Open LLM and How to Train It with $100K Budget](https://arxiv.org/pdf/2309.03852.pdf)
- [arxiv'23] [UniAP: Unifying Inter- and Intra-Layer Automatic Parallelism by Mixed Integer Quadratic Programming](https://arxiv.org/abs/2307.16375)
- [arxiv'23] Modeling Parallel Programs using Large Language Models
- [arxiv'23] [Proteus: Simulating the Performance of Distributed DNN Training](https://arxiv.org/abs/2306.02267)
- [arxiv'23] Automated Tensor Model Parallelism with Overlapped Communication for Efficient Foundation Model Training
- [arxiv'23] Decoupled Model Schedule for Deep Learning Training
- [arxiv'23] RAF: Holistic Compilation for Deep Learning Model Training
- [arxiv'23] Ada-Grouper: Accelerating Pipeline Parallelism in Preempted Network by Adaptive Group-Scheduling for Micro-Batches
- [arxiv'23] Does compressing activations help model parallel training?
- [arxiv'23] Colossal-Auto: Unified Automation of Parallelization and Activation Checkpoint for Large-scale Models
- [arxiv'23] Scaling Vision Transformers to 22 Billion Parameters
- [arxiv'23] Auto-Parallelizing Large Models with Rhino: A Systematic Approach on Production AI Platform
- [arxiv'23] TAP: Accelerating Large-Scale DNN Training Through Tensor Automatic Parallelisation
- [arxiv'23] [SuperScaler: Supporting Flexible DNN Parallelization via a Unified Abstraction](https://arxiv.org/abs/2301.08984)
- [arxiv'23] ATP: Adaptive Tensor Parallelism for Foundation Models

- [IPDPS'23] [MPipeMoE: Memory Efficient MoE for Pre-trained Models with Adaptive Pipeline Parallelism](https://liamding.cc/slides/MPipeMoE_IPDPS23.pdf)
- [CLUSTER'23] Prophet: Fine-grained Load Balancing for Parallel Training of Large-scale MoE Models
- [NeurIPS'23] [ASPEN: Breaking Operator Barriers for Efficient Parallelization of Deep Neural Networks](https://proceedings.neurips.cc/paper_files/paper/2023/hash/d899a31938c7838965b589d9b14a5ca6-Abstract-Conference.html)
- [NeurIPS'23] [DeepPCR: Parallelizing Sequential Operations in Neural Networks](https://arxiv.org/pdf/2309.16318)
- [DAC'23] MixPipe: Efficient Bidirectional Pipeline Parallelism for Training Large-Scale Models
- [SC'23] [Hanayo: Harnessing Wave-like Pipeline Parallelism for Enhanced Large Model Training Efficiency](https://arxiv.org/pdf/2308.15762.pdf)
- [SOSP'23] PIT: Optimization of Dynamic Sparse Deep Learning Models via Permutation Invariant Transformation
- [SOSP'23] [Oobleck: Resilient Distributed Training of Large Models Using Pipeline Templates](https://dl.acm.org/doi/abs/10.1145/3600006.3613152)
- [TPDS'23] [Fold3D: Rethinking and Parallelizing Computational and Communicational Tasks in the Training of Large DNN Models](https://ieeexplore.ieee.org/document/10050126)
- [HPCA'23] [Phloem: Automatic Acceleration of Irregular Applications with Fine-Grain Pipeline Parallelism](https://people.csail.mit.edu/qmn/papers/nguyen_phloem_hpca_2023_preprint.pdf)
- [ACL'23] [Sequence Parallelism: Long Sequence Training from System Perspective](https://aclanthology.org/2023.acl-long.134/)
- [CCGrid'23] A Deep Learning Pipeline Parallel Optimization Method
- [OSDI'23] MGG: Accelerating Graph Neural Networks with Fine-Grained Intra-Kernel Communication-Computation Pipelining on Multi-GPU Platforms
- [ATC'23] Accelerating Distributed MoE Training and Inference with Lina
- [ATC'23] SmartMoE: Efficiently Training Sparsely-Activated Models through Combining Offline and Online Parallelization
- [ATC'23] MSRL: Distributed Reinforcement Learning with Dataflow Fragments
- [Survey :mag:] [TPDS'23] A Survey on Auto-Parallelism of Large-Scale Deep Learning Training
- [ICML'23] [SWARM Parallelism: Training Large Models Can Be Surprisingly Communication-Efficient](https://arxiv.org/abs/2301.11913)
- [ICML'23] BPipe: Memory-Balanced Pipeline Parallelism for Training Large Language Models
- [ICS'23] A Hybrid Tensor-Expert-Data Parallelism Approach to Optimize Mixture-of-Experts Training
- [NSDI'23] TopoOpt: Co-optimizing Network Topology and Parallelization Strategy for Distributed Training Jobs
- [NSDI'23] Bamboo: Making Preemptible Instances Resilient for Affordable Training of Large DNNs
- [NSDI'23] [ARK: GPU-driven Code Execution for Distributed Deep Learning](https://www.usenix.org/conference/nsdi23/presentation/hwang)
- [SIGMOD'23] FlexMoE: Scaling Large-scale Sparse Pre-trained Model Training via Dynamic Device Placement
- [MLSys'23] On Optimizing the Communication of Model Parallelism
- [MLSys'23] [MegaBlocks: Efficient Sparse Training with Mixture-of-Experts](https://proceedings.mlsys.org/paper_files/paper/2023/hash/5a54f79333768effe7e8927bcccffe40-Abstract-mlsys2023.html)
- [MLSys'23] [Tutel: Adaptive Mixture-of-Experts at Scale](https://proceedings.mlsys.org/paper_files/paper/2023/hash/9412531719be7ccf755c4ff98d0969dc-Abstract-mlsys2023.html)
- [TPDS'23] Merak: An Efficient Distributed DNN Training Framework with Automated 3D Parallelism for Giant Foundation Models
- [PPoPP'23] Elastic Averaging for Efficient Pipelined DNN Training
- [PPoPP'23] Efficient All-Reduce for Distributed DNN Training in Optical Interconnect Systems
- [VLDB'23] MiCS: Near-linear Scaling for Training Gigantic Model on Public Cloud
- [VLDB'23] Galvatron: Efficient Transformer Training over Multiple GPUs Using Automatic Parallelism
- [ASPLOS'23] Mobius: Fine Tuning Large-Scale Models on Commodity GPU Servers
- [ASPLOS'23] Optimus-CC: Efficient Large NLP Model Training with 3D Parallelism Aware Communication Compression

- [arxiv'22] Colossal-AI: A Unified Deep Learning System For Large-Scale Parallel Training
- [arxiv'22] Using DeepSpeed and Megatron to Train Megatron-Turing NLG 530B, A Large-Scale Generative Language Model
- [ICPP'22] [Tesseract: Parallelize the Tensor Parallelism Efficiently](https://arxiv.org/abs/2105.14500)
- [MLSys'22] [Synthesizing optimal parallelism placement and reduction strategies on hierarchical systems for deep learning](https://proceedings.mlsys.org/paper_files/paper/2022/hash/f0f9e98bc2e2f0abc3e315eaa0d808fc-Abstract.html)
  - [arxiv](https://arxiv.org/abs/2110.10548)
- [NeurIPS'22] Fine-tuning Language Models over Slow Networks using Activation Quantization with Guarantees
- [SoCC'22] Accelerating Large-Scale Distributed Neural Network Training with SPMD Parallelism
- [MLSys'22] Pathways: Asynchronous distributed dataflow for ML
- [MLSys'22] [SRIFTY: Swift and Thrifty Distributed Neural Network Training on the Cloud](https://proceedings.mlsys.org/paper_files/paper/2022/hash/0cafb7890f6a7d4de65507d5bb7e0187-Abstract.html)
- [MLSys'22] [Efficient Strong Scaling Through Burst Parallel Training](https://proceedings.mlsys.org/paper_files/paper/2022/hash/b99e69074b2fa1d8c8fe0d5b60e19397-Abstract.html)
- [EuroSys'22] Varuna: scalable, low-cost training of massive deep learning models
- [ATC'22] Whale: Efficient Giant Model Training over Heterogeneous GPUs
- [NeurIPS'22] [AMP: Automatically Finding Model Parallel Strategies with Heterogeneity Awareness](https://arxiv.org/abs/2210.07297)
- [PPoPP'22] [FasterMoE: modeling and optimizing training of large-scale dynamic pre-trained models](https://dl.acm.org/doi/abs/10.1145/3503221.3508418)
- [ICML'22] [DeepSpeed-MoE: Advancing Mixture-of-Experts Inference and Training to Power Next-Generation AI Scale](https://arxiv.org/abs/2201.05596)
- [ICML'22] [GLaM: Efficient Scaling of Language Models with Mixture-of-Experts](https://proceedings.mlr.press/v162/du22c/du22c.pdf)
- [HPDC'22] Hare: Exploiting Inter-job and Intra-job Parallelism of Distributed Machine Learning on Heterogeneous GPUs
- [OSDI'22] Alpa: Automating Inter- and Intra-Operator Parallelism for Distributed Deep Learning
- [NSDI'22] Accelerating Collective Communication in Data Parallel Training across Deep Learning Frameworks

- [arxiv'21] Amazon SageMaker Model Parallelism: A General and Flexible Framework for Large Model Training
- [arxiv'21] GSPMD: General and Scalable Parallelization for ML Computation Graphs
- [JMLR'21] [Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity](https://arxiv.org/abs/2101.03961)
- [TPDS'21] TensorOpt: Exploring the Tradeoffs in Distributed DNN Training With Auto-Parallelism
- [ATC'21] Fine-tuning giant neural networks on commodity hardware with automatic pipeline model parallelism
- [SIGMOD'21] Heterogeneity-Aware Distributed Machine Learning Training via Partial Reduce [also in [2.10](#210-communication-optimization)]
- [MLSys'21] PipeMare: Asynchronous Pipeline Parallel DNN Training
- [ICLR'21] GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding
- [NeurIPS'21] Piper: Multidimensional Planner for DNN Parallelization
- [ICML'21] Memory-Efficient Pipeline-Parallel DNN Training
- [ICML'21] TeraPipe: Token-Level Pipeline Parallelism for Training Large-Scale Language Models
- [ICML'21] PipeTransformer: Automated Elastic Pipelining for Distributed Training of Large-scale Models
- [SC'21] Chimera: Efficiently Training Large-Scale Neural Networks with Bidirectional Pipelines
- [SC'21] Efficient Large-Scale Language Model Training on GPU Clusters Using Megatron-LM (`PTD-P` or `Megatron-LM v2`)
- [FAST'21] Behemoth: A Flash-centric Training Accelerator for Extreme-scale DNNs
- [PPoPP'21] DAPPLE: a pipelined data parallel approach for training large models
- [VLDB'21] Distributed Deep Learning on Data Systems: A Comparative Analysis of Approaches

- [HPCA'20] AccPar: Tensor Partitioning for Heterogeneous Deep Learning Accelerators
- [NeurIPS'20] Efficient Algorithms for Device Placement of DNN Graph Operators
- [arxiv'20] Megatron-LM: Training Multi-Billion Parameter Language Models Using Model Parallelism
- [KDD'20 Tutorial] DeepSpeed: System Optimizations Enable Training Deep Learning Models with Over 100 Billion Parameters
- [VLDB'20] PyTorch Distributed: Experiences on Accelerating Data Parallel Training
- [OSDI'20] A Unified Architecture for Accelerating Distributed DNN Training in Heterogeneous GPU/CPU Clusters (`BytePS`)
- [SOSP'19] PipeDream: Generalized Pipeline Parallelism for DNN Training
- [NeurIPS'20] [Language Models are Few-Shot Learners](https://proceedings.neurips.cc/paper_files/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html?utm_medium=email&utm_source=transaction) [**From OpenAI**]
  - [arxiv](https://arxiv.org/abs/2005.14165)
- [arxiv'20] [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361) [**From OpenAI**]

- [HPCA'19] [HyPar: Towards Hybrid Parallelism for Deep Learning Accelerator Array](https://arxiv.org/abs/1901.02067)
- [IEEE MICRO'19] [Optimizing Multi-GPU Parallelization Strategies for Deep Learning Training](https://arxiv.org/abs/1907.13257)
- [MLSys'19] [Beyond data and model parallelism for deep neural networks](https://arxiv.org/abs/1807.05358) (`FlexFlow`)
- [MLSys'19] TicTac: Accelerating Distributed Deep Learning with Communication Scheduling
- [EuroSys'19] Parallax: Sparsity-aware Data Parallel Training of Deep Neural Networks
- [EuroSys'19] Supporting Very Large Models using Automatic Dataflow Graph Partitioning (`Tofu`)
- [SOSP'19] A Generic Communication Scheduler for Distributed DNN Training Acceleration
- [NeurIPS'19] Mesh-TensorFlow: Deep Learning for Supercomputers
- [NeurIPS'19] GPipe: Efficient Training of Giant Neural Networks using Pipeline Parallelism
- [ICML'18] Exploring Hidden Dimensions in Parallelizing Convolutional Neural Networks

- [Survey :mag:] [IJCAI'22] Survey on Effcient Training of Large Neural Networks
- [Survey :mag:] [ACM CSUR'19] Demystifying Parallel and Distributed Deep Learning
- [Survey :mag:] [ACM CSUR'19] Scalable Deep Learning on Distributed Infrastructures: Challenges, Techniques, and Tools

### 2.7 DL job failures / Fault tolerance (resilient training)
- [arxiv'24] [SkyServe: Serving AI Models across Regions and Clouds with Spot Instances](https://arxiv.org/abs/2411.01438)
- [arxiv'24] [Cloud Atlas: Efficient Fault Localization for Cloud Systems using Language Models and Causal Insight](https://arxiv.org/abs/2407.08694)
- [arxiv'24] [ByteCheckpoint: A Unified Checkpointing System for Large Foundation Model Development](https://arxiv.org/abs/2407.20143)
- [arxiv'24] [Lazarus: Resilient and Elastic Training of Mixture-of-Experts Models with Adaptive Expert Placement](https://arxiv.org/abs/2407.04656)
- [arxiv'24] [PARALLELGPUOS: A Concurrent OS-level GPU Checkpoint and Restore System using Validated Speculation](https://arxiv.org/abs/2405.12079)
- [SOSP'24] [ReCycle: Resilient Training of Large DNNs using Pipeline Adaptation](https://arxiv.org/abs/2405.14009)
- [HPDC'24] [DataStates-LLM: Lazy Asynchronous Checkpointing for Large Language Models](https://dl.acm.org/doi/abs/10.1145/3625549.3658685)
- [EuroSys'24] [Just-In-Time Checkpointing: Low Cost Error Recovery from Deep Learning Training Failures](https://dl.acm.org/doi/abs/10.1145/3627703.3650085)
- [NSDI'24] [Parcae: Proactive, Liveput-Optimized DNN Training on Preemptible Instances](https://www.usenix.org/conference/nsdi24/presentation/duan)
- [arxiv'23] [Unicron: Economizing Self-Healing LLM Training at Scale](https://arxiv.org/abs/2401.00134)
- [VLDB'23] [Eficient Fault Tolerance for Recommendation Model Training via Erasure Coding](https://dl.acm.org/doi/abs/10.14778/3611479.3611514)
- [SOSP'23] [GEMINI: Fast Failure Recovery in Distributed Training with In-Memory Checkpoints](https://dl.acm.org/doi/abs/10.1145/3600006.3613145)
- [SOSP'23] [Oobleck: Resilient Distributed Training of Large Models Using Pipeline Templates](https://dl.acm.org/doi/abs/10.1145/3600006.3613152)
- [NSDI'23] Bamboo: Making Preemptible Instances Resilient for Affordable Training of Large DNNs
- [EuroSys'22] Varuna: scalable, low-cost training of massive deep learning models
- [ATC'22] Sibylla: To Retry or Not To Retry on Deep Learning Job Failure
- [MLSys'21] [Understanding and Improving Failure Tolerant Training for Deep Learning Recommendation with Partial Recovery](https://proceedings.mlsys.org/paper_files/paper/2021/hash/f0f9e98bc2e2f0abc3e315eaa0d808fc-Abstract.html)
- [FAST'21] CheckFreq: Frequent, Fine-Grained DNN Checkpointing
- [ICSE'20] An Empirical Study on Program Failures of Deep Learning Jobs

### 2.8 AutoML
- [OSDI'23] Hydro: Surrogate-Based Hyperparameter Tuning Service in Datacenters
- [NSDI'23] ModelKeeper: Accelerating DNN Training via Automated Training Warmup
- [OSDI'20] Retiarii: A Deep Learning Exploratory-Training Framework

### 2.9 Communication optimization & Network Infrastructure for ML
- [SC'24] [Optimizing Distributed ML Communication with Fused Computation-Collective Operations](https://arxiv.org/abs/2305.06942)
- [SC'24] Network-Offloaded Bandwidth-Optimal Broadcast and Allgather for Distributed AI
- [NeurIPS'24] [LSH-MoE: Communication-efficient MoE Training via Locality-Sensitive Hashing](https://openreview.net/forum?id=bjFhVbky5A)
- [arxiv'24] [LumosCore: Highly Scalable LLM Clusters with Optical Interconnect](https://arxiv.org/abs/2411.01503)
- [TPDS'24] [AutoDDL: Automatic Distributed Deep Learning With Near-Optimal Bandwidth Cost](https://arxiv.org/abs/2301.06813)
- [HOTI'24] [Unified Collective Communication (UCC): An Unified Library for CPU, GPU, and DPU Collectives](https://ieeexplore.ieee.org/abstract/document/10664373)
- [SC'24] [Switch-Less Dragonfly on Wafers: A Scalable Interconnection Architecture based on Wafer-Scale Integration](https://arxiv.org/abs/2407.10290)
- [HPDC'24] [Near-Optimal Wafer-Scale Reduce](https://dl.acm.org/doi/abs/10.1145/3625549.3658693)
- [arxiv'24] [HiCCL: A Hierarchical Collective Communication Library](https://arxiv.org/abs/2408.05962)
- [ICS'24] [gZCCL: Compression-Accelerated Collective Communication Framework for GPU Clusters](https://dl.acm.org/doi/abs/10.1145/3650200.3656636)
- [ICS'24] [Snoopie: A Multi-GPU Communication Profiler and Visualizer](https://dl.acm.org/doi/abs/10.1145/3650200.3656597)
- [arxiv'24] [CSPS: A Communication-Efficient Sequence-Parallelism based Serving System for Transformer based Models with Long Prompts](https://arxiv.org/abs/2409.15104)
- [arxiv'24] [Domino: Eliminating Communication in LLM Training via Generic Tensor Slicing and Overlapping](https://arxiv.org/abs/2409.15241)
- [arxiv'24] [Exploring GPU-to-GPU Communication: Insights into Supercomputer Interconnects](https://arxiv.org/abs/2408.14090v1)
- [arxiv'24] [Demystifying the Communication Characteristics for Distributed Transformer Models](https://arxiv.org/abs/2408.10197)
- [ICPP'24] [Sparse Gradient Communication with AlltoAll for Accelerating Distributed Deep Learning](https://dl.acm.org/doi/abs/10.1145/3673038.3673140)
- [NAIC @ SIGCOMM'24] [Proof-of-Concept of a Flexible and High-Fidelity Approach to Distributed DNN Training Emulation](https://dl.acm.org/doi/abs/10.1145/3672198.3673793)
- [NAIC @ SIGCOMM'24] [Eloquent: A More Robust Transmission Scheme for LLM Token Streaming](https://dl.acm.org/doi/10.1145/3672198.3673797)
- [NAIC @ SIGCOMM'24] [OmNICCL: Zero-cost Sparse AllReduce with Direct Cache Access and SmartNICs](https://dl.acm.org/doi/abs/10.1145/3672198.3673804)
- [SIGCOMM'24] [Rethinking Machine Learning Collective Communication as a Multi-Commodity Flow Problem](https://dl.acm.org/doi/10.1145/3651890.3672249)
- [SIGCOMM'24] [RDMA over Ethernet for Distributed Training at Meta Scale](https://dl.acm.org/doi/abs/10.1145/3651890.3672233)
- [SIGCOMM'24] [Accelerating Model Training in Multi-cluster Environments with Consumer-grade GPUs](https://dl.acm.org/doi/abs/10.1145/3651890.3672228)
- [SIGCOMM'24] [MCCS: A Service-based Approach to Collective Communication for Multi-Tenant Cloud](https://dl.acm.org/doi/abs/10.1145/3651890.3672252)
- [arxiv'24] [MLTCP: Congestion Control for DNN Training](https://arxiv.org/abs/2402.09589)
  - [HotNets'24] [MLTCP: A Distributed Technique to Approximate Centralized Flow Scheduling For Machine Learning](https://people.csail.mit.edu/ghobadi/papers/mltcp_hotnets_2024.pdf)
- [arxiv'24] [Accelerating Distributed Deep Learning using Lossless Homomorphic Compression](https://arxiv.org/abs/2402.07529)
- [arxiv'24] [ForestColl: Efficient Collective Communications on Heterogeneous Network Fabrics](https://arxiv.org/abs/2402.06787)
- [APNet'24] [Understanding Communication Characteristics of Distributed Training](https://people.csail.mit.edu/zhizhenzhong/papers/2024_APNET.pdf)
- [ICLR'24] [ZeRO++: Extremely Efficient Collective Communication for Large Model Training](https://openreview.net/forum?id=gx2BT0a9MQ)
- [ICLR'24] CO2: Efficient Distributed Training with Full Communication-Computation Overlap
  - [[arxiv](https://arxiv.org/abs/2401.16265)] [[openreview](https://openreview.net/forum?id=ZO5cn4IfaN)]
- [MLSys'24] [L-GreCo: Layerwise-Adaptive Gradient Compression for Efficient and Accurate Deep Learning](https://proceedings.mlsys.org/paper_files/paper/2024/file/9069a8976ff06f6443e7f4172990a580-Paper-Conference.pdf)
- [MLSys'24] [Lancet: Accelerating Mixture-of-Experts Training via Whole Graph Computation-Communication Overlapping](https://proceedings.mlsys.org/paper_files/paper/2024/file/339caf45a6fa281cae8adc6465343464-Paper-Conference.pdf)
- [ASPLOS'24] [T3: Transparent Tracking & Triggering for Fine-grained Overlap of Compute & Collectives](https://dl.acm.org/doi/10.1145/3620665.3640410)
- [ASPLOS'24] [TCCL: Discovering Better Communication Paths for PCIe GPU Clusters](https://dl.acm.org/doi/abs/10.1145/3620666.3651362)
- [ASPLOS'24] [Centauri: Enabling Efficient Scheduling for Communication-Computation Overlap in Large Model Training via Communication Partitioning](https://dl.acm.org/doi/abs/10.1145/3620666.3651379)
- [ASPLOS'24] [Two-Face: Combining Collective and One-Sided Communication for Efficient Distributed SpMM](https://dl.acm.org/doi/10.1145/3620665.3640427)
- [NSDI'24] [THC: Accelerating Distributed Deep Learning Using Tensor Homomorphic Compression](https://www.usenix.org/conference/nsdi24/presentation/li-minghao)
- [Survey :mag:] [arxiv'23] [Communication-Efficient Distributed Deep Learning: A Comprehensive Survey](https://arxiv.org/abs/2003.06307)
- [arxiv'23] [Optimized Network Architectures for Large Language Model Training with Billions of Parameters](https://arxiv.org/abs/2307.12169)
- [arxiv'23] [FlexShard: Flexible Sharding for Industry-Scale Sequence Recommendation Models](https://arxiv.org/abs/2301.02959)
- [arxiv'23] [Rethinking Memory and Communication Cost for Efficient Large Language Model Training](https://arxiv.org/abs/2310.06003)
- [arxiv'23] [Zen: Near-Optimal Sparse Tensor Synchronization for Distributed DNN Training](https://arxiv.org/abs/2309.13254)
- [arxiv'23] [Optimized Network Architectures for Large Language Model Training with Billions of Parameters](https://arxiv.org/abs/2307.12169)
- [arxiv'23] [TACOS: Topology-Aware Collective Algorithm Synthesizer for Distributed Training](https://arxiv.org/abs/2304.05301)
- [INFOCOM'23] [Libra: Contention-Aware GPU Thread Allocation for Data Parallel Training in High Speed Networks](https://ieeexplore.ieee.org/abstract/document/10228922)
- [ICDCS'23] [bbTopk: Bandwidth-Aware Sparse Allreduce with Blocked Sparsification for Efficient Distributed Training](https://ieeexplore.ieee.org/abstract/document/10272502)
- [ICML'23] [CocktailSGD: Fine-tuning Foundation Models over 500Mbps Networks](https://proceedings.mlr.press/v202/wang23t/wang23t.pdf)
  - Related to DT-FM (NeurIPS'22)
- [IPDPS'23] [MCR-DL: Mix-and-Match Communication Runtime for Deep Learning](https://arxiv.org/abs/2303.08374)
- [ASPLOS'23] [MSCCLang: Microsoft Collective Communication Language](https://dl.acm.org/doi/abs/10.1145/3575693.3575724)
- [ASPLOS'23] [Overlap Communication with Dependent Computation via Decomposition in Large Deep Learning Models](https://dl.acm.org/doi/abs/10.1145/3567955.3567959)
- [EuroSys'23] A2TP: Aggregator-aware In-network Aggregation for Multi-tenant Learning
- [EuroSys'23] Hi-Speed DNN Training with Espresso: Unleashing the Full Potential of Gradient Compression with Near-Optimal Usage Strategies
- [MLSys'23] Cupcake: A Compression Optimizer for Scalable Communication-Efficient Distributed Training
- [MLSys'23] On Optimizing the Communication of Model Parallelism
- [NSDI'23] TopoOpt: Co-optimizing Network Topology and Parallelization Strategy for Distributed Training Jobs
- [NSDI'23] Better Together: Jointly Optimizing ML Collective Scheduling and Execution Planning using SYNDICATE
- [NSDI'23] TACCL: Guiding Collective Algorithm Synthesis using Communication Sketches
- [EuroSys'22] [Out-of-order backprop: an effective scheduling technique for deep learning](https://dl.acm.org/doi/abs/10.1145/3492321.3519563)
- [ISCA'22] Themis: a network bandwidth-aware collective scheduling policy for distributed training of DL models
- [SC'22] HammingMesh: A Network Topology for Large-Scale Deep Learning
- [PPoPP'22] Near-optimal sparse allreduce for distributed deep learning
- [MLSys'22] [Synthesizing optimal parallelism placement and reduction strategies on hierarchical systems for deep learning](https://proceedings.mlsys.org/paper_files/paper/2022/hash/f0f9e98bc2e2f0abc3e315eaa0d808fc-Abstract.html) (`P^2`)
- [ASPLOS'22] [Breaking the Computation and Communication Abstraction Barrier in Distributed Machine Learning Workloads](https://arxiv.org/abs/2105.05720) (`CoCoNET`)
- [EuroSys'21] [DGCL: an efficient communication library for distributed GNN training](https://dl.acm.org/doi/abs/10.1145/3447786.3456233)
- [ICLR'21] [Multi-Level Local SGD for Heterogeneous Hierarchical Networks](https://openreview.net/forum?id=C70cp4Cn32)
- [SIGMOD'21] Heterogeneity-Aware Distributed Machine Learning Training via Partial Reduce [also in [2.5](#25-parallelism--distributed-training)]
- [SC'21] Flare: flexible in-network allreduce
- [NSDI'21] [Scaling Distributed Machine Learning with In-Network Aggregation](https://www.usenix.org/conference/nsdi21/presentation/sapio)
- [ISCA'21] [Enabling compute-communication overlap in distributed deep learning training platforms](https://dl.acm.org/doi/abs/10.1109/ISCA52012.2021.00049)
- [PPoPP'21] [Synthesizing optimal collective algorithms](https://dl.acm.org/doi/10.1145/3437801.3441620) (`SCCL`)
- [SIGCOMM'21] [SiP-ML: High-Bandwidth Optical Network Interconnects for Machine Learning Training](https://people.csail.mit.edu/ghobadi/papers/sipml_sigcomm_2021.pdf)
- [ISCA'20] [An in-network architecture for accelerating shared-memory multiprocessor collectives](https://dl.acm.org/doi/10.1109/ISCA45697.2020.00085)
- [NeurIPS'20] [Nimble: Lightweight and Parallel GPU Task Scheduling for Deep Learning](https://proceedings.neurips.cc/paper/2020/hash/5f0ad4db43d8723d18169b2e4817a160-Abstract.html)
- [PPoPP'20] Taming unbalanced training workloads in deep learning with partial collective operations
- [MLSys'20] [Blink: Fast and Generic Collectives for Distributed ML](https://proceedings.mlsys.org/paper_files/paper/2020/hash/cd3a9a55f7f3723133fa4a13628cdf03-Abstract.html)
- [MLSys'20] [PLink: Discovering and Exploiting Datacenter Network Locality for Efficient Cloud-based Distributed Training](https://proceedings.mlsys.org/paper_files/paper/2020/hash/eca986d585a03890a412587a2f5ccb43-Abstract.html)
- [OSDI'20] [A Unified Architecture for Accelerating Distributed DNN Training in Heterogeneous GPU/CPU Clusters](https://www.usenix.org/conference/osdi20/presentation/jiang) (`BytePS`)
- [MLSys'19] [Priority-based Parameter Propagation for Distributed DNN Training](https://arxiv.org/abs/1905.03960) (`P3`)
- [MLSys'19] TicTac: Accelerating Distributed Deep Learning with Communication Scheduling
- [SOSP'19] A generic communication scheduler for distributed DNN training acceleration (`ByteScheduler`)
- [ATC'17] Poseidon: An Efficient Communication Architecture for Distributed Deep Learning on GPU Clusters

### 2.10 DNN compiler
- [SOSP'24] [Scaling Deep Learning Computation over the Inter-core Connected Intelligence Processor with T10](https://dl.acm.org/doi/10.1145/3694715.3695955)
- [OSDI'23] Cocktailer: Analyzing and Optimizing Dynamic Control Flow in Deep Learning
- [OSDI'23] Welder: Scheduling Deep Learning Memory Access via Tile-graph
- [OSDI'23] Effectively Scheduling Computational Graphs of Deep Neural Networks toward Their Domain-Specific Accelerators
- [OSDI'23] EINNET: Optimizing Tensor Programs with Derivation-Based Transformations
- [OSDI'23] [Optimizing Dynamic Neural Networks with Brainstorm](https://www.usenix.org/conference/osdi23/presentation/cui)
- [OSDI'22] [ROLLER: Fast and Efficient Tensor Compilation for Deep Learning](https://www.usenix.org/conference/osdi22/presentation/zhu)
- [OSDI'20] [Rammer: Enabling Holistic Deep Learning Compiler Optimizations with rTasks](https://www.usenix.org/conference/osdi20/presentation/ma)
- [OSDI'20] [Ansor: Generating High-Performance Tensor Programs for Deep Learning](https://www.usenix.org/conference/osdi20/presentation/zheng)
- [ASPLOS'20] [FlexTensor: An Automatic Schedule Exploration and Optimization Framework for Tensor Computation on Heterogeneous System](https://dl.acm.org/doi/10.1145/3373376.3378508)
- [OSDI'18] [TVM: An Automated End-to-End Optimizing Compiler for Deep Learning](https://www.usenix.org/conference/osdi18/presentation/chen)

### 2.11 Model pruning and compression
- [ACL'23] [Distilling Step-by-Step! Outperforming Larger Language Models with Less Training Data and Smaller Model Sizes](https://arxiv.org/abs/2305.02301)
- [ICLR'23] [GPTQ: Accurate Post-Training Quantization for Generative Pre-trained Transformers](https://arxiv.org/abs/2210.17323)
- [OSDI'23] [AdaEmbed: Adaptive Embedding for Large-Scale Recommendation Models](https://www.usenix.org/conference/osdi23/presentation/lai)
- [ICML'22] [TSPipe: Learn from Teacher Faster with Pipelines](https://proceedings.mlr.press/v162/lim22a.html)

### 2.12 GNN training system
> For comprehensive list of GNN systems papers, refer to [https://github.com/chwan1016/awesome-gnn-systems](https://github.com/chwan1016/awesome-gnn-systems).

- [arxiv'24] [FastGL: A GPU-Efficient Framework for Accelerating Sampling-Based GNN Training at Large Scale](https://arxiv.org/abs/2409.14939)
- [ICPP'24] [GNNDrive: Reducing Memory Contention and I/O Congestion for Disk-based GNN Training](https://dl.acm.org/doi/abs/10.1145/3673038.3673063)
- [VLDB'24] [NeutronStream: A Dynamic GNN Training Framework with Sliding Window for Graph Streams](https://arxiv.org/abs/2312.02473)
- [arxiv'23] [ReFresh: Reducing Memory Access from Exploiting Stable Historical Embeddings for Graph Neural Network Training](https://arxiv.org/abs/2301.07482)
- [arxiv'23] [Helios: An Efficient Out-of-core GNN Training System on Terabyte-scale Graphs with In-memory Performance](https://arxiv.org/abs/2310.00837)
- [arxiv'23] [GNNPipe: Accelerating Distributed Full-Graph GNN Training with Pipelined Model Parallelism](https://browse.arxiv.org/pdf/2308.10087.pdf)
- [MLSys'23] [Adaptive Message Quantization and Parallelization for Distributed Full-graph GNN Training](https://proceedings.mlsys.org/paper_files/paper/2023/hash/0ea77501c3f6bcba97e082d03a40646d-Abstract-mlsys2023.html)
- [SIGMOD'23] DUCATI: A Dual-Cache Training System for Graph Neural Networks on Giant Graphs with the GPU
- [OSDI'23] [MGG: Accelerating Graph Neural Networks with Fine-Grained Intra-Kernel Communication-Computation Pipelining on Multi-GPU Platforms](https://www.usenix.org/system/files/osdi23-wang-yuke.pdf)
- [EuroSys'23] [MariusGNN: Resource-Efficient Out-of-Core Training of Graph Neural Networks](https://arxiv.org/abs/2202.02365)
- [KDD'22] [Distributed Hybrid CPU and GPU training for Graph Neural Networks on Billion-Scale Heterogeneous Graphs](https://dl.acm.org/doi/abs/10.1145/3534678.3539177)
- [VLDB'22] [TGL: a general framework for temporal GNN training on billion-scale graphs](https://www.vldb.org/pvldb/vol15/p1572-zhou.pdf)
- [OSDI'21] [P3: Distributed Deep Graph Learning at Scale](https://www.usenix.org/conference/osdi21/presentation/gandhi)

### 2.13 Congestion control for DNN training
- [arxiv'24] [MLTCP: Congestion Control for DNN Training](https://arxiv.org/abs/2402.09589)
- [HotNets'22] [Congestion Control in Machine Learning Clusters](https://people.csail.mit.edu/ghobadi/papers/unfairness_hotnets_2022.pdf) 

### 2.14 Others
- [ATC'24] [Centimani: Enabling Fast AI Accelerator Selection for DNN Training with a Novel Performance Predictor](https://www.usenix.org/conference/atc24/presentation/xie)

## 3. Inference System
- [arxiv'24] [SageAttention: Accurate 8-Bit Attention for Plug-and-play Inference Acceleration](https://arxiv.org/abs/2410.02367), ([Code](https://github.com/thu-ml/SageAttention))
- [arxiv'24] [SageAttention2 Technical Report: Accurate 4-Bit Attention for Plug-and-play Inference Acceleration](https://arxiv.org/abs/2411.10958), ([Code](https://github.com/thu-ml/SageAttention))
- [arxiv'24] [Optimizing Speculative Decoding for Serving Large Language Models Using Goodput](https://arxiv.org/abs/2406.14066)
- [ACL'24] [SwapMoE: Serving Off-the-shelf MoE-based Large Language Models with Tunable Memory Budget](https://arxiv.org/abs/2308.15030)
- [arxiv'24] [EcoServe: Maximizing Multi-Resource Utilization with SLO Guarantees in LLM Serving](https://arxiv.org/abs/2411.06364)
- [IPDPS'24] [Exploiting Inter-Layer Expert Affinity for Accelerating Mixture-of-Experts Model Inference](https://arxiv.org/abs/2401.08383)
- [arxiv'24] [EPS-MoE: Expert Pipeline Scheduler for Cost-Efficient MoE Inference](https://arxiv.org/abs/2410.12247)
- [NeurIPS'24] [Kangaroo: Lossless Self-Speculative Decoding for Accelerating LLMs via Double Early Exiting](https://openreview.net/forum?id=lT3oc04mDp)
- [NeurIPS'24] [Toward Efficient Inference for Mixture of Experts](https://openreview.net/forum?id=stXtBqyTWX)
- [arxiv'24] [Lynx: Enabling Efficient MoE Inference through Dynamic Batch-Aware Expert Selection](https://arxiv.org/abs/2411.08982)
- [SC'24] [PipeInfer: Accelerating LLM Inference using Asynchronous Pipelined Speculation](https://arxiv.org/abs/2407.11798)
- [NeurIPS'24 (spotlight)] [Sequoia: Scalable and Robust Speculative Decoding](https://openreview.net/forum?id=rk2L9YGDi2)
- [SC'24] [SMIless: Serving DAG-based Inference with Dynamic Invocations under Serverless Computing](https://www.computer.org/csdl/proceedings-article/sc/2024/529100a590/21HUVxvcnoA)
- [arxiv'24] [SuffixDecoding: A Model-Free Approach to Speeding Up Large Language Model Inference](https://arxiv.org/abs/2411.04975)
- [arxiv'24] [V-LoRA: An Efficient and Flexible System Boosts Vision Applications with LoRA LMM](https://arxiv.org/abs/2411.00915)
- [SenSys'24] [LiteMoE: Customizing On-device LLM Serving via Proxy Submodel Tuning](https://dl.acm.org/doi/abs/10.1145/3666025.3699355)
- [arxiv'24] [HOBBIT: A Mixed Precision Expert Offloading System for Fast MoE Inference](https://arxiv.org/abs/2411.01433)
- [arxiv'24] [NEO: Saving GPU Memory Crisis with CPU Offloading for Online LLM Inference](https://arxiv.org/abs/2411.01142)
- [arxiv'24] [SkyServe: Serving AI Models across Regions and Clouds with Spot Instances](https://arxiv.org/abs/2411.01438)
- [MICRO'24] [Pushing the Performance Envelope of DNN-based Recommendation Systems Inference on GPUs](https://arxiv.org/abs/2410.22249)
- [arxiv'24] [VL-Cache: Sparsity and Modality-Aware KV Cache Compression for Vision-Language Model Inference Acceleration](https://arxiv.org/abs/2410.23317)
- [arxiv'24] [ShadowKV: KV Cache in Shadows for High-Throughput Long-Context LLM Inference](https://arxiv.org/abs/2410.21465)
- [arxiv'24] [Is the GPU Half-Empty or Half-Full? Practical Scheduling Techniques for LLMs](https://arxiv.org/abs/2410.17840)
- [arxiv'24] [POD-Attention: Unlocking Full Prefill-Decode Overlap for Faster LLM Inference](https://arxiv.org/abs/2410.18038)
- [arxiv'24] [Fiddler: CPU-GPU Orchestration for Fast Inference of Mixture-of-Experts Models](https://arxiv.org/abs/2402.07033)
- [arxiv'24] [MagicPIG: LSH Sampling for Efficient LLM Generation](https://arxiv.org/abs/2410.16179)
- [arxiv'24] [Revisiting SLO and Goodput Metrics in LLM Serving](https://arxiv.org/abs/2410.14257)
- [arxiv'24] [EPIC: Efficient Position-Independent Context Caching for Serving Large Language Models](https://arxiv.org/abs/2410.15332v1)
- [arxiv'24] [ParallelSpec: Parallel Drafter for Efficient Speculative Decoding](https://arxiv.org/abs/2410.05589)
- [EuroSys'25] [Fast State Restoration in LLM Serving with HCache](https://arxiv.org/abs/2410.05004)
- [arxiv'24] [SwiftKV: Fast Prefill-Optimized Inference with Knowledge-Preserving Model Transformation](https://arxiv.org/abs/2410.03960)
- [arxiv'24] [TidalDecode: Fast and Accurate LLM Decoding with Position Persistent Sparse Attention](https://arxiv.org/abs/2410.05076)
- [arxiv'24] [vAttention: Dynamic Memory Management for Serving LLMs without PagedAttention](https://arxiv.org/abs/2405.04437)
- [arxiv'24] [Mnemosyne: Parallelization Strategies for Efficiently Serving Multi-Million Context Length LLM Inference Requests Without Approximations](https://arxiv.org/abs/2409.17264)
- [arxiv'24] [CSPS: A Communication-Efficient Sequence-Parallelism based Serving System for Transformer based Models with Long Prompts](https://arxiv.org/abs/2409.15104)
- [arxiv'24] [DynamoLLM: Designing LLM Inference Clusters for Performance and Energy Efficiency](https://arxiv.org/abs/2408.00741)
- [HPCA'24] [KRISP: Enabling Kernel-wise RIght-sizing for Spatial Partitioned GPU Inference Servers](https://ieeexplore.ieee.org/abstract/document/10071121)
- [arxiv'24] [Missile: Fine-Grained, Hardware-Level GPU Resource Isolation for Multi-Tenant DNN Inference](https://arxiv.org/abs/2407.13996)
- [arxiv'24] [Efficient LLM Scheduling by Learning to Rank](https://www.arxiv.org/abs/2408.15792)
- [arxiv'24] [P/D-Serve: Serving Disaggregated Large Language Model at Scale](https://arxiv.org/abs/2408.08147)
- [arxiv'24] [NanoFlow: Towards Optimal Large Language Model Serving Throughput](https://arxiv.org/abs/2408.12757v1)
- [arxiv'24] [MARLIN: Mixed-Precision Auto-Regressive Parallel Inference on Large Language Models](https://www.arxiv.org/abs/2408.11743)
- [SOSP'24] [PowerInfer: Fast Large Language Model Serving with a Consumer-grade GPU](https://dl.acm.org/doi/10.1145/3694715.3695964)
- [SOSP'24] [LoongServe: Efficiently Serving Long-Context Large Language Models with Elastic Sequence Parallelism](https://dl.acm.org/doi/10.1145/3694715.3695948)
- [SOSP'24] [Improving DNN Inference Throughput Using Practical, Per-Input Compute Adaptation](https://dl.acm.org/doi/10.1145/3694715.3695978)
- [SOSP'24] [Apparate: Rethinking Early Exits to Tame Latency-Throughput Tensions in ML Serving](https://arxiv.org/abs/2312.05385)
- [arxiv'24] [LLMServingSim: A HW/SW Co-Simulation Infrastructure for LLM Inference Serving at Scale](https://arxiv.org/abs/2408.05499v1)
- [ICPP'24] [GMM: An Efficient GPU Memory Management-based Model Serving System for Multiple DNN Inference Models](https://dl.acm.org/doi/abs/10.1145/3673038.3673122)
- [SIGCOMM'24] [CacheGen: KV Cache Compression and Streaming for Fast Large Language Model Serving](https://dl.acm.org/doi/abs/10.1145/3651890.3672274)
- [ES-FoMO @ ICML'24] [CO2: Precise Attention Score Observation for improving KV Cache Replacement in Large Language Models](https://openreview.net/pdf?id=02zPmtcZa0)
- [OSDI'24] [dLoRA: Dynamically Orchestrating Requests and Adapters for LoRA LLM Serving](https://www.usenix.org/conference/osdi24/presentation/wu-bingyang)
- [OSDI'24] [Parrot: Efficient Serving of LLM-based Applications with Semantic Variable](https://www.usenix.org/conference/osdi24/presentation/lin-chaofan)
- [OSDI'24] [USHER: Holistic Interference Avoidance for Resource Optimized ML Inference](https://www.usenix.org/conference/osdi24/presentation/shubha)
- [OSDI'24] [Fairness in Serving Large Language Models](https://www.usenix.org/conference/osdi24/presentation/sheng)
- [OSDI'24] [MonoNN: Enabling a New Monolithic Optimization Space for Neural Network Inference Tasks on Modern GPU-Centric Architectures](https://www.usenix.org/conference/osdi24/presentation/zhuang)
- [OSDI'24] [Taming Throughput-Latency Tradeoff in LLM Inference with Sarathi-Serve](https://www.usenix.org/conference/osdi24/presentation/agrawal)
- [OSDI'24] [ServerlessLLM: Low-Latency Serverless Inference for Large Language Models](https://www.usenix.org/conference/osdi24/presentation/fu)
- [OSDI'24] [InfiniGen: Efficient Generative Inference of Large Language Models with Dynamic KV Cache Management](https://www.usenix.org/conference/osdi24/presentation/lee)
- [OSDI'24] [Llumnix: Dynamic Scheduling for Large Language Model Serving](https://www.usenix.org/conference/osdi24/presentation/sun-biao)
- [OSDI'24] [DistServe: Disaggregating Prefill and Decoding for Goodput-optimized Large Language Model Serving](https://www.usenix.org/conference/osdi24/presentation/zhong-yinmin)
- [ATC'24] [Power-aware Deep Learning Model Serving with μ-Serve](https://www.usenix.org/conference/atc24/presentation/qiu)
- [ATC'24] [Fast Inference for Probabilistic Graphical Models](https://www.usenix.org/conference/atc24/presentation/jiang)
- [ATC'24] [Cost-Efficient Large Language Model Serving for Multi-turn Conversations with CachedAttention](https://www.usenix.org/conference/atc24/presentation/gao-bin-cost)
- [ATC'24] [PUZZLE: Efficiently Aligning Large Language Models through Light-Weight Context Switch](https://www.usenix.org/conference/atc24/presentation/lei)
- [ATC'24] [Quant-LLM: Accelerating the Serving of Large Language Models via FP6-Centric Algorithm-System Co-Design on Modern GPUs](https://www.usenix.org/conference/atc24/presentation/xia)
- [TPDS'24] [ElasticBatch: A Learning-Augmented Elastic Scheduling System for Batch Inference on MIG](https://ieeexplore.ieee.org/abstract/document/10605084)
- [Survey :mag:] [arxiv'24] [LLM Inference Serving: Survey of Recent Advances and Opportunities](https://arxiv.org/abs/2407.12391)
- [arxiv'24] [Metron: Holistic Performance Evaluation Framework for LLM Inference Systems](https://arxiv.org/abs/2407.07000)
- [arxiv'24] [Compress then Serve: Serving Thousands of LoRA Adapters with Little Overhead](https://www.arxiv.org/abs/2407.00066)
- [arxiv'24] [One Queue Is All You Need: Resolving Head-of-Line Blocking in Large Language Model Serving](https://arxiv.org/abs/2407.00047)
- [OSDI'24] [Parrot: Efficient Serving of LLM-based Applications with Semantic Variable](https://arxiv.org/abs/2405.19888)
- [arxiv'24] [MemServe: Context Caching for Disaggregated LLM Serving with Elastic Memory Pool](https://arxiv.org/abs/2406.17565)
- [ISCA'24] [ElasticRec: A Microservice-based Model Serving Architecture Enabling Elastic Resource Scaling for Recommendation Models](https://arxiv.org/abs/2406.06955v1)
- [ISCA'24] [Splitwise: Efficient generative LLM inference using phase splitting](https://arxiv.org/abs/2311.18677)
- [ICML'24] [HexGen: Generative Inference of Large Language Model over Heterogeneous Environment](https://arxiv.org/abs/2311.11514)
- [ICML'24] [MuxServe: Flexible Spatial-Temporal Multiplexing for Multiple LLM Serving](https://arxiv.org/abs/2404.02015)
- [HPCA'24] [An LPDDR-based CXL-PNM Platform for TCO-efficient Inference of Transformer-based Large Language Models](https://ieeexplore.ieee.org/document/10476443)
- [arxiv'24] [Helix: Distributed Serving of Large Language Models via Max-Flow on Heterogeneous GPUs](https://arxiv.org/abs/2406.01566)
- [MobiSys'24] [ARISE: High-Capacity AR Offloading Inference Serving via Proactive Scheduling](https://dl.acm.org/doi/10.1145/3643832.3661894)
- [MobiSys'24] [Pantheon: Preemptible Multi-DNN Inference on Mobile Edge GPUs](https://dl.acm.org/doi/abs/10.1145/3643832.3661878)
- [arxiv'24] [Hardware-Aware Parallel Prompt Decoding for Memory-Efficient Acceleration of LLM Inference](https://arxiv.org/abs/2405.18628)
- [arxiv'24] [HawkVision: Low-Latency Modeless Edge AI Serving](https://arxiv.org/abs/2405.19213)
- [MLSys'24] [HeteGen: Heterogeneous Parallel Inference for Large Language Models on Resource-Constrained Devices](https://proceedings.mlsys.org/paper_files/paper/2024/file/5431dca75a8d2abc1fb51e89e8324f10-Paper-Conference.pdf)
- [MLSys'24] [S-LoRA: Serving Thousands of Concurrent LoRA Adapters](https://proceedings.mlsys.org/paper_files/paper/2024/file/906419cd502575b617cc489a1a696a67-Paper-Conference.pdf)
- [MLSys'24] [Vidur: A Large-Scale Simulation Framework For LLM Inference](https://arxiv.org/abs/2405.05465)
- [arxiv'24] [The CAP Principle for LLM Serving](https://arxiv.org/abs/2405.11299)
- [WWW'24] [λGrapher: A Resource-Efficient Serverless System for GNN Serving through Graph Sharing](https://dl.acm.org/doi/abs/10.1145/3589334.3645383)
- [arxiv'24] [vAttention: Dynamic Memory Management for Serving LLMs without PagedAttention](https://arxiv.org/abs/2405.04437)
- [ICML'24] [CLLMs: Consistency Large Language Models](https://arxiv.org/abs/2403.00835)
- [arxiv'24] [BlockLLM: Multi-tenant Finer-grained Serving for Large Language Models](https://arxiv.org/abs/2404.18322)
- [EuroSys'24] [Model Selection for Latency-Critical Inference Serving](https://dl.acm.org/doi/abs/10.1145/3627703.3629565)
- [arxiv'24] [Mélange: Cost Efficient Large Language Model Serving by Exploiting GPU Heterogeneity](https://arxiv.org/abs/2404.14527)
- [arxiv'24] [Learn To be Efficient: Build Structured Sparsity in Large Language Models](https://arxiv.org/abs/2402.06126)
- [arxiv'24] [Sponge: Inference Serving with Dynamic SLOs Using In-Place Vertical Scaling](https://arxiv.org/abs/2404.00704v1)
- [ISCA'24] [Pre-gated MoE: An Algorithm-System Co-Design for Fast and Scalable Mixture-of-Expert Inference](https://arxiv.org/abs/2308.12066)
- [arxiv'24] [Minions: Accelerating Large Language Model Inference with Adaptive and Collective Speculative Decoding](https://arxiv.org/abs/2402.15678)
- [arxiv'24] [ALTO: An Efficient Network Orchestrator for Compound AI Systems](https://arxiv.org/abs/2403.04311)
- [ASPLOS'24] [ExeGPT: Constraint-Aware Resource Scheduling for LLM Inference](https://dl.acm.org/doi/abs/10.1145/3620665.3640383)
- [ASPLOS'24] [NeuPIMs: NPU-PIM Heterogeneous Acceleration for Batched LLM Inferencing](https://arxiv.org/abs/2403.00579)
- [arxiv'24] [ATP: Enabling Fast LLM Serving via Attention on Top Principal Keys](https://www.arxiv.org/abs/2403.02352)
- [arxiv'24] [Taming Throughput-Latency Tradeoff in LLM Inference with Sarathi-Serve](https://arxiv.org/abs/2403.02310)
- [ICML'24] [DéjàVu: KV-cache Streaming for Fast, Fault-tolerant Generative LLM Serving](https://arxiv.org/abs/2403.01876)
- [ICLR'24] [Model Tells You What to Discard: Adaptive KV Cache Compression for LLMs](https://arxiv.org/abs/2310.01801)
- [arxiv'24] [FlexLLM: A System for Co-Serving Large Language Model Inference and Parameter-Efficient Finetuning](https://arxiv.org/abs/2402.18789)
- [arxiv'24] [Wisdom of Committee: Distilling from Foundation Model to SpecializedApplication Model](https://arxiv.org/abs/2402.14035)
- [arxiv'24] [RelayAttention for Efficient Large Language Model Serving with Long System Prompts](https://arxiv.org/abs/2402.14808)
- [arxiv'24] [LLM-PQ: Serving LLM on Heterogeneous Clusters with Phase-Aware Partition and Adaptive Quantization](https://arxiv.org/abs/2403.01136)
  - [PPoPP'24 poster] [POSTER: LLM-PQ:Serving LLM on Heterogeneous Clusters with Phase-Aware Partition and Adaptive Quantization](https://dl.acm.org/doi/abs/10.1145/3627535.3638480)
- [NSDI'24] Approximate Caching for Efficiently Serving Diffusion Models
- [arxiv'24] [APIServe: Efficient API Support for Large-Language Model Inferencing](https://arxiv.org/abs/2402.01869)
- [arxiv'24] [ServerlessLLM: Locality-Enhanced Serverless Inference for Large Language Models](https://arxiv.org/abs/2401.14351)
- [arxiv'24] [MoE-Infinity: Activation-Aware Expert Offloading for Efficient MoE Serving](https://arxiv.org/abs/2401.14361)
- [arxiv'24] [FP6-LLM: Efficiently Serving Large Language Models Through FP6-Centric Algorithm-System Co-Design](https://arxiv.org/abs/2401.14112)
- [arxiv'24] [Accelerating Retrieval-Augmented Language Model Serving with Speculation](https://arxiv.org/abs/2401.14021)
- [arxiv'24] [CaraServe: CPU-Assisted and Rank-Aware LoRA Serving for Generative LLM Inference](https://arxiv.org/abs/2401.11240)
- [arxiv'24] [Inference without Interference: Disaggregate LLM Inference for Mixed Downstream Workloads](https://arxiv.org/abs/2401.11181)
- [arxiv'24] [DeepSpeed-FastGen: High-throughput Text Generation for LLMs via MII and DeepSpeed-Inference](https://arxiv.org/abs/2401.08671)
- [Survey :mag:] [arxiv'24] [Unlocking Efficiency in Large Language Model Inference: A Comprehensive Survey of Speculative Decoding](https://arxiv.org/abs/2401.07851)
- [arxiv'24] [Learned Best-Effort LLM Serving](https://arxiv.org/abs/2401.07886)
- [arxiv'24] [Infinite-LLM: Efficient LLM Service for Long Context with DistAttention and Distributed KVCache](https://arxiv.org/abs/2401.02669)
- [VLDB'24] [Flash-LLM: Enabling Cost-Effective and Highly-Efficient Large Generative Model Inference with Unstructured Sparsity](https://www.vldb.org/pvldb/vol17/p211-xia.pdf)
- [ASPLOS'24] [SpotServe: Serving Generative Large Language Models on Preemptible Instances](https://arxiv.org/abs/2311.15566)
- [ASPLOS'24] [SpecInfer: Accelerating Generative Large Language Model Serving with Speculative Inference and Token Tree Verification](https://dl.acm.org/doi/abs/10.1145/3620666.3651335)
- [arxiv'23] [DeltaZip: Multi-Tenant Language Model Serving via Delta Compression](https://arxiv.org/abs/2312.05215)
- [EMNLP'23] [Fast and Robust Early-Exiting Framework for Autoregressive Language Models with Synchronized Parallel Decoding](https://aclanthology.org/2023.emnlp-main.362/)
- [arxiv'23] [Draft & Verify: Lossless Large Language Model Acceleration via Self-Speculative Decoding](https://arxiv.org/abs/2309.08168)
- [arxiv'23] [Fairness in Serving Large Language Models](https://arxiv.org/abs/2401.00588)
- [arxiv'23] [Moirai: Towards Optimal Placement for Distributed Inference on Heterogeneous Devices](https://arxiv.org/abs/2312.04025)
- [arxiv'23] [Punica: Multi-Tenant LoRA Serving](https://arxiv.org/abs/2310.18547)
- [arxiv'23] [Pipeline Parallelism for DNN Inference with Practical Performance Guarantees](https://arxiv.org/abs/2311.03703)
- [arxiv'23] [SARATHI: Efficient LLM Inference by Piggybacking Decodes with Chunked Prefills](https://arxiv.org/abs/2308.16369)
- [arxiv'23] High-throughput Generative Inference of Large Language Models with a Single GPU
- [HPDC'23] Kairos: Building Cost-Efficient Machine Learning Inference Systems with Heterogeneous Cloud Resources
- [SOSP'23] Paella: Low-latency Model Serving with Virtualized GPU Scheduling
- [SOSP'23] [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/abs/2309.06180)
- [MLSys'23] [Efficiently Scaling Transformer Inference](https://proceedings.mlsys.org/paper_files/paper/2023/hash/523f87e9d08e6071a3bbd150e6da40fb-Abstract-mlsys2023.html)
- [EuroSys'23] Fast and Efficient Model Serving Using Multi-GPUs with Direct-Host-Access
- [EuroSys'23] Tabi: An Efficient Multi-Level Inference System for Large Language Models
- [EuroSys'23] Pocket: ML Serving from the Edge
- [OSDI'23] AlpaServe: Statistical Multiplexing with Model Parallelism for Deep Learning Serving
- [NSDI'23] SHEPHERD: Serving DNNs in the Wild
- [VLDB'23] Serving and Optimizing Machine Learning Workflows on Heterogeneous Infrastructures
- [ICML'23] [Fast Inference from Transformers via Speculative Decoding](https://proceedings.mlr.press/v202/leviathan23a.html)
- [SIGMOD'22] Serverless Data Science - Are We There Yet? A Case Study of Model Serving
- [OSDI'22] Orca: A Distributed Serving System for Transformer-Based Generative Models
- [OSDI'22] Microsecond-scale Preemption for Concurrent GPU-accelerated DNN Inferences
- [ATC'22] [SOTER: Guarding Black-box Inference for General Neural Networks at the Edge](https://www.usenix.org/conference/atc22/presentation/shen)
- [ATC'22] Serving Heterogeneous Machine Learning Models on Multi-GPU Servers with Spatio-Temporal Sharing
- [ATC'22] Tetris: Memory-efficient Serverless Inference through Tensor Sharing
- [ATC'22] PetS: A Unified Framework for Parameter-Efficient Transformers Serving
- [ATC'21] INFaaS: Automated Model-less Inference Serving
- [SoCC'21] Morphling: Fast, Near-Optimal Auto-Configuration for Cloud-Native Model Serving
- [arxiv'21] Supporting Massive DLRM Inference through Software Defined Memory
- [MobiCom'20] SPINN: Synergistic Progressive Inference of Neural Networks over Device and Cloud

## 4. Mixture of Experts (MoE)
> This is the list of papers about MoE training and inference (collected from [2.6](#26-distributed-training-parallelism) and [3](#3-inference-system)).

- [ML for Sys workshop @ NeurIPS'24] [IFMoE: An Inference Framework Design for Fine-grained MoE](https://mlforsystems.org/assets/papers/neurips2024/paper41.pdf)
- [ML for Sys workshop @ NeurIPS'24] [TurboMoE: Enhancing MoE Model Training with Smart Kernel-Fusion and Data Transformation](https://openreview.net/forum?id=huy8g3iKy0)
- [arxiv'24] [Dense Backpropagation Improves Routing for Sparsely-Gated Mixture-of-Experts](https://openreview.net/forum?id=huy8g3iKy0)
- [arxiv'24] [MoE-Lightning: High-Throughput MoE Inference on Memory-constrained GPUs](https://arxiv.org/abs/2411.11217)
- [MLSys'24] [SiDA-MoE: Sparsity-Inspired Data-Aware Serving for Efficient and Scalable Large Mixture-of-Experts Models](https://arxiv.org/abs/2310.18859)
- [arxiv'24] [Pro-Prophet: Systematic Load Balancing Method for Efficient Parallel Training of Large-scale MoE Models](https://arxiv.org/abs/2411.10003)
- [EMNLP'24] [Mixture of Diverse Size Experts](https://aclanthology.org/2024.emnlp-industry.118/)
- [ACL'24] [SwapMoE: Serving Off-the-shelf MoE-based Large Language Models with Tunable Memory Budget](https://arxiv.org/abs/2308.15030)
- [SoCC'24] [MoEsaic: Shared Mixture of Experts](https://dl.acm.org/doi/abs/10.1145/3698038.3698521)
- [KDD'24] [Efficient Mixture of Experts based on Large Language Models for Low-Resource Data Preprocessing](https://dl.acm.org/doi/10.1145/3637528.3671873)
- [arxiv'24] [Pipeline MoE: A Flexible MoE Implementation with Pipeline Parallelism](https://arxiv.org/abs/2304.11414)
- [IPDPS'24] [Exploiting Inter-Layer Expert Affinity for Accelerating Mixture-of-Experts Model Inference](https://arxiv.org/abs/2401.08383)
- [arxiv'24] [EPS-MoE: Expert Pipeline Scheduler for Cost-Efficient MoE Inference](https://arxiv.org/abs/2410.12247)
- [arxiv'24] [Shortcut-connected Expert Parallelism for Accelerating Mixture of Experts](https://arxiv.org/abs/2404.05019)
- [NeurIPS'24] [Toward Efficient Inference for Mixture of Experts](https://openreview.net/forum?id=stXtBqyTWX)
- [arxiv'24] [Lynx: Enabling Efficient MoE Inference through Dynamic Batch-Aware Expert Selection](https://arxiv.org/abs/2411.08982)
- [MLSys'24] [SiDA: Sparsity-Inspired Data-Aware Serving for Efficient and Scalable Large Mixture-of-Experts Models](https://proceedings.mlsys.org/paper_files/paper/2024/hash/698cfaf72a208aef2e78bcac55b74328-Abstract-Conference.html)
- [SC'24] [APTMoE: Affinity-Aware Pipeline Tuning for MoE Models on Bandwidth-Constrained GPU Nodes](https://www.computer.org/csdl/proceedings-article/sc/2024/529100b436/21HUWvO6IIo)
- [NeurIPS'24] [GraphMETRO: Mitigating Complex Graph Distribution Shifts via Mixture of Aligned Experts](https://openreview.net/forum?id=QtYg4g3Deu)
- [arxiv'24] [HOBBIT: A Mixed Precision Expert Offloading System for Fast MoE Inference](https://arxiv.org/abs/2411.01433)
- [arxiv'24] [Hunyuan-Large: An Open-Source MoE Model with 52 Billion Activated Parameters by Tencent](https://arxiv.org/abs/2411.02265)
- [NeurIPS'24] [LSH-MoE: Communication-efficient MoE Training via Locality-Sensitive Hashing](https://openreview.net/forum?id=bjFhVbky5A)
- [arxiv'24] [Hunyuan-Large: An Open-Source MoE Model with 52 Billion Activated Parameters by Tencent](https://arxiv.org/abs/2411.02265)
- [arxiv'24] [Uni-MoE: Scaling Unified Multimodal LLMs with Mixture of Experts](https://arxiv.org/abs/2405.11273)
- [NeurIPS'24] [Read-ME: Refactorizing LLMs as Router-Decoupled Mixture of Experts with System Co-Design](https://openreview.net/forum?id=i8JaxY7tDI)
- [arxiv'24] [ExpertFlow: Optimized Expert Activation and Token Allocation for Efficient Mixture-of-Experts Inference](https://arxiv.org/abs/2410.17954v1)
- [arxiv'24] [Demystifying the Compression of Mixture-of-Experts Through a Unified Framework](https://arxiv.org/abs/2406.02500)
- [arxiv'24] [Fiddler: CPU-GPU Orchestration for Fast Inference of Mixture-of-Experts Models](https://arxiv.org/abs/2402.07033)
- [arxiv'24] [Optimizing Mixture-of-Experts Inference Time Combining Model Deployment and Communication Scheduling](https://arxiv.org/abs/2410.17043)
- [arxiv'24] [MoE-Pruner: Pruning Mixture-of-Experts Large Language Model using the Hints from Its Router](https://arxiv.org/abs/2410.12013)
- [arxiv'24] [Duo-LLM: A Framework for Studying Adaptive Computation in Large Language Models](https://arxiv.org/abs/2410.10846)
- [arxiv'24] [MoH: Multi-Head Attention as Mixture-of-Head Attention](https://arxiv.org/abs/2410.11842v1)
- [arxiv'24] [AT-MoE: Adaptive Task-planning Mixture of Experts via LoRA Approach](https://arxiv.org/abs/2410.10896v1)
- [NeurIPS'24 (Splotlight)] [Flex-MoE: Modeling Arbitrary Modality Combination via the Flexible Mixture-of-Experts](https://arxiv.org/abs/2410.08245v1)
- [arxiv'24] [Aria: An Open Multimodal Native Mixture-of-Experts Model](https://arxiv.org/abs/2410.05993)
- [arxiv'24] [MC-MoE: Mixture Compressor for Mixture-of-Experts LLMs Gains More](https://arxiv.org/abs/2410.06270)
- [arxiv'24] [MoE++: Accelerating Mixture-of-Experts Methods with Zero-Computation Experts](https://arxiv.org/abs/2410.07348)
- [arxiv'24] [Upcycling Large Language Models into Mixture of Experts](https://arxiv.org/abs/2410.07524)
- [arxiv'24] [No Need to Talk: Asynchronous Mixture of Language Models](https://arxiv.org/abs/2410.03529)
- [arxiv'24] [Lazarus: Resilient and Elastic Training of Mixture-of-Experts Models with Adaptive Expert Placement](https://arxiv.org/abs/2407.04656)
- [arxiv'24] [HMoE: Heterogeneous Mixture of Experts for Language Modeling](https://arxiv.org/abs/2408.10681)
- [arxiv'24] [FedMoE: Personalized Federated Learning via Heterogeneous Mixture of Experts](https://arxiv.org/abs/2408.11304v1)
- [arxiv'24] [AquilaMoE: Efficient Training for MoE Models with Scale-Up and Scale-Out Strategies](https://www.arxiv.org/abs/2408.06567)
- [arxiv'24] [Layerwise Recurrent Router for Mixture-of-Experts](https://www.arxiv.org/abs/2408.06793)
- [arxiv'24] [Partial Experts Checkpoint: Efficient Fault Tolerance for Sparse Mixture-of-Experts Model Training](https://arxiv.org/abs/2408.04307)
- [SRW @ ACL'24] [MoExtend: Tuning New Experts for Modality and Task Extension](https://arxiv.org/abs/2408.03511v1)
- [arxiv'24] [MoDE: Effective Multi-task Parameter Efficient Fine-Tuning with a Mixture of Dyadic Experts](https://arxiv.org/abs/2408.01505)
- [arxiv'24] [Efficient Expert Pruning for Sparse Mixture-of-Experts Language Models: Enhancing Performance and Reducing Inference Costs](https://arxiv.org/abs/2407.00945)
- [arxiv'24] [Self-MoE: Towards Compositional Large Language Models with Self-Specialized Experts](https://arxiv.org/abs/2406.12034)
- [arxiv'24] [Skywork-MoE: A Deep Dive into Training Techniques for Mixture-of-Experts Language Models](https://arxiv.org/abs/2406.06563)
- [ICML'24] [Scaling Laws for Fine-Grained Mixture of Experts](https://openreview.net/pdf?id=yoqdlynCRs)
- [ICML'24] [Scaling Beyond the GPU Memory Limit for Large Mixture-of-Experts Model Training](https://openreview.net/forum?id=uLpyWQPyF9)
- [MLSys'24] [QMoE: Sub-1-Bit Compression of Trillion-Parameter Models](https://proceedings.mlsys.org/paper_files/paper/2024/file/c74b624843218d9b6713fcf299d6d5e4-Paper-Conference.pdf)
- [MLSys'24] [Lancet: Accelerating Mixture-of-Experts Training via Whole Graph Computation-Communication Overlapping](https://proceedings.mlsys.org/paper_files/paper/2024/file/339caf45a6fa281cae8adc6465343464-Paper-Conference.pdf)
- [arxiv'24] [CuMo: Scaling Multimodal LLM with Co-Upcycled Mixture-of-Experts](https://arxiv.org/abs/2405.05949)
- [arxiv'24] [AdaMoLE: Fine-Tuning Large Language Models with Adaptive Mixture of Low-Rank Adaptation Experts](https://arxiv.org/abs/2405.00361)
- [SIGIR'24] [M3oE: Multi-Domain Multi-Task Mixture-of Experts Recommendation Framework](https://arxiv.org/abs/2404.18465)
- [EuroSys'24] [ScheMoE: An Extensible Mixture-of-Experts Distributed Training System with Tasks Scheduling](https://dl.acm.org/doi/abs/10.1145/3627703.3650083)
- [arxiv'24] [MixLoRA: Enhancing Large Language Models Fine-Tuning with LoRA based Mixture of Experts](https://arxiv.org/abs/2404.15159)
- [ICLR'24] [Mixture of LoRA Experts](https://openreview.net/forum?id=uWvKBCYh4S)
- [arxiv'24] [Branch-Train-MiX: Mixing Expert LLMs into a Mixture-of-Experts LLM](https://arxiv.org/abs/2403.07816)
- [arxiv'24] [MoE-Infinity: Activation-Aware Expert Offloading for Efficient MoE Serving](https://arxiv.org/abs/2401.14361)
- [IJCAI'24] [LocMoE: A Low-overhead MoE for Large Language Model Training](https://arxiv.org/abs/2401.13920)
- [ISCA'24] [Pre-gated MoE: An Algorithm-System Co-Design for Fast and Scalable Mixture-of-Expert Inference](https://arxiv.org/abs/2308.12066)
- [EMNLP'23] [Adaptive Gating in Mixture-of-Experts based Language Models](https://aclanthology.org/2023.emnlp-main.217/)
- [ACL'23] [AutoMoE: Heterogeneous Mixture-of-Experts with Adaptive Computation for Efficient Neural Machine Translation](https://aclanthology.org/2023.findings-acl.580/)
- [arxiv'23] [Towards MoE Deployment: Mitigating Inefficiencies in Mixture-of-Expert (MoE) Inference](https://arxiv.org/abs/2303.06182)
- [ATC'23] [Accelerating Distributed MoE Training and Inference with Lina](https://www.usenix.org/conference/atc23/presentation/li-jiamin)
- [ATC'23] [SmartMoE: Efficiently Training Sparsely-Activated Models through Combining Offline and Online Parallelization](https://www.usenix.org/conference/atc23/presentation/zhai)
- [SIGMOD'23] FlexMoE: Scaling Large-scale Sparse Pre-trained Model Training via Dynamic Device Placement
- [ICS'23] A Hybrid Tensor-Expert-Data Parallelism Approach to Optimize Mixture-of-Experts Training
- [MLSys'23] [MegaBlocks: Efficient Sparse Training with Mixture-of-Experts](https://proceedings.mlsys.org/paper_files/paper/2023/hash/5a54f79333768effe7e8927bcccffe40-Abstract-mlsys2023.html)
- [MLSys'23] [Tutel: Adaptive Mixture-of-Experts at Scale](https://proceedings.mlsys.org/paper_files/paper/2023/hash/9412531719be7ccf755c4ff98d0969dc-Abstract-mlsys2023.html)
- [PPoPP'22] [FasterMoE: modeling and optimizing training of large-scale dynamic pre-trained models](https://dl.acm.org/doi/abs/10.1145/3503221.3508418)
- [SustaiNLP @ EMNLP'22] [Who Says Elephants Can't Run: Bringing Large Scale MoE Models into Cloud Scale Production](https://arxiv.org/abs/2211.10017)
- [NeurIPS'22] [Mixture-of-Experts with Expert Choice Routing](https://proceedings.neurips.cc/paper_files/paper/2022/hash/2f00ecd787b432c1d36f3de9800728eb-Abstract-Conference.html)
- [ICML'22] [DeepSpeed-MoE: Advancing Mixture-of-Experts Inference and Training to Power Next-Generation AI Scale](https://arxiv.org/abs/2201.05596)
- [ICML'22] [GLaM: Efficient Scaling of Language Models with Mixture-of-Experts](https://proceedings.mlr.press/v162/du22c/du22c.pdf)
- [JMLR'22] [Switch transformers: scaling to trillion parameter models with simple and efficient sparsity](https://dl.acm.org/doi/abs/10.5555/3586589.3586709)
- [ICLR'17] [Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer](https://openreview.net/forum?id=B1ckMDqlg)

## 5. LLM Long Context
- [SOSP'24] [LoongServe: Efficiently Serving Long-Context Large Language Models with Elastic Sequence Parallelism](https://dl.acm.org/doi/10.1145/3694715.3695948)
- [arxiv'24] [USP: A Unified Sequence Parallelism Approach for Long Context Generative AI](https://arxiv.org/abs/2405.07719)
- [arxiv'24] [Training Ultra Long Context Language Model with Fully Pipelined Distributed Transformer](https://arxiv.org/abs/2408.16978v1)
- [NeurIPS'24 Workshop] [Long Context RAG Performance of Large Language Models](https://arxiv.org/abs/2411.03538)
- [arxiv'24] [ShadowKV: KV Cache in Shadows for High-Throughput Long-Context LLM Inference](https://arxiv.org/abs/2410.21465)
- [arxiv'24] [Mnemosyne: Parallelization Strategies for Efficiently Serving Multi-Million Context Length LLM Inference Requests Without Approximations](https://arxiv.org/abs/2409.17264)
- [arxiv'24] [CSPS: A Communication-Efficient Sequence-Parallelism based Serving System for Transformer based Models with Long Prompts](https://arxiv.org/abs/2409.15104)
- [COLM'24] [TriForce: Lossless Acceleration of Long Sequence Generation with Hierarchical Speculative Decoding](https://arxiv.org/abs/2404.11912)
- [arxiv'24] [FocusLLM: Scaling LLM's Context by Parallel Decoding](https://arxiv.org/abs/2408.11745)
- [Survey :mag:] [IJCAI'24] [X-former Elucidator: Reviving Efficient Attention for Long Context Language Modeling](https://www.ijcai.org/proceedings/2024/904)

## 6. Federated Learning
- [arxiv'24] [FedMoE: Personalized Federated Learning via Heterogeneous Mixture of Experts](https://arxiv.org/abs/2408.11304v1)
- [MLSys'24] [LIFL: A Lightweight, Event-driven Serverless Platform for Federated Learning](https://arxiv.org/abs/2405.10968)
- [arxiv'24] [FedEx: Expediting Federated Learning over Heterogeneous Mobile Devices by Overlapping and Participant Selection](https://arxiv.org/abs/2407.00943)
- [KDD'24] [FedBiOT: LLM Local Fine-tuning in Federated Learning without Full Model](https://arxiv.org/abs/2406.17706)
- [CCGrid'24] [Apodotiko: Enabling Efficient Serverless Federated Learning in Heterogeneous Environments](https://arxiv.org/abs/2404.14033)
- [EuroSys'24] [Dordis: Efficient Federated Learning with Dropout-Resilient Differential Privacy](https://dl.acm.org/doi/abs/10.1145/3627703.3629559)
- [arxiv'24] [Decoupled Vertical Federated Learning for Practical Training on Vertically Partitioned Data](https://arxiv.org/abs/2403.03871v1)
- [SAC'24] [Training Heterogeneous Client Models using Knowledge Distillation in Serverless Federated Learning](https://arxiv.org/abs/2402.07295)
- [arxiv'23] [CAFE: Carbon-Aware Federated Learning in Geographically Distributed Data Centers](https://arxiv.org/abs/2311.03615)
- [arxiv'23] [Federated Learning of Large Language Models with Parameter-Efficient Prompt Tuning and Adaptive Optimization](https://arxiv.org/abs/2310.15080)
- [IMWUT'23] [AttFL: A Personalized Federated Learning Framework for Time-series Mobile and Embedded Sensor Data Processing](https://dl.acm.org/doi/abs/10.1145/3610917)
- [Survey :mag:] [FGCS'23] [Model aggregation techniques in federated learning: A comprehensive survey](https://www.sciencedirect.com/science/article/pii/S0167739X23003333)
- [SoCC'23] [Auxo: Heterogeneity-Mitigating Federated Learning via Scalable Client Clustering](https://arxiv.org/abs/2210.16656)
- [MLSys'23] [GlueFL: Reconciling Client Sampling and Model Masking for Bandwidth Efficient Federated Learning](https://proceedings.mlsys.org/paper_files/paper/2023/hash/3ed923f9f88108cb066c6568d3df2666-Abstract-mlsys2023.html)
- [WWW'23] [To Store or Not? Online Data Selection for Federated Learning with Limited Storage](https://arxiv.org/abs/2209.00195)
- [EuroSys'23] REFL: Resource-Efficient Federated Learning
- [VLDB'23] [FederatedScope: A Flexible Federated Learning Platform for Heterogeneity](https://www.vldb.org/pvldb/vol16/p1059-li.pdf)
- [RecSys'22] [Towards Fair Federated Recommendation Learning: Characterizing the Inter-Dependence of System and Data Heterogeneity](https://arxiv.org/abs/2206.02633)
- [TMLR'22] [Optimal Client Sampling for Federated Learning](https://arxiv.org/abs/2010.13723)
- [ICML'22] FedScale: Benchmarking Model and System Performance of Federated Learning at Scale
- [MobiSys'22] FedBalancer: data and pace control for efficient federated learning on heterogeneous clients
- [MobiCom'22] PyramidFL: A Fine-grained Client Selection Framework for Efficient Federated Learning
- [MLSys'22] PAPAYA: Practical, Private, and Scalable Federated Learning
- [AISTATS'22] Federated Learning with Buffered Asynchronous Aggregation
- [NeurIPS'21] Federated Reconstruction: Partially Local Federated Learning
- [NeurIPS'21] FjORD: Fair and Accurate Federated Learning under heterogeneous targets with Ordered Dropout
- [OSDI'21] Oort: Efficient Federated Learning via Guided Participant Selection
- [MICRO'21] AutoFL: Enabling Heterogeneity-Aware Energy Efficient Federated Learning
- [MLSys'19] Towards Federated Learning at Scale: System Design
- [Survey :mag:] [ACM CSUR'22] Federated Learning for Smart Healthcare: A Survey

## 7. Privacy-Preserving ML
- [DAC'23] Privacy-Preserving DNN Training with Prefetched Meta-Keys on Heterogeneous Neural Network Accelerators
- [ICLR'23] [MPCFormer: fast, performant and private Transformer inference with MPC](https://arxiv.org/abs/2211.01452)
- [NeurIPS'22] [Iron: Private Inference on Transformers](https://proceedings.neurips.cc/paper_files/paper/2022/hash/64e2449d74f84e5b1a5c96ba7b3d308e-Abstract-Conference.html)

## 8. ML APIs & Application-side Optimization
- [arxiv'24] [APIServe: Efficient API Support for Large-Language Model Inferencing](https://arxiv.org/abs/2402.01869)
- [OSDI'24] [ChameleonAPI: Automatic and Efficient Customization of Neural Networks for ML Applications](https://www.usenix.org/conference/osdi24/presentation/liu)
- [ICML'22] [Efficient Online ML API Selection for Multi-Label Classification Tasks](https://proceedings.mlr.press/v162/chen22ad.html) (`FrugalMCT`)
- [NeurIPS'20] [FrugalML: How to use ML Prediction APIs more accurately and cheaply](https://proceedings.neurips.cc/paper/2020/hash/789ba2ae4d335e8a2ad283a3f7effced-Abstract.html)

## 9. ML (LLM) for Systems
- [ICSE'25] [Large Language Models as Configuration Validators](https://www.computer.org/csdl/proceedings-article/icse/2025/056900a204/215aWCaXlSg)
- [NeurIPS'24] [IaC-Eval: A code generation benchmark for Infrastructure-as-Code programs](https://www.cs-pk.com/preprint-iac-eval.pdf)
- [arxiv'24] [Cloud Atlas: Efficient Fault Localization for Cloud Systems using Language Models and Causal Insight](https://arxiv.org/abs/2407.08694)
- [arxiv'24] [LLMTune: Accelerate Database Knob Tuning with Large Language Models](https://arxiv.org/abs/2404.11581)
- [SIGCOMM'24] [NetLLM: Adapting Large Language Models for Networking](https://dl.acm.org/doi/abs/10.1145/3651890.3672268)
- [arxiv'24] [LLM-Enhanced Data Management](https://arxiv.org/abs/2402.02643)
- [arxiv'24] [MPIrigen: MPI Code Generation through Domain-Specific Language Models](https://arxiv.org/abs/2402.09126)
- [arxiv'24] [Can Large Language Models Write Parallel Code?](https://arxiv.org/abs/2401.12554)
- [arxiv'23] [LLM-Assisted Code Cleaning For Training Accurate Code Generators](https://arxiv.org/abs/2311.14904)
- [arxiv'23] [Large Language Models for Compiler Optimization](https://arxiv.org/abs/2309.07062)
- [VLDB'23] [How Large Language Models Will Disrupt Data Management](https://www.vldb.org/pvldb/vol16/p3302-fernandez.pdf)

## 10. GPU kernel scheduling
- [arxiv'24] [ACS: Concurrent Kernel Execution on Irregular, Input-Dependent Computational Graphs](https://arxiv.org/abs/2401.12377)
- [RTAS'24] [Demystifying NVIDIA GPU Internals to Enable Reliable GPU Management](https://www.cs.unc.edu/~jbakita/rtas24-private.pdf)
  - slides: [link](https://www.cs.unc.edu/~jbakita/rtas24_slides.pdf)
- [OSDI'23] [Welder: Scheduling Deep Learning Memory Access via Tile-graph](https://www.usenix.org/conference/osdi23/presentation/shi)
- [arxiv'21] [Characterizing Concurrency Mechanisms for NVIDIA GPUs under Deep Learning Workloads](https://arxiv.org/abs/2110.00459)
- [SIGMETRICS'21] [Demystifying the Placement Policies of the NVIDIA GPU Thread Block Scheduler for Concurrent Kernels](https://dl.acm.org/doi/10.1145/3453953.3453972)
- [NeurIPS'20] [Nimble: Lightweight and Parallel GPU Task Scheduling for Deep Learning](https://proceedings.neurips.cc/paper/2020/hash/5f0ad4db43d8723d18169b2e4817a160-Abstract.html)
- [RTSS'17] [GPU Scheduling on the NVIDIA TX2: Hidden Details Revealed](https://ieeexplore.ieee.org/document/8277284)

## 11 Energy-efficiency for LLM (carbon-aware)
- [arxiv'24] [DynamoLLM: Designing LLM Inference Clusters for Performance and Energy Efficiency](https://arxiv.org/abs/2408.00741)
- [SOSP'24] [Perseus: Removing Energy Bloat from Large Model Training](https://arxiv.org/abs/2312.06902)
- [arxiv'23] [CAFE: Carbon-Aware Federated Learning in Geographically Distributed Data Centers](https://arxiv.org/abs/2311.03615)
- [ATC'23] EnvPipe: Performance-preserving DNN Training Framework for Saving Energy
- [NSDI'23] Zeus: Understanding and Optimizing GPU Energy Consumption of DNN Training

## VLM
- InternVL: Scaling up Vision Foundation Models and Aligning for Generic Visual-Linguistic Tasks
--Ziya-VL: Bilingual Large Vision-Language Model via Multi-Task Instruction Tuning
--MobileVLM V2: Faster and Stronger Baseline for Vision Language Model
--Towards Multimodal In-Context Learning for Vision & Language Models
--A Comprehensive Overhaul of Multimodal Assistant with Small Language Models
--Qwen-VL: A Versatile Vision-Language Model for Understanding, Localization, Text Reading, and Beyond
--Instruct-ReID: A Multi-purpose Person Re-identification Task with Instructions
--MLLMReID: Multimodal Large Language Model-based Person Re-identification
--MM1: Methods, Analysis & Insights from Multimodal LLM Pre-training
--A Survey on Multimodal Large Language Models
--Bunny: Efficient Multimodal Learning from Data-centric Perspective
--ModalVerse.pdf [私]
--ModaVerse: Efficiently Transforming Modalities with LLMs
--CoDi-2: In-Context, Interleaved, and Interactive Any-to-Any Generation
--VILA: On Pre-training for Visual Language Models
--InternVideo: General Video Foundation Models via Generative and Discriminative Learning
--LanguageBind: Extending Video-Language Pretraining to N-modality by Language-based Semantic Alignment
--Video-LLaVA: Learning United Visual Representation by Alignment Before Projection
--Video Understanding with Large Language Models: A Survey
--NExT-GPT: Any-to-Any Multimodal LLM
--TinyGPT-V: Efficient Multimodal Large Language Model via Small Backbones
--Vary: Scaling up the Vision Vocabulary for Large Vision-Language Models
--LLaVA 1.6 [私]
--Vary-Toy: Small Language Model Meets with Reinforced Vision Vocabulary
--MM-LLMs: Recent Advances in MultiModal Large Language Models
--LLaVA-Med: Training a Large Language-and-Vision Assistant for Biomedicine in One Day
--ScienceQA | Learn to Explain: Multimodal Reasoning via Thought Chains for Science Question Answering
--Multimodal Chain-of-Thought Reasoning in Language Models
--LLaMA-VID: An Image is Worth 2 Tokens in Large Language Models
--PALI-3 VISION LANGUAGE MODELS: SMALLER, FASTER, STRONGER
--MINIGPT-V2: LARGE LANGUAGE MODEL AS A UNIFIED INTERFACE FOR VISION-LANGUAGE MULTI-TASK LEARNING
--UNIFYING ARCHITECTURES, TASKS, AND MODALITIES THROUGH A SIMPLE SEQUENCE-TO-SEQUENCE LEARNING FRAMEWORK
--ChatBridge: Bridging Modalities with Large Language Model as a Language Catalyst
--Any-to-Any Generation via Composable Diffusion
--KOSMOS-2: Grounding Multimodal Large Language Models to the World
--LEGO:Language Enhanced Multi-modal Grounding Model [私]
--MobileVLM : A Fast, Reproducible and Strong Vision Language Assistant for Mobile Devices
--Ferret: Refer and Ground Anything Anywhere at Any Granularity
--Unified-IO 2: Scaling Autoregressive Multimodal Models with Vision, Language, Audio, and Action
--LION : Empowering Multimodal Large Language Model with Dual-Level Visual Knowledge
--ImageBind: One Embedding Space To Bind Them All
--ImageBind-LLM: Multi-modality Instruction Tuning
--Set-of-Mark Prompting Unleashes Extraordinary Visual Grounding in GPT-4V [私]
--COGVLM: VISUAL EXPERT FOR LARGE LANGUAGE MODELS
--PaLI-X: On Scaling up a Multilingual Vision and Language Model
--Learning to Prompt for Vision-Language Models
--OpenFlamingo: An Open-Source Framework for Training Large Autoregressive Vision-Language Models
--LLaVA: Visual Instruction Tuning
--MiniGPT-4: Enhancing Vision-Language Understanding with Advanced Large Language Models
--Flamingo: a Visual Language Model for Few-Shot Learning
--GLIP: Grounded Language-Image Pre-training
--Chinese CLIP: Contrastive Vision-Language Pretraining in Chinese
--Vision-Language Models for Vision Tasks: A Survey
--SimVLM: Simple Visual Language Model Pretraining with Weak Supervision
--Oscar: Object-Semantics Aligned Pre-training for Vision-Language Tasks
--BEiT3: Image as a Foreign Language: BEIT Pretraining for All Vision and Vision-Language Tasks
--CoCa: Contrastive Captioners are Image-Text Foundation Models
--VLMo: Unified Vision-Language Pre-Training with Mixture-of-Modality-Experts
--InstructBLIP: Towards General-purpose Vision-Language Models with Instruction Tuning
--Align before Fuse: Vision and Language Representation Learning with Momentum Distillation
--ViLT: Vision-and-Language Transformer Without Convolution or Region Supervision
--BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation
--BLIP-2: Bootstrapping Language-Image Pre-training with Frozen Image Encoders and Large Language Models
--CLIP: Learning Transferable Visual Models From Natural Language Supervision

## Others
- [CPAL'24 (PMLR)] [Jaxpruner: A Concise Library for Sparsity Research](https://proceedings.mlr.press/v234/lee24a.html)
- [arxiv'24] [Scorch: A Library for Sparse Deep Learning](https://arxiv.org/abs/2405.16883)
- [arxiv'24] [Drowning in Documents: Consequences of Scaling Reranker Inference](https://arxiv.org/abs/2411.11767)
- [arxiv'24] [Crafting Interpretable Embeddings for Language Neuroscience by Asking LLMs Questions](https://openreview.net/forum?id=mxMvWwyBWe)
- [arxiv'24] [Computational Bottlenecks of Training Small-scale Large Language Models](https://arxiv.org/abs/2410.19456)
- [Survey :mag:] [arxiv'24] [A Comprehensive Survey of Small Language Models in the Era of Large Language Models: Techniques, Enhancements, Applications, Collaboration with LLMs, and Trustworthiness](https://arxiv.org/abs/2411.03350)
- [arxiv'24] [AI Metropolis: Scaling Large Language Model-based Multi-Agent Simulation with Out-of-order Execution](https://arxiv.org/abs/2411.03519)
- [ASPLOS'25 (to appear)] [PipeLLM: Fast and Confidential Large Language Model Services with Speculative Pipelined Encryption](https://arxiv.org/abs/2411.03357)
- [NeurIPS'24] [Are More LLM Calls All You Need? Towards Scaling Laws of Compound Inference Systems](https://arxiv.org/abs/2403.02419)
- [NeurIPS'24 Workshop] [Long Context RAG Performance of Large Language Models](https://arxiv.org/abs/2411.03538)
- [arxiv'24] [Stochastic Monkeys at Play: Random Augmentations Cheaply Break LLM Safety Alignment](https://arxiv.org/abs/2411.02785)
- [arxiv'24] [DroidSpeak: Enhancing Cross-LLM Communication](https://arxiv.org/abs/2411.02820v1)
- [arxiv'24] [Disaggregating Embedding Recommendation Systems with FlexEMR](https://arxiv.org/abs/2410.12794)
- [arxiv'24] [JudgeBench: A Benchmark for Evaluating LLM-based Judges](https://arxiv.org/abs/2410.12784)
- [VLDB'25] [Chameleon: a heterogeneous and disaggregated accelerator system for retrieval-augmented language models](https://arxiv.org/abs/2310.09949)
- [arxiv'24] [You Only Need One Step: Fast Super-Resolution with Stable Diffusion via Scale Distillation](https://arxiv.org/abs/2401.17258)
- [arxiv'24] [Computing in the Era of Large Generative Models: From Cloud-Native to AI-Native](https://arxiv.org/abs/2401.12230)
- [Survey :mag:] [arxiv'24] [A Survey of Resource-efficient LLM and Multimodal Foundation Models](https://arxiv.org/abs/2401.08092)
- [arxiv'23] [Efficiently Programming Large Language Models using SGLang](https://arxiv.org/abs/2312.07104)
- [MICRO'23] [Path Forward Beyond Simulators: Fast and Accurate GPU Execution Time Prediction for DNN Workloads](https://dl.acm.org/doi/10.1145/3613424.3614277)


# References
This repository is motivated by:
- https://github.com/HuaizhengZhang/Awesome-System-for-Machine-Learning
- https://github.com/S-Lab-System-Group/Awesome-DL-Scheduling-Papers
- https://github.com/ganler/ResearchReading
- https://jeongseob.github.io/readings_mlsys.html
- https://github.com/chwan1016/awesome-gnn-systems
- https://github.com/ConnollyLeon/awesome-Auto-Parallelism
