 

# Robot ROMO 

## 1. Descripción del robot   

Robot automático para monitoreo de transacciones de servicios inteligentes que requieren resolución de recaptcha. 

 

### - Utilidad 
 

Garantizar el funcionamiento y validar la página de sistema de pagos de Bancoomeva (https://pagospse.bancoomeva.com.co/psehosting/#/productos) y oficina virtual (https://oficinavirtual.bancoomeva.com.co/IB/presentation/bccp_mb/index.htm) sin interacción humana y con códigos captcha, enviando un archivo Excel del resultado del monitoreo, esta validación se repite cada 2 horas. 

 

Antes de ejecutar el robot se debe instalar y configurar correctamente para su uso (Ver sección 3) 

 

## 2. Requerimientos técnicos 

 

 ![1](https://user-images.githubusercontent.com/88993846/143276307-c0a6925f-b64f-4afe-88ff-478c010557e4.JPG)


 

## 3. Procedimiento de Instalación, configuración y ejecución del robot 

 

### - Instalación y licenciamiento de ROCKETBOT  

 

1. Descargar ROCKETBOT (https://www.rocketbot.com/en/studio/) disponible en Windows, Linux y Mac. 

 ![2](https://user-images.githubusercontent.com/88993846/143276355-0e9b70d3-ff98-4de9-8623-9d40315a6adc.JPG)


2. Descomprimir archivo .ZIP. 

3. Entrar en la carpeta y ejecutar Rocketbot.exe 

4. Se abrirá el navegador predeterminado y requerirá una licencia 

 

 
![3](https://user-images.githubusercontent.com/88993846/143276396-0f4cfe34-c9f1-4239-841a-6e1d4d5689ad.JPG)

 

La licencia se puede obtener en el siguiente link (https://license.rocketbot.co/) y llenando el formulario de la imagen inferior, el token del formulario se encuentra en el navegador abierto por Rocketbot. 

 
![4](https://user-images.githubusercontent.com/88993846/143276450-91b176cb-de64-42cd-a1bb-010038ce0fad.JPG)

 

Al enviar el formulario, se enviará el código de licencia al correo registrado, para finalmente pegarlo en el navegador abierto por Rocketbot y activarlo.  

 

### - Instalación y configuración de robot ROMO  

 

1. Descargar el robot (ROMO) del repositorio archivo .db (https://github.com/CrisMBG1/Robot_Bancoomeva)  


2. Importar el robot a Rocketbot pulsando Cargar DB de proyecto: 

 ![5](https://user-images.githubusercontent.com/88993846/143276477-24b59942-5baf-45ab-85a2-d91d7e31cbb3.JPG)
 

3. Abrir el robot (Robot_Bancoomeva.db) y seleccionar Sistema_Pagos_Ingreso. 

  
![6](https://user-images.githubusercontent.com/88993846/143276489-f6757137-be0c-4dd3-acd5-8cf8516946d0.jpg)
 

4. Una vez abierto se deben instalar los módulos (2captcha, webpro y Files) en install mods: 

 ![7](https://user-images.githubusercontent.com/88993846/143276640-595d2cf9-c979-40bf-b97d-4f067b1b1a7b.jpg)


Y realizar la siguiente búsqueda e instalación.  

 
![8](https://user-images.githubusercontent.com/88993846/143276955-ba931c0d-1daf-47e8-9bf6-dfef974e4f65.JPG)

 

5. En variables se debe definir la ubicación (Dirección) donde se va a guardar el archivo Excel donde se almacena el monitoreo, verificar que la dirección contenga el símbolo “/” en lugar de “\”. 

 

Ejemplo: "C:\Users\Carpeta\Carpeta2" 

Cambiando "\" por "/":  

 "C:/Users/Carpeta/Carpeta2" 

 

Email, contraseña de email y email del destinatario, si no se logra enviar el correo electrónico (Ver solución a errores comunes).  

Si se tiene el api key para la solución de módulos recaptcha se debe agregar y hacer los pasos de la etapa (4. Módulos externos) 

 

Por defecto el número de documento que se usa para ingresar al sistema de pagos es C.C 94492704, tomado por las credenciales compartidas por la mesa que realiza la tarea de verificación, pero se puede modificar este número de documento en las variables.  

 
![9](https://user-images.githubusercontent.com/88993846/143277035-7bb9895c-a83e-4465-8039-9b755a3b41fa.JPG)

 

### - Ejecutar el Robot  

Una vez configurado y definido las variables para hacer la ejecución del robot se debe dar clic en ejecutar, posteriormente se abrirá el navegador y cuando ingrese el número de documento se soluciona el captcha manualmente (Para automatizar el captcha ver 4. Instalación de modulo externo 2Captcha) 


![10](https://user-images.githubusercontent.com/88993846/143277130-93328bdb-344f-4d6c-b970-3e628b0af9ba.JPG)


En caso de querer parar el robot, alguna falla o modificar algo: 

 

Se debe abrir el debugger del robot (este se abre automáticamente cuando se ejecuta), clic en Stop y cerrar:  


 ![11](https://user-images.githubusercontent.com/88993846/143277174-f253ad2a-5685-4408-b2ca-587f0dcce61f.JPG)


Ir a rocketbot y asegurarse de que no esté activo (Botón de Detener en color rojo oscuro) de lo contrario darle a detener. 

 

![12](https://user-images.githubusercontent.com/88993846/143277203-7189ee0f-f95a-46c7-8d0c-c9b3d163b9ae.JPG)


 

## 4. Solución a errores comunes 

 

### - Error al abrir navegador 

Este error se debe a la versión de ChromeDriver que tiene instalada por defecto ROCKETBOT.  

 
![13](https://user-images.githubusercontent.com/88993846/143277274-086177ee-d76a-458e-9add-55bd379011d8.JPG)

 

El error muestra la versión de ChromeDriver que debe tener ROCKETBOT, para esto se dirige a él link (https://chromedriver.storage.googleapis.com/index.html) y se selecciona la versión que muestra el error y se descarga el archivo .zip. 

 

 ![14](https://user-images.githubusercontent.com/88993846/143277313-ba5398ae-0d64-436c-bdef-778f63e86f27.JPG)


Una vez descargado el archivo .zip, se extrae, y se copia el archivo extraido para pegarlo en la carpeta (....\Rocketbot\drivers\win\chrome) donde se descargó ROCKETBOT y se reemplaza. 

Si estás en mac debes ir a rocketbot/drivers/mac/chrome 

 

### - No envía el correo electrónico  

 

El correo electrónico que enviará el email debe habilitar el uso de aplicaciones poco seguras y debe ser GMAIL, debido a los módulos usados en ROMO. Para esto se debe: 

1. Ingresar a la cuenta de Gmail 


2. Dar clic en la imagen de tu cuenta de Gmail. 

 ![15](https://user-images.githubusercontent.com/88993846/143277370-a58e204d-0366-4bd0-beff-a89a632c9c84.JPG)


3. Luego dar clic en “Administra tu Cuenta de Google” 

 ![16](https://user-images.githubusercontent.com/88993846/143277395-e5c210cb-59de-4531-8e52-8f7f69da757a.JPG)


 4. Clic en “Seguridad” 

 ![17](https://user-images.githubusercontent.com/88993846/143277411-5c6c4cf7-9756-4b42-8222-e7d46406ae99.JPG)


5. Ir al apartado “Acceso de apps menos seguras” y dar click en “Activar el acceso” 

 ![18](https://user-images.githubusercontent.com/88993846/143277427-33221009-80fb-44c2-8e42-75e707769224.JPG)


6. Finalmente activar “Permitir el acceso de apps menos seguras” 

  ![19](https://user-images.githubusercontent.com/88993846/143277439-8dc130a0-91d7-4537-84d2-36450a027460.JPG)


Si se utiliza otro tipo de dominio de correo electrónico se debe cambiar el robot Enviar_Email con los módulos correspondientes a ese dominio de correo. 

 

## 5. Instalación de modulo externo 2Captcha: 

Para agregar el módulo reCaptcha se debe: 

1. Crear una cuenta en la página (https://2captcha.com/). 

2. Agregar fondos (Monto mínimo de 3 dólares + IVA). 

3. Copiar la API Key generada en 2Captcha. 

4. Pegar el API Key en el módulo 2Captcha ubicado en el robot principal Sistema_Pagos_Ingreso.  

 
![20](https://user-images.githubusercontent.com/88993846/143277543-eb963114-b9aa-4f55-8204-b8360bf757df.JPG)

 
5. Ir a la pestaña Robot y abrir el robot P1_Ingreso_inicial_Servicio. 

6. Habilitar los 2 comandos deshabilitados y eliminar comando de esperar. 

![21](https://user-images.githubusercontent.com/88993846/143277595-a0dfe389-68ce-4b42-86ca-95a3dc822759.JPG)

 

## 6. Descripción del proceso  

**Robot 1 - Monitoreo del funcionamiento del sistema de pagos - Bancoomeva** 

1. Abrir navegador  
   
2. Buscar enlace: https://pagospse.bancoomeva.com.co/psehosting/#/productos    

3. Verificar estado de la página y agregar estado a Excel   

4. Clic estado de cuenta asociado    

5. Número de identificación y código de seguridad  

6. Verificar estado del inicio de sesión y agregar estado a Excel   

7. Seleccionar el valor a pagar   

8. Selecciona la opción de PSE  

9. Verificar estado de la página ACH y agregar estado a Excel   

10. Abre proveedor de pagos   

11. Selecciona el Bancoomeva y continuar    

12. Verificar estado de la página de PSE y agregar estado a Excel   

13. Se ingresa el correo electrónico y luego ir al banco    

14. Verificar estado de sistema de pagos y agregar estado a Excel   

15. Clic en persona natural    

16. Se selecciona el tipo de documento y numero de ID y clic en iniciar sesión  

17. Ingresa contraseña   

18. Clic en ingresar   

19. Verificar la página de selección de cuenta y agregar estado a Excel   

20. Envió del Email con Excel de estados de la pagina  

21. Cerrar conexión  

 

**Robot 2 - Monitoreo del funcionamiento oficina virtual - Bancoomeva**	 

1. Abrir nueva pestaña  

2. Buscar enlace: https://oficinavirtual.bancoomeva.com.co/IB/presentation/bccp_mb/index.htm  

3. Verificar estado de la página y agregar estado a Excel   

4. Ingresar número de documento  

5. Clic en iniciar sesión  

6. Verificar estado del inicio de sesión y agregar estado a Excel   

7. Ingresar la contraseña  

8. Clic en iniciar sesión  

9. Verificación del funcionamiento de todas las pestañas y agregar estado a Excel 

 

## 7. Arquitectura del robot 

El robot este compuesto de por tres etapas, donde inicialmente se tienen las variables de entrada, el robot padre que llama a los módulos robots hijos para facilitar el Código y la etapa de salida que envía el archivo Excel a un correo electrónico.  

 

 ![22](https://user-images.githubusercontent.com/88993846/143277684-2996ef9e-24db-4b0e-82cf-e36d6617ae1e.JPG)


## 8. Descripción individual de los módulos  

 

### - Sistema_pagos_Ingreso 

Robot padre donde se controlan todos los robots y contiene la serie total de pasos para el monitoreo de las páginas de sistema de pagos y oficina virtual. Ver diagrama completo (https://github.com/CrisMBG1/Robot_Bancoomeva) 

 

 

### - P1_Ingreso_inicial_Servicio 

Robot que hace el proceso de inicio de sesión y resolución del módulo reCaptcha.  

 

 

### - Crear Excel 

Robot para la creación del archivo Excel que almacena el monitoreo.  

 

 

### - Agregar Excel  

Robot que agrega los estados del proceso de monitoreo al Excel.  

 

 

 

### - Enviar_Email 

Robot que realiza él envió del email configurando el servidor de Gmail, verificar la apertura y envió de archivo Excel con el monitoreo.  

 

 

 

 

## 9. Actividades pendientes 

Pagar y Habilitar el módulo 2Captcha (Ver sección de 4. Instalación de modulo externo 2Captcha) o este video explicativo del fabricante para añadir el reCaptcha (https://www.youtube.com/watch?v=BDDghM17ZCk) 

 

Tener el licenciamiento para la ejecución del robot para realizar la implementación, debido a que se quiere que el robot este activo continuamente, para más información sobre el licenciamiento se puede comunicar a siguiente teléfono 3187068554 asesora de Rocketbot en Colombia.  
