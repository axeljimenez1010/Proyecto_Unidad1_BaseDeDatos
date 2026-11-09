
<p align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTMy8h0-if_AU5roBFbgcnCNAoX2Hw1osOZBe6sZMgkKfI3QFk04_K6eYCr&s=10" alt="Logo de la Universidad" width="150">
</p>

<h1 align="center">INFORME DE FIN DE UNIDAD</h1>

<h2 align="center">
  Sistema de Inteligencia y Estadística Agrícola para la Provincia de Loja
</h2>

<p align="center">
  <strong>FEIRNNR - Carrera de Computación</strong>
</p>

---

## Datos Generales

| Información | Detalle |
|---|---|
| **Asignatura** | Base de Datos |
| **Ciclo** | 3 A |
| **Unidad** | 1 |
| **Docente** | Edwin René Guamán Quinche |
| **Estudiante** | Axel Joao Jiménez Palta |
| **Fecha** | |

### Resultado de aprendizaje de la unidad

Modelar bases de datos de problemas reales, bajo los principios de solidaridad, transparencia, responsabilidad y honestidad.

---

## Índice

1. [Título](#1-título)
2. [Contexto del problema](#2-contexto-del-problema)
3. [Objetivos](#3-objetivos)
4. [Modelos conceptuales de bases de datos](#4-modelos-conceptuales-de-bases-de-datos)
5. [Código SQL](#5-código-sql)
6. [Consultas de álgebra relacional y SQL](#6-consultas-de-álgebra-relacional-y-sql)
7. [Conclusiones](#7-conclusiones)
8. [Bibliografía](#8-bibliografía)

---

## 1. Título

**Sistema de Inteligencia y Estadística Agrícola para la Provincia de Loja**

## 2. Contexto del problema

La provincia de Loja cuenta con una importante actividad agrícola distribuida entre sus diferentes cantones y sectores. Sin embargo, la información relacionada con la producción de cultivos y los precios del mercado se encuentra dispersa y poco organizada. La falta de una base de datos centralizada dificulta relacionar las cantidades producidas con las variaciones de precios, lo que impide identificar con claridad si los aumentos responden a problemas de producción, condiciones climáticas o factores relacionados con la comercialización.

Esta situación afecta tanto a los agricultores como a los consumidores y a las instituciones que necesitan información confiable para tomar decisiones. Por ello, surge la necesidad de diseñar una base de datos relacional que permita organizar la información de los cantones, sectores, categorías de productos, períodos de cosecha y registros de producción. De esta manera, será posible almacenar y consultar datos sobre las cantidades producidas y los precios promedio, facilitando el análisis de la actividad agrícola y contribuyendo a una mejor comprensión del comportamiento del mercado en la provincia de Loja.

## 3. Objetivos

### 3.1. Objetivo General

Diseñar e implementar una base de datos relacional para gestionar la información estadística y productiva del sector agrícola de la provincia de Loja, mediante el modelado lógico y físico, con la finalidad de analizar la disponibilidad de alimentos y su impacto en la fluctuación de precios regionales.

### 3.2. Objetivos Específicos

- Elaborar el diagrama Entidad-Relación y el modelo relacional para estructurar la jerarquía territorial, los catálogos botánicos y los registros de producción agrícola, garantizando la normalización de los datos.
- Construir el esquema físico en SQL utilizando sentencias DDL para la creación de tablas con sus respectivas restricciones, y comandos DML para la inserción de datos que permitan ejecutar y validar consultas de álgebra relacional.

---

## 4. Modelos conceptuales de bases de datos

### 4.1. Modelo Entidad-Relación (E-R)

<p align="left">
  <img src="https://drive.google.com/uc?id=1OIWA-ts1wC48HzXD9DCvDzKWMYJ_DHTE" alt="Descripción" width="70%">
</p>

<p style="text-align:center; font-size:12px;">Figura 1. Diagrama Entidad-Relacion del Sistema de Inteligencia y Estadística Agrícola Regional </p>

### 4.2. Modelo Relacional

#### 4.2.1. Tabla Categoría

| Atributo | Tipo de Dato | Tipo de Clave | Referencia (FK) |
|---|---|---|---|
| id_categoria | INT | **PK** | - |
| nombre | VARCHAR(100) | - | - |
| descripcion | VARCHAR(255) | - | - |
| tipo_comercio | VARCHAR(50) | - | - |

#### 4.2.2. Tabla Cantón

| Atributo | Tipo de Dato | Tipo de Clave | Referencia (FK) |
|---|---|---|---|
| id_canton | INT | **PK** | - |
| nombre | VARCHAR(100) | - | - |
| zona_provincial | VARCHAR(50) | - | - |

#### 4.2.3. Tabla Sector

| Atributo | Tipo de Dato | Tipo de Clave | Referencia (FK) |
|---|---|---|---|
| id_sector | INT | **PK** | - |
| nombre | VARCHAR(100) | - | - |
| tipo_clima | VARCHAR(50) | - | - |
| id_canton | INT | **FK** | CANTON(id_canton) |

#### 4.2.4. Tabla Producto

| Atributo | Tipo de Dato | Tipo de Clave | Referencia (FK) |
|---|---|---|---|
| id_producto | INT | **PK** | - |
| nombre | VARCHAR(100) | - | - |
| variedad | VARCHAR(100) | - | - |
| id_categoria | INT | **FK** | CATEGORIA(id_categoria) |

#### 4.2.5. Tabla Meses_Cosecha

| Atributo | Tipo de Dato | Tipo de Clave | Referencia (FK) |
|---|---|---|---|
| id_producto | INT | **PK / FK** | PRODUCTO(id_producto) |
| mes | VARCHAR(20) | **PK** | - |

#### 4.2.6. Tabla Registro_Produccion

| Atributo | Tipo de Dato | Tipo de Clave | Referencia (FK) |
|---|---|---|---|
| id_registro | INT | **PK** | - |
| fecha_registro | DATE | - | - |
| cantidad_produccion | DECIMAL(10,2) | - | - |
| nivel_abundancia | VARCHAR(50) | - | - |
| precio_promedio | DECIMAL(10,2) | - | - |
| ciclo_agricola | VARCHAR(50) | - | - |
| id_producto | INT | **FK** | PRODUCTO(id_producto) |
| id_sector | INT | **FK** | SECTOR(id_sector) |

### 4.3. Diagrama Relacional

<p align="left">
  <img src="https://drive.google.com/uc?id=1ozULqDx4n_E7JebDNMNzQwRzHsMAWaZD" alt="Descripción" width="70%">
</p>

<p style="text-align:center; font-size:12px;">Figura 2. Diagrama Relacional del Sistema de Inteligencia y Estadística Agrícola Regional. </p>

---

## 5. Código SQL

### 5.1. Creación de Tablas (DDL)

#### Tabla Categoría

```sql
CREATE TABLE CATEGORIA (
    id_categoria  INT          NOT NULL AUTO_INCREMENT,
    nombre        VARCHAR(100) NOT NULL,
    descripcion   VARCHAR(255),
    tipo_comercio VARCHAR(50),
    PRIMARY KEY (id_categoria)
);

```

#### Tabla Cantón

```sql
CREATE TABLE CANTON (
    id_canton       INT          NOT NULL AUTO_INCREMENT,
    nombre          VARCHAR(100) NOT NULL,
    zona_provincial VARCHAR(50)  NOT NULL,
    PRIMARY KEY (id_canton)
);

```

#### Tabla Sector

```sql
CREATE TABLE SECTOR (
    id_sector  INT          NOT NULL AUTO_INCREMENT,
    nombre     VARCHAR(100) NOT NULL,
    tipo_clima VARCHAR(50)  NOT NULL,
    id_canton  INT          NOT NULL,
    PRIMARY KEY (id_sector),
    FOREIGN KEY (id_canton) REFERENCES CANTON(id_canton)
);

```

### 5.2. Inserción de Datos (DML)

#### Inserción en la tabla Categoría

```sql
-- Agregar INSERT INTO CATEGORIA
```

#### Inserción en la tabla Cantón

```sql
-- Agregar INSERT INTO CANTON
```

#### Inserción en la tabla Sector

```sql
-- Agregar INSERT INTO SECTOR
```

---

## 6. Consultas de álgebra relacional y SQL

### 6.1. Ejercicio 1 — Selección (σ)

**Enunciado:** Obtener los registros de producción agrícola con nivel de abundancia "Alto" y precio promedio superior a 500 dólares por tonelada.

**Álgebra Relacional:**

```text
Agregar expresión algebraica
```

**Consulta SQL:**

```sql
-- Agregar consulta SQL
```

**Resultado esperado:**

*Agregar resultado.*

---

### 6.2. Ejercicio 2 — Proyección (π) y Producto Cartesiano (×)

**Enunciado:** Relacionar los cantones de la provincia con las categorías agrícolas, obteniendo todas las combinaciones posibles.

**Álgebra Relacional:**

```text
Agregar expresión algebraica
```

**Consulta SQL:**

```sql
-- Agregar consulta SQL
```

**Resultado esperado:**

*Agregar resultado.*

---

### 6.3. Ejercicio 3 — Selección y Proyección (σ + π)

**Enunciado:** Obtener el nombre, variedad y tipo de comercio de los productos pertenecientes a la categoría "Cereales".

**Álgebra Relacional:**

```text
Agregar expresión algebraica
```

**Consulta SQL:**

```sql
-- Agregar consulta SQL
```

**Resultado esperado:**

*Agregar resultado.*

---

### 6.4. Ejercicio 4 — Reunión Natural / JOIN (⋈)

**Enunciado:** Identificar los productos agrícolas cultivados en sectores con clima "Cálido Seco".

**Álgebra Relacional:**

```text
Agregar expresión algebraica
```

**Consulta SQL:**

```sql
-- Agregar consulta SQL
```

**Resultado esperado:**

*Agregar resultado.*

---

### 6.5. Ejercicio 5 — División (÷)

**Enunciado:** Identificar los productos agrícolas cosechados y registrados en los sectores definidos para la consulta.

**Álgebra Relacional:**

```text
Agregar expresión algebraica
```

**Consulta SQL:**

```sql
-- Agregar consulta SQL
```

**Resultado esperado:**

*Agregar resultado.*

---

## 7. Conclusiones

*Agregar las conclusiones del informe.*

---

## 8. Bibliografía

[1] E. F. Codd, "A Relational Model of Data for Large Shared Data Banks," *Communications of the ACM*, vol. 13, no. 6, pp. 377-387, Jun. 1970.

[2] P. P. Chen, "The Entity-Relationship Model—Toward a Unified View of Data," *ACM Transactions on Database Systems*, vol. 1, no. 1, pp. 9-36, Mar. 1976.

[3] Instituto Nacional de Estadística y Censos (INEC), *Encuesta de Superficie y Producción Agropecuaria Continua (ESPAC) 2024*, Ecuador, abr. 2025.
