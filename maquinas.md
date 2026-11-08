# Registro de máquinas

Fecha: 2026-11-08.

## VM de Pecas (en uso)

- RAM: 7.7 GB total, ~0.5 GB libre. Swap: 1 GB (partición /dev/loop0).
- CPU: 4. Disco: 150 GB, 146 GB libres.
- Es la máquina que corre el puente Groq, el orquestador y las pruebas.
- **No es una máquina persistente de verdad**: el home persiste, pero la
  máquina se reemplaza con los despliegues y los procesos no sobreviven.
  Lo que sobrevive son los archivos del home y las tareas programadas.
- No se puede ampliar el swap: el contenedor bloquea `swapon` aunque
  haya sudo (intentado 2026-11-08, ver `memoria/swap.md`).

## Oracle Always Free ARM (no creada)

- 4 vCPU, 24 GB de RAM, $0. Es la máquina a costo cero que sí corre
  TwIL-8B local (~10 GB en uso) y los loops de agente con memoria real.
- Falta crearla: necesita cuenta de Oracle (con tarjeta para verificar)
  y la capacidad no está garantizada; Oracle puede reclamar instancias
  ociosas.
- No hay ninguna máquina virtual creada por Pecas. Lo que existe es esta
  VM, el puente y el workflow de Actions.

## GitHub Actions (repo público, en uso)

- 7 GB de RAM por corrida, minutos gratis en repos públicos.
- El orquestador de CAPCOT corre diario a las 07:00 CDMX y guarda el
  reporte en el repo. Es el análogo a costo cero de la máquina
  persistente para el coordinador.
