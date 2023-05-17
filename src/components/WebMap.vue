<template>
  <div id="map-view">
    <h2>nested h2 tag</h2>
  </div>
  <h2>another h2 tag. mode = {{ mode }}</h2>
  <h3>a h3 tag. msg = {{ msg }}</h3>
</template>


<script lang="ts">

import ArcGISMap from '@arcgis/core/WebMap';
import MapView from '@arcgis/core/views/MapView';

export default {

  name: 'WebMap',
  props: {
    msg: String,
    Project: Object,
  },

  data() {
    return {
      editing: false,
      editedProject: {
        ArcGis_Last_Updated: '0',
        Link_Map_ArcGis: 'https://stackoverflow.com/questions/54884488/how-can-i-solve-the-error-ts2532-object-is-possibly-undefined',
        PDF_Last_Updated: '0',
        Link_Map_PDF: '0',
        JPG_Last_Updated: '0',
        Link_Map_JPG: '0',
      },
      mode: 'arc',
      modesDropdown: [
          { text: 'Image', value: 'jpg' },
          { text: 'PDF', value: 'pdf' },
          { text: 'ArcGIS', value: 'arc' },
      ],
      imageLink: null,
    }
  },

  // data: () => ({
  //   mode: 'arc',
  // }),

  mounted() {
    const map = new ArcGISMap({
      portalItem: {
        id: this.msg
      }
    });

    const view = new MapView({
      map,
      container: "map-view"
    });

    view.when(() => {
      console.log('view ready')
    })
  },
}
</script>

<style>
  /* esri styles */
  @import url('https://js.arcgis.com/3.23/esri/css/esri.css');
  #map-view {
    height: 400px;
    width: 400px;
  }
</style>