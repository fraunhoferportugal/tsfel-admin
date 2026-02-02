# GSoC 2026 Project Ideas

``TSFEL`` is a mature, open-source Python library for efficient and reproducible feature extraction from time-series data. The GitHub repository is [here](https://github.com/fraunhoferportugal/tsfel), which contains links to our project documentation and communication channels.

It provides a well-documented, actively maintained collection of feature extraction methods spanning the **statistical**, **temporal**, **spectral**, and **fractal** domains, and is used by research groups and applied projects worldwide.

``TSFEL`` offers GSoC contributors:

- A stable and production-ready codebase  
- Direct mentorship from long-term maintainers  

The library’s modular design and decorator-based feature system make it particularly well suited for **scoped, incremental contributions** that fit within the GSoC timeline. All projects are mentored by active `TSFEL` maintainers and are designed to deliver reusable functionality that will hopefully remain part of the library well beyond the GSoC period.

The projects presented here are our selected proposals for Google Summer of Code 2026. Additional details for each project are provided below.
 
## Project #1: Deep Feature Extraction – Pretrained Embeddings for Time Series

__Complexity__: Medium

__Duration__ 350 hours

__Mentors__: Duarte Folgado ([@dmfolgado](https://github.com/dmfolgado)) and 
Marília Barandas ([@mbarandas](https://github.com/mbarandas)) 

## Description

This project aims to extend `TSFEL` with a new **deep** feature set, enabling the extraction of fixed-length embeddings from time series using pretrained deep learning models in an inference-only setting.

`TSFEL` currently provides a large collection of hand-crafted features implemented as individual feature functions in the `tsfel.feature_extraction`, each annotated with decorators that associate the function with a specific feature domain (temporal, statistical, spectral, or fractal).

The main objective is to introduce a new feature domain, **deep**, and implement one or more example deep features that internally rely on pretrained models to produce embeddings. As a concrete example implementation, the project will integrate **TS2Vec** as a deep feature extractor, using a pretrained model strictly for inference. The resulting embeddings will be treated as features and made available through the standard `TSFEL` extraction pipeline, alongside classical features.

By embedding this functionality directly into TSFEL’s existing feature extraction mechanism, users can combine classical signal-processing features and deep representations in a single, consistent workflow, without maintaining external pipelines for windowing, normalization, or model execution.


### Required Skills
- Python 3
- Git and GitHub
- Basic understanding of time-series analysis
- Familiarity with deep learning frameworks (e.g., PyTorch) for inference

Optional (but useful):
- Experience with self-supervised or representation learning
- Writing clean, testable, open-source code

### Expected Outcome(s)
- Introduction of a new `TSFEL` feature domain (deep) implemented consistently with existing feature sets.
- One or more deep feature functions implemented in the `tsfel.feature_extraction.features.py`, annotated with the appropriate TSFEL decorators.
- At least one fully integrated pretrained encoder (inference-only) producing fixed-length embeddings per window or per signal.
- Documentation and examples showing how to combine classical TSFEL features with deep embeddings in downstream ML pipelines.
- Basic evaluation demonstrating correctness, stability, and practical runtime compared to the current available feature sets.

### References

1. Barandas, M., Folgado, D., Fernandes, L., Santos, S., Abreu, M., Bota, P., ... & Gamboa, H. (2020). TSFEL: Time Series Feature Extraction Library. SoftwareX, 11, 100456.
2. Bento, N., Rebelo, J., Barandas, M., Carreiro, A. V., Campagner, A., Cabitza, F., & Gamboa, H. (2022). Comparing Handcrafted Features and Deep Neural Representations for Domain Generalization in Human Activity Recognition. Sensors, 22(19), 7324.
3. Yue, Z., Wang, Y., Duan, J., Yang, T., Huang, C., Tong, Y., & Xu, B. (2022, June). TS2Vec: Towards Universal Representation of Time Series. In Proceedings of the AAAI conference on artificial intelligence (Vol. 36, No. 8, pp. 8980-8987).


## Project #2: Query-Based Feature Extraction – Reference-Aware Time Series Features

__Complexity__: Medium

__Duration__: 350 hours

__Mentors__: Marília Barandas ([@mbarandas](https://github.com/mbarandas)) and 
Duarte Folgado ([@dmfolgado](https://github.com/dmfolgado))

### Description

This project aims to extend `TSFEL` with a new feature domain dedicated to query-based (reference-based) feature extraction, enabling the computation of features that explicitly compare an input time-series window with a user-provided reference (query) signal.

`TSFEL` currently provides a large collection of hand-crafted features implemented as individual feature functions in the `tsfel.feature_extraction`, each annotated with decorators that associate the function with a specific feature domain (temporal, statistical, spectral, or fractal).

The main objective of this project is to introduce a new feature domain, **query**, where features are computed by comparing the input window to a given query signal. These features may include distance measures, similarity scores, alignment costs, correlation-based metrics, and other comparison-based descriptors.

As a concrete implementation, this project will integrate `TSFEL` with the existing `TSSEARCH` package, which already provides a collection of time-series similarity and search measures. The `TSFEL` feature extraction pipeline will be extended to optionally accept a query signal, and the new query-based feature functions will internally rely on `TSSEARCH` measures to compute comparison features between each window and the reference.

By embedding this functionality directly into TSFEL's existing feature extraction mechanism, users will be able to seamlessly combine classical handcrafted features and query-based similarity features in a single, consistent workflow, without maintaining separate pipelines for feature extraction and similarity computation.


### Required Skills

- Python 3
- Git and GitHub
- Basic understanding of time-series analysis
- Familiarity with similarity measures and distance metrics for time series

Optional (but useful):
- Knowledge of time-series alignment methods (e.g., DTW, correlation, elastic distances)
- Writing clean, testable, open-source code

### Expected Outcome(s)

- Introduction of a new `TSFEL` feature domain (query) implemented consistently with existing feature sets.
- Extension of the `TSFEL` feature extraction API to optionally accept a reference/query time series.
- Integration of `TSSEARCH` measures as backend operators for query-based feature computation.
- Documentation and examples showing how to extract classical `TSFEL` features together with query-based features in downstream ML pipelines.
- Basic evaluation demonstrating correctness, stability, and practical runtime compared to the current available feature sets.

### References

1. Barandas, M., Folgado, D., Fernandes, L., Santos, S., Abreu, M., Bota, P., ... & Gamboa, H. (2020). TSFEL: Time series feature extraction library. SoftwareX, 11, 100456.

2. Folgado, D., Barandas, M., Antunes, M., Nunes, M. L., Liu, H., Hartmann, Y., ... & Gamboa, H. (2022). Tssearch: Time series subsequence search library. SoftwareX, 18, 101049.