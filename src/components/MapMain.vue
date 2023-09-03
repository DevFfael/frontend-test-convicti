<template>
  <div>
    <div id="map" class="map"></div>
  </div>
</template>

<script>
import 'ol/ol.css';
import Map from 'ol/Map';
import View from 'ol/View';
import TileLayer from 'ol/layer/Tile';
import OSM from 'ol/source/OSM';
import Feature from 'ol/Feature';
import Point from 'ol/geom/Point';
import { fromLonLat } from 'ol/proj';
import { Vector as VectorLayer } from 'ol/layer';
import { Vector as VectorSource } from 'ol/source';

export default {
  mounted() {
    const map = new Map({
      target: 'map',
      layers: [
        new TileLayer({
          source: new OSM(),
        }),
        new VectorLayer({
          source: new VectorSource({
            features: [
              new Feature({
                geometry: new Point(fromLonLat([-44.181216, -19.939843])),
              }),
            ],
          }),
        }),
      ],
      view: new View({
        center: fromLonLat([-44.181216, -19.939843]),
        zoom: 15,
      }),
    });
  },
};
</script>

<style lang="sass">
.map
  width: 100%
  height: 800px
  padding: 20px 16px


.ol-layer
  border-radius: 1rem
  overflow: hidden
</style>
