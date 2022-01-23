<template>
<div class='app-ctn'>
  <div class='btn-ctn'>
    <button class='shuffle-btn'  @click="onClick">Get Pics!</button> 
  </div>
  <div class='row'>
    <MainDisplay :pic="selectedPic" />
    <PicTileContainer @picSelect="onPicSelect" :pics="pics"/>
  </div>
</div>
</template>

<script>
import axios from 'axios';
import PicTileContainer from './components/PicTileContainer'
import MainDisplay from './components/MainDisplay'

const API_KEY = 'RgHviaFJ7jdJSxeJ781Wfw0qLRStIajXzuFWbf23';

export default {
  name: 'App',
  components: {
    PicTileContainer,
    MainDisplay
  },
  data(){
    return {
      pics: [],
      selectedPic: null,
    }
  },
  methods: {
    onPicSelect(pic){
      this.selectedPic = pic;
    },
    onClick(){
      axios
        .get('https://api.nasa.gov/planetary/apod', {
          params: {
            api_key: API_KEY,
            count: 5
          }
        })
        .then(response => {
          console.log(response.data)
          this.pics = response.data;
        })
    }
  }
}
</script>

<style scoped>
.shuffle-btn {
  width: 7em;
  height: 3em; 
}
.btn-ctn {
  display: flex;
  justify-content: center;
}
</style>