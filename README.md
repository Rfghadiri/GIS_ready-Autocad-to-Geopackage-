# GIS_ready-Autocad-to-Geopackage-
# AutoCAD to GIS App — Installation Tutorial

## 1. Install ODA File Converter
1. Download and install ODA File Converter.
2. Make sure the application is installed and can be opened.

## 2. Install Miniforge and GDAL

### 2.1. Install Miniforge3
1. Download Miniforge3 for Windows 64-bit from the official website:
   https://conda-forge.org/download/
2. Install it using the default settings.

**Note:** A separate Python installation is not required. Miniforge provides Python through its environments.

### 2.2. Create the Python environment
1. Open **Miniforge Prompt** from the Windows Start menu.
2. Run the following commands one at a time:

```bat
conda create -n autocadgis python=3.12 gdal -c conda-forge
conda activate autocadgis
```

3. Verify the installation by running:

```bat
python -c "from osgeo import gdal, ogr; print('GDAL:', gdal.__version__); print('DXF:', ogr.GetDriverByName('DXF') is not None); print('SHP:', ogr.GetDriverByName('ESRI Shapefile') is not None)"
```

The installation is successful if a GDAL version is displayed and both `DXF` and `SHP` return `True`.

## 3. Run the application

1. Extract `AutoCAD_to_GIS_App_v2.zip` to a folder, for example:

   `C:\AutoCAD_to_GIS_App`

2. Open the extracted `AutoCAD_to_GIS_App` folder in File Explorer.
3. Click the address bar, type `cmd`, and press Enter.
4. In the Command Prompt window, run:

```bat
conda activate autocadgis
python autocad_to_gis_app.py
```

**Important:** If `conda activate autocadgis` does not work in Command Prompt, open Miniforge Prompt and navigate to the extracted application folder instead.

## 4. Configure the application

1. Select the input folder containing your DWG files.
2. Select the output folder.
3. Set the ODA File Converter executable path, if it is not detected automatically.
4. Choose the required output formats and start the conversion.

Example ODA installation path:

`C:\Program Files\ODA\ODAFileConverter 27.9.0\ODAFileConverter.exe`

## 5. Verify the output

Open the generated SHP or GeoPackage files in QGIS and verify that the geometries and attributes have been converted correctly.

**Note:** The coordinate reference system (CRS) should not be assigned unless the source drawing's coordinate system is known.
