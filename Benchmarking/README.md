
# Maestro Simulator: Mapping File Guide for Llama Results

## Introduction

The Maestro simulator provides a platform to run complex models by simulating their execution across various hardware architectures. The Llama model in particular showcases an optimized framework that utilizes the advanced processing elements (PE) within a PIM (Processing-in-Memory) array and communication via a 2D mesh NoC (Network-on-Chip). Below is an architectural overview of the system, which includes both memory and computation units.

![LEAP Architecture](LEAP_ARCHITECTURE.png)

This architecture enables a highly parallel and low-latency processing framework that integrates both static and dynamic data management systems.

## How to Use Mapping File on Maestro Simulator

### 1. **Prerequisites**
   - Download the Maestro Simulator https://maestro.ece.gatech.edu/docs/build/html/index.html .
   - Ensure you have access to Hugging face repo to have access to the model information in order to identify the model size ex: hidden size, ffn_size..etc.
   - The mapping file should be provided in the correct format as per the model.

### 2. **Running the Mapping File**
     To run the mapping file, follow these steps:

   1. **Create the mapping file**:
      Ensure that the created mapping file consist of attention layers and FFN layers per decoder with proper dataflow. example: https://github.com/BMsemi/Neuromorphic_X1/tree/samarth/Benchmarking/Llama_3_2_1B

   2. **Modify Configuration Parameters**:
      Edit the file based on your simulation requirements in the accelerator file. Pay attention to parameters such as Num_PE, L1/L2 and NoC/offchip               bandwidth to optimize performance.

   3. **Execute the Simulation**:
      Once the mapping file, accelerator file is configured and make sure to include the created mapping file in the .sh file then execute the simulation with       the following command:
      ```bash
      scons -c && scons && ./run_example.sh
      ```

   4. **Monitor the Simulation Output**:
      After the simulation runs, output logs will be generated to provide insights into performance, throughput, and latency.

### 3. **Understanding the Dataflow**
   The dataflow section in each layer maps the spatial and temporal computation across the processing units with considering two levels cluster level 0 and 1.    This step is critical for optimizing performance across the processing units and ensuring minimal latency for each operation.

   - **Spatial Mapping**: Assign chunks of iteration across PE in parallel.
   - **Temporal Mapping**: Assign loop iteraions to the same PE overtime.
   - **Cluster directive**: Groups the PE.

### 4. **Optimizing Throughput and Latency**
   - Use **Parallelism**: Increase the level of parallelism by adjusting the number of processing elements (PE), cluster size and increase/decrease in input/output channels.
   - **Memory Size**: Make sure that memory sizes are optimized for the workload to avoid data transfer bottlenecks.

## Conclusion

The mapping file configuration can greatly influence the performance of your simulation on the Maestro platform. By adjusting the layers and configuration parameters and you can achieve a high throughput and low latency, maximizing the efficiency of the Llama model on your hardware architecture.

## References

- **LEAP**: [LEAP: LLM Inference on Scalable PIM-NoC Architecture with Balanced Dataflow and Fine-Grained Parallelism](https://arxiv.org/abs/2405.02351)
