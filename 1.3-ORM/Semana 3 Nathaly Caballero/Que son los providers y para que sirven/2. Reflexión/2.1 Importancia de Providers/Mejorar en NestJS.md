## Importancia de Providers

Los **providers** en NestJS son componentes fundamentales para la aplicación, ya que cumplen varias funciones importantes:

1. **Inyección de Dependencias (DI)**: Los proveedores son los objetos que se inyectan en otros componentes, como controladores, servicios u otros proveedores. Esto permite la creación de aplicaciones modularizadas y desacopladas, lo que facilita la reutilización del código y la realización de pruebas unitarias.

2. **Organización del Código**: Los proveedores ayudan a organizar el código de la aplicación. Al definir servicios, controladores y otros componentes como proveedores, se establece una estructura clara y coherente para la aplicación, lo que facilita su mantenimiento y escalabilidad.

3. **Gestión de la Lógica de Negocio**: Los proveedores encapsulan la lógica de negocio de la aplicación. Por ejemplo, un servicio puede contener métodos para acceder y manipular datos, mientras que un controlador puede manejar las solicitudes HTTP y delegar la lógica de negocio al servicio correspondiente.

4. **Configuración de la Aplicación**: Los proveedores pueden utilizarse para gestionar la configuración de la aplicación, como la conexión a la base de datos, la autenticación, la autorización, entre otros aspectos. Esto permite una configuración centralizada y flexible de la aplicación.

5. **Extensibilidad**: Los proveedores en NestJS son extensibles y personalizables. Pueden ser decorados con diferentes decoradores y configurados con opciones específicas según las necesidades de la aplicación. Esto facilita la adaptación de la aplicación a diferentes entornos y requisitos.

## CLI

La CLI o Línea de comandos es una de las cosas que nos hará más simple la vida pues nos permite de forma rápida crear archivos con la estructura necesaria par el correcto funcionamiento con el framework. Es algo que actualmente los frameworks o librerías enfocadas a enterprise ven ya como parte de un mínimo para su distribución. Por estas razones es importante leer el apartado de [Scrips CLI en NestJS](https://docs.nestjs.com/cli/scripts).

## Documentación

La documentación de un proyecto es algo que a la mayoría de desarrolladores no nos encanta. Pues dentro de NestJS, con solo un simple comando tendremos una documentación bastante rigurosa, entendible e incluso interactiva del proyecto gracias al generador [compodoc](https://compodoc.app/). Para ello solo escribiremos lo siguiente en la raíz de nuestro proyecto:

``` cmd
npx @compodoc/compodoc -p tsconfig.json -s
```

Esto genera una carpeta **documentation** en la raíz del proyecto y levanta un servicio [HTTP](https://es.wikipedia.org/wiki/Protocolo_de_transferencia_de_hipertexto) para que podamos verlo en [http://localhost:8080](http://localhost:8080/):
