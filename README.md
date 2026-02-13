# GeoRef — Browser-Based Raster Georeferencing Tool

A lightweight, client-side web application for georeferencing raster images (scanned maps, aerial photos, etc.) directly in your browser. No server required — runs entirely on GitHub Pages.

## 🌍 Features

- **Upload any raster**: JPG, PNG, TIFF, BMP, WebP
- **Interactive GCP placement**: Click on the image to place Ground Control Points with zoom/pan controls
- **Quick Corner Bounds**: Enter known map extent and auto-assign coordinates to corner GCPs
- **Multiple export formats**:
  - **GeoTIFF** (.tif) — Full georeferenced raster with embedded CRS
  - **World File** (.jgw/.pgw/.tfw) — Sidecar affine transform file
  - **GCP File** (.points) — QGIS-compatible ground control points
  - **GCP Table** (.csv) — Spreadsheet-friendly coordinate table
  - **Projection File** (.prj) — WKT projection definition
- **CRS support**: WGS 84, UTM Zone 46N/47N/48N
- **Affine transform**: Least-squares computation from 3+ GCPs

## 🚀 Quick Start

### Use Online
Visit the deployed site: `https://geonet-myanmar.github.io/georef/`

### Run Locally
Simply open `index.html` in any modern browser. No build tools or dependencies to install.

```bash
git clone https://github.com/geonet-myanmar/georef.git
cd georef
# Open index.html in your browser
```

## 📖 Usage

1. **Upload** a raster image (drag & drop or click to browse)
2. **Place GCPs** by clicking on known locations in the image (corners, grid intersections, etc.)
3. **Enter coordinates** for each GCP (longitude/latitude in decimal degrees)
   - Or use **Quick Corner Bounds** for maps with known rectangular extent
4. **Export** your georeferenced data from the Export tab

### Workflow for Topographic Maps

If you have a map sheet with known geographic extent (like Myanmar 1:50,000 topos):

1. Upload the scanned map image
2. Click on the 4 corner intersections of the map grid
3. Enter the bounding coordinates in "Quick Corner Bounds" (e.g., 96°00'–96°15'E, 22°15'–22°30'N → West: 96.00, East: 96.25, South: 22.25, North: 22.50)
4. Click "Apply Bounds to 4 GCPs" — coordinates are auto-assigned
5. Export as GeoTIFF or World File

## 🛠 Technical Details

- **Pure client-side**: All processing happens in the browser via JavaScript
- **Libraries**: [GeoTIFF.js](https://geotiffjs.github.io/) for TIFF reading/writing
- **Transform**: 6-parameter affine transform via least-squares fitting
- **No server**: Suitable for GitHub Pages, Netlify, or any static hosting

## 📁 Project Structure

```
georef/
├── index.html    # Complete application (single file)
└── README.md     # This file
```

## 🌐 Deploying to GitHub Pages

1. Create a new GitHub repository
2. Push `index.html` and `README.md` to the `main` branch
3. Go to **Settings → Pages → Source** → select `main` branch
4. Your app will be live at `https://<username>.github.io/<repo-name>/`

## License

MIT License
