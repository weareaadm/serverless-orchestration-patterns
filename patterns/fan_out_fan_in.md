# Patrón Fan-Out / Fan-In

El patrón Fan-Out / Fan-In es un diseño fundamental de orquestación que se utiliza cuando una única entrada debe dividirse en múltiples tareas paralelas y posteriormente consolidarse en un único resultado.  
Permite un paralelismo masivo al mismo tiempo que mantiene un flujo de trabajo controlado y determinista.

En la arquitectura de orquestación, este patrón es implementado por la capa de orquestación, la cual distribuye el trabajo entre múltiples funciones sin estado (*stateless*) y luego agrega sus resultados.

---

## Modelo Conceptual

```text
               Evento de Entrada
                       ↓
                  Orquestador
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
 Función Tarea A  Función Tarea B  Función Tarea C
        ↓              ↓              ↓
        └──────────────┼──────────────┘
                       ↓
              Paso de Agregación
                       ↓
                Resultado Final
```