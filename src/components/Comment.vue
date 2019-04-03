<template lang='html'>
  <div id="comment">
    <button type="button" @click="toogleMap">评论按钮</button>
    <ul>
      <li v-for="item in arr" :key="item.text" @click="addItem">{{item.text}}</li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ['krpano'],
  data () {
    return {
      arr: [
        {text: 1},
        {text: 2},
        {text: 3}
      ]
    };
  },
  methods: {
    toogleMap(){
      this.krpano.call(`switch(layer[mapcontainer].visible)`);
    },
    addItem(){
      let text = this.arr[this.arr.length-1].text;
      this.arr.push({
        text: ++text
      })
    }
  }
}
</script>
<style lang='css' scoped>
  #comment {
    position: absolute;
    left: 50%;
    top: 50%;
    z-index: 1;
  }
  ul {
    width: 300px;
    height: 100px;
    background-color: rgba(0,0,0,0.5);
    display: flex;
  }
  li {
    flex: 1;
    box-sizing: border-box;
    text-align: center;
    border: 1px solid #00f;
    font-size: 50px;
    color: #f00;
    line-height: 100px;
    cursor: pointer;
  }
</style>