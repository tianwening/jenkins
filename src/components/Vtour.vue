<template lang='html'>
  <div id="panowrap">
    <comment :krpano="krpano"></comment>
    <div id="pano"></div>
  </div>
</template>
<script>
import Comment from './Comment'
export default {
  data(){
    return {
      krpano: null
    };
  },
  components: {Comment},
  methods: {
    krpano_onready_callback(krpano_interface){
      this.krpano = krpano_interface;
    }
  },
  mounted(){
    embedpano({
      swf: "static/vtour/tour.swf",
      xml: "static/vtour/tour.xml",
      target: "pano",
      html5: "auto",
      mobilescale: "1.0",
      passQueryParameters: true,
      onready: this.krpano_onready_callback
    })
  }
}
</script>
<style lang='css' scoped>
  #panowrap {
    width: 100%;
    height: 100%;
  }
  #pano {
    width: 100%;
    height: 100%;
  }
</style>