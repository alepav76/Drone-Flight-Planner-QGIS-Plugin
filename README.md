Drone Flight Planner — QGIS Plugin

Authors: A. Pavan, P. Paganini, M. Potleca

QGIS plugin for the automated planning of photogrammetric drone flights. It generates flight strips at a constant AGL (Above Ground Level) altitude, based on a GeoTIFF DTM and a survey area (QGIS polygon layer or KML file).

Installation

Copy the plugin folder
Copy the entire drone_flight_planner/ folder into the QGIS plugins directory:

Windows:
C:\Users<username>\AppData\Roaming\QGIS\QGIS3\profiles\default\python\plugins\

Linux/macOS:
~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/

The final structure should be:
plugins/
└── drone_flight_planner/
├── init.py
├── plugin.py
├── dialog.py
├── drone_core.py
├── metadata.txt
└── icons/
└── icon.svg

Install Python Dependencies
The plugin uses external libraries that must be installed in the QGIS Python environment. Open OSGeo4W Shell (Windows) or a terminal with the QGIS Python environment active:

pip install rasterio shapely pyproj scipy numpy

On Windows with QGIS standalone, use:
C:\Program Files\QGIS 3.x\OSGeo4W.bat
pip install rasterio shapely pyproj scipy numpy

On Linux:
python3 -m pip install rasterio shapely pyproj scipy numpy

Activate the plugin in QGIS

Open QGIS

Go to Plugins -> Manage and Install Plugins

Select the Installed tab

Search for Drone Flight Planner and check the box

The plugin will appear in the Plugins -> Drone Flight Planner menu and toolbar

Usage

Open the plugin from Plugins -> Drone Flight Planner

Input Tab:

Select the DTM GeoTIFF file

Select the survey area (QGIS polygon layer or KML file)

Leave EPSG=0 for auto-detection, or specify the code if needed

Flight Parameters Tab:

Set AGL, FOV, Overlap, Sidelap

The preview shows calculated swath and spacing in real-time

Output Tab:

Specify the KML save path

Enable "Load KML in QGIS upon completion"

Click Generate Flight Plan

Parameters
AGL (Default 50 m): Flight altitude above ground
FOV (Default 70 deg): Camera field of view
Overlap (Default 70%): Longitudinal overlap
Sidelap (Default 70%): Lateral overlap
DTM Step (Default 5 m): Sampling resolution
Smoothing (Default 30 m): Gaussian sigma for altitude smoothing
EPSG (Default 0): DTM CRS if not automatically recognized

Troubleshooting
"No module named rasterio": Install dependencies (see step 2)
"DTM CRS could not be determined": Specify the EPSG code manually (e.g., 32633)
"No strips generated": Verify that the survey area overlaps with the DTM extent
"KML does not load": Try adding it manually via Layer -> Add Vector Layer

AUTHORS AND LICENSE
Authors: A. Pavan, P. Paganini, M. Potleca. License: GNU GPL v3.
Developed with the assistance of Claude (Anthropic AI) to optimize code structure, performance, and GUI integration.
