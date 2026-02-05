# Waller Operator - Evaluation Binary

Self-running demo proving O(N log N) pyramid attention at extreme sequence lengths.

## Requirements

- Linux (Ubuntu 20.04 or later)
- NVIDIA GPU with 24GB+ VRAM
- CUDA drivers installed

## Which file to use

| File | Hardware |
|------|----------|
| waller_eval_x86 | H100, H200, A100, or any x86 datacenter GPU |
| waller_eval_arm64 | GH200 (Grace Hopper) |

## Running it

chmod +x waller_eval_x86
./waller_eval_x86

Takes about 5 minutes. No input needed.

## What to watch

The "Mem" column stays under 4GB even as sequence length passes 1 million tokens. The "Std" column shows what standard attention would require. When you see "1099 GB [IMPOSSIBLE]", that's the point.

## Contact

e@ewaller.com
