<template>
<div class='tile'>
  <li class='pic-tile' @click="onPicSelect">
    <img class="thumbnail" :src="picURL" alt="Image">
    <h5>{{ pic.title }}</h5>
  </li>
</div>
</template>

<script>
export default {
  name: 'PicTile',
  props: {
    pic: Object
  },
  computed: {
    picURL(){
      return this.pic.url
    }
  },
  methods: {
    onPicSelect(){
      this.$emit('picSelect', this.pic);
    }
  }
}
</script>

<style scoped>
.thumbnail {
  width: 100px;
  height: 100px;
}
.pic-tile {
  list-style-type: none;
  display: flex;
  flex-direction: row;
  margin-top: 10px;
  align-items: center;
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 5px;
  box-shadow: 1px 2px 10px;
  transition: 250ms;
  cursor: pointer;
}
.pic-tile:hover {
  box-shadow: 1px 2px 6px;
}

</style>