## Resumen General de Prisma

Prisma es un ORM moderno con JavaScript y TypeScript. Proporciona una capa de abstracción sobre la base de datos, simplificando las operaciones de lectura, escritura y consulta de datos, al tiempo que promueve un enfoque orientado a objetos.

### Características principales

- **ORM tipo seguro**: Genera automáticamente un cliente TypeScript con un modelo de datos tipo seguro basado en el esquema de la base de datos.
- **Consultas intuitivas**: Utiliza un lenguaje de consulta intuitivo y expresivo basado en JavaScript/TypeScript, evitando la necesidad de escribir SQL directamente.
- **Migraciones de base de datos**: Proporciona un sistema de migraciones que permite realizar cambios en el esquema de la base de datos de manera segura y controlada.
- **Múltiples bases de datos**: Admite una amplia gama de bases de datos relacionales populares, como PostgreSQL, MySQL, SQLite, SQL Server y Oracle.
- **Rendimiento optimizado**: Utiliza consultas optimizadas y agrupadas para minimizar las operaciones de lectura/escritura en la base de datos.
- **Ecosistema robusto**: Cuenta con una creciente comunidad y un ecosistema de herramientas y complementos.

### Componentes clave

1. **Prisma Client**: Una biblioteca TypeScript/JavaScript generada automáticamente que proporciona una API tipo segura para interactuar con la base de datos.
2. **Prisma Studio**: Una herramienta visual para explorar y administrar los datos de la base de datos, y ejecutar consultas y mutaciones.
3. **Prisma Migrate**: Un conjunto de herramientas de línea de comandos para gestionar migraciones de bases de datos y aplicar cambios en el esquema.
4. **Prisma Schema**: Un archivo de esquema donde se definen los modelos de datos, las relaciones y otros aspectos de la estructura de la base de datos.

### Definición de modelos y tablas

En Prisma, las tablas de la base de datos se definen como modelos en el archivo `schema.prisma`. Estos modelos representan las entidades de la aplicación, y sus propiedades corresponden a las columnas de las tablas. Prisma admite una amplia gama de tipos de datos escalares y compuestos, así como la definición de relaciones entre modelos.

### Migraciones de tablas

Cuando se realizan cambios en los modelos definidos en el archivo `schema.prisma`, Prisma puede generar migraciones que actualizan automáticamente el esquema de la base de datos. Estas migraciones crean, modifican o eliminan tablas según sea necesario, manteniendo el esquema de la base de datos sincronizado con el código de la aplicación.
## Comandos más importantes de Prisma
### Instalar Prisma


```bash
npm install prisma
```

### Iniciar un nuevo proyecto Prisma

```bash
npx prisma init
```

### Generar modelos de base de datos a partir de schema.prisma

```bash
npx prisma generate
```

### Migrar cambios en el modelo de base de datos

```bash
npx prisma migrate dev
```

### Ejecutar semillas para poblar la base de datos

```bash
npx prisma db seed
```

### Desplegar la base de datos a un entorno de producción

```bash
npx prisma migrate deploy
```

### Generar diagrama visual del modelo de base de datos

```bash
npx prisma studio
```

### Actualizar Prisma CLI

```bash
npm install prisma@latest --save-dev
```

### Verificar versión de Prisma CLI

```bash
npx prisma --version
```