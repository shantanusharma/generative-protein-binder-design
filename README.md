# NVIDIA BioNeMo Blueprint: Protein Binder Design

![A workflow diagram of the Protein Design Blueprint](docs/Protein_Design_Architecture_Diagram.png)

The NVIDIA BioNeMo Blueprint for protein binder design shows how generative AI and accelerated NIM microservices can be used to design binders to a target protein sequence smarter and faster. This workflow simplifies the process of _in silico_ protein binder design by automatically generating binder sequences and predicted structures for the binder and target.

This Blueprint takes as input a valid amino acid protein sequence. It utilizes the following models:

- **OpenFold3**: An all-atom biomolecular complex structure prediction model (PyTorch implementation of AlphaFold3) that predicts single-chain and multi-chain protein structures, as well as protein complexes with DNA, RNA, and ligands.
- **ProteinMPNN**: a deep learning model for predicting amino acid sequences for protein backbones.
- **RFDiffusion**: a generative model of protein backbones for protein binder design.

Once completed, this Blueprint outputs predicted multimer structures (in PDB format) for the target protein sequence and any generated peptide binders. These binder-target multimeric structures can then be assessed to find binders that effectively bind the target protein.

## System Requirements

The docker compose setup for this NIM Agent Blueprint requires the following specifications:
- At least 100 GB of fast NVMe SSD space
- A modern CPU with at least 24 CPU cores
- At least 64 GB of RAM
- Three or more NVIDIA L40s, A100, or H100 GPUs

## Get Started

- [Deploy with Docker Compose](deploy)
- [Deploy with Helm](protein-design-chart)
- [Source code](src)

## Quick Start
Deploy the blueprint using [Docker Compose](deploy) or [Helm](protein-design-chart)
```bash
cd ./src
jupyter notebook
```

## Set Up With Docker Compose

Navigate to the [deploy](deploy) directory to learn how to start up the NIMs.

## Set up with Helm

Follow the instructions in the [protein-design-chart](protein-design-chart) directory and deploy the Helm chart

## Notebook

An example of how to call each protein binder design step is located in [src/protein-binder-design.ipynb](src/protein-binder-design.ipynb)

## License

**GOVERNING DOWNLOAD TERMS:** Use of this blueprint software is governed by the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license, and enables use of separate open source and proprietary software, models, data and services governed by their respective licenses below:

1. Use of the RfDiffusion NIM is governed by the [NVIDIA Software License Agreement](https://www.nvidia.com/en-us/agreements/enterprise-software/nvidia-software-license-agreement/) and [Product-Specific Terms for AI Products](https://www.nvidia.com/en-us/agreements/enterprise-software/product-specific-terms-for-ai-products/). Use of the model is governed by the [NVIDIA AI Foundation Models Community License Agreement](https://www.nvidia.com/en-us/agreements/enterprise-software/nvidia-ai-foundation-models-community-license-agreement/). Additional Information: [BSD license](https://opensource.org/licenses/BSD-3-Clause).

2. Use of the ProteinMPNN NIM is governed by the [NVIDIA Software License Agreement](https://www.nvidia.com/en-us/agreements/enterprise-software/nvidia-software-license-agreement/) and [Product-Specific Terms for NVIDIA AI Products](https://www.nvidia.com/en-us/agreements/enterprise-software/product-specific-terms-for-ai-products/). Use of the model is governed by the [NVIDIA Community Model License](https://www.nvidia.com/en-us/agreements/enterprise-software/nvidia-community-models-license/). Additional Information: [MIT License](https://github.com/dauparas/ProteinMPNN/blob/8907e6671bfbfc92303b5f79c4b5e6ce47cdef57/LICENSE).

3. Use of the OpenFold3 NIM is governed by the [NVIDIA Software License Agreement](https://www.nvidia.com/en-us/agreements/enterprise-software/nvidia-software-license-agreement/) and [Product-Specific Terms for NVIDIA AI Products](https://www.nvidia.com/en-us/agreements/enterprise-software/product-specific-terms-for-ai-products/). Use of the model is governed by the [NVIDIA Open Model License](https://www.nvidia.com/en-us/agreements/enterprise-software/nvidia-open-model-license/). Additional Information: [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0).

This project will download and install additional third-party open source software projects. Review the license terms of these open source projects before use, found in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
