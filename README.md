# Llama 3.1 Function Calling Fine-tuning

This repository is a fork of `https://github.com/pytorch/torchtitan` to facilitate additional training of Llama 3.1 models for function calling via the `Salesforce/xlam-function-calling-60k` dataset. The setup is optimized for running in a Kubernetes (K8s) environment using SkyPilot, setup for the 3.1 8B model out of the box

The dataset is tokenized into the llama expected format and imported through this hugging face dataset `hooman125/xlam-function-calling-60k-llama3`.

## Quick Start

1. **Customize the SkyPilot Configuration**
   - Edit the `task_multinode.yaml` file to match your Kubernetes environment settings, ensuring the correct parameters for your cluster and resources.

2. **Customize configs / llama3_8b.toml**
    - Refer to official torchtitan documentation on how to setup LLama 8b, 70b, 405b, or plug in other models via scripts/ convert_llama_to_dcp.py

2. **Trigger Training**
   `sky launch sky_train_llama.yaml -c llama31-titan --env WANDB_API_KEY= --env HF_TOKEN=`

3. **Logging**
   - Training progress is logged using TensorBoard for easy monitoring and analysis.

This setup ensures efficient distributed training and logging via 3D parallel / FSDP2, tailored for function calling applications with Llama 3.1. 
