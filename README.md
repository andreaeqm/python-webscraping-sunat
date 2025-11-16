# Automatización de descarga de reportes de exportación

Nota: este es un proyecto en proceso. La primera etapa es la extracción de datos, pero luego tengo la intención de manejar estos datos en una sola base para analizar la heterogeneidad productiva de las firmas del sector agroexportador y su impacto en la dinámica del mismo sector.

## Objetivo

Automatizar la descarga de reportes de exportación para un conjunto de firmas desde el portal de Aduanet de la SUNAT.

Para ello, se transforma una tarea manual repetitiva (ingresar un RUC, hacer clic en las opciones para el reporte, descarga del archivo Excel) en un script automatizado que genera una carpeta para los archivos Excel de los reportes.

## Herramientas utilizadas

* Lenguaje: Python
* Librería principal: Selenium para la automatización del navegador web (navegación, ingreso de datos y clicks).
* Entorno: Jupyter Notebook

## Lógica del Script

1.  El primer paso es configurar el driver. Se inicia el `WebDriver` de Selenium, configurando una carpeta de descarga predeterminada donde se guardarán todos los reportes de Excel.
2.  En segundo lugar, se accede a la página de Aduanet.
3.  En tercer lugar, se declara una lista con las RUCs de las firmas cuyos reportes de exportación se requieren para el análisis. Por ejemplo, firmas exportadoras de arándanos.
4.  En cuarto lugar, se utiliza un bucle que itera sobre la lista de RUCs.
    * Ingresa el código correspondiente.
    * Selecciona criterios de búsqueda: año y tipo de reporte (exportación)
    * Realiza la búsqueda 
    * Espera a que esté visible el botón de descarga. Si no aparece debido a que no hay reportes registrados para esa firma en ese año, regresa a la página inicial y pasa al siguiente RUC.
    * Si hay reportes para ese año, será visible el botón de descarga y el script hace click en dicho botón.
5. Una vez que la descarga es exitosa, el script imprime un mensaje de confirmación en la consola, creando un registro en tiempo real de cada descarga completada.

## Resultados del Proceso

El éxito del script se verifica de dos maneras:

### A. Output: Carpeta de Reportes Descargados

Los archivos de Excel se descargan y se almacenan exitosamente en la carpeta de destino, listos para ser procesados o analizados.

<img width="718" height="359" alt="Screenshot 2025-11-16 at 12 28 55 PM" src="https://github.com/user-attachments/assets/5b1f7350-e6a1-427b-8467-58272d4161a6" />


### B. Registro de Ejecución

La consola proporciona un seguimiento en vivo, confirmando que cada iteración del bucle se completó y que la descarga fue iniciada.

<img width="628" height="471" alt="Screenshot 2025-11-16 at 12 31 39 PM" src="https://github.com/user-attachments/assets/674af218-615a-4ef2-aea2-ec5465aca33b" />
