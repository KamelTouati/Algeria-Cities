# Algeria Wilayas & Communes 2026 🇩🇿

A developer-friendly and structured dataset containing all **69 wilayas (provinces)** and **1,541 communes (municipalities)** of Algeria, including **geographic coordinates (longitude/latitude)**.

---

## 📦 Dataset Overview

| Item        | Count                               |
| ----------- | ----------------------------------- |
| Wilayas     | 69                                  |
| Communes    | 1,541                               |
| Coordinates | Included (Latitude/Longitude)       |
| Geometries  | MultiPolygon (Surfaces) & Point (Chefs-lieux) |
| Formats     | CSV, JSON, GeoJSON, SQL, PHP, SHP*, XLSX* |
| Country     | Algeria 🇩🇿                          |

_* SHP and XLSX formats are generated automatically and available in the [Releases](../../releases) section._

---

## ✨ Features

- Complete list of **69 Algerian wilayas** (2026 administrative organization)
- Full coverage of **1,541 communes**
- **MultiPolygon boundaries & surfaces** for all 1,541 communes (`algeria_communes.geojson`)
- **MultiPolygon boundaries & surfaces** for all 69 wilayas (`algeria_wilayas.geojson`)
- **Point coordinates** of all chefs-lieux (`algeria_cities.geojson`)
- Accurate **surface area in km²** (`surface_km2`) for every commune and wilaya
- Multilingual data (**Arabic / French**)
- Available in multiple formats for easy integration: **CSV, JSON, GeoJSON, SQL, PHP, SHP**
- Ready to use for **GIS, Leaflet, Mapbox, QGIS, and backend systems**

---

## 📁 Repository Structure

```
algeria-cities/
│
├── csv/
│   └── algeria_cities.csv         # CSV format with coordinates & surface_km2
├── geojson/
│   ├── algeria_communes.geojson   # MultiPolygon boundaries of 1,541 communes (surfaces)
│   ├── algeria_wilayas.geojson    # MultiPolygon boundaries of 69 wilayas (surfaces)
│   └── algeria_cities.geojson     # Point markers for all 1,541 commune centers
├── json/
│   └── algeria_cities.json        # JSON format
├── php/
│   └── algeria_cities.php         # PHP associative array
├── shp/
│   ├── algeria_communes_shp.zip   # ESRI Shapefile of 1,541 communes (WGS84, UTF-8)
│   └── algeria_wilayas_shp.zip    # ESRI Shapefile of 69 wilayas (WGS84, UTF-8)
├── sql/
│   └── algeria_cities.sql         # SQL dump & table schema
└── README.md
```

---

## 📄 Data Structure

| Column          | Type    | Description                                  |
| --------------- | ------- | -------------------------------------------- |
| id              | integer | Unique identifier of the commune (1-1541)    |
| commune_name    | string  | Commune name in Arabic                       |
| commune_name_fr | string  | Commune name in French                       |
| daira_name      | string  | Daira name in Arabic                         |
| daira_name_fr   | string  | Daira name in French                         |
| wilaya_code     | integer | Official wilaya numeric code (1-69)          |
| wilaya_name     | string  | Wilaya name in Arabic                        |
| wilaya_name_fr  | string  | Wilaya name in French                        |
| code_commune    | integer | Official commune administrative code (ONS)   |
| Lat             | float   | Latitude (chef-lieu)                         |
| Long            | float   | Longitude (chef-lieu)                        |
| surface_km2     | float   | Area / Surface in square kilometers (km²)    |

---

## 🗺️ GeoJSON Geometries Guide

### 1. Communes Surfaces (`geojson/algeria_communes.geojson` & `shp/algeria_communes_shp.zip`)
Contains vector boundaries (`MultiPolygon`) for each of the 1,541 communes, fully compliant with RFC 7946 and OGC CRS84, optimized for both web mapping and desktop GIS (QGIS, ArcGIS, MapInfo).

```javascript
// Example: Leaflet GeoJSON layer for communes
fetch('geojson/algeria_communes.geojson')
  .then(res => res.json())
  .then(data => {
    L.geoJSON(data, {
      style: { color: '#006233', weight: 1, fillOpacity: 0.2 },
      onEachFeature: (feature, layer) => {
        layer.bindPopup(`<b>${feature.properties.commune_name_fr}</b> (${feature.properties.commune_name})<br>
                        Wilaya: ${feature.properties.wilaya_name_fr} (${feature.properties.wilaya_code})<br>
                        Superficie: ${feature.properties.surface_km2} km²`);
      }
    }).addTo(map);
  });
```

### 2. Wilayas Surfaces (`geojson/algeria_wilayas.geojson`)
Contains the aggregated boundaries (`Polygon` and `MultiPolygon`) for each of the 69 wilayas of Algeria.

### 3. Chef-lieu Points (`geojson/algeria_cities.geojson`)
Contains lightweight `Point` coordinates for markers/pins.

---

## 🤝 Contributing

Contributions are welcome!

You can help by:

- Fixing incorrect coordinates
- Adding missing communes
- Improving data accuracy
- Enhancing formats or structure
- Improving documentation

### Steps

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Submit a Pull Request

---

## 🐞 Issues

If you find any error or want to request a feature, please open an issue:

**Issues:**
`../../issues`

Please include:

- Wilaya name
- Commune name
- Description of the issue
- Suggested correction

---

## 📜 License

MIT License

---

## ⭐ Support

If this dataset helps your project, consider giving the repository a **star** ⭐ to support future updates.
