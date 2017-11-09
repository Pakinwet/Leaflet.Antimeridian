# Leaflet.Antimeridian
A plugin to allow polygons and polylines to naturally draw across the Antimeridian (or the Internation Date Line) instead of always wrapping across the Greenwich meridian.

Useful when displaying lines that might cross or partially cross the Antimeridian.

Simple polygons/polylines without using Leaflet.Antimeridian |
------|
![Leaflet](https://user-images.githubusercontent.com/28913842/32580626-00c1d9f2-c49b-11e7-9782-bf88cdd70c23.png) |

 Using Leaflet.Antimeridian |
 ------|
![using Leaflet.Antimeridian](https://user-images.githubusercontent.com/28913842/32580625-ff534a56-c49a-11e7-831e-984b57651e00.png)

## [Demo](https://briannaandco.github.io/Leaflet.Antimeridian/)
## Installation
Requires leaflet@1.0.0.

## Usage

This plugin may be downloaded as a single Javascript file and directly included in the project.
It may also be downloaded as an NPM project, complete with tests and examples.

### Javascript Download



```html
<script src="path/to/leaflet@1.0.2/dist/leaflet.js"></script>
<script src="path/to/Leaflet.Antimeridian-src.js"></script>
```

## Usage
To create a L.Wrapped.Polyline or L.Wrapped.Polygon, simply pass an array of latlngs to the factory function or the constructor as the first argument. The second optional argument is options object.

```javascript
var mymap = L.map('mapid').setView([51.505, -0.09], 1);
L.tileLayer('http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  maxZoom: 18
}).addTo(mymap);

var pointList = [new L.LatLng(20.00, 140.0), L.LatLng(50.00, -120.0), L.LatLng(70.50, 170.0)];

//Create and display a wrapping polygon.
new L.Wrapped.Polygon(pointList, {
    color: 'red',
    weight: 3,
    opacity: 0.5,
    smoothFactor: 1,
    noWrap:true
  }).addTo(mymap);

//Create and display a wrapping polyline over the same set of points.
  new L.Wrapped.Polyline(pointList, {
    color: 'blue',
    weight: 3,
    opacity: 0.5,
    smoothFactor: 1,
    noWrap:true
    }).addTo(mymap);
});
```
## API reference
### Factorys
Factory|Description
------|-------
L.Wrapped.Polyline(`LatLng[]` _latlngs_, `options` _options?_)|Create a automatically wrapping polyline that will take all the usual polyline options.
L.wrappedPolyline(`LatLng[]` _latlngs_, `options` _options?_)|Factory method that wraps the L.Wrapped.Polyline constructor.
L.Wrapped.Polygon(`LatLng[]` _latlngs_, `options` _options?_)|Create a automatically wrapping polygon that will take all the usual polygon options.
L.wrappedPolygon(`LatLng[]` _latlngs_, `options` _options?_)|Factory method that wraps the L.Wrapped.Polygon constructor.

### Utility Methods
Method|Returns|Description
------|-------|-----------
L.Wrapped.sign(`Number` _number_)|`Number`|Returns NaN for non-numbers, 0 for 0, -1 for negative numbers, 1 for positive numbers
L.Wrapped.calculateAntimeridianLat(`LatLng` _latLngA_, `LatLng` _latLngB_)|`Number`|Calculates the latitude at which the two points will cross the Antimeridian. Returns the latitude.
L.Wrapped.isCrossMeridian(`LatLng` _latLngA_, `LatLng` _latLngB_)|`boolean`|Returns true if the line between the two LatLngs crosses either meridian.
L.Wrapped.isBreakRing(`LatLng` _latLngA_, `LatLng` _latLngB_)|`boolean`|Returns true if the line between the two LatLngs should be broken across the meridian.

## [License](https://opensource.org/licenses/MIT)
