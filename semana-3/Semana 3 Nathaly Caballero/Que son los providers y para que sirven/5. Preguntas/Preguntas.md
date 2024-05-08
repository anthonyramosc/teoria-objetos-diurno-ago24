## Nathaly Caballero

---
1. **¿Qué son los proveedores en Nest?**
   - [ ] a) Clases que gestionan el trabajo con los datos de la aplicación.
   - [ ] b) Componentes esenciales utilizados para la inyección de dependencias.
   - [ ] c) Conjunto de clases encargadas de realizar la inyección de servicios.
   
   **Respuesta correcta: b)**
   Explicación: Los proveedores en NestJS son componentes esenciales utilizados para la inyección de dependencias. La idea principal de un proveedor es permitir que los objetos creen relaciones entre sí, delegando en gran medida al sistema de ejecución de Nest la tarea de "conectar" estos objetos de manera eficiente.

2. **¿Cuál es uno de los principios básicos de la programación que la inyección de dependencia facilita?**
   - [ ] a) Separación del código por responsabilidades.
   - [ ] b) Coordinación directa entre módulos de la aplicación.
   - [ ] c) Dependencia directa entre clases y controladores.
   
   **Respuesta correcta: a)**
   Explicación: La inyección de dependencia facilita el principio de separación del código por responsabilidades. Al separar las responsabilidades de esta manera, el código se vuelve más modular, fácil de mantener y de probar. Además, permite reutilizar componentes en diferentes partes de la aplicación y facilita la introducción de cambios sin afectar a otras partes del sistema.

3. **¿Qué tarea se realiza automáticamente por el CLI al generar las clases inyectables?**
   - [ ] a) Declaración de servicios.
   - [ ] b) Configuración de controladores.
   - [ ] c) Declaración de proveedores mediante el decorador @Module().
   
   **Respuesta correcta: c)**
   Explicación: Al generar clases inyectables mediante el CLI de NestJS, se realiza automáticamente la declaración de proveedores mediante el decorador @Module(). Esto se debe a que Nest.js utiliza el concepto de módulos para organizar y estructurar la aplicación, y el decorador @Module() se utiliza para definir los módulos de la aplicación y especificar los proveedores que estarán disponibles dentro del módulo.

## David Correa

4. **¿Cuál es una responsabilidad de los servicios en Nest?**
   - [ ] a) Gestionar la lógica de negocio en una clase aparte.
   - [ ] b) Realizar operaciones de entrada y salida de datos en la base de datos.
   - [ ] c) Definir la estructura y diseño de la aplicación.
   
   **Respuesta correcta: a)**
   Explicación: Una de las responsabilidades de los servicios en NestJS es gestionar la lógica de negocio en una clase aparte. Los servicios encapsulan y gestionan la lógica de negocio de la aplicación en clases separadas, promoviendo así la modularidad y la separación de preocupaciones, lo que facilita el mantenimiento y la reutilización del código.

5. **¿Cómo se realiza la inyección de un servicio en un controlador en Nest?**
   - [ ] a) Importando el servicio y utilizando una función injectService().
   - [ ] b) Mediante una declaración explícita de dependencias en el constructor.
   - [ ] c) Importando el servicio y luego llamando a una función setService().
   
   **Respuesta correcta: b)**
   Explicación: La inyección de un servicio en un controlador en NestJS se realiza mediante una declaración explícita de dependencias en el constructor. Al definir parámetros en el constructor con el tipo de las clases que deseamos inyectar, aseguramos que Nest maneje la creación e inyección de estas dependencias de manera automática.

6. **¿Cuál es uno de los beneficios de utilizar proveedores en Nest para gestionar las dependencias entre los diferentes componentes de la aplicación?**
   - [ ] a) Aumentar el acoplamiento entre módulos.
   - [ ] b) Promover la creación de código menos legible y mantenible.
   - [ ] c) Fomentar la creación de código más legible, mantenible y fácil de probar.
   
   **Respuesta correcta: c)**
   Explicación: Uno de los beneficios de utilizar proveedores en NestJS para gestionar las dependencias entre los diferentes componentes de la aplicación es fomentar la creación de código más legible, mantenible y fácil de probar. Al separar las responsabilidades y promover la modularidad a través de la inyección de dependencias, se facilita la creación de código que es más claro, mantenible y más fácil de probar.

---