## Bases De Datos
of. 215, segundo piso de aulas, una hora despues o antes

monitora kolayap@unal.edu.co sabado 8-9

### Preguntas

- como importar sql a access
- insert in to en sql
- que son los identificadores, cuando se escoge entidad relacion
- que atributos no se ponen sino hasta en nivel fisico
- como se escriben las variables en general
- como es que son las lineas obligatorias opcionales en barker, para repasar
- una relacion que atributos lleva

### Introduccion

**Sistema de gestion de base de datos(SGBD o DBMS ):** Un conjunto de programas de software que permiten definir, crear, manipular y administrar bases de datos, proporcionando una forma estructurada y segura de almacenar y recuperar información.

los tres niveles de abstracción en la arquitectura de un sistema de bases de datos

**Nivel Interno o Físico (infraestructura)**: Es el nivel más bajo y describe cómo se almacenan los datos realmente en el hardware (estructuras de datos complejas y de bajo nivel). Es de interés para los desarrolladores que necesitan optimizar el rendimiento.

**Nivel Lógico o Conceptual (diseño):** Es el nivel intermedio y describe qué datos se almacenan y las relaciones entre ellos. Oculta la complejidad del nivel físico presentando estructuras simples (como tablas). Es el nivel que utilizan los administradores de bases de datos (DBA) para diseñar el esquema global.

**Nivel de Vistas o externo (lo que los usuarios ven):** Es el nivel más alto y describe sólo una parte de la base de datos para un grupo de usuarios específico. Su objetivo es simplificar la interacción ocultando información que no es relevante para un usuario final, proporcionando una vista personalizada de los datos.

### Clase 2

**Data:** Conjunto de hechos en bruto, sin procesar, que por sí mismos pueden carecer de significado.  
**Informacion:** El resultado de procesar, organizar o **interpretar la data** de forma que tenga significado y utilidad

![](https://jhonmosquera.com/wp-content/uploads/2024/01/Evolucion-de-las-bases-de-datos-a-traves-del-tiempo-1024x349.jpg)  

### Clase 3

**llaves unicas:** Las llaves candidatas que no fueron elegidas como primaria se llaman llaves alternas (o secundarias).
**llave foranea:** Una llave foránea es un atributo en una tabla que hace referencia a la llave primaria de otra tabla 

### Clase 4

**Integridad por referencia (o integridad referencial)** 

👉 Es una regla de consistencia en bases de datos que asegura que un valor de llave foránea en una tabla siempre debe corresponder a un valor existente de llave primaria en otra tabla.

**Integridad por valor (también llamada integridad de dominio o integridad de valores)**

👉 Es la regla que garantiza que los valores almacenados en un atributo (columna) sean válidos, correctos y pertenezcan al dominio definido para ese atributo.

**Un diccionario** de datos contiene metadatos, es decir,
datos acerca de los datos.


**Bloque de datos**
```
+-----------------------------+
| Cabecera (metadata)         |  <-- 100 bytes
+-----------------------------+
| Directorio de registros     |  <-- punteros
+-----------------------------+
| Área de datos (registros)   |  <-- varias filas
+-----------------------------+
| Espacio libre               |  <-- para crecer
+-----------------------------+
```

1. **Cabecera (Header)**

   * Contiene **información de control** sobre el bloque:

     * Tipo de bloque.
     * Espacio libre disponible.
     * Identificadores (por ejemplo, a qué tabla pertenece).

2. **Directorio de registros (Row/Slot Directory)**

   * Una especie de índice interno que indica dónde empieza cada registro lógico dentro del bloque.
   * Permite que, si un registro se mueve dentro del bloque, no tengas que reescribir todo, solo actualizar la referencia en el directorio.

3. **Área de datos (Data / Row Area)**

   * Aquí se almacenan realmente los **registros lógicos (tuplas)**.
   * Pueden estar ordenados o no, según el gestor.

4. **Espacio libre (Free Space)**

   * Reservado para futuras inserciones o actualizaciones dentro del mismo bloque.
   * Evita tener que mover registros a otro bloque en cuanto se modifica un valor.

**Oracle Database (o Oracle DB)** es un sistema de gestión de bases de datos relacional (RDBMS) desarrollado por Oracle Corporation.

Caracteristicas:  
- Relacional: Significa que organiza los datos en tablas estructuradas con filas y columnas, y estas tablas se relacionan entre sí
- robusto
- seguridad
- potente y escalable

#### SQL
![](https://pandorafms.com/blog/wp-content/uploads/2024/02/graph-sqlvsnosql-1.png)

**SQL (Structured Query Language, lenguaje de consulta estructurada):** Es un lenguaje estándar para bases de datos relacionales (RDBMS como Oracle, MySQL, PostgreSQL, SQL Server).

- Características: Datos en tablas estructuradas con esquemas fijos (columnas definidas). Usa consultas como SELECT, INSERT, JOIN para relacionar tablas.
- Ventajas: Excelente para transacciones complejas, integridad de datos y consultas relacionales. Ideal para aplicaciones como finanzas, e-commerce o sistemas de gestión donde la consistencia es crucial.
- Desventajas: Menos flexible para datos no estructurados o escalado masivo.
Ejemplo: SELECT * FROM usuarios WHERE edad > 18;

#### No SQL
Diseñadas para manejar datos no estructurados o semi-estructurados de manera más flexible y escalable. A diferencia de SQL, no usan tablas fijas ni un esquema rígido; en cambio, permiten almacenar datos en formatos variados, como documentos, pares clave-valor, grafos o columnas.
- Flexibilidad: No requieren un esquema fijo, lo que las hace ideales para datos que cambian frecuentemente (como en redes sociales o big data).
- Escalabilidad horizontal: Fáciles de distribuir en múltiples servidores (escalado "hacia afuera"), lo que las hace perfectas para grandes volúmenes de datos y alto tráfico.

## Clase 6

### importacion y exportacion (metodos
)
api  
json

**XML (eXtensible Markup Language)** es un lenguaje de marcado diseñado para almacenar y transportar datos de manera estructurada y legible tanto para humanos como para máquinas.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<estudiante>
    <nombre>Ana González</nombre>
    <carrera>Ingeniería en Sistemas</carrera>
</estudiante>
```
**YAML (YAML Ain't Markup Language)** YAML es un formato de serialización de datos legible por humanos, diseñado para ser fácil de escribir y leer. Se usa comúnmente para archivos de configuración, intercambio de datos y definición de estructuras. 

```yaml
estudiante:
  id: 2024001
  nombre: "Ana González"
  carrera: "Ingeniería en Sistemas"
  materias:
    - "Matemáticas Avanzadas"
    - "Programación Web"
```

**XML (Extensible Markup Language):**

Es un lenguaje de marcado para estructurar datos de manera jerárquica, usando etiquetas similares a HTML (ej. <persona><nombre>Juan</nombre><edad>30</edad></persona>).

- Uso: Común en configuraciones, intercambio de datos entre sistemas (ej. en servicios web antiguos como SOAP), o documentos como RSS para noticias.
- Ventajas: Muy flexible y extensible (puedes definir tus propias etiquetas). Soporta validación con esquemas (XSD).
- Desventajas: Puede ser verbose (usa mucho texto para etiquetas), lo que lo hace más "pesado" que otros formatos.
- Ejemplo en bases de datos: En Oracle, puedes almacenar XML en columnas de tipo XMLType, que se guardan en bloques como datos estructurados.  

**JSON (JavaScript Object Notation):**

Es un formato ligero para representar datos como objetos clave-valor, similar a un diccionario (ej. {"nombre": "Juan", "edad": 30}).

- Uso: Muy popular en APIs web modernas (ej. para enviar datos entre un servidor y una app móvil), configuración y almacenamiento de datos no estructurados. Es nativo en JavaScript, pero se usa en todos los lenguajes.
- Ventajas: Fácil de leer/escribir por humanos y máquinas, compacto y rápido de parsear (procesar).
- Desventajas: No soporta comentarios nativos ni tipos de datos complejos como fechas sin conversión.
- Ejemplo en bases de datos: Muchas bases (como PostgreSQL o Oracle) tienen tipos JSON/JSONB para almacenar directamente JSON en tablas, distribuido en bloques.

**API (Application Programming Interface):**

No es un formato, sino una interfaz que define cómo dos piezas de software se comunican. Es como un "contrato" para intercambiar datos o funciones (ej. una API de Google Maps te permite integrar mapas en tu app).
Uso: Común en web (REST APIs), donde se envían datos en formatos como JSON o XML. Por ejemplo, la API de Twitter te deja obtener tweets.

- Tipos: RESTful (basadas en HTTP), GraphQL (más flexible), SOAP (más antiguo y estructurado con XML).
- Ventajas: Permite integración entre sistemas sin reinventar la rueda (ej. usar la API de Stripe para pagos).
- Desventajas: Requiere autenticación y puede tener límites (ej. rate limiting).
- Relación con formatos: Las APIs suelen usar JSON o XML para los datos enviados/recibidos, y estos pueden guardarse en bases de datos en bloques.

**YAML (YAML Ain't Markup Language):**

Es un formato legible para humanos, usado para serializar datos con indentación
```
persona:
  nombre: Juan
  edad: 30
```
- Uso: Principalmente para archivos de configuración (ej. en Docker, Kubernetes o Ansible), pero también para datos. Es como JSON pero más amigable para editar manualmente.
- Ventajas: Muy legible (usa espacios en lugar de llaves), soporta comentarios y listas complejas.
Desventajas: Sensible a la indentación (un espacio mal puesto rompe todo), y puede ser más lento de procesar que JSON.
- Ejemplo en bases de datos: Puedes almacenar YAML como texto en una columna, y se guardaría en bloques como cualquier string largo.

## Clase 7 (diseño de bases de daños)
bottom up
top down

Modelo Entidad Relacion (barker)
![](https://i.ytimg.com/vi/8IwxQqn4FHw/maxresdefault.jpg)
3 partes:
1. concepto(10)
Entidad:
Relacion: interaccion entre 2 o mas entidades
Atributo:

2. metodologia(11 pasos, 4 productos)
3. herramientas

Campos Multivariados = cuando un campo guarda varios valores en un mismo atributo (ej. “Teléfonos: 311-222-3333, 312-444-5555”). Eso no debería pasar en un modelo normalizado.

Campos Redundantes = información repetida innecesariamente en varias tablas (ej. guardar el nombre de la ciudad en cada usuario en lugar de tener una tabla Ciudad).


matriz varias entidades

**¿A qué lado se dibuja la línea punteada o sólida?**

Se dibuja del lado de la entidad cuya participación es opcional u obligatoria.
Es decir:

Si el empleado debe pertenecer a un departamento → línea sólida del lado de Empleado.

Si el departamento puede existir sin empleados → línea punteada del lado de Departamento.

## Clase 8

La extensión **CDM** en bases de datos se refiere comúnmente al Common Data Model (Modelo de Datos Común)

modelo fisico de access es el modelo de relaciones

Pasos
0. evaluar el problema
1. posibles entidades
2. posibles relacion
3. relaciones, cardinalidad, obligatoriedad
4. atributos de la entidades
5. modelo entidad relacion(cdm)
6. transformar relaciones m-n a 1-n, 
   a. se genera una entidad intermedia (debil o interseccion)
   b. se asocian 2 relaciones 1-n hacia la nueva entidad
   c. colocar la primera parte de la relacion original
   caracteristicas: cardinalidad, participacion(obligatoriedad), dependencia
7. identificar atributos o relaciones nuevas para la entidad debil
8. construir el modelo logico con todos las entidades y relaciones
9. (PDM)physical data model, toda entidad se convierte ahora en estructura(tabla),1DF1X, toda relacion se convierte en un enlace de lado 1 hacia el n(1), generando la FK, todos los atributos a la est(tabla
10. generar bases de datos
11. correr script


que significa dependencia en modelo de relaciones barker
dertermina que esto tienen sentido si existen las dos entidades

matriz extendida

tarea: identificar todas las servidumbres o chazas que dominan en la universidad
desarrolar base de datos para las maquinas y movibles de la universidad

## Clase 10

🔹 1. MODELO CONCEPTUAL (CDM)

📘 Qué es:

Es el modelo más abstracto. Se centra en las entidades, atributos y relaciones del negocio, sin preocuparse por cómo se implementará en una base de datos real.


💡 En PowerDesigner:

Se crea con New → Conceptual Data Model (CDM).

Usa entidades, atributos, relaciones (1:1, 1:N, M:N), cardinalidades y opcionalidad.

🧩 Propósito:

Entender y comunicar la estructura lógica del negocio con lenguaje visual (diagramas ER).

No tiene tipos de datos ni restricciones físicas.


✅ Ventajas:

Fácil de entender por usuarios no técnicos.

Detecta errores conceptuales antes de pasar a la parte técnica.

Sirve como documentación funcional del sistema.


---

🔹 2. MODELO LÓGICO (LDM)

📘 Qué es:

Representa cómo se organizarán los datos en una base de datos relacional, pero aún sin atarse a un motor específico (ni Access, ni MySQL, etc.).

Aquí las entidades se vuelven tablas y las relaciones se vuelven claves primarias y foráneas.


🧩 Lo que contiene:

Tablas, columnas, PK, FK, UK.

Tipos de datos genéricos (por ejemplo, String, Integer, Date).

Relaciones convertidas a claves foráneas.

Normalización de estructuras.


✅ Ventajas:

Prepara el diseño para implementarlo en cualquier SGBD.

Permite optimizar estructuras antes de definir detalles físicos.

Mantiene independencia del sistema gestor.


---

🔹 3. MODELO FÍSICO (PDM)

📘 Qué es:

Es el modelo técnico real que define exactamente cómo se creará la base de datos en un SGBD específico (MySQL, Access, SQL Server, Oracle, PostgreSQL, etc.).

Aquí el diseño ya está ajustado a las reglas y tipos de datos del motor elegido.


🧩 Contiene:

Tipos de datos específicos (INT, VARCHAR(50), DATE, FLOAT...).

Índices, restricciones (CHECK, DEFAULT, NOT NULL), triggers, vistas.

Propiedades de rendimiento (tamaño, relaciones en cascada, etc.).

Código SQL autogenerado.


✅ Ventajas:

Se puede exportar directamente a SQL para crear la base de datos.

Permite validar integridad, optimización y compatibilidad con el SGBD.

Representa exactamente cómo funcionará la base de datos en la práctica.

---

**Base de Datos (BD)**
Conjunto organizado de datos estructurados que se almacenan electrónicamente y se gestionan de forma eficiente.

**Sistema de Gestión de Bases de Datos (SGBD)**
Software que permite crear, mantener y administrar bases de datos (ej: MySQL, Oracle, PostgreSQL).

**Dependencia de Datos**
Cuando la información está vinculada y afecta a otras.

**Independencia de Datos**
Capacidad de modificar el esquema sin afectar las aplicaciones.

Independencia física: Cambiar almacenamiento sin afectar lógica

Independencia lógica: Cambiar estructura sin afectar programas

**Ejemplos de Sistemas de Bases de Datos**
MySQL - Open source popular

Oracle - Empresarial avanzado

PostgreSQL - Open source robusto

MongoDB - Base de datos NoSQL

SQLite - Ligero para aplicaciones móviles

**Código XML**
xml
<contacto>
    <nombre_referencia>martha</nombre_referencia>
    <telefono>31654654</telefono>
</contacto>

**Código JSON**
json
{
    "nombre_referencia": "martha",
    "telefono": "31654654"
}

proyecto mas o menos 15 entidades

siguiente tema oracle live crear cuenta
descargar oracle 11

## Clase 11

1. posibles entidades:
   estudiantes, trabajos academicos, normas legales, resultados ia, trabajos academicos antiguos, proceso estudiantil

subir cdm
matrices en excel del modelo
documento soporte metodologico}

## Clase 12 Conceptos avanzados

1. Supertipos
2. Subtipos
3. Arcos o relaciones exclusivas
4. Relaciones recursivas
5. Ciclos y validaciones(relaciones transitivas)

Perfecto 👍
Aquí tienes una **explicación completamente teórica** —sin tanto código— de los conceptos avanzados de modelado en bases de datos.
Está en formato **Markdown (MD)**, para que puedas copiarlo tal cual en tu trabajo o apuntes.

---

# 📘 Conceptos avanzados del modelado de datos

---

## 1. **Supertipos**

Un **supertipo** es una **entidad general** que agrupa características comunes a varias entidades más específicas.
Permite **reducir la redundancia** de atributos y mantener la consistencia del modelo.

* Es como una “categoría padre” de la que heredan varias subcategorías.
* Todos los **subtipos** comparten el mismo identificador (clave primaria) del supertipo.
* Cada instancia del supertipo puede corresponder a una o más instancias de sus subtipos, dependiendo de las reglas del negocio.

**Ejemplo teórico:**
Una entidad **Persona** puede ser un supertipo de **Profesor** y **Estudiante**, ya que ambos tienen atributos comunes (nombre, identificación, dirección).

**Ventajas:**

* Evita duplicar atributos.
* Facilita la actualización de información común.
* Mejora la claridad conceptual del modelo.

**Desventajas:**

* Puede complicar la implementación física si el sistema no maneja herencia de manera nativa.

---

## 2. **Subtipos**

Los **subtipos** representan **especializaciones** de un supertipo.
Cada subtipo hereda los atributos y relaciones del supertipo, pero también puede tener **atributos o relaciones exclusivas**.

**Tipos de especialización:**

* **Disyunta:** una instancia del supertipo puede pertenecer **solo a un** subtipo.
  Ejemplo: una persona puede ser *estudiante* o *profesor*, pero no ambas.
* **Solapada:** una instancia puede pertenecer a **más de un** subtipo.
  Ejemplo: una persona puede ser *profesor* y *administrador* al mismo tiempo.
* **Total:** todas las instancias del supertipo deben pertenecer a algún subtipo.
* **Parcial:** algunas instancias pueden no pertenecer a ningún subtipo.

**Importancia teórica:**
Los subtipos permiten reflejar **jerarquías y herencias de información**, similar a la herencia en programación orientada a objetos, pero dentro del contexto de las bases de datos.

---

## 3. **Arcos o relaciones exclusivas**

Un **arco** (también llamado *relación exclusiva*) es un **mecanismo gráfico** usado para mostrar que **una entidad puede relacionarse con solo una de varias alternativas posibles**.

**Ejemplo conceptual:**
Una entidad **Pago** puede estar asociada **a una Tarjeta o a una Cuenta Bancaria**, pero **no a ambas** al mismo tiempo.
El arco entre las relaciones indica esa exclusividad.

**Propósito:**

* Garantizar que una instancia elija una sola de las relaciones posibles.
* Evitar ambigüedad o redundancia en la representación del modelo.

**Importancia:**
El arco ayuda a **expresar reglas de negocio complejas**, como decisiones o exclusiones mutuas entre relaciones posibles.

**En resumen:**

> Un arco define que, de un conjunto de relaciones alternativas, **solo una puede ser verdadera** para cada instancia.

---

## 4. **Relaciones recursivas**

Una **relación recursiva** (o autorrelación) ocurre cuando **una entidad se relaciona consigo misma**.
Es decir, una instancia de la entidad puede estar asociada con otra instancia de la misma entidad.

**Ejemplos comunes:**

* En una empresa, un **Empleado** puede ser **jefe de otro Empleado**.
* En una jerarquía de cursos, un **Curso avanzado** puede tener como **requisito otro Curso**.

**Características:**

* La misma entidad aparece dos veces en la relación, pero con **roles distintos** (por ejemplo, *Empleado–Supervisor*).
* Se debe definir la **cardinalidad** y **opcionalidad** en ambos lados de la relación.

**Importancia teórica:**
Permite modelar **estructuras jerárquicas o dependencias internas**, sin crear entidades adicionales que no aporten semántica.

**Ventajas:**

* Simplifica la representación de jerarquías y estructuras organizativas.
* Permite consultas que recorren relaciones dentro de la misma tabla (como cadenas de mando o árboles de dependencias).

---

## 5. **Ciclos y validaciones (relaciones transitivas)**

Este concepto combina dos ideas clave: **ciclos entre relaciones** y **dependencias transitivas**.

### A) **Ciclos en las relaciones**

Un **ciclo** se da cuando un conjunto de relaciones entre entidades forma una cadena que **vuelve al punto de origen**.
Ejemplo:
`A` se relaciona con `B`, `B` con `C` y `C` vuelve a relacionarse con `A`.

**Problemas teóricos:**

* Puede generar **inconsistencias** o **dificultades de inserción** (por las dependencias circulares).
* Dificulta mantener la **integridad referencial**, ya que cada entidad depende de otra que aún no existe.
* En algunos casos, estos ciclos representan una **dependencia conceptual real** (por ejemplo, productos que se componen entre sí).

**Solución teórica:**

* Analizar si el ciclo es **lógico y necesario** o si surge de un **mal diseño**.
* Romper el ciclo con una entidad intermedia o redefiniendo las relaciones jerárquicas.

---

### B) **Validaciones y relaciones transitivas**

Una **relación transitiva** ocurre cuando una relación entre dos entidades **se puede deducir** de otras relaciones existentes.

**Ejemplo:**

* Si *A* está relacionado con *B* y *B* con *C*, entonces *A* está indirectamente relacionado con *C*.

**En el contexto de dependencias funcionales:**

* Una **dependencia transitiva** significa que un atributo depende de otro atributo no clave, lo que **viola la tercera forma normal (3FN)**.
* Por ejemplo, si `Estudiante → Carrera` y `Carrera → Facultad`, entonces `Estudiante → Facultad` es una dependencia transitiva.

**Validación teórica:**

* Detectar dependencias transitivas permite **normalizar** el modelo y eliminar redundancias.
* En modelos conceptuales, se debe evitar que una entidad dependa indirectamente de otra por medio de un atributo intermedio.

---

## 📚 Resumen comparativo

| Concepto                   | Qué representa                                       | Ejemplo conceptual            | Objetivo principal                         |
| -------------------------- | ---------------------------------------------------- | ----------------------------- | ------------------------------------------ |
| **Supertipo**              | Entidad general que agrupa características comunes   | Persona                       | Evitar duplicación de atributos            |
| **Subtipo**                | Entidad específica que hereda del supertipo          | Estudiante, Profesor          | Especializar y añadir atributos propios    |
| **Arco**                   | Exclusividad entre varias relaciones posibles        | Pago → (Tarjeta **o** Cuenta) | Asegurar que solo una relación se cumpla   |
| **Relación recursiva**     | Entidad que se relaciona consigo misma               | Empleado–Supervisor           | Modelar jerarquías o dependencias internas |
| **Ciclos / transitividad** | Dependencias circulares o deducibles entre entidades | Estudiante–Carrera–Facultad   | Verificar consistencia y normalización     |

---

## 🧩 Conclusión

Estos conceptos son fundamentales cuando el modelo de datos se vuelve más complejo y realista.
Permiten representar **herencia, exclusividad, jerarquía y dependencias** de una forma coherente con las reglas del negocio.
Su correcta identificación y uso ayuda a construir **modelos conceptuales más precisos, mantenibles y consistentes**.

---

¿Quieres que te haga un ejemplo completo en texto (como un mini diagrama ER con supertipo, subtipos y una relación recursiva) para que veas cómo se representan todos estos conceptos juntos?

## Clase 13

Repaso conceptos avanzados

## Clase 14

