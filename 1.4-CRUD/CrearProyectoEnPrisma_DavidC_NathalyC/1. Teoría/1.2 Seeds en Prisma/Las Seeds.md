## Seeds en Prisma

En el desarrollo de aplicaciones, a menudo es útil tener una forma de cargar datos de prueba o iniciales en la base de datos. Esto puede ser especialmente útil durante la fase de desarrollo y pruebas para simular diferentes escenarios y casos de uso. Prisma proporciona una funcionalidad llamada "Seeds" que nos permite hacer precisamente eso.

### ¿Qué son los Seeds en Prisma?

Los Seeds son scripts que se ejecutan para cargar datos iniciales en la base de datos. Estos scripts se definen en un archivo separado y se pueden ejecutar en cualquier momento durante el ciclo de desarrollo o despliegue de la aplicación.

### Creando un archivo de Seeds

Para crear un archivo de Seeds, primero debemos crear una nueva carpeta llamada `prisma/seeds` dentro de nuestro proyecto. Dentro de esta carpeta, crearemos un nuevo archivo, por ejemplo, `dev.ts` o `production.ts`, dependiendo del entorno en el que queramos ejecutar los Seeds.

Aquí hay un ejemplo de cómo podría verse un archivo de Seeds `dev.ts`:

```typescript
import { PrismaClient } from '@prisma/client'
const prisma = new PrismaClient()

async function main() {
  // Borra todos los datos existentes
  await prisma.user.deleteMany({})

  // Crea nuevos usuarios
  const user1 = await prisma.user.create({
    data: {
      email: 'user1@example.com',
      name: 'User One',
    },
  })

  const user2 = await prisma.user.create({
    data: {
      email: 'user2@example.com',
      name: 'User Two',
    },
  })

  console.log({ user1, user2 })
}

main()
  .catch((e) => console.error(e))
  .finally(async () => {
    await prisma.$disconnect()
  })
```

En este ejemplo, primero importamos el cliente Prisma y creamos una instancia. Luego, definimos una función `main` asíncrona que realiza las siguientes operaciones:

1. Elimina todos los datos existentes de la tabla `User` utilizando `prisma.user.deleteMany({})`.
2. Crea dos nuevos usuarios utilizando `prisma.user.create(...)` con diferentes correos electrónicos y nombres.
3. Imprime los nuevos usuarios creados en la consola.

Finalmente, la función `main` se ejecuta y se maneja cualquier error que pueda ocurrir. Después de que se completa la operación, se cierra la conexión a la base de datos.
### Creando archivo `seed.js/.ts`

Si estás usando typescript, dentro del archivo `package.json` inserta el comando:

```json
"prisma": {
  "seed": "ts-node prisma/seed.ts"
},
```

O si estas usando javascript, dentro del mismo archivo inserta el comando:

```json
"prisma": {
  "seed": "node prisma/seed.js"
},
```

### Ejecutando los Seeds

Para ejecutar los Seeds, simplemente ejecuta el archivo que contiene el script de Seeds utilizando Node.js:

```bash
npx prisma db seed --preview-feature
```

Este comando buscará automáticamente el archivo de Seeds correspondiente (`dev.ts` o `production.ts`) en la carpeta `prisma/seeds` y ejecutará el script.

El flag `--preview-feature` se utiliza en el comando `npx prisma db seed` para habilitar funciones experimentales de Prisma que aún están en fase de vista previa o desarrollo. Estas características aún no son estables y pueden cambiar en versiones futuras de Prisma.