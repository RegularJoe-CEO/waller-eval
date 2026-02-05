# Waller Operator v1.0 - Memory-Efficient Attention for LLM Inference

The Waller Operator eliminates O(N²) memory bottlenecks in transformer attention, achieving **O(N log N) memory** and **constant ~14ms latency** across 4K-2.6M token sequences on NVIDIA H100.

## 🚀 Quick Start

Download `waller_eval_x86` and run:

```bash
chmod +x waller_eval_x86
./waller_eval_x86 --help
```

**Adjust CLI parameters** for custom sequence lengths, batch sizes, head dimensions, and more:

```bash
./waller_eval_x86 --seq_len 131072 --batch_size 1 --num_heads 32 --head_dim 128
```

**Requirements:**
- NVIDIA H100 GPU (sm_90) or A100 (sm_80)
- CUDA 12.8
- x86_64 Linux

## 📊 Benchmark Results

See full results at: `waller-eval/RESULTS.md`

**Key Performance:**
- **Memory:** O(N log N) vs O(N²) standard attention
- **Latency:** ~14ms constant across 4K-2.6M tokens
- **Equivalence:** Mathematically identical to standard softmax attention
- **No retraining required**

## 🔬 Technical Details

- Built: Feb 2026
- Platform: x86_64 Linux
- CUDA Compute: sm_80 (A100), sm_90 (H100)
- Size: 0.97 MB

## 📜 Patent & Licensing

**Patent Pending:** US Provisional Application filed Feb 2026  
**Title:** Memory-Efficient Attention Computation System and Method

**Licensing inquiries:** e@ewaller.com

## 🏢 Waller Systems 

Breakthrough IP in AI inference, energy efficiency, and materials science.

**Contact:** e@ewaller.com  
**Web:** luxiedge.com 
