# Supplementary experiments

## 1. Introduction

The anonymous repository is built for showing the supplementary experiments during the 
rebuttal and response period of paper "LAMEE: A Light All-MLP Framework Leveraging Joint Time-Frequency Information for 
Time Series Prediction" (paper id 191) in SIGKDD 2023.

Sperifically, we conduct three types of supplementary experiments:
> E1: Supplementary performance comparisons.

> E2: Supplementary effeciency comparisons.

> E3: A visualization for comparison between high-dimensional embeddings and raw features.


## 2. Supplementary performance comparisons

We have utilized a fair third party benchmark that is publicly accessible ([link](https://github.com/thuml/Time-Series-Library)) to compare 14 influential time series forecasting 
studies that has been presented in recent years on 9 datasets (8 of which are public). We would like to express our sincere appreciation to the 
authors of this benchmark.

These compared studies are:
> 1. Connecting the Dots: Multivariate Time Series Forecasting with Graph Neural Networks. KDD, 2020. (MTGNN) ([paper](https://dl.acm.org/doi/abs/10.1145/3394486.3403118)) ([code](https://github.com/nnzhan/MTGNN))

> 2. Enhancing the locality and breaking the memory bottleneck of transformer on time series forecasting. NeurIPS, 2019. (LogTrans) ([paper](https://arxiv.org/pdf/1907.00235.pdf))

> 3. Neural Jump Ordinary Differential Equations: Consistent Continuous-Time Prediction and Filtering. ICLR, 2021. (NJODE) ([paper](https://arxiv.org/pdf/2006.04727.pdf)) ([code](https://github.com/HerreraKrachTeichmann/NJODE))

> 4. Informer: Beyond efficient transformer for long sequence time-series forecasting. AAAI, 2021. (Informer) ([paper](https://ojs.aaai.org/index.php/AAAI/article/view/17325))

> 5. Autoformer: Decomposition transformers with auto-correlation for long-term series forecasting. NeurIPS, 2021. (Autoformer) ([paper](https://arxiv.org/pdf/2106.13008.pdf))

> 6. Pyraformer: Low-complexity pyramidal attention for long-range time series modeling and forecasting. ICLR, 2022. (Pyraformer) ([paper](https://openreview.net/forum?id=0EXmFzUn5I))

> 7. FEDformer: Frequency enhanced decomposed transformer for long-term series forecasting. ICML, 2022. (Fedformer) ([paper](https://arxiv.org/pdf/2201.12740.pdf))

> 8. Non-stationary Transformers: Exploring the Stationarity in Time Series Forecasting. NeurIPS, 2022. (NSTrans) ([paper](https://openreview.net/forum?id=ucNDIDRNjjv))

> 9. Etsformer: Exponential smoothing transformers for time-series forecasting. NeurIPS, 2022. (ETSformer)  ([paper](https://openreview.net/forum?id=5m_3whfo483))

> 10. MICN: Multi-scale Local and Global Context Modeling for Long-term Series Forecasting. ICLR, 2023. (MICN) ([paper](https://openreview.net/forum?id=zt53IDUR1U))

> 11. Are Transformers Effective for Time Series Forecasting? AAAI, 2023. (DLinear) ([paper](https://arxiv.org/abs/2205.13504))

> 12. Crossformer: Transformer utilizing cross-dimension dependency for multivariate time series forecasting. ICLR, 2023. (Crossformer) ([paper](https://openreview.net/forum?id=vSVLM2j9eie))

> 13. Less is more: Fast multivariate time series forecasting with light sampling-oriented mlp structures. Arxiv, 2022. (LightTS) ([paper](https://arxiv.org/abs/2207.01186))

> 14. TimesNet: Temporal 2D-Variation Modeling for General Time Series Analysis. ICLR, 2023. (TimesNet) ([paper](https://openreview.net/forum?id=ju_Uqw384Oq))


These studies include Transformer based methods (2, 4, 5, 6, 7, 8, 9,and 12), convolutional neural networks based methods (1, 10, and 14), 
neural ordinary differential equations based method (3), and multi-layer perceptron based methods (11 and 13).
We have rewritten the code of 1 and 3 to perform our experiments, the rest of the code is taken directly from this benchmark.

These experiments are conducted on 9 datasets: illness, stock (not public for now due to privacy and economic concerns), electricity, traffic, weather, ETT series (contains 4 datasets). 
These datasets can be directly obtained in ([BaiduCloud](https://pan.baidu.com/s/1r3KhGd0Q9PJIUZdfEYoymg?pwd=i9iy)).

The detailed performance comparison:
![Results](performance_comp.png)


Higher resolution image please see ([Link](./performance_comp.pdf))

## 3. Supplementary efficiency comparisons

In this section, we perform efficiency comparisons with several baselines including 
Transformer based methods (Informer, Autoformer, and Fedformer), MLP based (DLinear), and 
convolutional neural network based methods (MICN and TimeNet). 

Specifically, 
the efficiency comparisons will be conducted in terms of number of parameters (million), 
time consumption (seconds per epoch), and memory usage (GB), respectively denoted as 
\# Para, TC, and MU for short. 

The detailed performance comparison:
![Efficiency](efficiency_comp.png)

Higher resolution image please see ([Link](./effeciency_comp.pdf))

## 4. A visualization for comparison between high-dimensional embeddings and raw features.


In this paper, we directly use the raw features rather than performing high-dimensional 
embeddings. And we found that the former strategy can perform better than the latter, shown as
the performance comparison of ablation model "LAMEE (embeddings)" in Section 4.3.  


This means that the feature dimension will remain constant across the entire model, and the dimension
of latent space equals to the feature dimension. 

From the view of matrix theory, we assume that performing high-dimensional
embeddings will yield a non-full rank of latent representations in high-dimensional
spaces, and result in information redundancy. We simply conduct an experiment to illustrate the 
phenomenon. 

Specifically, we extract the latent representations after the first projection in a 
well-trained Transformer model, 
and use TSNE dimensionality reduction algorithm to project the representations into an
1-dimensional space. 
We compare the sequence after dimensionality reduction and the original input sequence, 
it obviously that the sequence after dimensionality reduction seriously distorts the 
sequence of the original input, shown as:
![Comparison](latent_eff.png)



Higher resolution image please see ([Link](./latent_eff.pdf)).

Note that this is just an assumption based on the experimental phenomenon. In the future, we will 
pay more attention to this phenomenon and try to explain it. 