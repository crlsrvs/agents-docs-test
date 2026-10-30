# Documentación para desarrollo con agentes de IA

Colección reutilizable de prompts y convenciones para preparar proyectos de software desarrollados con asistencia de agentes de IA. Permite definir el producto, establecer criterios de ingeniería y generar instrucciones operativas adaptadas al repositorio.

Está orientada principalmente a proyectos nuevos y puede adaptarse a proyectos existentes, respetando sus configuraciones y decisiones vigentes. Las convenciones se aplican según el lenguaje, la arquitectura y las necesidades de cada proyecto.

## Archivos de la colección

| Archivo | Propósito |
| --- | --- |
| [Instrucciones.md](Instrucciones.md) | Procedimiento completo de preparación, revisión y mantenimiento del proyecto. |
| [Prompt - PRD creation.md](Prompt%20-%20PRD%20creation.md) | Guía de descubrimiento para definir progresivamente el producto y elaborar su PRD. |
| [Convenciones de código.md](Convenciones%20de%20c%C3%B3digo.md) | Estándares técnicos de organización, nomenclatura, formato, contratos, pruebas y control de versiones. |
| [Convenciones para agentes.md](Convenciones%20para%20agentes.md) | Reglas de contexto, autonomía, seguridad, ejecución, verificación y comunicación. |
| [Prompt - AGENTS.md](Prompt%20-%20AGENTS.md) | Procedimiento para generar o actualizar `AGENTS.md` y `.editorconfig` a partir de la documentación y el estado real del proyecto. |

## Orden de uso

Realiza estos pasos en el repositorio del proyecto que quieras preparar. Consulta [Instrucciones.md](Instrucciones.md) para conocer el procedimiento detallado y sus comprobaciones.

1. **Definir el producto.** Utiliza `Prompt - PRD creation.md` con un asistente de IA y guarda el PRD revisado en `docs/PRD.md`.
2. **Incorporar las convenciones.** Copia `Convenciones de código.md` y `Convenciones para agentes.md` dentro de `docs/`.
3. **Preparar el generador.** Copia temporalmente `Prompt - AGENTS.md` dentro de `docs/`.
4. **Generar las instrucciones.** Desde la raíz del proyecto, utiliza un agente con acceso al repositorio y capacidad para editar archivos, con la siguiente instrucción:

   > Ejecuta el procedimiento contenido en `docs/Prompt - AGENTS.md`. Analiza los tres documentos fuente y el estado real del repositorio. Genera o actualiza exclusivamente `AGENTS.md` y `.editorconfig`, siguiendo las restricciones del prompt. No implementes funcionalidades ni instales dependencias.

5. **Revisar el resultado.** Comprueba que los archivos generados respeten el PRD, las convenciones y las herramientas disponibles. Resuelve los conflictos que impidan comenzar el desarrollo.

## Resultado esperado

Después de revisar los archivos generados, el proyecto conserva esta documentación:

```text
proyecto/
├── AGENTS.md
├── .editorconfig
└── docs/
    ├── PRD.md
    ├── Convenciones de código.md
    └── Convenciones para agentes.md
```

La copia temporal de `docs/Prompt - AGENTS.md` puede eliminarse después de aprobar el resultado. Conserva el prompt original en esta colección para futuras actualizaciones.

`AGENTS.md` y `.editorconfig` se generan en inglés; el informe del generador se entrega en español. Antes de desarrollar con un agente, comprueba que su herramienta cargue las instrucciones de `AGENTS.md`.

## Mantenimiento

Cuando cambien los requisitos, la arquitectura o las convenciones, actualiza el documento fuente correspondiente y revisa qué instrucciones de `AGENTS.md` necesitan ajustes. Conserva las reglas específicas del proyecto que sigan siendo válidas.

RTK y CodeGraph son herramientas opcionales, descritas en [Instrucciones.md](Instrucciones.md). La preparación debe utilizar las decisiones confirmadas y las herramientas disponibles en cada proyecto.
