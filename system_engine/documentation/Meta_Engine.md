# README: Meta-Engine v2.0

**Versión**: 2.0.0-alpha  
**Fecha**: 2026-01-25  
**Archivo**: `meta_engine_v2.0.yaml`  
**Proyecto**: System Engine (Materialización del Programa GCD)

---

## Descripción

El **meta_engine_v2.0.yaml** es el núcleo operativo del System Engine. Es un motor agnóstico para el diseño iterativo de frameworks y metodologías, basado en la filosofía del Segundo Wittgenstein.

### ¿Qué hace este motor?

Orquesta la construcción colaborativa entre Usuario e IA de:
1. **Conceptual Asset**: Framework o Metodología (documento .md)
2. **Operational Engine**: Motor operacional para ejecutar el asset (archivo .yaml)
3. **Construction Diary**: Trazabilidad del proceso (CONSTRUCTION_LOG.md)

---

## Fundamento Filosófico

### Segundo Wittgenstein: Lenguaje como Acción

Este YAML **no describe** cómo la IA "piensa", sino que **prescribe** cómo la IA debe "componer".

**Conceptos clave**:
- **Juegos de Lenguaje**: Cada tarea es un juego con sus propias reglas
- **Gramática Prescriptiva**: Definir movimientos válidos, no contenidos fijos
- **Sistema de Bisagras**: Proposiciones que deben permanecer fijas
- **Parecido de Familia**: Conceptos relacionados sin esencia común
- **Seguimiento de Reglas**: Dominar una técnica, no interpretar símbolos

### Anti-Patrón

❌ **Evitar**: La ilusión de automatización total  
✅ **Recordar**: El humano aporta Forma de Vida (propósito y validación ética)

---

## Antes de Usar: Checklist de Preparación

### ✅ Requisitos Obligatorios

- [ ] **Background & Rationale documentado**
  - [ ] ¿Por qué necesitas este framework/metodología?
  - [ ] ¿Cómo sabrás que está terminado?
  - [ ] ¿Quiénes son los stakeholders?
  - [ ] ¿Qué NO puedes hacer bajo ninguna circunstancia?

- [ ] **Grounded Knowledge recopilado**
  - [ ] Al menos 1 fuente primaria del dominio
  - [ ] Fuentes clasificadas: primary, secondary, supporting
  - [ ] Master_Index.md si son múltiples archivos

- [ ] **Claridad sobre el tipo de Output**
  - [ ] ¿Es un Framework (estructura conceptual)?
  - [ ] ¿O es una Methodology (proceso paso a paso)?

- [ ] **Expectativas realistas**
  - [ ] Entiendes que NO es automatización instantánea
  - [ ] Estás dispuesto a iterar múltiples veces (3-10+ iteraciones típicas)
  - [ ] Estás listo para tomar decisiones en conflictos
  - [ ] Tienes tiempo para un proceso de 1-4 horas (según complejidad)

---

## Guía de Uso

### 1. Preparación de Inputs

Coloca tus archivos en directorios con estructura flat:

```
/inputs/
  /background_rationale/
    contexto.md
    objetivos.md
  
  /grounded_knowledge/
    Master_Index.md
    fuente_primaria_1.md
    fuente_primaria_2.pdf
    fuente_secundaria_1.md
```

### 2. Ejecución del Proceso

El meta-engine guía a través de **5 fases**:

```
FASE 1: Ingestión de Contexto
↓ [CHECK para avanzar]

FASE 2: Fundamentos y Bisagras
↓ [CHECK para avanzar]

FASE 3: Construcción Iterativa
↓ [CHECK para avanzar]

FASE 4: Stress Testing
↓ [CHECK para avanzar]

FASE 5: Finalización
```

### 3. Comandos Disponibles

| Comando | Uso | Efecto |
|---------|-----|--------|
| `CHECK` | Validar fase actual | Avanza al siguiente Gate |
| `REVISITAR FASE X` | Regresar a fase anterior | Retrocede manteniendo aprendizaje |
| `CONSOLIDAR` | Guardar progreso | Genera snapshot temporal |
| `RESOLVE A/B/C` | Resolver conflicto | Aplica opción seleccionada |
| `STATUS` | Ver estado | Muestra fase, constraints, progreso |

### 4. Interacción Típica

Después de cada respuesta del sistema, recibirás opciones:

```
(A) Profundizar en esta sección
(B) Desafiar o criticar lo propuesto
(C) Avanzar al siguiente paso
(D) Consolidar progreso en artefacto temporal
```

No todas las opciones aparecen siempre; el sistema adapta según contexto.

---

## Sistema de Clasificación de Constraints

Durante la Fase 2, verás constraints marcados con símbolos:

- `[?]` **Tentative**: Supuesto razonable sin validar
- `[✓]` **Accepted**: Usuario validó explícitamente
- `[⚓]` **Bisagra**: Anclado en Grounded Knowledge, no negociable

**Ejemplo**:
```
CONSTRAINTS PROPUESTOS:
[⚓] El framework debe ser tecnológicamente agnóstico (fuente: paper X, §3)
[✓] Máximo 6 conceptos primarios (validado por Usuario en iteración 3)
[?] Asumimos usuarios con 3+ años de experiencia en arquitectura
```

**Tu rol**: Validar los `[?]` promoviendo a `[✓]` o corrigiendo.

---

## Fitness Criteria (Fase 4: Stress Testing)

Selecciona **2-5 criterios** para validar tu Output:

| Criterio | Pregunta Clave | Recomendado Para |
|----------|----------------|------------------|
| **Usability** | ¿Un novato puede usarlo sin ayuda? | Methodologies ⭐ |
| **Completeness** | ¿Cubre todos los aspectos críticos? | Ambos ⭐ |
| **Coherence** | ¿Las partes son mutuamente consistentes? | Frameworks ⭐ |
| **Evolvability** | ¿Se puede extender sin romper? | Frameworks ⭐ |
| **Resilience** | ¿Maneja casos extremos elegantemente? | Ambos ⭐ |

**No es obligatorio aplicar todos**. El sistema te guiará según el tipo de Output.

---

## Outputs Generados

Al finalizar, recibirás **3 archivos**:

1. **`[Nombre]_v1.0_MVP.md`**: Conceptual Asset
   - Metadata + Philosophical Foundation
   - Core Content (Ontología o Proceso)
   - Application Guide
   - Known Limitations (si aplica)

2. **`[nombre]_engine_v1.yaml`**: Operational Engine
   - Hereda elementos del meta-engine padre
   - Especializa command_vocabulary al dominio
   - Instrucciones operacionales

3. **`CONSTRUCTION_LOG.md`**: Trazabilidad
   - Decisiones de diseño y rationale
   - Conceptos emergentes
   - Iteraciones por sección
   - Dead ends documentados

---

## Expectativas Realistas

### ✅ Lo que este sistema SÍ hace:

- Estructurar el proceso de diseño conceptual
- Detectar conflictos y ambigüedades temprano
- Garantizar coherencia entre inputs y outputs
- Documentar trazabilidad completa del proceso
- Generar herramientas operativas (no solo documentos)

### ❌ Lo que este sistema NO hace:

- Automatizar completamente el pensamiento
- Generar contenido sin fuentes documentales
- Tomar decisiones éticas o estratégicas por ti
- Producir resultados instantáneos
- Funcionar sin participación activa del Usuario

**Metáfora**: El meta-engine es tu **socio de diseño**, no un generador mágico.

---

## Para Usuarios Avanzados

Si ya has usado este sistema antes, puedes:

### Optimizaciones
- Ajustar fitness_criteria según experiencia previa
- Proponer estructura de Output basada en materializaciones anteriores
- Usar `CONSOLIDAR` estratégicamente para sesiones largas
- Referir a CONSTRUCTION_LOGs de proyectos previos para evitar dead ends

### Contribución a la Comunidad
- Comparte tu CONSTRUCTION_LOG como caso de estudio
- Documenta patrones de iteración que funcionaron bien
- Reporta limitaciones o mejoras al meta_engine.yaml
- Contribuye a la evolución del Programa GCD

---

## Filosofía de Evolución

Este Meta-Engine v2.0 es una **materialización viva** del Programa GCD.

> *"El lenguaje es uso en contexto."* — Wittgenstein

El sistema mejora conforme:
1. Más Outputs sean generados
2. Más patrones sean identificados
3. Más usuarios contribuyan sus Construction Logs

**Futuras versiones** incorporarán:
- Patrones de iteración documentados
- Mejoras al conflict_resolution basadas en casos reales
- Nuevos fitness criteria descubiertos en práctica
- Refinamientos a la inheritance_protocol

---

## Herencia Recursiva

Los Operational Engines que este meta-engine genera pueden, a su vez, generar sistemas hijo:

```
Meta-Engine v2.0 (Nivel 0)
    ↓ genera
RSAF + rsaf_engine_v1.yaml (Nivel 1)
    ↓ puede generar
Microservices Framework + micro_engine_v1.yaml (Nivel 2)
```

**Elementos que siempre se heredan**:
- Gate protocol (CHECK, REVISITAR FASE, etc.)
- Anti-drift mechanism
- Interaction parameters (tono, formato, idioma)
- Input analysis logic

**Elementos que se especializan**:
- Command vocabulary (ANALYZE, MAP, SYNTHESIZE son del dominio)
- Mode selector (puede refinar juegos de lenguaje)

---

## Resolución de Problemas

### "El sistema detectó drift pero estoy en el tema correcto"

Si recibes un "Resumen de Situación" y consideras que NO hay desviación:
- Explica cómo tu comentario se relaciona con el objetivo
- El sistema registrará "false positive" y continuará
- No se interrumpirá de nuevo en ese hilo

### "Los constraints propuestos no reflejan mis necesidades"

Durante Fase 2:
- Usa opción (B) "Desafiar o criticar"
- El sistema aplicará conflict_resolution protocol
- Puedes `REVISITAR FASE 1` si el Background no era claro

### "El Output no pasó fitness criteria"

- Comando: `REVISITAR FASE 3` para refinar
- O documenta la limitación como "Known Limitation"
- No todo Output puede ser perfecto; la honestidad es parte del rigor

---

## Soporte y Contacto

**Autor**: Oscar Maya  
**Email**: oscarmaya23@gmail.com  
**Proyecto**: System Engine (GCD)

**Documentación adicional**:
- `README_SYSTEM_ENGINE.md` - Visión general del proyecto
- `meta_engine_v2_0_REFINEMENT_GUIDE.md` - Decisiones de diseño técnico
- `COMPARISON_v0.1_vs_v2.0.md` - Evolución del sistema

---

**Última actualización**: 2026-01-25  
**Licencia**: [Por definir según decisión del autor]
