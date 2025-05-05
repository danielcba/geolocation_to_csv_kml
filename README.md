# Geolocalización de IP con ipinfo y Exportación a KML

Este script en Python realiza la geolocalización de direcciones IP utilizando el servicio de `ipinfo` y exporta los resultados a un archivo CSV y un archivo KML. El archivo KML puede abrirse en software como Google Earth para visualizar las ubicaciones geográficas de las direcciones IP.

## Funcionalidades

- Utiliza la API de `ipinfo` para obtener información de geolocalización (ciudad, región, país, latitud, longitud, ASN y dirección IP) de una lista de direcciones IP.
- Los resultados se guardan en un archivo CSV para facilitar su análisis.
- Los puntos de geolocalización también se guardan en un archivo KML para su visualización en herramientas de mapas como Google Earth.
- Maneja múltiples direcciones IP desde un archivo CSV de entrada.

## Requisitos

Antes de ejecutar el script, asegúrate de tener instaladas las siguientes bibliotecas de Python:

- `pandas`
- `ipinfo`
- `simplekml`

Puedes instalar estas bibliotecas usando pip:

```bash
pip install pandas ipinfo simplekml
```

## Archivos

- `geo.csv`: Archivo CSV de entrada que contiene una lista de direcciones IP a geolocalizar. Debe tener una columna llamada `direcciones` donde cada fila contenga una dirección IP.
- `ipinfo_resultados.csv`: Archivo CSV de salida con los resultados de la geolocalización, incluyendo ciudad, región, país, latitud, longitud, ASN y dirección IP.
- `resultados.kml`: Archivo KML de salida que contiene los puntos geográficos de cada dirección IP, que pueden abrirse en Google Earth u otro software de mapas.

## Cómo Usar

1. **Preparar el Archivo de Entrada**:
   - Crea un archivo CSV llamado `geo.csv` con una columna titulada `direcciones` que contenga las direcciones IP que deseas geolocalizar.

   Ejemplo de archivo `geo.csv`:
   ```csv
   direcciones
   8.8.8.8
   1.1.1.1
   ```

2. **Ejecutar el Script**:
   - Reemplaza el `access_token` en el script con tu token de acceso de `ipinfo`. Si no tienes uno, puedes obtenerlo creando una cuenta en [ipinfo.io](https://ipinfo.io/).
   - Ejecuta el script de Python:
   ```bash
   python geolocation_to_csv_kml.py
   ```

3. **Salidas**:
   - Después de ejecutar el script, obtendrás dos archivos:
     - `ipinfo_resultados.csv`: Este archivo contendrá la información de geolocalización (ciudad, región, país, latitud, longitud, ASN y dirección IP) de cada dirección IP.
     - `resultados.kml`: Este archivo KML puede cargarse en Google Earth para visualizar las ubicaciones de las direcciones IP.

## Ejemplo de Salida

El archivo CSV resultante (`ipinfo_resultados.csv`) tendrá un formato similar al siguiente:

```csv
Ciudad,Región,País,Latitud,Longitud,ASN,Direccion_ip
Mountain View,California,US,37.386,-122.084,AS15169 Google LLC,8.8.8.8
Sydney,Nueva Gales del Sur,AU,-33.494,151.051,AS13335 Cloudflare Inc,1.1.1.1
```

El archivo KML (`resultados.kml`) incluirá marcadores con la ubicación geográfica de cada dirección IP, visualizables en Google Earth.

## Notas

- La API de `ipinfo` tiene límites de uso según el tipo de cuenta que poseas (gratuita o de pago). Asegúrate de revisar estos límites antes de ejecutar el script en una gran lista de direcciones IP `(para cuentas gratuitas el límite es de 50.000 IPs por mes)`.
- Si no se puede obtener la geolocalización de una dirección IP, el script continuará procesando las demás direcciones.

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo [MIT License](LICENSE). para más información.
