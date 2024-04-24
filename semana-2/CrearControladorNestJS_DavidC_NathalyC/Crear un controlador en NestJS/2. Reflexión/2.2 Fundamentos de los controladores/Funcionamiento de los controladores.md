El siguiente diagrama nos indica como **los controladores** y la capa de servicio **trabajan juntos** para llevar a cabo una lógica, pero son dos cosas completamente diferentes.
![](https://codigoencasa.com/content/images/2022/06/controladores.png)

**Los controladores se ocupan esencialmente de las rutas** de su aplicación. Un controlador puede tener varias _rutas diferentes_ y todo depende del mecanismo de enrutamiento para controlar **qué controlador recibe qué solicitud.**

Pero qué pasa si vuelcas toda tu lógica de negocio dentro de los controladores. Tal vez **registrar un nuevo usuario** si el usuario aún no está registrado o llevar a cabo controles de validación sólo dentro de los controladores.

Eso no tiene mucho sentido después de todo. Probablemente **no haría mucha diferencia** si sólo tienes una _pequeña aplicación_. Pero cuando la aplicación crece y tienes que **registrar más controladores y rutas** y tienes que escribir más lógica de negocio, ahí es donde las cosas parecen salirse de control y ciertamente no son mantenibles.

### Arquitectura

1. **Controladores:** El único propósito de un controlador es recibir las peticiones de la aplicación y ocuparse de las rutas.
1. **Capa de servicio:** Esta parte del bloque debe incluir únicamente la lógica de negocio. Por ejemplo, todas las operaciones **CRUD** y los métodos para determinar cómo se pueden crear, almacenar y actualizar los datos.
1. **Capa de acceso a los datos:** Esta capa se **encarga y proporciona la lógica para acceder** a los datos almacenados en un almacenamiento persistente de algún tipo. Por ejemplo un **ODM como Mongoose.**

## Comandos CLI para crear un controlador:

Primero que todo, en esta parte vamos a referenciar todos los comando CLI a un controlador llamado **'cats'**.
#### **1. Crear un controlador normal**

Para crear un controlador normal podemos usar:

```cmd
nest generate controller cats
```

o también podemos usar la versión abreviada:

```
nest g co cats
```

#### **2. ### Evitar que cree los archivos de pruebas:**

Cuando creamos un controlador de la forma cotidiana, se crea un archivo que no esperábamos, llamado "**name_controller.specs.ts**". Este archivo sirve para crear las pruebas unitarias de este controlador.

Si no quieres que se cree tal archivo, puede ingresar el siguiente comando:

```cmd
nest g co cats --no-spec
```

#### **3. Ver un preview de lo qué va a crear el CLI:**

Existe otro comando que permite ver lo que haría el generador de código del CLI antes que modifique ningún archivo en el sistema. Para realizar esta acción, debemos insertar el siguiente comando:

```cmd
nest g co cats --dry-run
```

#### **### 4. Colocar los controladores en otras rutas:**

Ahora vamos a suponer que necesitas crear una **estructura de carpetas diferente** a la que el CLI genera. Por ejemplo, si quieres tener una carpeta llamada "controllers" y dentro de ella meter todos tus controladores.

Esto lo puedes hacer insertando el siguiente comando:

```cmd
nest g co controllers/cats
```

Esas serían las diferentes formas de crear un controlador.