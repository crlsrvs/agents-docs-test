
## 1. Propósito y alcance

Este documento establece convenciones técnicas de organización, nomenclatura, formato, tipado, contratos, testing, documentación, control de versiones y colaboración para desarrollar software consistente, mantenible y verificable.

Se aplica a proyectos con distintos lenguajes, frameworks y arquitecturas, desarrollados por personas o agentes de IA. Es una fuente normativa para generar `AGENTS.md`, junto con las convenciones para agentes, el PRD y la configuración real del repositorio.

**No es una instrucción para instalar dependencias, inicializar herramientas o modificar proyectos automáticamente.**

### Interpretación de las reglas

- **DEBE:** cumplimiento obligatorio cuando la regla sea aplicable.
    
- **NO DEBE:** comportamiento prohibido.
    
- **PREFERIR:** práctica recomendada, salvo alternativa mejor justificada.
    
- **CUANDO CORRESPONDA:** aplicable según el lenguaje, framework, arquitectura o naturaleza del proyecto.
    

Las convenciones específicas de un lenguaje, framework o decisión arquitectónica documentada prevalecen sobre las preferencias generales de este documento dentro de su ámbito técnico.

---

## 2. Principios de diseño y calidad

El código DEBE favorecer:

1. **Simplicidad:** soluciones claras y comprensibles, sin complejidad innecesaria.
    
2. **Responsabilidad única:** componentes y módulos con responsabilidades bien delimitadas.
    
3. **Cohesión:** mantener relacionados los elementos que cumplen una misma responsabilidad.
    
4. **Bajo acoplamiento:** minimizar dependencias innecesarias entre módulos.
    
5. **Reutilización justificada:** extraer código compartido cuando exista una necesidad real.
    
6. **Legibilidad:** nombres expresivos, flujos comprensibles y estructuras consistentes.
    
7. **Mantenibilidad:** facilitar la modificación y extensión sin afectar comportamientos ajenos.
    

NO DEBE introducirse una abstracción únicamente para anticipar una necesidad hipotética.

PREFERIR código explícito y fácil de comprender frente a soluciones excesivamente genéricas o ingeniosas.

No aplicar principios como DRY, SOLID o patrones de diseño de manera dogmática cuando aumenten la complejidad sin un beneficio concreto.

---

## 3. Arquitectura y organización del código

### 3.1. Estructura del proyecto

La organización del código DEBE respetar la arquitectura definida para el proyecto.

Cuando no exista una arquitectura establecida, PREFERIR una organización que agrupe responsabilidades relacionadas, separe funcionalidades, controle dependencias y facilite localizar archivos y evolucionar módulos de forma independiente cuando sea posible.

La arquitectura Feature-First puede ser una opción adecuada, pero NO DEBE imponerse cuando el framework, los requisitos o las decisiones técnicas justifiquen otra estructura.

### 3.2. Co-location

PREFERIR ubicar cerca de su implementación los archivos que comparten una responsabilidad o cambian por la misma razón.

Esto puede incluir:

- Componentes y sus estilos específicos.
    
- Hooks, controladores o servicios relacionados.
    
- Modelos, tipos y esquemas propios de una funcionalidad.
    
- Pruebas unitarias de los elementos anteriores.
    

La co-localización NO DEBE imponerse cuando existan convenciones del framework o necesidades técnicas que justifiquen otra ubicación.

Las pruebas de integración y end-to-end pueden utilizar directorios independientes cuando resulte más apropiado.

### 3.3. Código compartido

Un componente, servicio o utilidad DEBE trasladarse a un módulo compartido solamente cuando exista una necesidad concreta de reutilización o una responsabilidad transversal. NO DEBE crearse código compartido para funcionalidades exclusivas de un módulo sin justificación técnica.

PREFERIR mantener las abstracciones cerca de sus consumidores hasta que exista una razón clara para generalizarlas.

---

## 4. Convenciones de nomenclatura

Los identificadores DEBEN utilizar nombres descriptivos, consistentes y acordes con las convenciones del lenguaje.

NO DEBEN utilizarse nombres engañosos ni abreviaturas innecesarias. Evitar abreviaturas ambiguas, nombres genéricos y términos que no representen su responsabilidad.

### 4.1. Convenciones generales

|Convención|Aplicación preferida|Ejemplo|
|---|---|---|
|`camelCase`|Variables, funciones y métodos en JavaScript/TypeScript|`getUserProfile`|
|`PascalCase`|Clases, interfaces, tipos y componentes React/Vue/Angular cuando corresponda|`UserProfileCard`|
|`snake_case`|Columnas de base de datos y claves de API cuando el contrato o la convención adoptada lo establezca|`user_profile_id`|
|`SCREAMING_SNAKE_CASE`|Constantes globales conceptuales y variables de entorno|`MAX_RETRY_COUNT`|

La tabla se limita a los contextos indicados. Las convenciones idiomáticas del lenguaje y las reglas del framework DEBEN respetarse; por ejemplo, Python utiliza habitualmente `snake_case` para funciones y variables.

### 4.2. Nombres semánticos

- Las funciones DEBEN expresar claramente su propósito.
    
- Los nombres de variables DEBEN representar su contenido.
    
- Los tipos y clases DEBEN representar conceptos concretos.
    
- Los booleanos DEBERÍAN utilizar nombres que expresen una condición, como `isLoading`, `hasPermission` o `canEdit`.
    
- Las constantes DEBEN diferenciarse de variables mutables mediante las convenciones propias del lenguaje.
    

### 4.3. Nomenclatura de archivos

PREFERIR nombres de archivos consistentes con su responsabilidad y el framework.

En proyectos JavaScript/TypeScript, cuando no exista otra convención:

- Componentes: `UserProfileCard.tsx`.
    
- Hooks personalizados: `useUserProfile.ts`.
    
- Módulos y utilidades generales: nombres descriptivos, preferentemente `kebab-case`.
    
- Pruebas: mismo nombre base del archivo probado, seguido de `.spec` o `.test`.
    

Los archivos especiales exigidos por un framework DEBEN respetar su nomenclatura oficial.

No mezclar convenciones de nombres equivalentes dentro de un mismo proyecto sin una razón documentada.

---

## 5. Formato y estilo del código

### 5.1. Reglas generales

El código DEBE mantener un formato consistente. PREFERIR herramientas automáticas de formateo y análisis estático compatibles con el stack.

Las herramientas configuradas son la referencia para los aspectos que controlan. NO DEBEN introducirse preferencias manuales que contradigan innecesariamente sus reglas.

### 5.2. EditorConfig

Adoptar [EditorConfig](https://editorconfig.org/) como mecanismo base de consistencia entre editores cuando sea aplicable.

Para proyectos nuevos, PREFERIR:

- `root = true`.
    
- Codificación `utf-8`.
    
- Saltos de línea `lf`.
    
- Nueva línea final mediante `insert_final_newline = true`.
    
- Eliminación de espacios finales mediante `trim_trailing_whitespace = true`, salvo excepciones justificadas.
    
- Indentación definida según el lenguaje y las herramientas utilizadas.
    

Como referencia inicial:

- JavaScript, TypeScript, JSON y YAML: preferir 2 espacios si no existe otra convención.
    
- Python: preferir 4 espacios.
    
- Lenguajes que requieren tabulaciones o formateadores específicos: respetar sus convenciones.
    

La configuración DEBE ser coherente con el formateador del proyecto.

No es necesario imponer una única indentación a todos los tipos de archivo.

### 5.3. Herramientas de formato

PREFERIR la herramienta de formateo estándar del lenguaje o aquella ya adoptada por el proyecto.

Evitar incorporar múltiples herramientas que resuelvan la misma responsabilidad y produzcan resultados incompatibles.

Las configuraciones de formato DEBEN mantenerse versionadas cuando formen parte del proyecto.

---

## 6. Tipado, contratos y validación de datos

### 6.1. Tipado

Cuando el lenguaje lo permita, PREFERIR mecanismos de tipado estático y configuraciones estrictas.

Ejemplos:

- TypeScript: preferir `strict` y tipos explícitos cuando la inferencia no sea suficiente.
    
- Python: utilizar anotaciones de tipos en interfaces y funciones relevantes, complementadas con herramientas de verificación cuando corresponda.
    

Evitar tipos excesivamente permisivos, conversiones inseguras y supresiones injustificadas de errores de tipado.

En TypeScript, PREFERIR `unknown`, tipos específicos o genéricos apropiados antes que `any`.

Las excepciones DEBEN responder a una necesidad técnica concreta.

### 6.2. Contratos entre módulos

Los límites entre módulos y servicios DEBEN utilizar contratos claros.

PREFERIR:

- Interfaces explícitas cuando aporten claridad.
    
- Tipos de datos consistentes.
    
- Responsabilidades de entrada y salida bien definidas.
    
- Separación entre modelos de dominio y representaciones externas cuando resulte necesaria.
    

Evitar duplicar contratos o estructuras de datos sin justificación.

### 6.3. Validación de datos externos

Los datos provenientes de fuentes no confiables DEBEN validarse antes de utilizarse como información confiable del dominio.

Esto incluye, cuando corresponda:

- Solicitudes HTTP.
    
- Respuestas de APIs externas.
    
- Formularios.
    
- Archivos importados.
    
- Variables de entorno.
    
- Mensajes externos o entradas de usuario.
    

PREFERIR mecanismos de validación compatibles con el stack y reutilizar las herramientas ya adoptadas.

No asumir que el tipado estático sustituye la validación en tiempo de ejecución.

### 6.4. Contratos de API

Cuando existan APIs, DEBEN respetarse sus contratos documentados.

Si el proyecto utiliza OpenAPI u otro mecanismo equivalente, mantener la implementación y la especificación consistentes.

NO DEBEN modificarse unilateralmente formatos, nombres de campos o estructuras públicas que puedan afectar a los consumidores existentes.

---

## 7. Manejo de errores y operaciones asíncronas

### 7.1. Manejo de errores

Los errores DEBEN manejarse en el nivel que tenga responsabilidad para interpretarlos, recuperarse o comunicarlos.

NO DEBEN:

- Silenciarse sin justificación.
    
- Capturarse para ignorarlos.
    
- Convertirse indiscriminadamente en respuestas exitosas.
    
- Exponer información interna sensible al usuario final.
    

PREFERIR errores descriptivos, contextuales y compatibles con los mecanismos establecidos por el proyecto.

La distinción entre errores esperados del negocio y fallos técnicos DEBE mantenerse clara cuando corresponda.

### 7.2. Operaciones asíncronas

Las operaciones asíncronas DEBEN contemplar adecuadamente sus estados de éxito y error.

Cuando aplique, considerar:

- Timeouts.
    
- Cancelación de operaciones.
    
- Condiciones de carrera.
    
- Reintentos limitados.
    
- Idempotencia.
    
- Manejo de recursos y limpieza.
    

No implementar reintentos indefinidos ni asumir que una operación externa siempre tendrá éxito.

Los mecanismos adicionales de resiliencia DEBEN justificarse según los riesgos reales de la aplicación.

---

## 8. Dependencias y configuración

### 8.1. Gestión de dependencias

Las dependencias DEBEN gestionarse utilizando el package manager y las convenciones del proyecto.

- Mantener consistencia con el archivo de bloqueo de dependencias (_lockfile_) cuando corresponda.
    
- Evitar mezclar gestores de paquetes sin una necesidad explícita.
    
- Preferir funcionalidades nativas o bibliotecas existentes antes de incorporar nuevas herramientas.
    
- Evitar dependencias redundantes o incompatibles.
    
- Respetar las restricciones de versiones establecidas.
    

No cambiar versiones mayores o sustituir bibliotecas sin considerar su compatibilidad y consecuencias.

### 8.2. Configuración del entorno

La configuración dependiente del entorno DEBE separarse del código de negocio cuando corresponda.

PREFERIR variables de entorno o mecanismos equivalentes para valores configurables y sensibles.

NO DEBEN almacenarse credenciales, tokens ni secretos reales en archivos versionados.

Cuando sea útil, mantener un archivo de ejemplo que documente las variables necesarias sin incluir información sensible.

---

## 9. Convenciones de testing

### 9.1. Principios generales

Las pruebas DEBEN verificar comportamientos observables y requisitos relevantes.

PREFERIR pruebas:

- Deterministas.
    
- Independientes entre sí.
    
- Reproducibles.
    
- Claras y enfocadas.
    
- Resistentes a refactorizaciones que no modifiquen el comportamiento.
    

Evitar pruebas que dependan innecesariamente de detalles internos de implementación.

No es obligatorio crear un archivo de pruebas por cada archivo de código. La cobertura debe responder al comportamiento y los riesgos relevantes.

### 9.2. Patrón Arrange-Act-Assert (AAA)

PREFERIR el patrón AAA en las pruebas unitarias:

1. **Arrange:** preparar entradas, dependencias y condiciones iniciales.
    
2. **Act:** ejecutar el comportamiento bajo prueba.
    
3. **Assert:** verificar los resultados esperados.
    

Las tres etapas DEBEN ser reconocibles, aunque no requieren comentarios explícitos cuando la prueba resulte suficientemente clara.

### 9.3. Nomenclatura y ubicación

En proyectos JavaScript/TypeScript, PREFERIR la nomenclatura de la sección 4.3, con sufijos como `.spec.ts`, `.spec.tsx`, `.test.ts` o `.test.tsx`.

PREFERIR mantener las pruebas unitarias cerca de su implementación (_co-location_).

Las pruebas de integración y end-to-end pueden organizarse por flujos, servicios o escenarios completos.

Respetar las convenciones del framework de testing existente.

### 9.4. Cobertura y mantenimiento

Las pruebas DEBEN contemplar los comportamientos relevantes y, según el riesgo:

- Casos exitosos.
    
- Errores y condiciones límite.
    
- Validaciones.
    
- Transiciones de estado.
    
- Contratos entre componentes.
    
- Regresiones de defectos corregidos.
    

PREFERIR pruebas de regresión cuando se corrijan errores reproducibles.

Las pruebas unitarias NO DEBEN depender innecesariamente de la red, el tiempo real o servicios externos no controlados.

No imponer porcentajes arbitrarios de cobertura sin una política específica del proyecto.

---

## 10. Documentación del código

### 10.1. Comentarios y documentación técnica

Los comentarios DEBEN aportar información que no resulte evidente al leer el código.

PREFERIR explicar:

- Intención de negocio.
    
- Restricciones no obvias.
    
- Decisiones técnicas relevantes.
    
- Invariantes.
    
- Efectos secundarios.
    
- Contratos públicos complejos.
    

NO DEBEN utilizarse comentarios para repetir literalmente lo que hace una instrucción evidente.

### 10.2. JSDoc / TSDoc

En proyectos JavaScript/TypeScript, PREFERIR JSDoc o TSDoc para documentar comportamientos cuyo propósito no resulte suficientemente claro mediante nombres y tipos.

Utilizarlos especialmente para APIs públicas, reglas de negocio complejas, restricciones importantes, efectos secundarios relevantes y contratos que requieran explicaciones adicionales.

Evitar anotaciones redundantes que únicamente repitan tipos ya expresados claramente por TypeScript.

En otros lenguajes, utilizar sus mecanismos idiomáticos de documentación.

### 10.3. Archivos estándar del repositorio

Mantener los siguientes archivos cuando aporten valor al proyecto:

|Archivo|Responsabilidad|
|---|---|
|`README.md`|Objetivo, instalación, ejecución y orientación general|
|`CONTRIBUTING.md`|Guía de contribución, pruebas y colaboración|
|`ARCHITECTURE.md`|Arquitectura general, responsabilidades y decisiones de diseño|
|`SECURITY.md`|Políticas y procedimientos de reporte de vulnerabilidades|
|`CHANGELOG.md`|Historial de cambios relevantes entre versiones|

`README.md` DEBERÍA existir en los proyectos destinados a ser mantenidos o utilizados por otros desarrolladores.

Los demás archivos son condicionales y NO DEBEN crearse vacíos únicamente para completar una estructura predefinida.

Evitar duplicar documentación entre archivos. PREFERIR referencias cruzadas cuando corresponda.

---

## 11. Control de versiones y colaboración

### 11.1. Conventional Commits

Adoptar [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) como estándar para nombrar commits cuando el proyecto utilice Git y no exista una política diferente.

Formato:

`<type>(<scope>): <description>`

El ámbito (_scope_) es opcional.

Tipos recomendados:

|Tipo|Uso|
|---|---|
|`feat`|Nueva funcionalidad|
|`fix`|Corrección de errores|
|`docs`|Cambios de documentación|
|`refactor`|Reestructuración sin cambio funcional intencional|
|`test`|Incorporación o modificación de pruebas|
|`chore`|Mantenimiento general|
|`build`|Cambios en el sistema de construcción o dependencias|
|`ci`|Cambios en integración o entrega continua|
|`perf`|Mejoras de rendimiento|
|`style`|Cambios de formato sin impacto funcional|

Ejemplos:

- `feat(auth): add session expiration`
    
- `fix(api): handle invalid user input`
    
- `docs: update installation instructions`
    
- `refactor(users): simplify validation logic`
    

Los cambios incompatibles DEBEN identificarse mediante `!` después del tipo o ámbito, o mediante el pie `BREAKING CHANGE:` con su descripción, siguiendo la especificación.

Los mensajes DEBEN describir los cambios realizados y evitar descripciones ambiguas.

### 11.2. Semantic Versioning (SemVer)

Cuando el proyecto utilice versiones públicas basadas en un contrato de compatibilidad, adoptar [Semantic Versioning 2.0.0](https://semver.org/lang/es/).

Formato:

`MAJOR.MINOR.PATCH`

- **MAJOR:** cambios incompatibles con la API pública.
    
- **MINOR:** nuevas funcionalidades compatibles con versiones anteriores.
    
- **PATCH:** correcciones compatibles con versiones anteriores.
    

La aplicación de SemVer requiere identificar claramente qué constituye la API pública del producto o biblioteca.

Los proyectos que no gestionen versiones públicas o tengan otro esquema de publicación NO DEBEN incrementar versiones artificialmente por cada modificación.

### 11.3. GitHub Flow

Cuando el proyecto utilice GitHub como plataforma de colaboración, PREFERIR [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow), salvo que exista otra estrategia adoptada.

Este flujo contempla:

1. Crear una rama descriptiva para un conjunto de cambios relacionados.
    
2. Implementar y registrar modificaciones mediante commits coherentes.
    
3. Abrir un Pull Request para solicitar revisión.
    
4. Completar las verificaciones y revisiones requeridas.
    
5. Integrar los cambios en la rama principal mediante el mecanismo autorizado.
    

PREFERIR ramas de vida corta y cambios de alcance controlado.

Las políticas de revisión, protección de ramas e integración DEBEN respetar la configuración del repositorio.

### 11.4. Changelog

Cuando el proyecto mantenga un historial de versiones destinado a usuarios o consumidores, adoptar [Keep a Changelog](https://keepachangelog.com/).

El archivo `CHANGELOG.md` DEBERÍA documentar cambios relevantes utilizando, cuando correspondan, estas categorías:

- `Added`
    
- `Changed`
    
- `Deprecated`
    
- `Removed`
    
- `Fixed`
    
- `Security`
    

PREFERIR una sección `Unreleased` para cambios relevantes que todavía no forman parte de una versión publicada.

El changelog debe comunicar cambios significativos y comprensibles para los consumidores, sin convertirse en una copia exhaustiva del historial Git.

---

## 12. Aplicación de las convenciones

Estas convenciones DEBEN aplicarse de forma coherente con el lenguaje, el framework, la arquitectura vigente, los requisitos del PRD, las decisiones arquitectónicas documentadas y las herramientas y configuraciones reales del repositorio.

Las reglas generales NO DEBEN utilizarse para sustituir convenciones específicas ya establecidas y técnicamente justificadas.

En proyectos nuevos, las preferencias indicadas sirven como valores iniciales cuando no existan decisiones previas.

En proyectos existentes, PREFERIR preservar las convenciones actuales que resulten compatibles con los requisitos, evitando reorganizaciones o migraciones innecesarias.

Las excepciones relevantes deben quedar justificadas y documentadas mediante los mecanismos habituales del proyecto.

**El objetivo es producir código consistente, comprensible y mantenible, sin imponer herramientas, arquitecturas ni procesos que el proyecto no necesita.**

Este documento define estándares técnicos. Las instrucciones sobre autonomía, planificación, ejecución de tareas, gestión del contexto y reporte del trabajo corresponden a «Convenciones para agentes».
