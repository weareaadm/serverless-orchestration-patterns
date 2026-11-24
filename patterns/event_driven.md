# Patrón de Arquitectura Dirigida por Eventos (Event-Driven)

El patrón Dirigido por Eventos (*Event-Driven*) es la base de los sistemas modernos *serverless* y nativos de la nube (*cloud-native*).  
En lugar de ejecutar flujos de trabajo de forma síncrona o en procesos fuertemente acoplados, los sistemas reaccionan ante **eventos** y los propagan a través de componentes independientes y de bajo acoplamiento (*loosely coupled*).

En el diagrama de arquitectura de orquestación, este patrón comienza en la capa de **Fuentes de Eventos (*Event Sources*)** y activa todo el flujo de trabajo a través del motor de orquestación.

Este diseño permite que los sistemas escalen de forma natural, se mantengan resilientes ante fallos y evolucionen sin afectar a los componentes existentes.

---

## Modelo Conceptual

```text
[ Fuente de Eventos (Event Source) ]
                 ↓
[ Función Sin Estado (Stateless Function) ]
                 ↓
[ Orquestador (Orchestrator) ]
                 ↓
[ Servicios Externos / Almacenamiento / APIs ]
```