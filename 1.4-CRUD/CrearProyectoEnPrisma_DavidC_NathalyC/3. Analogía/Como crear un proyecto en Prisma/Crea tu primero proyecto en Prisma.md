## Pasos para crear un nuevo proyecto en Prisma
### 1. Instalar Prisma CLI

Primero, necesitamos instalar la herramienta de línea de comandos de Prisma (Prisma CLI) de manera global en nuestro sistema. Ejecuta el siguiente comando en tu terminal:

```bash
npm install -save-dev prisma
```

### 2. Crear un nuevo proyecto

Crea una nueva carpeta para tu proyecto y navega hasta ella en la terminal:

```bash
mkdir mi-proyecto
cd mi-proyecto
```

`mkdir` sirve para crear una nueva carpeta.

### 3. Inicializar un nuevo proyecto Prisma

Dentro de la carpeta del proyecto, ejecuta el siguiente comando para inicializar un nuevo proyecto Prisma:

```bash
prisma init
```

Este comando creará dos archivos en tu proyecto:

- `schema.prisma`: Aquí se define el esquema de tu base de datos, incluyendo modelos, relaciones y más.
- `.env`: Este archivo se utiliza para almacenar variables de entorno, como la cadena de conexión a tu base de datos.

### 4. Configurar el esquema Prisma

Abre el archivo `schema.prisma` en tu editor de código preferido. Aquí puedes definir tus modelos de datos que representan las tablas de tu base de datos.

Un ejemplo sencillo de un modelo `User` podría ser:

```prisma
model User {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  name      String?
  posts     Post[]
}

model Post {
  id        Int      @id @default(autoincrement())
  title     String
  content   String?
  published Boolean  @default(false)
  author    User     @relation(fields: [authorId], references: [id])
  authorId  Int
}
```

### 5. Configurar la conexión a la base de datos

En el archivo `.env`, agrega tu cadena de conexión a la base de datos. Por ejemplo, para una base de datos PostgreSQL:

```
DATABASE_URL="postgresql://user:password@localhost:5432/mydb?schema=public"
```

Reemplaza `user`, `password`, `localhost:5432` y `mydb` con tus credenciales y detalles de conexión específicos.

### 6. Ejecutar migraciones

Después de definir tus modelos y configurar la conexión a la base de datos, puedes ejecutar migraciones para crear o actualizar las tablas en tu base de datos.

Primero, ejecuta el siguiente comando para crear una migración inicial:

```bash
prisma migrate dev --name init
```

Este comando creará una nueva carpeta `migrations` con archivos que describen los cambios a realizar en la base de datos.

Luego, aplica la migración ejecutando:

```bash
prisma migrate deploy
```

Ahora tu base de datos está lista para ser utilizada con Prisma.

### 7. Uso de Prisma en tu aplicación

Puedes interactuar con tu base de datos utilizando el cliente Prisma en tu aplicación JavaScript/TypeScript. Instala la biblioteca `@prisma/client` como una dependencia de desarrollo:

```bash
npm install @prisma/client
```

Luego, en tu código, puedes importar y utilizar el cliente Prisma:

```javascript
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

// Ejemplo de uso
async function main() {
  const newUser = await prisma.user.create({
    data: {
      email: 'example@example.com',
      name: 'John Doe',
    },
  })
  console.log('Nuevo usuario creado:', newUser)
}

main()
  .catch(console.error)
  .finally(async () => {
    await prisma.$disconnect()
  })
```
