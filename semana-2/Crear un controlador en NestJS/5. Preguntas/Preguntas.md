## Nathaly Caballero

1. *¿Qué responsabilidad tienen los controladores?*
   - [ ] Manejar las solicitudes y enviar las respuestas correspondientes al cliente.
   - [ ] Crear una sola ruta para que sea responsable de diversas acciones.
   - [ ] Representar el objeto request.

**Respuesta correcta:** A. Porque utiliza un enfoque de separación de responsabilidades para mejorar la organización del código y facilitar su mantenimiento y poder adaptarse fácilmente a diferentes tipos de clientes.

2. *¿Cuál es el propósito de usar un prefijo de ruta en el decorador `@Controller()` en NestJS?*
   - [ ] Para definir métodos HTTP específicos como GET o POST para las rutas del controlador.
   - [ ] Para agrupar un conjunto de rutas relacionadas bajo un prefijo común, reduciendo la redundancia en la definición de rutas.
   - [ ] Para especificar diferentes métodos de autenticación para las rutas que están bajo el controlador.

**Respuesta correcta:** B. Porque todas las rutas definidas en el controlador pueden compartir un prefijo común en este caso, "cats", lo que evita la necesidad de repetir esta parte de la ruta en cada una de las rutas subyacentes del controlador. Esto hace que el código sea más organizado y menos propenso a errores, ya que se maneja la base de la ruta en un solo lugar.

3. *¿Cómo puede un controlador en NestJS obtener acceso al objeto request de la plataforma subyacente?*
   - [ ] Utilizando el decorador `@Inject()` para inyectar el objeto request directamente en el constructor del controlador.
   - [ ] Agregando el decorador `@Req()` a un parámetro en el método del controlador para inyectar el objeto request.
   - [ ] Llamando a una función global `getRequest()` dentro del método del controlador.

**Respuesta correcta:** B. Porque para obtener el objeto request en un controlador de NestJS, se debe utilizar el decorador `@Req()`. Este decorador se aplica a un parámetro en el método del controlador, lo que permite que NestJS inyecte automáticamente el objeto request de la plataforma subyacente, que por defecto es Express.

## David Correa

4. *¿Qué decorador se debe utilizar en NestJS para crear un controlador que maneje solicitudes de creación de nuevos registros?*
   - [ ] `@Put()`
   - [ ] `@Post()`
   - [ ] `@Get()`

**Respuesta correcta:** B. El uso de `@Post()` indica al framework que el método designado es el responsable de procesar las solicitudes POST enviadas a la ruta especificada.

5. *¿Cómo se puede acceder a un parámetro dinámico de ruta en un método de un controlador en NestJS?*
   - [ ] Utilizando el decorador `@Body()` para extraer el parámetro de la ruta.
   - [ ] Utilizando el decorador `@Query()` para capturar el parámetro de la ruta.
   - [ ] Utilizando el decorador `@Param()` para acceder al parámetro de la ruta.

**Respuesta correcta:** C. El decorador `@Param()` en NestJS se utiliza para anotar un parámetro del método del controlador, permitiendo que los parámetros de la ruta sean accesibles dentro del método.

6. *¿Cómo asegura NestJS que un controlador específico, como CatsController, sea reconocido y manejado por el framework?*
   - [ ] Registrando el CatsController directamente en el servidor principal de la aplicación.
   - [ ] Incluyendo CatsController en el array de controladores dentro del decorador `@Module()` en el módulo correspondiente.
   - [ ] Instalando un paquete npm adicional que automáticamente registre todos los controladores.

**Respuesta correcta:** B. Porque debe ser incluido en el array de controladores en el decorador `@Module()` de algún módulo, típicamente en el módulo donde se va a usar o en el módulo raíz de la aplicación si no se especifica otro módulo. NestJS puede fácilmente identificar y crear instancias de los controladores listados, gestionando así las solicitudes dirigidas a sus rutas.
