# Robot_Bancoomeva

1. Descripción del robot  

 

Robot automático para monitoreo de transacciones de servicios inteligentes que requieren resolución de reCaptcha. 

 

Utilidad  

 

Garantizar el funcionamiento y validar la página de sistema de pagos de Bancoomeva (https://pagospse.bancoomeva.com.co/psehosting/#/productos) y oficina virtual (https://oficinavirtual.bancoomeva.com.co/IB/presentation/bccp_mb/index.htm) sin interacción humana y con códigos captcha, enviando un archivo Excel del resultado del monitoreo.  

Antes de ejecutar el robot se debe instalar y configurar correctamente para su uso (Ver sección 3) 

 
![Diagrama flujo robot](https://user-images.githubusercontent.com/88993846/143071546-89326a6f-77f7-4a3f-af53-d117751174b6.jpg)

Requerimientos técnicos 

 

 

 

Procedimiento de Instalación del robot 

 

Instalación y licenciamiento de ROCKETBOT  

 

Descargar ROCKETBOT (https://www.rocketbot.com/en/studio/) disponible en Windows, Linux y Mac. 

 

Descomprimir archivo .ZIP. 

Entrar en la carpeta y ejecutar Rocketbot.exe 

Se abrirá el navegador predeterminado y requerirá una licencia 

 

 

 

La licencia se puede obtener en el siguiente link (https://license.rocketbot.co/) y llenando el formulario de la imagen inferior, el token del formulario se encuentra en el navegador abierto por Rocketbot. 

 

 

Al enviar el formulario, se enviará el código de licencia al correo registrado, para finalmente pegarlo en el navegador abierto por Rocketbot y activarlo.  

 

Instalación y configuración de robot ROMO  

 

Descargar el robot (ROMO) del repositorio archivo .db (https://github.com/CrisMBG1/Robot_Bancoomeva)  

 

Importar el robot a Rocketbot pulsando Cargar DB de proyecto: 

 

 

Abrir el robot (Robot_Bancoomeva.db) y seleccionar Sistema_Pagos_Ingreso. 

 

 

 

Una vez abierto se deben instalar los módulos (2captcha, webpro y Files) en install mods: 

 

Y realizar la siguiente búsqueda e instalación.  

 

 

En variables se debe definir la ubicación (Dirección) donde se va guardar el archivo Excel donde se almacena el monitoreo, ejemplo: C:/Users/Carpeta/Escritorio, verificar que la dirección contenga el símbolo “/” en lugar de “\”. Número de identificación, contraseña del usuario de prueba, email, contraseña de email y email del destinatario. Si se tiene el api key para la solución de módulos recaptcha se debe agregar y hacer los pasos de la etapa (Módulos externos) 

 

 

 

 

 

 

Configuración EMAIL 

 

En la pestaña Robot se da clic en el robot Enviar_Email 

 

 

 

Al abrir la pestaña se dirige a variables y se define el mail (Email que enviará el correo electrónico), pass (Contraseña del correo) y destinatario. 

 

 

 

Solución a errores comunes 

 

Error al abrir navegador 

 

Este error se debe a la versión de ChromeDriver que tiene instalada por defecto ROCKETBOT.  

 

 

El error muestra la versión de ChromeDriver que debe tener ROCKETBOT, para esto se dirige a él link (https://chromedriver.storage.googleapis.com/index.html) y se selecciona la versión que muestra el error y se descarga el archivo .zip. 

 

Una vez descargado el archivo .zip, se extrae, y se copia el archivo para pegarlo en la carpeta (....\Rocketbot\drivers\win\chrome) donde se descargó ROCKETBOT y se reemplaza.  

 

No envía el correo electrónico  

 

El correo electrónico que enviará el email debe permitir el uso de robots y debe ser GMAIL debido a los módulos usados en ROMO, si se utiliza otro tipo de dominio de correo electrónico se debe cambiar el robot Enviar_Email con los módulos correspondientes a ese dominio de correo.  

 

 

Arquitectura del robot 

 

El robot este compuesto de por tres etapas, donde inicialmente se tienen las variables de entrada, el robot padre que llama a los módulos robots hijos para facilitar el Código y la etapa de salida que envía el archivo Excel a un correo electrónico.  

 

 

Descripción individual de los módulos  

 

Sistema_pagos_Ingreso 

Robot padre donde se controlan todos los robots y contiene la serie total de pasos para el monitoreo de las páginas de sistema de pagos y oficina virtual.  

Ver diagrama compelto () 

 

 

P1_Ingreso_inicial_Servicio 

Robot que hace el proceso de inicio de sesión y resolución del módulo reCaptcha.  

 

 

Crear Excel 

Robot para la creación del archivo Excel que almacena el monitoreo.  

 

 

Agregar Excel  

Robot que agrega los estados del proceso de monitoreo al Excel.  

 

 

 

Enviar_Email 

Robot que realiza él envió del email configurando el servidor de Gmail, verificar la apertura y envió de archivo Excel con el monitoreo.  

 

 

 

 

 

 

Módulos externos 

 

2Captcha 

Para agregar el módulo reCaptcha se debe: 

 

Crear una cuenta en la página (https://2captcha.com/)  

Agregar fondos (Monto mínimo de 3 dólares + IVA) 

Copiar la API Key generada en 2Captcha 

Habilitar los 2 comandos deshabilitados y pegar el API Key en el modulo 2Captcha ubicado en el robot P1_Ingreso_inicial_Servicio.  

Interfaz de usuario gráfica, Texto, Aplicación, Correo electrónico

Descripción generada automáticamente 

 

Eliminar espera de 25 segundos para evitar la demora.  

 

Descripción del proceso  

 

Robot 1 - Monitoreo del funcionamiento del sistema de pagos - Bancoomeva  

 

Abrir navegador     

Buscar enlace: https://pagospse.bancoomeva.com.co/psehosting/#/productos   

Verificar estado de la página y agregar estado a Excel   

Clic estado de cuenta asociado    

Número de identificación y código de seguridad  

Verificar estado del inicio de sesión y agregar estado a Excel   

Seleccionar el valor a pagar   

Selecciona la opción de PSE  

Verificar estado de la página ACH y agregar estado a Excel   

Abre proveedor de pagos   

Selecciona el Bancoomeva y continuar    

Verificar estado de la página de PSE y agregar estado a Excel   

Se ingresa el correo electrónico y luego ir al banco    

Verificar estado de sistema de pagos y agregar estado a Excel   

Clic en persona natural    

Se selecciona el tipo de documento y numero de ID y clic en iniciar sesión  

Ingresa contraseña   

Clic en ingresar   

Verificar la página de selección de cuenta y agregar estado a Excel   

Envió del Email con Excel de estados de la pagina  

Cerrar conexión  

 

Robot 2 - Monitoreo del funcionamiento oficina virtual - Bancoomeva 	 

 

Abrir nueva pestaña  

Buscar enlace: https://oficinavirtual.bancoomeva.com.co/IB/presentation/bccp_mb/index.htm 

Verificar estado de la página y agregar estado a Excel   

Ingresar número de documento  

Clic en iniciar sesión  

Verificar estado del inicio de sesión y agregar estado a Excel   

Ingresar la contraseña  

Clic en iniciar sesión  

Verificación del funcionamiento de todas las pestañas y agregar estado a Excel 

 

 

Actividades pendientes 

 

Pagar y Habilitar el módulo 2Captcha (Ver sección de módulos externos) 

Hacer que el robot se ejecute durante cada 1 para la verificación de  

Tener el licenciamiento para la ejecución del robot.  

