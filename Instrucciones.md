
## 1. Objetivo

Establecer un procedimiento reproducible para preparar proyectos de software que serán desarrollados con asistencia de agentes de IA, como Codex, Gemini CLI, Claude Code u otros.

El objetivo es que cada proyecto cuente con:

- Un PRD que defina los requisitos y restricciones del producto.
    
- Convenciones de código consistentes.
    
- Convenciones operativas para agentes de IA.
    
- Un archivo `AGENTS.md` adaptado al proyecto.
    
- Una configuración `.editorconfig` coherente con el stack.
    

**La preparación debe completarse antes de comenzar a implementar funcionalidades de negocio.**

Este procedimiento está orientado principalmente a proyectos nuevos, pero puede adaptarse a repositorios existentes.

---

## 2. Herramientas opcionales

Considerar las siguientes herramientas únicamente cuando aporten un beneficio concreto:

- **RTK:** [https://github.com/rtk-ai/rtk](https://github.com/rtk-ai/rtk)
    
- **CodeGraph:** [https://github.com/colbymchenry/codegraph](https://github.com/colbymchenry/codegraph)
    

Estas herramientas pueden mejorar determinados flujos de trabajo, pero no son requisitos para inicializar el proyecto.

No instalar herramientas adicionales únicamente para completar este procedimiento.

---

## 3. Inicializar el repositorio

Desde la terminal, ubicarse en el directorio raíz del proyecto.

Si todavía no es un repositorio Git, ejecutar:

```
git init
```

Crear el directorio de documentación:

```
mkdir -p docs
```

Si el repositorio ya existe, conservar su configuración, historial y archivos actuales.

No sobrescribir configuraciones existentes sin revisarlas previamente.

---

## 4. Crear el PRD

Utilizar el archivo:

`Prompt - PRD creation.md`

Ejecutarlo en un asistente de IA para definir progresivamente:

- Objetivo y alcance del producto.
    
- Requisitos funcionales.
    
- Reglas de negocio.
    
- Stack tecnológico.
    
- Arquitectura, cuando corresponda.
    
- Requisitos no funcionales.
    
- Criterios de aceptación.
    
- Funcionalidades fuera de alcance.
    
- Decisiones pendientes.
    

Guardar el resultado en:

`docs/PRD.md`

### Validación del PRD

Antes de continuar, comprobar que:

1. Los objetivos y funcionalidades principales estén definidos.
    
2. Los criterios de aceptación sean verificables.
    
3. Las restricciones técnicas estén identificadas.
    
4. No existan contradicciones importantes sin resolver.
    
5. Las decisiones pendientes estén diferenciadas de las confirmadas.
    

No es obligatorio resolver todas las decisiones técnicas antes de continuar, siempre que las pendientes no impidan generar instrucciones operativas coherentes.

---

## 5. Incorporar las convenciones

Copiar los siguientes archivos dentro de `docs/`:

- `Convenciones para agentes.md`
    
- `Convenciones de código.md`
    

Estos documentos establecen las normas generales del proyecto.

### Responsabilidades

**Convenciones para agentes**

Define cómo deben trabajar los agentes de IA: gestión del contexto, autonomía, planificación, seguridad, ejecución, verificación y comunicación.

**Convenciones de código**

Define estándares de ingeniería: arquitectura, nomenclatura, formato, tipado, contratos, testing, documentación y control de versiones.

**PRD**

Define qué debe construirse, cómo debe comportarse y cuáles son las restricciones específicas del proyecto.

Los tres documentos deben complementarse sin duplicar innecesariamente sus responsabilidades.

---

## 6. Preparar el generador de AGENTS.md

Copiar temporalmente el archivo:

`Prompt - AGENTS.md`

Dentro del directorio:

`docs/`

La estructura esperada antes de ejecutar el generador será:

```
proyecto/
└── docs/
    ├── PRD.md
    ├── Convenciones para agentes.md
    ├── Convenciones de código.md
    └── Prompt - AGENTS.md
```

### Seleccionar el agente

Utilizar preferentemente un modelo con buena capacidad de razonamiento y análisis de código para esta etapa.

El agente debe tener acceso al repositorio y capacidad para leer y modificar los archivos autorizados.

No es necesario utilizar el mismo proveedor o modelo durante todo el desarrollo.

---

## 7. Generar AGENTS.md y .editorconfig

Desde la raíz del proyecto, iniciar el agente de IA mediante su herramienta de terminal.

Proporcionarle la siguiente instrucción:

> Ejecuta el procedimiento contenido en `docs/Prompt - AGENTS.md`. Analiza los tres documentos fuente y el estado real del repositorio. Genera o actualiza exclusivamente `AGENTS.md` y `.editorconfig`, siguiendo las restricciones del prompt. No implementes funcionalidades ni instales dependencias.

El generador debe:

1. Leer los documentos fuente.
    
2. Inspeccionar el repositorio.
    
3. Identificar tecnologías y decisiones confirmadas.
    
4. Consolidar las convenciones aplicables.
    
5. Detectar contradicciones y decisiones pendientes.
    
6. Generar `AGENTS.md` en la raíz.
    
7. Generar `.editorconfig` en la raíz.
    
8. Verificar la coherencia de ambos archivos.
    
9. Informar los resultados y limitaciones.
    

### Condiciones importantes

- No inventar tecnologías, comandos ni configuraciones inexistentes.
    
- No modificar los tres documentos fuente.
    
- No instalar dependencias ni inicializar frameworks.
    
- No generar código de negocio.
    
- No reemplazar decisiones arquitectónicas confirmadas.
    
- No realizar cambios fuera de los dos archivos autorizados.
    

Si aparece una contradicción que impida continuar de forma fiable, resolverla antes de aprobar el resultado.

Los archivos generados deben estar redactados en inglés, conforme al prompt generador.

---

## 8. Revisar los resultados

Antes de comenzar el desarrollo, revisar manualmente:

### AGENTS.md

- Representa correctamente el proyecto.
    
- Respeta los requisitos y restricciones del PRD.
    
- Incorpora las convenciones relevantes.
    
- No contiene instrucciones contradictorias.
    
- No menciona herramientas o comandos ficticios.
    
- Diferencia las decisiones confirmadas de las pendientes.
    
- Incluye reglas de verificación y límites de autonomía.
    
- Utiliza rutas válidas del repositorio.
    

### .editorconfig

- Contiene reglas compatibles con el lenguaje y las herramientas.
    
- Define correctamente codificación y saltos de línea.
    
- No contradice configuraciones de formato existentes.
    

**Importante:** si el proyecto todavía no tiene herramientas de desarrollo instaladas, `AGENTS.md` no debe incluir comandos de verificación inventados.

Estos comandos podrán incorporarse posteriormente cuando exista una configuración real.

No es necesario modificar el repositorio para satisfacer artificialmente una verificación.

---

## 9. Limpiar los archivos temporales

Una vez revisados y aprobados los archivos generados, puede eliminarse la copia temporal de:

`docs/Prompt - AGENTS.md`

Conservar el prompt original en la colección de documentos reutilizables para futuras inicializaciones y actualizaciones.

Mantener en el proyecto:

- `docs/PRD.md`
    
- `docs/Convenciones para agentes.md`
    
- `docs/Convenciones de código.md`
    
- `AGENTS.md`
    
- `.editorconfig`
    

No eliminar documentación fuente necesaria para mantener o regenerar las instrucciones del proyecto.

---

## 10. Registrar la configuración inicial

Antes de realizar el commit, revisar el estado del repositorio:

```
git status
```

Comprobar que no se estén incorporando:

- Credenciales o secretos.
    
- Archivos temporales innecesarios.
    
- Configuraciones personales del entorno.
    
- Dependencias o artefactos generados accidentalmente.
    

Agregar los archivos revisados al área de preparación de Git.

Cuando corresponda, crear el commit inicial:

```
git commit -m "chore: initial project setup and agent conventions"
```

El commit debe incluir únicamente los archivos aprobados para el repositorio.

Si se trabaja sobre un proyecto existente, respetar su estrategia de ramas y commits.

---

## 11. Comenzar el desarrollo

Una vez completada la preparación:

1. Confirmar que el PRD esté disponible.
    
2. Confirmar que `AGENTS.md` refleje las decisiones vigentes.
    
3. Confirmar que `.editorconfig` sea coherente con el proyecto.
    
4. Resolver cualquier contradicción que bloquee la implementación.
    
5. Iniciar las tareas de desarrollo utilizando el agente elegido.
    

A partir de este punto, puede utilizarse un modelo más económico o rápido para tareas rutinarias, reservando modelos de mayor capacidad para problemas complejos.

### Compatibilidad entre agentes

`AGENTS.md` será la referencia operativa común.

Sin embargo, cada herramienta puede utilizar mecanismos diferentes para descubrir o cargar las instrucciones.

Antes de trabajar con un nuevo agente, comprobar que efectivamente está leyendo `AGENTS.md`.

Si requiere configuración adicional, realizarla de acuerdo con la documentación de esa herramienta, procurando mantener una sola fuente de contenido normativo.

---

## 12. Mantenimiento de las convenciones

La configuración inicial no es necesariamente definitiva.

Cuando cambien significativamente los requisitos, la arquitectura o las convenciones técnicas:

1. Actualizar el documento fuente correspondiente.
    
2. Evaluar el impacto sobre `AGENTS.md`.
    
3. Regenerar o actualizar las instrucciones afectadas.
    
4. Conservar las reglas específicas válidas que hayan surgido durante el desarrollo.
    
5. Verificar que los cambios no introduzcan contradicciones.
    

No regenerar `AGENTS.md` indiscriminadamente ante modificaciones menores.

La actualización debe responder a cambios reales en las instrucciones necesarias para trabajar sobre el proyecto.

**Objetivo final:** mantener un entorno de desarrollo asistido por IA consistente, verificable y adaptable, sin depender de un proveedor, modelo o framework específico.
