---
noteId: "1bebb480f47f11eea17ae738b13bf5c5"
tags: []

---

# Experimental evaluation in the article Embedding-based-data-matching-for-disparate-data-sources (DAWAK 2024)

***Abstract of the paper***

Dealing with heterogeneous sources is an important challenge in the field of knowledge discovery and management. Schema matching methods are employed to solve this problem using three approaches: schema-based, instance-based, or a combination. This paper focuses on mapping between a schema-available (only) data source and a data source containing both schema and instance (both). Given the lack of suitable methods for aligning these two types of sources, we propose an approach using embedding models to provide vector modelling of sources and calculate similarities between data. Our solution consists in combining domain-specific embedding models and cross-domain embedding models to make data matching possible and efficient between the above-mentioned data sources.
We have conducted several experiments using the Valentine datasets to evaluate our data matching method on several disparate tabular data. The result indicate effectiveness in terms of stability and ablation handling.

Keywords: Schema Matching · Disparate data Source structures · Embeddings

***Summary of the experimental evaluation***

Our experimental assessment aims at (i) evaluating the efficiency of our proposal, and (ii) evaluating the usability of the proposed centrality metrics in a real application.

***Technical environment***

We deploy our approach and its variations using PyTorch version 1.6.0a0+9907a3e with NVIDIA CUDA 11.0.167. The training is conducted on a cluster of 12 Dell C6420 servers, each equipped with dual Intel Xeon Gold 6136 processors, boasting 12 cores running at 3 GHz. These servers are equipped with 192 GB of RAM, and each CPU has a Max Memory Per CPU of 7500 MB.


***Datasets***

In our experiments, we exploited the potential of five dataset categories, as described in the ["Valentine"](https://zenodo.org/records/5084605). These collections range from matching simple structured datasets to more complex configurations. 


***Effectiveness & Stability***

A detailed examination of algorithmic stability was carried out through a random selection of 10 unique datasets, which were then tested in several configurations of different hyperparameter values in table 2. As shown by [19], random walks have an impact on graphs projection and may affect performance. We focused on three important hyperparameters that influence the generation of random walks in our algorithm (walk length, walk Strategy and number of sentences) and then applied a grid-search on their values, resulting in 12 configurations. To ensure a complete and reliable evaluation, each configuration was run 10 times.

To sum up, our efficiency experiments represent a total of 35616 runs: 371 data sets x 96 hyperparameter configurations. 
And for noise, we count a total of 1200 runs: 10 datasets x 12 configurations x 10 runs.
The results of our experiments and their execution times are presented in the files ablation_effectiveness_stability.csv and noise.csv.

This rigorous approach is essential for evaluating the reliability of an algorithm
and its ability to provide consistent results for a given dataset and configuration,
guaranteeing both generalisation and optimal performance.

**Ablation**

The ablation study aimed to evaluate two approaches: the combined approach and the cross-domain approach. An experiment based solely on the domain-specific model is unfeasible due to the incompatibility between the heterogeneous structures of the datasets and the requirements of the EMBDI algorithm, which is designed for aligning comparable data structures.

Our experiments were conducted on different categories of datasets, incorporating noise levels up to "N2". The choice of 'N2' as the threshold was motivated by the noticeable drop in average F1 scores observed with more complex noise types above this level. This strategy allowed us to evaluate the response of two approaches to perturbed data(addition of prefixes/suffixes, abbreviations). Using 96 different configurations, we examined and contrasted the performance of the two methods. 

To sum up, our ablation experiments represent a total of 35616 runs: 371 data sets x 96 hyperparameter configurations. 
The results of our experiments and their execution times are presented in the  ablation_effectiveness_stability.csv file.