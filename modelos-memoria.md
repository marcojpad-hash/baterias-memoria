# Requisitos de memoria por modelo

Fecha: 2026-11-08.

## Por API (0 de RAM local)

| Modelo | Dónde corre | RAM local |
|---|---|---|
| openai/gpt-oss-120b (Groq) | API de Groq | 0 |
| openai/gpt-oss-20b (Groq) | API de Groq | 0 |
| gemini-3-flash-preview (Gemini) | API de Google | 0 |

Estos son los que alimentan al agente hoy: no necesitan memoria local,
pero tienen límite de velocidad (Groq: 8.000 TPM).

## Local (necesitan RAM de verdad)

| Modelo | Pesos | Memoria en uso | Dónde cabe |
|---|---|---|---|
| TwIL-8B (Q4_K_M) | ~5 GiB | ~10 GB | Oracle ARM 24 GB |
| TwIL-8B (bf16) | ~16.4 GiB | más de 16 GB | Oracle ARM 24 GB |
| gpt-oss:20b (Ollama) | ~13 GB descarga | ~13 GB o más | Oracle ARM 24 GB |

Ninguno cabe en la VM de Pecas (7.7 GB total, ~0.5 GB libre).
