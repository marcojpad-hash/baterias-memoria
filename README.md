> **MEMORIA COMPARTIDA OBLIGATORIA:** Antes de cualquier trabajo, cualquier modelo debe leer [AGENTS.md](AGENTS.md), [el protocolo transversal](https://github.com/marcojpad-hash/memoria-compartida/blob/main/PROTOCOLO_MEMORIA_COMPARTIDA_OBLIGATORIA.md) y [el índice de memoria](https://github.com/marcojpad-hash/memoria-compartida/blob/main/INDICE.md); consultar los hechos pertinentes y sincronizar los hechos durables al terminar. No empezar desde la memoria conversacional.

# baterias-memoria (privado)

La batería de memoria: el cableado que alimenta de memoria al stack de
agente a costo cero. No genera RAM: la memoria viene de las máquinas. Lo
que guarda este repo es el registro de qué máquina tiene cuánta memoria,
qué modelo necesita cuánta, y cómo poner una máquina en línea.

## Las máquinas (verificado 2026-11-08)

| Máquina | RAM | Estado |
|---|---|---|
| VM de Pecas | 7.7 GB total, ~0.5 GB libre; swap 1 GB | en uso; no se puede ampliar el swap (el contenedor bloquea `swapon`) |
| Oracle Always Free ARM | 4 vCPU, 24 GB RAM | no creada; es la máquina a costo cero que sí corre TwIL-8B |
| GitHub Actions (repo público) | 7 GB por corrida | en uso para el orquestador (diario 07:00 CDMX) |

## Los modelos y su memoria

| Modelo | Memoria en uso | Dónde cabe |
|---|---|---|
| openai/gpt-oss-120b (por Groq) | 0 local (corre en la API) | en cualquier máquina |
| openai/gpt-oss-20b (por Groq) | 0 local (corre en la API) | en cualquier máquina |
| TwIL-8B (local, Q4_K_M) | ~10 GB | Oracle ARM 24 GB; NO cabe en la VM de Pecas |
| gpt-oss:20b (Ollama local) | ~13 GB descarga | Oracle ARM 24 GB |

## Qué hay aquí

- `maquinas.md` — registro de máquinas.
- `modelos-memoria.md` — requisitos de memoria por modelo.
- `memoria/swap.md` — el intento de memoria virtual bloqueado.

## Regla

Un repo es almacenamiento, no RAM. Más repos dan más espacio en disco,
no más memoria. La memoria vive en la máquina que corre el trabajo.
