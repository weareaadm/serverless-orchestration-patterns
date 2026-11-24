# Patrón de Manejo de Errores y Dead Letter Queue (DLQ)

En los sistemas distribuidos y *serverless*, los fallos no son excepciones; son una parte esperada de la operación normal.  
El patrón de Manejo de Errores (*Error Handling*) garantiza que los fallos sean **visibles, rastreables, recuperables y aislados**, en lugar de ser ignorados silenciosamente o provocar inestabilidad en todo el sistema.

En la arquitectura de orquestación, este patrón está representado por el **flujo de Eventos de Error** (*Error Events flow*) y la **Cola de Mensajes Fallidos (*Dead Letter Queue* - DLQ)**.

---

## Modelo Conceptual

```text
Ejecución de la Tarea
     ↓
  Fallo Detectado
     ↓
Política de Reintentos Aplicada
     ↓
Éxito → Continuar Flujo de Trabajo
     ↓
Fallo Tras los Reintentos
     ↓
Cola de Mensajes Fallidos (DLQ)
```