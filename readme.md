# Curso SQL - Strctured Query Lenguage
En español sería algo asi como **Lenguaje de Consultas Estructuradas**.
Es un **lenguaje de programación**, y por lo tanto es un lenguaje estandarizado, que nos permite trabajar con **Bases de Datos relacionales**

## 01 - Historias y Usos
Originalmente, los datos se almacenaban en simples archivos de formas ordenadas, con sistemas de clave valor o afines.

#### Edgar Codd
Inventó el algebra relacional. Sirve para relacionar conjuntos y trabajarlos.
Y de ese concepto, crea un sistema de bases de datos con algebra relacional.

#### Usos
- Crear y administrar bases de datos. Incluyendo agregar, almacenar, eliminar datos, tablas, y otros objetos;
- Realizar consultas;
- Creacion de restricciones y reglas de integridad;
- Generar informes, analisis de datos;
- Ususarios y permisos para modificar los datos;
- etc

## 02 - Fundamentos de Bases de Datos
#### Entidad
Es la representacion de algo. Como es el dibujo de una casa, no es la casa, es una representacion de la casa.
En este sentido, lo que hacemos con las entidades es almacenar informacion sobre las entidades en bases de datos.

Por ejemplo, en una tienda, una entidad puede ser Cliente. La nomenclatura que se usa para representar las entidades se llaman **Notación de Chen**. Que permite ver entidades y sus relaciones.

Toda entidad tiene *Atributos* que le definen sus características. *La representamos con un cuadrado*.
Ejemplo: Casa
#### Atributos
Hay varias clases de atributos.

##### a - Atributos Simples:
Contienen datos únicos.
*Los representamos con un óvalo*.
Ejemplo: Valor $

##### b - Atributos Compuestos:
Son aquellos que se componen de otros atributos. Que pueden ser simples o no.
Ejemplo: Hambientes: baños, comedor, cocina, etc

##### c- Atributos Multivalor:
Son aquellos que tienen más de un valor. *Los representamos con un doble ovalo*.
Ejemplo: Ventanas, Hambientes, etc

##### d- Atributos Derivados:
Son aquellos que podemos obtener por medio de otro atributo. *Los representamos con un ovalo en linea punteada*.
Ejemplo: Antiguedad. La podemos obtener de la fecha de construccion

##### e- Key:
Es un atributo único, es el ID de una entidad. *Se representa subrayado* Ejemplo: El numero del registro inmobiliario

## 03 - TABLAS (TABLE)
```sql
CREATE DATABASE "Clientes"
```
Es una tabla. Se organiza en filas y columnas.
```sql
CREATE TABLE "Clientes"
```

#### Fields
Las columnas se denominan **CAMPOS (Fields)**

Todo campo requiere un tipo (type):
- Integer: Es para almancenar numeros (edad, precio, cantidades, etc)
- Text: Almacena todo lo referente a texto (nombre, direccion, etc)
- Blob: Almacena datos binarios
- Real: Es el equivalente a float (hasta 8b)
- Numeric: Numeros con una precision numerica muy alta. Numeros muy grandes (Pi por ejemplo)

A demás del type se le pueden asignar otras propiedades:
- "Default": Es un valor que se aplicará por defecto a un campo en caso de no asignarse uno propio.
- "PK": (Primary Key) lo evalua como clave primaria.
- "AI": (Auto Increment) Es una propiedad de la clave primaria para que incremente automaticamente.
- "NN": (Not Null)
- "Check": 

#### Records
Las columnas se denominan **REGISTROS (Record)**.
A su vez, a las "celdas" se las denominan **VALOR DEL CAMPO (Field Value)**

## 04 - CONSULTA (Query)
Es el medio por el cual se realiza una busqueda de datos en una base de datos.
En realidad, TODA accion que se realize sobre una base de datos se denomina consulta.
*CRUD: Create, Read, Update, Delete.*

#### a - Consulta
El * es el caracter universal para "TODO"
```SQL
SELECT *
```
Con cada consulta nos devuelve *una tabla nueva* con los resultados de esa consulta. Podemos pedir una consulta de solo una columna, o de varias seguidas con coma.
```SQL
SELECT nombre, edad FROM persona
```
Podemos utlizar AS para asignar un nick a una columna. Así tambien podemos hacer operaciones aritmeticas:
```SQL
SELECT nombre AS user_name, edad * 2 FROM persona
```


#### b - Insert
Comando INSERT INTO para agregar. Podemos agregar solo uno, o varios creando *tuplas* separadas con coma.
```SQL
INSERT INTO persona (nombre, apellido, edad)
VALUE('Juan','Gomez',26),
     ('Predro','Ramirez',24),
     ('Lucas','Suarez',25)
```

## 05 - Identificadores (ID)

#### Primary Key
Es el ID que hace unico a un registro con el fin de poder identificarlo.

Una clave primaria puede ser autoincremental o no, pero siempre tendrá dos requisitos obligatorios:
- Nunca pueden ser nulos (Null)
- Nunca pueden repetirse (ya que justamente buscan ser únicos para identificar fehacientemente un registro)

#### Forein Key
Hace referencia a una Key de otra tabla

## 06 - EJEMPLO DE BASE DE DATOS Y TABLAS RELACIONADAS
![Imagen de tabla relacional de Northwind](https://en.wikiversity.org/wiki/File:Northwind_E-R_Diagram.png)

<a href='https://en.wikiversity.org/wiki/Database_Examples/Northwind' target=_blank>Northwind.db</a>

## 07 - Order by
Permite ordenar la tabla en referencia a una columna.

El orden ascente que sigue es el siguiente:
1- Null
2- Numeros
3- Caracteres Especiales
4- Letras 

```SQL
SELECT * FROM products
ORDER BY price ASC
```
Por defecto es `ASC` (ascendente).