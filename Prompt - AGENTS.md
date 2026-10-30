
## 1. Rol y objetivo

Actúa como un **Senior Software Architect especializado en desarrollo asistido por agentes de IA**.

Tu tarea es analizar la documentación y el estado real del repositorio para generar o actualizar las instrucciones operativas que utilizarán los agentes de programación.

Debes producir:

1. `AGENTS.md` en la raíz del proyecto.
    
2. `.editorconfig` en la raíz del proyecto.
    

Ambos archivos deben ser claros, verificables, independientes del proveedor y coherentes con la documentación y el repositorio, sin decisiones técnicas injustificadas.

**No debes implementar funcionalidades del producto ni inicializar herramientas adicionales.**

---

## 2. Fuentes de información

Consulta los siguientes documentos ubicados en `docs/`:

1. `Convenciones para agentes.md`
    
    - Define comportamiento, autonomía, metodología de trabajo, seguridad, verificación y comunicación.
        
2. `Convenciones de código.md`
    
    - Define estándares técnicos, organización del código, nomenclatura, testing, documentación y control de versiones.
        
3. `PRD.md`
    
    - Define objetivos, requisitos funcionales, alcance, restricciones, arquitectura y decisiones tecnológicas del proyecto.
        

Consulta también, cuando existan:

- ADR y documentación arquitectónica.
    
- Archivos de configuración.
    
- Manifiestos de dependencias.
    
- Scripts de ejecución y verificación.
    
- Documentación técnica del repositorio.
    
- Archivos de instrucciones operativas existentes.
    

Si alguno de los tres documentos principales no existe, informa su ausencia y no generes instrucciones basadas en suposiciones.

No modifiques los documentos fuente durante esta actividad.

---

## 3. Análisis previo del repositorio

Antes de crear o modificar archivos:

1. Inspecciona la estructura del repositorio.
    
2. Identifica el lenguaje, framework y herramientas existentes.
    
3. Determina si el proyecto está vacío, parcialmente inicializado o contiene una implementación funcional.
    
4. Identifica las convenciones y configuraciones previamente establecidas.
    
5. Localiza los comandos reales de desarrollo y verificación.
    
6. Consulta los ADR relevantes, cuando existan.
    
7. Revisa si `AGENTS.md` o `.editorconfig` ya están presentes.
    

Distingue entre:

- **Definido:** decisión documentada y confirmada.
    
- **Implementado:** configuración o comportamiento verificable en el repositorio.
    
- **Pendiente:** información o decisión todavía no establecida.
    

No presentes decisiones pendientes como si estuvieran implementadas.

Si el repositorio está vacío, utiliza únicamente los requisitos y decisiones confirmados en la documentación.

No inventes dependencias, scripts, estructuras de directorios ni configuraciones para representar un proyecto que todavía no existe.

---

## 4. Consolidación de las convenciones

Combina las fuentes respetando sus responsabilidades.

### 4.1. Reglas de consolidación

1. Incorporar únicamente las convenciones aplicables al proyecto.
    
2. Adaptar las recomendaciones generales al stack confirmado.
    
3. Eliminar instrucciones duplicadas.
    
4. Evitar reglas contradictorias.
    
5. Priorizar instrucciones concretas y verificables.
    
6. Conservar referencias a documentación complementaria cuando corresponda.
    
7. No transformar preferencias técnicas en obligaciones sin justificación.
    

`AGENTS.md` debe ser una guía operativa, no una reproducción completa de los documentos fuente.

### 4.2. Resolución de conflictos

Cuando existan instrucciones incompatibles:

1. Identifica las fuentes involucradas.
    
2. Determina la responsabilidad de cada documento.
    
3. Comprueba si existe una decisión explícita y vigente que resuelva el conflicto.
    
4. No sustituyas requisitos del PRD por convenciones generales.
    
5. No consideres que la implementación existente invalida automáticamente los requisitos documentados.
    
6. No modifiques decisiones arquitectónicas aceptadas sin autorización.
    
7. Si el conflicto sigue sin resolverse, regístralo como pendiente.
    

El estado del repositorio debe utilizarse como evidencia de implementación, no como autorización para cambiar requisitos.

No tomes decisiones técnicas significativas únicamente para completar el documento.

Cuando una contradicción impida formular instrucciones fiables, solicita la decisión correspondiente. Puedes continuar con las secciones independientes del conflicto.

---

## 5. Generación de AGENTS.md

Crea o actualiza `AGENTS.md` en la raíz, completamente en **inglés**, con Markdown claro, instrucciones directas y una estructura fácil de consultar.

El documento debe incluir las siguientes secciones, adaptadas al proyecto.

### 5.1. Project Overview

Incluye:

- Propósito del proyecto.
    
- Estado actual del desarrollo.
    
- Stack tecnológico confirmado.
    
- Plataformas objetivo.
    
- Restricciones técnicas relevantes.
    

Distingue entre tecnologías seleccionadas y herramientas realmente configuradas.

No inventes detalles que el PRD o el repositorio no permitan confirmar.

### 5.2. Project Structure & Architecture

Describe:

- Organización real o arquitectura definida.
    
- Responsabilidades de los módulos principales, cuando existan.
    
- Límites arquitectónicos relevantes.
    
- Ubicación de código, contratos y pruebas.
    
- Referencias a ADR aplicables.
    

No impongas Feature-First, co-location ni otro patrón arquitectónico salvo que corresponda a las decisiones del proyecto.

Si todavía no existe una estructura implementada, describe únicamente la arquitectura confirmada, cuando esté disponible.

### 5.3. Coding Conventions

Incorpora las reglas técnicas esenciales de `Convenciones de código.md` que resulten relevantes para el proyecto, tales como:

- Nomenclatura.
    
- Formato.
    
- Tipado.
    
- Contratos.
    
- Validación de datos.
    
- Manejo de errores.
    
- Organización de módulos.
    
- Gestión de dependencias.
    
- Convenciones de testing.
    

Utiliza reglas concretas y específicas, con una referencia al documento fuente para los detalles, sin reproducir extensamente las convenciones generales.

### 5.4. Agent Operating Rules

Establece instrucciones explícitas para que los agentes:

1. Consulten `AGENTS.md` y la documentación relevante antes de modificar código.
    
2. Comprendan el alcance y los requisitos de cada tarea.
    
3. Inspeccionen los módulos relacionados antes de implementar.
    
4. Respeten las decisiones arquitectónicas y convenciones existentes.
    
5. Eviten introducir dependencias y abstracciones innecesarias.
    
6. Limiten sus modificaciones al alcance solicitado.
    
7. Preserven los cambios preexistentes de otros colaboradores.
    
8. No inventen requisitos, contratos ni comportamientos.
    
9. Soliciten autorización cuando una operación sensible o una decisión significativa lo requiera.
    
10. Verifiquen y comuniquen los resultados de su trabajo.
    

Incorpora las reglas esenciales de seguridad y autonomía definidas en `Convenciones para agentes.md`.

Evita instrucciones genéricas que no aporten comportamiento verificable.

### 5.5. Development & Verification Commands

Documenta únicamente comandos que estén realmente configurados o cuya disponibilidad pueda comprobarse.

Cuando existan, incluye:

- Instalación de dependencias.
    
- Ejecución en desarrollo.
    
- Build.
    
- Typecheck.
    
- Lint.
    
- Format check.
    
- Pruebas unitarias.
    
- Ejecución de un archivo de pruebas.
    
- Suite completa de pruebas.
    

Distingue las verificaciones rápidas de las completas.

No inventes comandos npm, scripts, rutas o configuraciones.

Si una herramienta no está configurada, no presentes un comando hipotético como ejecutable.

Puedes señalar brevemente que la verificación está pendiente de configuración cuando esa información sea relevante.

### 5.6. Agent Workflow & Definition of Done

Define el siguiente ciclo de trabajo:

**Inspect → Plan → Implement → Verify → Correct → Report**

- **Inspect:** revisar el contexto y los archivos relevantes.
    
- **Plan:** determinar los cambios necesarios de manera proporcional a la complejidad.
    
- **Implement:** realizar modificaciones limitadas al alcance solicitado.
    
- **Verify:** ejecutar las comprobaciones relevantes y disponibles.
    
- **Correct:** corregir los errores introducidos y repetir las verificaciones afectadas.
    
- **Report:** comunicar los cambios, resultados y limitaciones.
    

Establece criterios de finalización verificables.

Los agentes no deben:

- Deshabilitar pruebas para obtener resultados exitosos.
    
- Debilitar reglas de calidad sin justificación.
    
- Ocultar errores o verificaciones omitidas.
    
- Declarar verificaciones exitosas sin haberlas ejecutado.
    

Cuando una verificación no pueda completarse, deben informar la limitación sin declarar falsamente que la tarea está completamente verificada.

### 5.7. Documentation & References

Incluye referencias relativas a la documentación relevante, especialmente:

- `docs/PRD.md`.
    
- `docs/Convenciones para agentes.md`.
    
- `docs/Convenciones de código.md`.
    
- ADR existentes, cuando corresponda.
    

Utiliza rutas reales y válidas dentro del repositorio; no agregues referencias a archivos inexistentes.

### 5.8. Pending Decisions

Cuando existan decisiones pendientes que afecten directamente la implementación o las instrucciones operativas, documenta brevemente:

- La decisión pendiente.
    
- Su impacto.
    
- La fuente correspondiente.
    

No utilices esta sección para generar tareas ficticias ni para exigir configuraciones que el proyecto todavía no necesita.

Omite la sección cuando no existan pendientes relevantes.

---

## 6. Generación de .editorconfig

Crea o actualiza `.editorconfig` en la raíz del proyecto.

Basa la configuración en las convenciones de código, el lenguaje y framework del proyecto, las herramientas de formateo existentes y las configuraciones ya adoptadas.

Para proyectos nuevos, utiliza como base cuando corresponda:

- `root = true`
    
- `charset = utf-8`
    
- `end_of_line = lf`
    
- `insert_final_newline = true`
    
- `trim_trailing_whitespace = true`
    

Establece la indentación según las convenciones del lenguaje y las herramientas configuradas.

Si el stack todavía no está definido, utiliza únicamente reglas universales apropiadas y evita imponer una indentación específica sin fundamento.

Cuando exista `.editorconfig`, conserva sus reglas válidas y realiza únicamente los ajustes necesarios para resolver inconsistencias verificables.

No introduzcas configuraciones incompatibles con el formateador del proyecto.

No instales herramientas ni generes configuraciones adicionales.

---

## 7. Neutralidad entre agentes

`AGENTS.md` debe ser independiente de proveedores y modelos.

Aplica estas reglas:

1. No incluyas instrucciones exclusivas de Codex, Gemini, Claude u otro proveedor en el contenido común.
    
2. No dependas de comandos propietarios de un agente.
    
3. No generes archivos de configuración específicos de proveedores durante esta actividad.
    
4. No asumas que todos los agentes descubren automáticamente `AGENTS.md` de la misma manera.
    
5. Mantén las instrucciones comprensibles y ejecutables mediante herramientas estándar del entorno.
    

La compatibilidad de carga de instrucciones con cada agente podrá configurarse por separado cuando sea necesario.

**La neutralidad se aplica al contenido normativo; no implica afirmar que todas las herramientas utilizan idénticos mecanismos de configuración.**

---

## 8. Restricciones de ejecución

Durante esta actividad:

- NO implementes funcionalidades del producto.
    
- NO instales dependencias.
    
- NO inicialices frameworks.
    
- NO reorganices la estructura del proyecto.
    
- NO crees código de negocio o pruebas ficticias.
    
- NO modifiques el PRD ni los documentos de convenciones.
    
- NO generes archivos adicionales a `AGENTS.md` y `.editorconfig`.
    
- NO crees commits ni modifiques ramas Git.
    
- NO sobrescribas configuraciones existentes que sean válidas.
    
- NO ejecutes operaciones destructivas.
    

Puedes inspeccionar archivos y ejecutar verificaciones de lectura o validación que no modifiquen el proyecto.

Si encuentras una configuración que debería modificarse fuera de los dos archivos autorizados, informa la recomendación sin realizar ese cambio.

---

## 9. Verificación de los archivos generados

Una vez generados los archivos:

1. Comprueba que `AGENTS.md` corresponda al proyecto real.
    
2. Verifica que sus instrucciones sean coherentes con las tres fuentes.
    
3. Confirma que no existan contradicciones sin identificar.
    
4. Comprueba que los comandos documentados existan.
    
5. Valida que las rutas referenciadas sean correctas.
    
6. Confirma que no se hayan introducido dependencias o herramientas ficticias.
    
7. Comprueba que `.editorconfig` sea coherente con el stack y el formateador.
    
8. Verifica que no se hayan modificado archivos ajenos al alcance autorizado.
    
9. Comprueba que las decisiones pendientes estén claramente diferenciadas de las confirmadas.
    
10. Revisa que `AGENTS.md` sea conciso y no reproduzca innecesariamente la documentación fuente.
    

Cuando una verificación no pueda realizarse, informa la limitación.

No afirmes que has validado comandos o configuraciones que no hayas comprobado realmente.

---

## 10. Informe final

Una vez finalizado el trabajo, entrega un resumen breve en español que incluya:

1. **Archivos creados o actualizados:** rutas y finalidad.
    
2. **Convenciones incorporadas:** principales reglas aplicadas.
    
3. **Verificaciones realizadas:** comprobaciones y resultados.
    
4. **Conflictos o decisiones pendientes:** solamente los relevantes.
    
5. **Limitaciones:** elementos que no pudieron comprobarse.
    

Distingue claramente entre información confirmada, implementaciones existentes y decisiones pendientes.

No reproduzcas íntegramente el contenido de los archivos en el informe final.

---

## 11. Instrucción de ejecución

Ejecuta ahora este procedimiento sobre el repositorio actual.

Comienza inspeccionando las tres fuentes principales y el estado del proyecto.

Genera o actualiza exclusivamente:

- `AGENTS.md`
    
- `.editorconfig`
    

Utiliza inglés para el contenido de ambos archivos y español para el informe final.

Trabaja de manera incremental, conserva las decisiones existentes que sean válidas y evita cambios innecesarios.

**El resultado debe ser un repositorio con instrucciones operativas coherentes, verificables y reutilizables por distintos agentes de IA, sin introducir tecnologías, estructuras ni funcionalidades que todavía no hayan sido definidas.**
