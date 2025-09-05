Buscar en google "Google Cloud Console gmail api", 
https://console.cloud.google.com/auth/
aceptar las condiciones y habilidar la funcion de Gmail API

crear Credenciales, ir a Crear ID de cliente de OAuth:
# completar datos de la app
Información de la app
    Nombre de la aplicación
        TestDjangoApp
El nombre de la aplicación que solicita el consentimiento
Correo electrónico de asistencia del usuario
            sebastian.marquez@esim.edu.ar

Public: Usuarios Externos
Informacion de contacto: corre@gmail.com
Aceptar condiciones

# Crear ID de cliente de OAuth
Un ID de cliente se usa con el fin de identificar una sola app para los servidores de OAuth de Google. Si la app se ejecuta en varias plataformas, cada una necesitará su propio ID de cliente. Consulta Configura OAuth 2.0  para obtener más información. Obtén más información  sobre los tipos de clientes de OAuth.

Tipo de aplicación
    Aplicación web
Nombre
    Cliente-Escritorio1
URIs de redireccionamiento autorizados → agregá

    http://localhost:8000/google/callback
    Descargar Json

# dependencias
pip install google-api-python-client google-auth google-auth-oauthlib python-dotenv
# opcional para sanitizar HTML de correos
pip install bleach

# crear proyecto y app
django-admin startproject mibandejagmail 
cd mibandejagmail 
python manage.py startapp gmailbox

# en caso de error No se pudo obtener el token: (insecure_transport) OAuth 2 MUST 
En PowerShell ingresar:

$env:OAUTHLIB_INSECURE_TRANSPORT = "1"
python manage.py runserver

# Correr las migraciones y ejecutar el proyecto
python manage.py migrate
python manage.py runserver