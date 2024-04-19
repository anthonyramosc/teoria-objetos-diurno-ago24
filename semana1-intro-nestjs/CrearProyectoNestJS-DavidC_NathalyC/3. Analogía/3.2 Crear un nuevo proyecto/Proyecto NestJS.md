## Pasos para crear un nuevo proyecto en NestJS

### 1. Crea un nuevo proyecto

Después de instalar la CLI de Nest en el apartado de [[Instalar Nest JS]], ahora puedes crear un nuevo proyecto Nest. Abre el directorio donde quieras crear tu proyecto y ejecuta el siguiente comando, sustituyendo "**project_name**" por el nombre de tu proyecto:

```cmd
nest new project_name
```

Después de ejecutar el comando para crear un nuevo proyecto, te aparecerá una pantalla como la siguiente:

![[Pasted image 20240407193017.png]]

La CLI te pedirá que elijas un gestor de paquetes (npm o Yarn). Selecciona tu opción preferida, y la CLI creará un nuevo proyecto Nest con el gestor de paquetes que tu eligas.

### 2. Inicia la aplicación que acabas de crear

Navega al directorio del proyecto recién creado utilizando el símbolo del sistema, con el siguiente comando:

``` cmd
cd nest-app
```

Después inicia la aplicación ejecutando el siguiente comando:

``` cmd
npm run start
```

Este comando inicia el servidor de desarrollo, que visualizará todos los cambios dentro de los archivos y recargará automáticamente la aplicación cuando realices actualizaciones.

### 3. Prueba en localhost

Abre tu navegador web y navega hasta [localhost:3000](http://localhost:3000). Deberías ver el mensaje de bienvenida predeterminado de la aplicación Nest: «**¡Hello World!»**

![[Pasted image 20240407195105.png | 500]]

La navegación del localhost puede variar, puede ingresar en el archivo main.ts de su proyecto para identificar la **URL** de su aplicación, tal como se muestra en la imagen: 

![[Pasted image 20240407193836.png]]

El número que se encuentra en el código:

``` typescript
async function bootstrap() {
const app = await NestFactory.create(AppModule);
await app.listen(3000);
}
```

El número "**3000**" del código es la dirección de **localhost**, es decir:

Si el número es **8080**, entonces la url será [localhost:8080](http://localhost:8080)

```
███████ ███████ ██      ██  ██████ ██ ██████   █████  ██████  ███████ ███████ 
██      ██      ██      ██ ██      ██ ██   ██ ██   ██ ██   ██ ██      ██      
█████   █████   ██      ██ ██      ██ ██   ██ ███████ ██   ██ █████   ███████ 
██      ██      ██      ██ ██      ██ ██   ██ ██   ██ ██   ██ ██           ██ 
██      ███████ ███████ ██  ██████ ██ ██████  ██   ██ ██████  ███████ ███████
```