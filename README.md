# function-app-azure

The steps to set up all are in the following links:

## Create a single database - Azure SQL Database
https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal

## Create a Function APP
https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-python?pivots=python-mode-configuration

## Connect Azure Functions to Azure SQL Database using Visual Studio Code
https://learn.microsoft.com/en-us/azure/azure-functions/functions-add-output-binding-azure-sql-vs-code?pivots=programming-language-python&tabs=in-process%2Cv1

After configure that, its very simple to work.

In the azure extension in Visual Studio Code, you can create a new function. This function is created in a local folder that you have choose in the VS Code. 

Archivos principales:

1) local.settings.json:
	Este archivo es comun para todo un **resource group**, no solo para una función. Entonces, en este archivo vas a poder definir las credenciales para acceder a la base de datos SQL con el parámetro **SqlConnectionString**, también vas a poder definir variables de entorno para acceder desde la función.

2) function.json
	Este archivo es particular para cada funcion. Acá vas a definir los **bindings** que son simples definiciones que escribis una sola vez y podes usarlas de manera fácil en el código. Por ejemplo, podes definir el Timer Trigger, definir el nombre de una query a la base de datos o definir el nombre para acceder a una tabla de la base de datos para escribir una fila nueva (es obligatorio, definir la direccion del binding cuando definir el acceso a una tabla de la base de datos, es decir si queres acceder a la tabla "token" de la base de datos (que vas a tener que haber permitido el acceso a esta base en local.settings.json previamente) tanto para leerla como para escribirla, entonces vas a necesitar 2 bindings definidos.
	
3) __init__.py_
	Es la función en python definida para cada function. **Le tenes que pasar como parámetros los bindings creados en function.json para poder utilizarlos**

4) requirements.txt
	Es necesario definir todos los módulos que se van a utilizar en el resource group para que pueda instalarlos en la maquina virtual que se crea.
