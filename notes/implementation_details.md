## Canonical Lossy Compression Pipeline

x
 → Encoder (transform)
 → z (continuous latent)
 → Quantizer
 → q (discrete symbols)
 → Entropy model P(q)
 → Entropy coder
 → bitstream

## Implementation Details

| Compression Stage | TCRAE (TCN–RNN AE) | Tokenization-based Compression |
|------------------|-------------------|--------------------------------|
| Input signal | Continuous time series | Continuous time series |
| Transform coding | Deep TCN encoder + RNN | Lightweight learned encoder |
| Continuous latent `z` | High-precision, dense | Intermediate embeddings |
| Explicit quantization | ❌ Absent (implicit only) | ✔️ Present (tokenizer / codebook) |
| Discrete symbols `q` | ❌ None | ✔️ Finite token vocabulary |
| Entropy modeling | ❌ Not used | ✔️ Learned symbol distribution |
| Entropy coding | ❌ Not used | ✔️ Arithmetic / ANS coding |
| Compression control | Architectural bottleneck | Token granularity + entropy |
| Output representation | Latent tensors | Bitstream |
| Compression metric | Proxy (latent size) | True bits per sample |
| Pipeline completeness | Partial (transform only) | Full neural codec |
