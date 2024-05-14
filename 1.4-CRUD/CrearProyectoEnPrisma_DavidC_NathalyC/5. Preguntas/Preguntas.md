## Nathaly Caballero
---
1. ¿Cuál es el archivo principal donde se definen los modelos de datos en Prisma?

- [ ] models.js
- [ ] schema.prisma
- [ ] database.json

**Explicación**: b) schema.prisma  
El archivo `schema.prisma` es el lugar donde se definen los modelos de datos, las relaciones y otros aspectos de la estructura de la base de datos en Prisma.

2. ¿Qué comando se utiliza para generar una nueva migración de base de datos en Prisma?

- [ ] prisma migrate up
- [ ] prisma migrate dev --name nombre_migracion
- [ ] prisma migrate create

**Explicación**: b) prisma migrate dev --name nombre_migracion  
Este comando genera una nueva migración de base de datos en Prisma, donde `--name` se utiliza para asignarle un nombre descriptivo a la migración.

3. ¿Cuál de las siguientes bases de datos NO es compatible con Prisma?

- [ ] PostgreSQL
- [ ] MySQL
- [ ] MongoDB

**Explicación**: c) MongoDB  
Prisma es compatible con bases de datos relacionales como PostgreSQL, MySQL, SQLite, SQL Server y Oracle, pero no con bases de datos NoSQL como MongoDB.
## David Correa
---
4. ¿Qué decorador se utiliza en Prisma para definir una propiedad como clave primaria?

- [ ] @primary
- [ ] @id
- [ ] @key

**Explicación**: b) @id  
El decorador `@id` se utiliza en Prisma para definir una propiedad como la clave primaria de un modelo.

5. ¿Cuál de las siguientes opciones describe correctamente cómo se definen las relaciones uno a muchos (1:N) en Prisma?

- [ ] Utilizando la sintaxis `@relation`
- [ ] Utilizando la sintaxis `[]` en el lado "muchos" de la relación
- [ ] Utilizando la sintaxis `@oneToMany`

**Explicación**: b) Utilizando la sintaxis `[]` en el lado "muchos" de la relación  
En Prisma, las relaciones uno a muchos se definen utilizando la sintaxis `[]` en el lado "muchos" de la relación.

6. ¿Qué herramienta de Prisma se utiliza para explorar y administrar los datos de la base de datos de forma visual?

- [ ] Prisma Studio
- [ ] Prisma CLI
- [ ] Prisma Playground


**Explicación**: a) Prisma Studio  
Prisma Studio es una herramienta visual que permite explorar y administrar los datos de la base de datos, así como ejecutar consultas y mutaciones directamente desde una interfaz gráfica de usuario.