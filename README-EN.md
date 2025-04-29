# IP Geolocation with ipinfo and KML Export

This Python script performs IP geolocation using the `ipinfo` service and exports the results to a CSV file and a KML file. The KML file can be opened in software such as Google Earth to visualize the geographical locations of the IP addresses.

## Features

- Uses the `ipinfo` API to retrieve geolocation information (city, region, country, latitude, longitude, ASN, and IP address) for a list of IP addresses.
- The results are saved into a CSV file for easy analysis.
- The geolocation points are also saved into a KML file for visualization in mapping tools like Google Earth.
- Handles multiple IP addresses from a CSV input file.

## Requirements

Before running the script, ensure you have the following Python packages installed:

- `pandas`
- `ipinfo`
- `simplekml`

You can install these packages using pip:

```bash
pip install pandas ipinfo simplekml
```

## Files

- `geo.csv`: The input CSV file containing a list of IP addresses to be geolocated. It should have a column named `direcciones` where each row contains one IP address.
- `ipinfo_resultados.csv`: The output CSV file with the geolocation results, including city, region, country, latitude, longitude, ASN, and IP address.
- `resultados.kml`: The output KML file that contains the geographical points for each IP address, which can be opened with Google Earth or other mapping software.

## How to Use

1. **Prepare the Input File**:
   - Create a CSV file named `geo.csv` with a column titled `direcciones` that contains the IP addresses you want to geolocate.

   Example `geo.csv` file:
   ```csv
   direcciones
   8.8.8.8
   1.1.1.1
   ```

2. **Run the Script**:
   - Replace the placeholder `access_token` in the script with your `ipinfo` access token. If you don't have one, you can obtain it by creating an account on [ipinfo.io](https://ipinfo.io/).
   - Execute the Python script:
   ```bash
   python geolocation_to_csv_kml.py
   ```

3. **Outputs**:
   - After running the script, you'll get two files:
     - `ipinfo_resultados.csv`: This file will contain the geolocation information (city, region, country, latitude, longitude, ASN, and IP address) for each IP address.
     - `resultados.kml`: This KML file can be loaded into Google Earth to visualize the locations of the IP addresses.

## Example Output

The resulting CSV file (`ipinfo_resultados.csv`) will look like:

```csv
Ciudad,Región,País,Latitud,Longitud,ASN,Direccion_ip
Mountain View,California,US,37.386,-122.084,AS15169 Google LLC,8.8.8.8
Sydney,New South Wales,AU,-33.494,151.051,AS13335 Cloudflare Inc,1.1.1.1
```

The KML file (`resultados.kml`) will include placemarks for each IP's geographical location, viewable in Google Earth.

## Notes

- The `ipinfo` API has rate limits depending on the type of account you have (free or paid). Make sure to check these limits before running the script on a large list of IP addresses (for free accounts the limit is 50,000 IPs per month).
- If an IP address cannot be geolocated, the script will still continue processing the other addresses.

## License

This project is open-source and available under the [MIT License](LICENSE).
