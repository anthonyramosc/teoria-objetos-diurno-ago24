## Decoradores de controladores en NestJS

Los decoradores dentro de NestJS permiten configurar y extender la funcionalidad de los controladores. Estos decoradores proporcionan una sintaxis clara y expresiva para definir la estructura y el comportamiento de los controladores, lo que facilita la lectura y el mantenimiento del código.

En la siguiente imagen, se muestra el controlador más común de NestJS(cats), donde están definidos varios decoradores:

![](https://lh6.googleusercontent.com/xShgusM4Bu1se0qyhMIrVyDpu7Jat_1NYJZbrUa0LpbHm01d8ZYygT4l9OzlGaltNNtrpN_KhONOT498Fw8YVfs_cpeRIEn7xP_YwIASy7alyX9JdPQ1FIdD8F8mZWlUr1qDufn0sctPZlV6f_DOYHOSrm8L48dPnoR7HjTq5vfhRFMOEAm5IUOaxpKueg)

Ahora vamos a ver el funcionamiento de el controlador y los decoradores de la imagen:

1. **Importación**: Se importa el `Controller` y `Get` desde el paquete `@nestjs/common`, que proporciona los decoradores básicos para la construcción de controladores.

2. **Definición del controlador**: El decorador `@Controller('cats')` define que este controlador manejará las solicitudes dirigidas a la ruta base `/cats`.

3. **Método `@Get()`**: El decorador `@Get()` define un método HTTP GET que responderá a la ruta `/cats`. El método `findAll()` devolverá una cadena que dice "This action returns all cats".

4. **Método `findAll()`**: Este método simplemente devuelve la cadena "This action returns all cats".

5. **Exportación del controlador**: La clase `CatsController` se exporta para que pueda ser utilizada en otro lugar de la aplicación.

En resumen, este código define un controlador básico de gatos en NestJS, con un único método GET que devuelve una cadena de texto.

## Decoradores Principales

1. `@Controller()`
   - **Definición**: Define la ruta base del controlador.
   - **Uso**: Se utiliza para especificar la ruta base del controlador. Esto establece el prefijo de ruta para todas las rutas definidas en el controlador.

2. `@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`
   - **Definición**: Definen los métodos HTTP permitidos para una ruta específica.
   - **Uso**: Se utilizan para indicar el método HTTP que se manejará en una ruta determinada. Estos decoradores se colocan antes de los métodos del controlador.

3. `@Param()`
   - **Definición**: Permite acceder a los parámetros de la ruta.
   - **Uso**: Se utiliza para inyectar los parámetros de la ruta en los métodos del controlador. Esto permite procesar y responder a solicitudes dinámicas.

4. `@Body()`
   - **Definición**: Permite acceder al cuerpo de la solicitud HTTP.
   - **Uso**: Se utiliza para inyectar el cuerpo de la solicitud HTTP en los métodos del controlador. Esto permite procesar los datos enviados por el cliente.

5. `@Query()`
   - **Definición**: Permite acceder a los parámetros de consulta de la solicitud HTTP.
   - **Uso**: Se utiliza para inyectar los parámetros de consulta de la solicitud HTTP en los métodos del controlador. Esto permite procesar y responder a solicitudes con parámetros de consulta.

6. `@Headers()`
   - **Definición**: Permite acceder a los encabezados de la solicitud HTTP.
   - **Uso**: Se utiliza para inyectar los encabezados de la solicitud HTTP en los métodos del controlador. Esto permite procesar y responder a solicitudes con información específica en los encabezados.

7. `@Res()` y `@Req()`
   - **Definición**: Permiten acceder directamente al objeto de respuesta y solicitud HTTP, respectivamente.
   - **Uso**: Se utilizan para inyectar el objeto de respuesta o solicitud HTTP en los métodos del controlador. Esto permite un mayor control y personalización de la respuesta HTTP.

8. `@HttpCode()`, `@Header()` y `@Redirect()`
   - **Definición**: Permiten personalizar la respuesta HTTP.
   - **Uso**: Se utilizan para establecer el código de estado HTTP, agregar encabezados personalizados y redirigir la respuesta, respectivamente.

9. `@UseGuards()`, `@UseInterceptors()` y `@UsePipes()`
   - **Definición**: Permiten aplicar guardias, interceptores y tuberías a los controladores.
   - **Uso**: Se utilizan para agregar funcionalidad adicional a los controladores, como autenticación, transformación de datos y validación.

Cada uno de los decoradores desempeña un papel crucial en la configuración y el comportamiento de los controladores, lo que ayuda a mantener una aplicación organizada y escalable.

### Explicación de Controlador

```typescript
import { Body, Controller, Get, Param, Post, Put } from '@nestjs/common';
import { CreateCatDto } from './dto/create-cat.dto';
import { UpdateCatDto } from './dto/update-cat.dto';
import { Cat } from './entities/cat.entity';
import { CatsService } from './cats.service';

@Controller('cats')
export class CatsController {
  constructor(private readonly catsService: CatsService) {}

  @Get()
  findAll(): Cat[] {
    return this.catsService.findAll();
  }

  @Get(':id')
  findOne(@Param('id') id: string): Cat {
    return this.catsService.findOne(id);
  }

  @Post()
  create(@Body() createCatDto: CreateCatDto): Cat {
    return this.catsService.create(createCatDto);
  }

  @Put(':id')
  update(@Param('id') id: string, @Body() updateCatDto: UpdateCatDto): Cat {
    return this.catsService.update(id, updateCatDto);
  }
}
```

Vamos a analizar el código del controlador paso a paso:

1. **Importaciones**:
   - Se importan varios decoradores de `@nestjs/common`, como `Body`, `Controller`, `Get`, `Param`, `Post` y `Put`. Estos decoradores se utilizan para definir la estructura y el comportamiento del controlador.
   - Se importan dos clases DTO (Data Transfer Object): `CreateCatDto` y `UpdateCatDto`, que se utilizarán para manejar los datos de creación y actualización de gatos.
   - Se importa la entidad `Cat`, que probablemente representa la estructura de un gato.
   - Se importa el servicio `CatsService`, que se utilizará para interactuar con la lógica de negocio relacionada con los gatos.

2. **Definición del controlador**:
   - El decorador `@Controller('cats')` define que este controlador manejará las solicitudes dirigidas a la ruta base `/cats`.

3. **Inyección de dependencia**:
   - En el constructor del controlador, se inyecta el servicio `CatsService`. Esto permite que el controlador acceda a la lógica de negocio relacionada con los gatos.

4. **Método `@Get()`**:
   - El decorador `@Get()` define un método HTTP GET que responderá a la ruta `/cats`.
   - El método `findAll()` llama al servicio `CatsService.findAll()` para obtener una lista de todos los gatos y la devuelve.

5. **Método `@Get(':id')`**:
   - El decorador `@Get(':id')` define un método HTTP GET que responderá a la ruta `/cats/:id`.
   - El método `findOne()` utiliza el decorador `@Param('id')` para acceder al parámetro de ruta `id`, y luego llama al servicio `CatsService.findOne(id)` para obtener un gato específico y lo devuelve.

6. **Método `@Post()`**:
   - El decorador `@Post()` define un método HTTP POST que responderá a la ruta `/cats`.
   - El método `create()` utiliza el decorador `@Body()` para acceder a los datos enviados en el cuerpo de la solicitud (representados por la clase `CreateCatDto`). Luego, llama al servicio `CatsService.create(createCatDto)` para crear un nuevo gato y devuelve el resultado.

7. **Método `@Put(':id')`**:
   - El decorador `@Put(':id')` define un método HTTP PUT que responderá a la ruta `/cats/:id`.
   - El método `update()` utiliza el decorador `@Param('id')` para acceder al parámetro de ruta `id` y el decorador `@Body()` para acceder a los datos de actualización (representados por la clase `UpdateCatDto`). Luego, llama al servicio `CatsService.update(id, updateCatDto)` para actualizar un gato específico y devuelve el resultado.

Al final nos dimos cuenta que este controlador expone cuatro endpoints HTTP: obtener una lista de todos los gatos, obtener un gato por su id, crear un nuevo gato y actualizar un gato existente. El controlador utiliza la inyección de dependencias para acceder a los servicios relacionados con la lógica de negocio de los gatos.

##### Referencias:
- _Manual de NeSTJS_. (s. f.). DesarrolloWeb.com. https://desarrolloweb.com/manuales/manual-nestjs.