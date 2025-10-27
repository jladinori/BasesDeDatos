## Bases De Datos
of. 215, segundo piso de aulas, una hora despues o antes

monitora kolayap@unal.edu.co sabado 8-9

### Preguntas

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

** (Structured Query Language, lenguaje de consulta estructurada):** Es un lenguaje estándar para bases de datos relacionales (RDBMS como Oracle, My, PostgreSQL, SQL Server).

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
- evaluar el problema
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


que significa dependencia en modelo de relaciones barker?
dertermina que esto tienen sentido si existen las dos entidades

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
documento soporte metodologico

## Clase 12 Conceptos avanzados

1. Supertipos
2. Subtipos
3. Arcos o relaciones exclusivas(regla de tabla, usa constraint, alter table)
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

TAREA: aprender sql


Atomicidad: Hace referencia a dividir los datos en su valor atómico para ser almacenados, es decir, el menor valor en el que siguen teniendo sentido.

Ejemplo: Los campos “Nombre_est” y “Apellido_est” de la tabla “ESTUDIANTE” descomponen el nombre completo de un estudiante en nombre y apellido, los cuales siguen teniendo sentido por sí mismo. Además, estos campos no pueden dividirse más, ya que no tendrían un sentido o significado claro.

La integridad referencial se puede observar en la vista relaciones, como por ejemplo entre Ciudad y Pais, cada ciudad pertenece a un país; y depende de este, ya que pueden existir ciudades con el mismo código de distintos paises, por lo tanto el campo Id_Pais de Ciudad depende de Id_Pais de Pais.



Reglas Prácticas para Tu Tarea
✅ USA PK COMPUESTA cuando:
Creas tabla intermedia para relación N:M

La combinación de FK es naturalmente única

No necesitas que otras tablas referencien esta PK

Las FK no son excesivamente largas

✅ USA PK SIMPLE cuando:
La tabla representa una entidad con existencia propia

Permites duplicados en la combinación de FK

Otras tablas necesitan referenciar esta PK

Las FK son muy largas o complejas

✅ MANTÉN PK ORIGINAL cuando:
Solo agregas FK a una tabla existente

La tabla ya tiene una PK bien definida

Estás en relación 1:N (no creas tabla nueva)

---

# **SQL Básico - Explicación para Principiantes**

## **¿Qué es SQL?**
SQL (Structured Query Language) es el lenguaje para comunicarte con bases de datos. Es como hablarle a la base de datos para que te dé información o guarde datos.

---

## **Los 4 Comandos Fundamentales (CRUD)**

### **1. SELECT - Leer Datos (El más importante)**

#### **Estructura básica:**
```sql
SELECT columnas 
FROM tabla 
WHERE condición;
```

#### **Ejemplos prácticos:**
```sql
-- Ver TODOS los clientes
SELECT * FROM clientes;

-- Ver solo nombres y emails
SELECT nombre, email FROM clientes;

-- Ver clientes de una ciudad específica
SELECT nombre, telefono 
FROM clientes 
WHERE ciudad = 'Bogotá';

-- Ordenar resultados
SELECT * FROM productos 
ORDER BY precio DESC;
```

### **2. INSERT - Agregar Datos**

#### **Estructura:**
```sql
INSERT INTO tabla (columna1, columna2) 
VALUES (valor1, valor2);
```

#### **Ejemplos:**
```sql
-- Agregar un nuevo cliente
INSERT INTO clientes (nombre, email, ciudad) 
VALUES ('María García', 'maria@email.com', 'Medellín');

-- Agregar producto
INSERT INTO productos (nombre, precio, stock) 
VALUES ('Laptop', 1500000, 10);
```

### **3. UPDATE - Actualizar Datos**

#### **Estructura:**
```sql
UPDATE tabla 
SET columna = nuevo_valor 
WHERE condición;
```

#### **Ejemplos:**
```sql
-- Cambiar el precio de un producto
UPDATE productos 
SET precio = 1600000 
WHERE id = 5;

-- Aumentar stock de todos los productos en 5 unidades
UPDATE productos 
SET stock = stock + 5;

-- ⚠️ CUIDADO: Sin WHERE actualiza TODOS los registros
```

### **4. DELETE - Eliminar Datos**

#### **Estructura:**
```sql
DELETE FROM tabla 
WHERE condición;
```

#### **Ejemplos:**
```sql
-- Eliminar un cliente específico
DELETE FROM clientes 
WHERE id = 10;

-- Eliminar productos sin stock
DELETE FROM productos 
WHERE stock = 0;

-- ⚠️ CUIDADO EXTREMO: Esto borra TODO
DELETE FROM productos;  -- ¡NO HACER!
```

---

## **Cláusulas Esenciales con Analogías**

### **WHERE - El Filtro**
```sql
-- Como buscar en un almacén:
SELECT * FROM productos 
WHERE precio < 100000;          -- Productos baratos

SELECT * FROM clientes 
WHERE ciudad = 'Bogotá';        -- Clientes de Bogotá

SELECT * FROM pedidos 
WHERE fecha >= '2024-01-01';    -- Pedidos de este año
```

### **ORDER BY - El Organizador**
```sql
-- Como ordenar una lista:
SELECT * FROM productos 
ORDER BY precio ASC;            -- Más baratos primero

SELECT * FROM empleados 
ORDER BY salario DESC;          -- Mejor pagados primero

SELECT * FROM clientes 
ORDER BY ciudad, nombre;        -- Por ciudad y luego por nombre
```

### **LIMIT - El Selector**
```sql
-- Como pedir "solo los primeros 3":
SELECT * FROM productos 
ORDER BY precio DESC 
LIMIT 5;                        -- Los 5 productos más caros

SELECT * FROM clientes 
LIMIT 10;                       -- Solo 10 clientes
```

---

## **Consultas con Múltiples Tablas (JOIN)**

### **INNER JOIN - La Intersección**
```sql
-- Clientes que han hecho pedidos
SELECT clientes.nombre, pedidos.fecha, pedidos.total
FROM clientes
INNER JOIN pedidos ON clientes.id = pedidos.cliente_id;
```

### **LEFT JOIN - Todo de la izquierda**
```sql
-- Todos los clientes, tengan o no pedidos
SELECT clientes.nombre, pedidos.fecha
FROM clientes
LEFT JOIN pedidos ON clientes.id = pedidos.cliente_id;
```

---

## **Funciones Útiles**

### **Funciones de Agregación:**
```sql
-- Contar
SELECT COUNT(*) FROM clientes;                    -- Total clientes

-- Sumar
SELECT SUM(total) FROM pedidos;                   -- Total vendido

-- Promedio
SELECT AVG(precio) FROM productos;                -- Precio promedio

-- Máximo y Mínimo
SELECT MAX(precio), MIN(precio) FROM productos;   -- Producto más caro y más barato
```

### **GROUP BY - Agrupar Resultados**
```sql
-- Ventas por ciudad
SELECT ciudad, COUNT(*) as total_clientes
FROM clientes
GROUP BY ciudad;

-- Total vendido por cliente
SELECT cliente_id, SUM(total) as total_gastado
FROM pedidos
GROUP BY cliente_id;
```

---

## **Ejemplos del Mundo Real**

### **Sistema de Tienda:**
```sql
-- 1. Productos más vendidos
SELECT producto_id, COUNT(*) as veces_vendido
FROM detalle_pedidos
GROUP BY producto_id
ORDER BY veces_vendido DESC
LIMIT 10;

-- 2. Clientes que más gastan
SELECT c.nombre, SUM(p.total) as total_gastado
FROM clientes c
JOIN pedidos p ON c.id = p.cliente_id
GROUP BY c.id, c.nombre
ORDER BY total_gastado DESC
LIMIT 5;

-- 3. Productos que necesitan reposición
SELECT nombre, stock
FROM productos
WHERE stock < 10;
```

### **Sistema de Biblioteca:**
```sql
-- Libros prestados actualmente
SELECT l.titulo, c.nombre, p.fecha_prestamo
FROM libros l
JOIN prestamos p ON l.id = p.libro_id
JOIN clientes c ON p.cliente_id = c.id
WHERE p.fecha_devolucion IS NULL;

-- Libros más populares
SELECT l.titulo, COUNT(*) as veces_prestado
FROM libros l
JOIN prestamos p ON l.id = p.libro_id
GROUP BY l.id, l.titulo
ORDER BY veces_prestado DESC;
```

---

## **Errores Comunes de Principiantes**

### **❌ SIN WHERE en UPDATE/DELETE:**
```sql
-- ¡PELIGRO! Actualiza TODOS los registros
UPDATE productos SET precio = 100000;  -- ❌
DELETE FROM clientes;                  -- ❌

-- ✅ SIEMPRE usar WHERE
UPDATE productos SET precio = 100000 WHERE id = 5;  -- ✅
DELETE FROM clientes WHERE id = 10;                 -- ✅
```

### **❌ Confundir = con LIKE:**
```sql
-- Para texto exacto
SELECT * FROM clientes WHERE nombre = 'Juan';      -- ✅ Solo "Juan"

-- Para búsqueda parcial  
SELECT * FROM clientes WHERE nombre LIKE 'Juan%';  -- ✅ "Juan", "Juan Carlos"
```

### **❌ Olvidar comillas en texto:**
```sql
SELECT * FROM clientes WHERE nombre = Juan;        -- ❌ ERROR
SELECT * FROM clientes WHERE nombre = 'Juan';      -- ✅ CORRECTO
```

---

## **Tabla Resumen de Comandos Básicos**

| Comando | Para Qué Sirve | Ejemplo |
|---------|----------------|---------|
| **SELECT** | Ver datos | `SELECT nombre FROM clientes;` |
| **INSERT** | Agregar datos | `INSERT INTO clientes (nombre) VALUES ('Ana');` |
| **UPDATE** | Modificar datos | `UPDATE clientes SET ciudad='Bogotá' WHERE id=1;` |
| **DELETE** | Eliminar datos | `DELETE FROM clientes WHERE id=5;` |
| **WHERE** | Filtrar resultados | `SELECT * FROM productos WHERE precio > 100000;` |
| **ORDER BY** | Ordenar resultados | `SELECT * FROM clientes ORDER BY nombre;` |
| **LIMIT** | Limitar resultados | `SELECT * FROM productos LIMIT 5;` |

---

## **Ejercicios para Practicar**

### **Base de datos: EMPLEADOS**
```sql
-- 1. Ver todos los empleados
SELECT * FROM empleados;

-- 2. Empleados que ganan más de 2 millones
SELECT nombre, salario FROM empleados WHERE salario > 2000000;

-- 3. Empleados de departamento "Ventas"
SELECT * FROM empleados WHERE departamento = 'Ventas';

-- 4. Ordenar empleados por salario (mayor a menor)
SELECT * FROM empleados ORDER BY salario DESC;

-- 5. Los 3 empleados mejor pagados
SELECT * FROM empleados ORDER BY salario DESC LIMIT 3;
```

---

## **Consejos para Empezar**

### **1. Empieza con SELECT:**
- Primero domina cómo **leer** datos
- Usa `WHERE` para filtrar
- Usa `ORDER BY` para organizar

### **2. Practica con datos reales:**
- Crea una base de datos simple
- Inserta tus propios datos
- Haz preguntas y respóndelas con SQL

### **3. Siempre prueba con SELECT antes de UPDATE/DELETE:**
```sql
-- ANTES de eliminar, verifica qué vas a eliminar
SELECT * FROM clientes WHERE ciudad = 'Cartagena';  -- ✅ Primero
DELETE FROM clientes WHERE ciudad = 'Cartagena';    -- ✅ Después
```

**Recuerda**: SQL es como aprender un nuevo idioma. Comienza con estas frases básicas y poco a poco formarás oraciones más complejas. ¡La práctica es clave! 🚀

---

Block (o página): unidad mínima de transferencia entre disco y memoria. Un DBMS lee/escribe en bloques (p. ej. 4 KB, 8 KB según motor). Los índices y datos se almacenan y acceden en bloques.

Data file (archivo de datos): archivo físico en disco que contiene los bloques/páginas que almacenan las tablas, índices y demás estructuras. Un DBMS puede usar uno o varios data files para distribuir almacenamiento.

Relación: el data file está formado por muchos bloques; operaciones I/O leen/escriben bloques desde el data file.

## Clase 13

Repaso conceptos avanzados

## Semana 10-1

He diseñado una base de datos para rastrear/analizar datos históricos aeronáuticos. El objetivo principal de la base de datos es resolver el problema de calificar qué aerolíneas son mejores o peores en función de su puntualidad.
Para ello, es necesario comparar el tiempo en un momento determinado del día con los vuelos entrantes y salientes en un aeropuerto concreto.
Empecemos por lo más sencillo: diseñar la aplicación de introducción de datos para la información de las siguientes 7 entidades:
- Registro meteorológico.
- Estación meteorológica.
- Ciudad.
- Aeropuerto.
- Aerolínea.
- Ruta.
- Aeronave.
Recuerda que la base de datos ya está diseñada, por lo que en algún momento tendré que inicializarla en el servidor.



## Semana 10.2

