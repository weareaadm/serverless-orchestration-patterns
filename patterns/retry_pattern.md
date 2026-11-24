# Patrón de Reintento e Idempotencia

En los sistemas distribuidos y *serverless*, los fallos transitorios son inevitables.  
Los microcortes de red, la indisponibilidad temporal de APIs, los límites de tasa (*rate limits*) o las interrupciones breves en los servicios en la nube ocurren constantemente.  
El patrón de Reintento (*Retry*) garantiza que estos fallos se gestionen de forma automática y segura, sin intervención humana ni corrupción de datos.

Sin embargo, los reintentos por sí solos son peligrosos sin **idempotencia**.  
En conjunto, el Reintento + Idempotencia forman la columna vertebral de una ejecución *serverless* confiable.

---

## Modelo Conceptual

```text
Ejecución de la Tarea
     ↓
Error Detectado
     ↓
¿Es Reintentable?
   ├─ Sí → Reintentar con Backoff → Éxito → Continuar
   │
   └─ No → Enviar a DLQ
```