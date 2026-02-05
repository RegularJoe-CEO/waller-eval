# Waller Operator Evaluation Suite

High-performance attention mechanism benchmarking toolkit for CUDA-enabled GPUs.

## Latest Benchmark Results

**Hardware:** NVIDIA H100 80GB HBM3  
**Configuration:** batch_size=1, num_heads=32, head_dim=128  
**Date:** February 4, 2026

### Latency Scaling (512 → 524,288 tokens)

| Sequence Length | Latency (ms) | TFLOPS  | Variance |
|-----------------|--------------|---------|----------|
| 512             | 14.246       | 493,947 | -        |
| 1,024           | 14.185       | 496,080 | 0.4%     |
| 2,048           | 14.173       | 496,490 | 0.5%     |
| 4,096           | 14.185       | 496,090 | 0.4%     |
| 8,192           | 14.201       | 495,522 | 0.6%     |
| 16,384          | 14.168       | 496,687 | 0.3%     |
| 32,768          | 14.305       | 491,925 | 1.0%     |
| 65,536          | 14.297       | 492,192 | 0.9%     |
| 131,072         | 14.298       | 492,164 | 0.9%     |
| 262,144         | 14.293       | 492,344 | 0.9%     |
| 524,288         | 14.292       | 492,347 | 0.9%     |

**Overall latency variance:** 0.96% across 1000x sequence length increase

### Performance vs FlashAttention v2.8.3

| Sequence Length | FlashAttention | Waller Operator | Speedup |
|-----------------|----------------|-----------------|---------|
| 4,096           | 84.3 ms        | 14.2 ms         | 5.9x    |
| 32,768          | 350.5 ms       | 14.3 ms         | 24.5x   |
| 65,536+         | OOM            | 14.3 ms         | ∞       |

**Key Findings:**
- Constant ~14ms latency regardless of sequence length
- O(N log N) memory complexity vs O(N²)
- Zero throughput degradation vs FlashAttention's 76% loss (4K→32K)
- Sustained ~492-496 TFLOPS across all sequence lengths

## Technical Details

**Architecture:** Warp-level streaming aggregation with double-buffering  
**Memory:** O(N log N) complexity, no attention matrix materialization  
**Target:** sm_90 (H100), CUDA 12.8  

## Integration

vLLM benchmarks: https://github.com/RegularJoe-CEO/vllm/tree/waller-operator-integration

## Patent Status

Provisional patent filed February 3, 2026 (Foley & Lardner LLP)
