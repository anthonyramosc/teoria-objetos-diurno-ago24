### Definiendo modelos

Para definir un modelo en Prisma, se utiliza la sintaxis `model` seguida del nombre del modelo. Dentro del bloque del modelo, se especifican las propiedades (columnas) de la tabla.

Aquí hay un ejemplo de cómo definir un modelo `User` en Prisma:

```prisma
model User {
  id        Int     @id @default(autoincrement())
  email     String  @unique
  name      String?
  password  String
  createdAt DateTime @default(now())
}
```

En este ejemplo, el modelo `User` tiene las siguientes propiedades:

- `id`: Una columna de tipo `Int` que es la clave primaria (`@id`) y se auto-incrementa (`@default(autoincrement())`).
- `email`: Una columna de tipo `String` que debe ser única (`@unique`).
- `name`: Una columna de tipo `String` opcional (indicado por `?`).
- `password`: Una columna de tipo `String`.
- `createdAt`: Una columna de tipo `DateTime` que se establece automáticamente en el momento actual (`@default(now())`).

### Tipos de datos

Prisma admite una amplia gama de tipos de datos escalares, como `String`, `Boolean`, `Int`, `Float`, `Decimal`, `DateTime` y más. Además, también admite tipos compuestos como `Json` y tipos personalizados definidos por el usuario.

### Relaciones

Prisma permite definir relaciones entre modelos, lo que facilita el trabajo con datos relacionales. Hay dos tipos principales de relaciones:

1. **Relaciones uno a uno (1:1)**: Se definen utilizando la sintaxis `@relation`.
2. **Relaciones uno a muchos (1:N)**: Se definen utilizando la sintaxis `[]` en el lado "muchos" de la relación.

Aquí hay un ejemplo que muestra una relación uno a muchos entre los modelos `User` y `Post`:

```prisma
model User {
  id    Int    @id @default(autoincrement())
  email String @unique
  posts Post[]
}

model Post {
  id        Int     @id @default(autoincrement())
  title     String
  content   String?
  author    User    @relation(fields: [authorId], references: [id])
  authorId  Int
}
```

En este ejemplo, un usuario puede tener muchos posts (`posts Post[]`), y cada post pertenece a un usuario específico (`author User`). La relación se define utilizando la sintaxis `@relation` y `authorId` como campo de referencia.

### Migraciones de tablas

Cuando se realizan cambios en los modelos definidos en el archivo `schema.prisma`, Prisma puede generar migraciones que actualizan automáticamente el esquema de la base de datos. Estas migraciones crean, modifican o eliminan tablas en la base de datos según sea necesario.

Para generar y aplicar migraciones, se utilizan los siguientes comandos de Prisma CLI:

```bash
# Genera una nueva migración
prisma migrate dev --name nombre_migracion

# Aplica la migración a la base de datos
prisma migrate deploy
```

Las migraciones generadas se almacenan en la carpeta `migrations` del proyecto, lo que permite realizar un seguimiento de los cambios en el esquema de la base de datos a lo largo del tiempo.

En resumen, Prisma proporciona una forma sencilla y expresiva de definir modelos y tablas en el archivo `schema.prisma`, lo que facilita el trabajo con datos relacionales en aplicaciones JavaScript/TypeScript. Además, Prisma maneja automáticamente las migraciones de tablas, lo que simplifica el proceso de mantener el esquema de la base de datos sincronizado con el código de la aplicación.