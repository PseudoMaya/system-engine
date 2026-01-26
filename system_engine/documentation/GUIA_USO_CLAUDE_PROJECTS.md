# Guía de Uso: System Engine en Claude Projects

**Versión**: 2.0.0-alpha  
**Fecha**: 2026-01-25  
**Prerequisito**: Cuenta de Claude con acceso a Projects

---

## Introducción

Esta guía te enseña cómo **ejecutar el System Engine v2.0** usando la funcionalidad de **Projects** de Claude. Es la forma recomendada de uso porque permite cargar el meta-engine y los inputs de forma persistente.

**Tiempo estimado de setup**: 10-15 minutos (primera vez)

---

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

- [ ] **Inputs preparados** (ver `README_META_ENGINE_v2.0.md` sección "Checklist de Preparación")
  - [ ] `background_rationale.md` documentado
  - [ ] Grounded Knowledge recopilado y clasificado
  - [ ] (Opcional) `Master_Index.md` si tienes múltiples fuentes

- [ ] **Archivos del System Engine**
  - [ ] `meta_engine_v2.0.yaml`
  - [ ] `README_META_ENGINE_v2.0.md` (recomendado incluir)

---

## Setup Inicial: Crear Proyecto en Claude

### Paso 1: Acceder a Projects

1. Abre Claude (web: claude.ai o app de escritorio)
2. En la barra lateral izquierda, busca la sección **"Projects"**
3. Haz clic en **"+ New Project"** o **"Crear Proyecto"**

```
┌─────────────────────────────────────┐
│ Claude                               │
│                                      │
│  Chats                               │
│  Projects                            │
│    > + New Project         ← AQUÍ   │
│                                      │
│  Settings                            │
└──────────────────────────────────────┘
```

### Paso 2: Configurar el Proyecto

**Nombre del proyecto**: Usa nomenclatura descriptiva según estrategia elegida.

#### Estrategia A: Proyecto Específico (Recomendado para primera vez)
```
Nombre: "SE - [Nombre del Output] - [Fecha]"
Ejemplo: "SE - RSAF - 2026-01-25"
```

**Ventajas**: 
- Clara separación entre materializaciones
- Historial organizado
- No hay riesgo de mezclar inputs

**Desventajas**:
- Duplicas el meta_engine.yaml en cada proyecto

#### Estrategia B: Proyecto Reutilizable (Para usuarios avanzados)
```
Nombre: "System Engine Workspace"
```

**Ventajas**:
- Un solo proyecto
- Meta-engine siempre disponible
- Cambias inputs según necesidad

**Desventajas**:
- Debes limpiar inputs anteriores entre materializaciones
- Historial de chats mezclado

**Recomendación inicial**: Usa **Estrategia A** para tu primera materialización.

### Paso 3: Configurar Project Knowledge

Una vez creado el proyecto, accede a **"Project Knowledge"** (puede aparecer como "Knowledge" o "Archivos del Proyecto").

**Archivos a cargar**:

```
Project Knowledge/
├─ meta_engine_v2.0.yaml           (obligatorio)
├─ README_META_ENGINE_v2.0.md      (recomendado)
├─ background_rationale.md         (obligatorio)
├─ grounded_knowledge_fuente1.md   (obligatorio, al menos 1)
├─ grounded_knowledge_fuente2.pdf  (opcional)
└─ Master_Index.md                 (opcional, útil si >3 fuentes)
```

**Nota importante sobre flat namespace**:
- Claude Projects **no soporta carpetas/directorios**
- Todos los archivos se ven en lista plana
- Por eso usamos nomenclatura descriptiva en nombres de archivo
- Ejemplo: `background_rationale.md`, `grounded_rsaf_paper1.md`, `grounded_rsaf_paper2.md`

**Instrucciones de carga**:

1. Haz clic en **"Add content"** o **"Agregar contenido"**
2. Selecciona **"Upload files"** o **"Subir archivos"**
3. Carga los archivos uno por uno o en bloque
4. Verifica que todos aparezcan listados

```
Project Knowledge (5 archivos)
├─ meta_engine_v2.0.yaml (48 KB)
├─ README_META_ENGINE_v2.0.md (9 KB)
├─ background_rationale.md (3 KB)
├─ grounded_knowledge_rsaf_paper.md (12 KB)
└─ Master_Index.md (1 KB)
```

### Paso 4: (Opcional) Custom Instructions

Si usas **Estrategia B** (proyecto reutilizable), configura instrucciones personalizadas:

1. En configuración del proyecto, busca **"Custom Instructions"**
2. Agrega:

```markdown
Este proyecto ejecuta el System Engine v2.0 para generar Frameworks 
y Metodologías.

Siempre:
- Consultar meta_engine_v2.0.yaml como fuente de gobierno
- Seguir las 5 fases del governance_process
- Usar comandos CHECK, REVISITAR FASE X, CONSOLIDAR según corresponda
```

---

## Iniciar la Construcción: Crear Chat

### Paso 5: Abrir Nuevo Chat en el Proyecto

1. Dentro del proyecto, haz clic en **"New Chat"** o **"Nuevo Chat"**
2. **Nombra el chat** usando nomenclatura estándar:

```
Formato: "[Nombre Output] - SE v2.0 - [Fecha Inicio]"

Ejemplos buenos:
✅ "RSAF - SE v2.0 - 2026-01-24"
✅ "Data Governance Framework - SE v2.0 - 2026-01-26"
✅ "Research Methodology - SE v2.0 - 2026-02-01"

Ejemplos malos:
❌ "Framework"  (muy genérico)
❌ "Chat 1"     (no descriptivo)
❌ "Proyecto"   (confuso)
```

**Por qué es importante el naming**:
- Identificas el chat en historial fácilmente
- Sabes qué versión del meta-engine usaste
- Trazas cuándo iniciaste la construcción

### Paso 6: Prompt de Inicialización

**Usa este template** (copia y adapta):

```markdown
Voy a usar el System Engine v2.0 para generar un [Framework/Methodology] 
sobre [TEMA ESPECÍFICO].

**Archivos cargados en Project Knowledge:**
- meta_engine_v2.0.yaml (motor de gobierno)
- README_META_ENGINE_v2.0.md (referencia de uso)
- background_rationale.md (contexto y objetivos)
- grounded_knowledge_[nombre].md (fuentes documentales)
[- Master_Index.md (índice de fuentes)] ← Solo si aplica

**INSTRUCCIÓN:** 
Ejecuta el meta_engine_v2.0.yaml siguiendo las 5 fases del 
governance_process. Comienza con FASE 1: Context Ingestion.

Lee todos los archivos de input disponibles, valida que sean 
completos según input_analysis_logic, y preséntame un resumen 
de lo que comprendiste antes de avanzar.

Espero tu confirmación de que los inputs son suficientes para 
proceder, o que me indiques qué falta.
```

**Ejemplo concreto**:

```markdown
Voy a usar el System Engine v2.0 para generar un Framework sobre 
Arquitectura de Soluciones empresariales.

**Archivos cargados en Project Knowledge:**
- meta_engine_v2.0.yaml (motor de gobierno)
- README_META_ENGINE_v2.0.md (referencia de uso)
- background_rationale.md (contexto y objetivos)
- grounded_rsaf_paper1.md (paper académico sobre arquitectura)
- grounded_rsaf_best_practices.md (guía de mejores prácticas)
- Master_Index.md (índice de las 2 fuentes)

**INSTRUCCIÓN:** 
Ejecuta el meta_engine_v2.0.yaml siguiendo las 5 fases del 
governance_process. Comienza con FASE 1: Context Ingestion.

Lee todos los archivos de input disponibles, valida que sean 
completos según input_analysis_logic, y preséntame un resumen 
de lo que comprendiste antes de avanzar.

Espero tu confirmación de que los inputs son suficientes para 
proceder, o que me indiques qué falta.
```

**¿Por qué este formato funciona?**
- ✅ Explícito sobre qué archivo YAML usar (Claude ve varios archivos)
- ✅ Lista los recursos disponibles (ayuda a Claude a orientarse)
- ✅ Da comando directo: "Ejecuta fase 1"
- ✅ Pide validación antes de empezar (evita que Claude asuma inputs incompletos)
- ✅ Establece expectativa de diálogo (no generación automática)

---

## Durante la Ejecución: Flujo de Trabajo

### Fase 1: Context Ingestion

**Qué esperar**: Claude leerá tus inputs y te presentará un resumen.

**Tu acción**: 
- Revisa que Claude haya comprendido correctamente
- Si algo falta o es incorrecto, corrígelo ahora
- Cuando estés satisfecho, responde: **`CHECK`**

### Fase 2: Foundations

**Qué esperar**: Claude propondrá 3-7 constraints marcados con símbolos:
```
[⚓] Constraint anclado en fuente
[✓] Constraint validado previamente
[?] Supuesto tentativo
```

**Tu acción**:
- Valida los `[?]` promoviendo a `[✓]` o corrigiendo
- Desafía constraints que no te convenzan (opción B)
- Cuando estés conforme, responde: **`CHECK`**

### Fase 3: Drafting (Iterativo)

**Qué esperar**: Claude propondrá estructura y construirá sección por sección.

**Tus herramientas**:
```
(A) Profundizar en esta sección
(B) Desafiar o criticar lo propuesto  
(C) Avanzar al siguiente paso
(D) Consolidar progreso en artefacto temporal

Comandos:
- CONSOLIDAR: Guarda snapshot temporal
- REVISITAR FASE 2: Si necesitas ajustar constraints
- STATUS: Ver estado actual
```

**Tip**: En sesiones largas (>20 mensajes), usa `CONSOLIDAR` cada 5-7 secciones completadas.

### Fase 4: Stress Testing

**Qué esperar**: Claude te preguntará qué fitness criteria quieres aplicar.

**Tu acción**:
- Selecciona 2-5 criterios según tipo de Output (ver README)
- Claude generará escenarios adversariales
- Si falla algún test → `REVISITAR FASE 3` para refinar
- Si todo pasa → **`CHECK`**

### Fase 5: Finalization

**Qué esperar**: Claude generará **3 archivos**:
1. `[Nombre]_v1.0_MVP.md` (Conceptual Asset)
2. `[nombre]_engine_v1.yaml` (Operational Engine)
3. `CONSTRUCTION_LOG.md` (Trazabilidad)

**Tu acción**:
- Revisa los outputs generados
- Si satisfacen criterios de éxito → **`CHECK FINAL`**
- Claude finalizará presentándote los 3 archivos

---

## Extraer los Outputs

### Método 1: Copiar desde Chat

Los archivos aparecerán en el chat como bloques de código:

```markdown
# Archivo: rsaf_framework_v1.0_MVP.md
[contenido completo]
```

**Cómo extraer**:
1. Haz clic en el botón de copiar (esquina superior derecha del bloque)
2. Pega en tu editor de texto favorito
3. Guarda con el nombre indicado

### Método 2: Pedirle a Claude que consolide

Si los archivos son muy largos y aparecen fragmentados:

```
Por favor, presenta el Conceptual Asset completo en un solo bloque 
de código markdown, seguido del Operational Engine en un bloque YAML, 
y finalmente el Construction Log.
```

### Método 3: Usar funcionalidad de descarga (si disponible)

Algunos chats en Projects permiten descargar archivos directamente. 
Verifica si aparece opción de descarga junto a los bloques de código.

---

## Estrategias Avanzadas

### Reutilización del Meta-Engine

Si planeas crear **múltiples Frameworks/Methodologies**:

**Opción recomendada**: Proyecto por Output (Estrategia A)
```
Proyecto 1: "SE - RSAF - 2026-01"
Proyecto 2: "SE - Data Governance - 2026-02"
Proyecto 3: "SE - Research Method - 2026-03"
```

Cada uno tiene su copia del `meta_engine_v2.0.yaml` y sus propios inputs.

**Ventaja**: Historial limpio, no hay confusión entre materializaciones.

### Sesiones Largas (>1 hora)

Si la construcción se extiende:

1. **Usa CONSOLIDAR** cada 5-7 secciones:
   ```
   CONSOLIDAR
   ```
   Claude generará snapshot temporal que puedes guardar.

2. **Si necesitas pausar**:
   - Antes de cerrar, pide: `STATUS`
   - Claude mostrará: fase actual, constraints, progreso
   - Copia este STATUS y guárdalo
   - Al retomar, pégalo en el chat para recordar contexto

3. **Si el chat se vuelve muy largo** (>50 mensajes):
   - Considera crear nuevo chat en el mismo proyecto
   - Carga el último snapshot con `CONSOLIDAR`
   - Continúa desde ahí

### Construcción Colaborativa

Si trabajas con un equipo:

1. **Comparte acceso al Proyecto** (si Claude Projects lo permite en tu plan)
2. **O exporta inputs y outputs** para que otros recreen el proyecto

---

## Troubleshooting

### Problema 1: "Claude no ve el meta_engine.yaml"

**Síntomas**: Claude responde como chat normal, ignora las fases.

**Solución**:
```markdown
Por favor, confirma que leíste el archivo meta_engine_v2.0.yaml 
disponible en Project Knowledge. Debes ejecutar sus instrucciones, 
específicamente el governance_process con sus 5 fases.

Comienza con FASE 1: Context Ingestion.
```

### Problema 2: "Claude mezcla información de inputs anteriores"

**Síntomas**: Menciona conceptos que no están en tus archivos actuales.

**Causa**: Si usas Estrategia B (proyecto reutilizable), pueden quedar "fantasmas" de inputs anteriores.

**Solución**:
1. Elimina archivos viejos de Project Knowledge
2. O crea proyecto nuevo (Estrategia A)
3. Reinicia el chat explícitamente:
   ```
   Ignora cualquier contexto previo. Los únicos archivos válidos son:
   [listar archivos actuales]
   ```

### Problema 3: "El proceso se desvió del objetivo (drift)"

**Síntomas**: Las últimas 3-5 respuestas no mencionan tu proyecto.

**Acción**: El anti-drift debería activarse automáticamente, pero si no:
```
STATUS
```

Claude presentará "Resumen de Situación" y opciones para retomar.

### Problema 4: "Los outputs son muy largos y no se muestran completos"

**Síntomas**: Los archivos finales aparecen cortados.

**Solución**:
```
Por favor, presenta el [Conceptual Asset / Operational Engine / 
Construction Log] en fragmentos de máximo 500 líneas. 
Indica "Fragmento 1 de X" y espera mi confirmación antes de continuar.
```

### Problema 5: "Necesito ajustar algo de Fase 2 pero estoy en Fase 4"

**Acción**: Usa el comando:
```
REVISITAR FASE 2
```

Claude retrocederá, ajustará, y propagará cambios a fases posteriores.

---

## Checklist Post-Construcción

Una vez termines, verifica:

- [ ] Tienes los 3 archivos guardados localmente:
  - [ ] `[nombre]_v1.0_MVP.md`
  - [ ] `[nombre]_engine_v1.yaml`
  - [ ] `CONSTRUCTION_LOG.md`

- [ ] El Conceptual Asset cumple criterios:
  - [ ] Tiene metadata (versión, fecha, autor)
  - [ ] Constraints están marcados con símbolos
  - [ ] Incluye ejemplos de aplicación
  - [ ] Declara limitaciones conocidas (si hay)

- [ ] El Operational Engine:
  - [ ] Hereda elementos del meta_engine padre
  - [ ] Tiene command_vocabulary especializado
  - [ ] Es sintácticamente válido (YAML)

- [ ] El Construction Log documenta:
  - [ ] Decisiones clave de diseño
  - [ ] Conceptos emergentes
  - [ ] Dead ends intentados
  - [ ] Número de iteraciones por sección

**Si todo está chequeado**: ¡Felicidades! Has completado tu primera materialización del System Engine v2.0.

---

## Próximos Pasos Sugeridos

### Validar el Output

1. **Prueba el Conceptual Asset**:
   - Aplícalo a un caso real
   - ¿Funciona como esperabas?
   - ¿Los constraints tienen sentido en práctica?

2. **Comparte el Construction Log**:
   - Si el proceso fue exitoso, considera compartirlo
   - Ayuda a la evolución del SE
   - Email del autor: oscar.ernesto.maya@gmail.com

### Generar un Output de Nivel 2

Si tu Output era un Framework, úsalo para generar algo más específico:

```
Proyecto: "SE - [Framework Hijo] - [Fecha]"
Project Knowledge:
  ├─ [nombre]_engine_v1.yaml  (el que acabas de generar)
  ├─ [nombre]_v1.0_MVP.md     (ahora es Grounded Knowledge)
  ├─ background_nuevo.md      (contexto del hijo)
  └─ grounded_nuevo_*.md      (fuentes adicionales)
```

Esto valida la recursividad del sistema.

---

## Recursos Adicionales

- **README_META_ENGINE_v2.0.md**: Guía conceptual completa
- **README_SYSTEM_ENGINE.md**: Visión general del proyecto
- **meta_engine_v2_0_REFINEMENT_GUIDE.md**: Decisiones técnicas
- **COMPARISON_v0.1_vs_v2.0.md**: Evolución del sistema

---

## Soporte

**Autor**: Oscar Maya  
**Email**: oscarmaya23@gmail.com

**Reporta problemas con**:
- Descripción detallada del error
- Fase en la que ocurrió
- Screenshot del mensaje de Claude (si aplica)
- Archivos de input que usaste (si son compartibles)

---

**Última actualización**: 2026-01-25  
**Versión de esta guía**: 1.0
