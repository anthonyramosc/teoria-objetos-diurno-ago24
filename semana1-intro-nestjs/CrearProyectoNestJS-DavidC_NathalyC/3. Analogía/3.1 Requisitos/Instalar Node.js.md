## Versiones de Node.js

| Versión LTS                      | Versión Actual          |
| -------------------------------- | ----------------------- |
| Soporte a Largo Plazo (18 meses) | Última versión de Node  |
| Información adicional            | Menos soporte (8 meses) |
| Ayuda de la comunidad            | Exposición a errores    |

## Pasos para instalar Node.js

### 1. **Descargar el Instalador de Windows**
Primeramente se debe descargar el archivo de instalación [Windows (.msi)](https://nodejs.org/en/download/) del sitio web oficial de Node.js. Este instalador MSI cuenta con archivos esenciales para instalar, actualizar o modificar la versión existente de Node.js.

Es de destacar que el instalador también lleva el [Gestor de paguetes de Node.js (npm)](https://kinsta.com/es/base-de-conocimiento/que-es-npm/) dentro de él. Esto significa que no necesitas instalar el npm por separado.
> **Nota**
>- Al momento de abrir el instalador, asegúrese de seleccionar la versión correcta de su sistema operativo.
>	- **32 bits, 64 bits**

![[Pasted image 20240407161228.png]]

### 2.  Comenzar con el proceso de Instalación

Una vez ejecutado el archivo **.msi**, comenzará el proceso de instalación. 
Para seguir adelante, acepta el acuerdo de licencia de Node.js, marca la casilla **«Acepto»** y haz clic en **Siguiente**:

![[Pasted image 20240407161738.png]]

A continuación, elige una carpeta donde quieras **instalar Node.js:**
> **Nota**
> - Se recomienda que la instalación continúe en el directorio destinado por **Node.js**


![[Pasted image 20240407161912.png]]

En la siguiente pantalla no vamos a modificar ningún apartado, por lo que, para continuar haz clic en **Siguiente:**

![[Pasted image 20240407162422.png]]

Node.js te ofrece opciones para instalar herramientas para módulos nativos. Si estás interesado, haz clic en la casilla, de lo contrario haz clic en **Siguiente** para seguir con la opción predeterminada:

![[Pasted image 20240407162612.png]]

### 3. Ejecutar la Instalación de Node.js en Windows

En esta pantalla, debes dar clic en **Instalar** para comenzar con la instalación de Node.js

![[Pasted image 20240407162817.png]]

El sistema completará la instalación en unos segundos o minutos y te mostrará un mensaje de éxito. Haz clic en el botón **Finalizar** para cerrar el instalador de Node.js.

![[Pasted image 20240407162844.png]]

### 4. Verificar la Instalación de Node.js
Ahora que tienes Node.js, debemos comprobar que se ha instalado con éxito.

Para **Verificar** la instalación y la versión de Node.js, debes abrir el [CMD de Windows](https://www.lifewire.com/command-prompt-2625840) e introduce el siguiente comando: 

```cmd
Node --version
```

Y para comprobar la versión del Gestor de paquetes de Node.js (npm), introduce el siguiente comando: 

``` cmd
npm --version
```

Al momento de ejecutar cada comando, nos debe salir una pantalla como la siguiente: 

![[Pasted image 20240407163837.png]]

==**Links de Información:**==
[CMD](https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/cmd)
[npm](https://kinsta.com/es/base-de-conocimiento/que-es-npm/ )
[command prompt](https://www.lifewire.com/command-prompt-2625840)