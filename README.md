<table>
  <tr>
    <td align="center"><img src="bm-lab-logo-white.jpg" alt="BM LABS Logo" width="200"/></td>
    
</table>

# BM Labs Model Compilation and Execution

At **BM Labs**, we don’t maintain a curated model zoo. Instead, we recommend customers select or train their own models and use our automated tools to generate executable Dataflow Program (DFP) files (`.dfp`).

### Key Points:
- **No Model Modifications**:  
  Our tools compile models without altering the original source (no pruning or distillation), ensuring high accuracy.

- **High Performance**:  
  The compiled DFPs achieve high utilization of **BM Labs** hardware without needing retraining or special datasets.

- **Open-Source Performance Estimation**:  
  We leverage open-source tools for accurate performance estimation, ensuring the best optimization for your hardware.

- **Public Model Repository**:  
  A collection of publicly available models is tested and optimized on **BM Labs** hardware. You can download or recreate these models using our tools.

### Customization:
- **Model Optimization**:  
  Customers can choose to prune, quantize, or distill models to balance accuracy and performance before compiling.

### How to Get Started:
1. **Select or Train a Model**  
2. **Estimate Performance Using Open-Source Tools**  
3. **Compile with BM Labs Tools**  
4. **Download and Run the DFP**
