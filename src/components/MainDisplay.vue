<template>
  <div v-if="pic" class='col-md-8 main-display card'>
    <img :src="picURL" alt="" class='card-image-top main-display-image'>
    <h3 class='card-title'>{{ pic.title }}</h3>
    <p class='card-text'>{{ pic.explanation }}</p>
  </div>
</template>

<script>
export default {
  name: 'MainDisplay',
  props: {
    pic: Object
  },
  computed: {
    picURL(){
      const { url } = this.pic;
      return url;
    }
  }
}
</script>

<style scoped>
.main-display-image {
  height: 60%;
  width: 60%;
}
.main-display {
  padding-left: 3em;
}
h3 {
  border-bottom: 1px solid #ddd;
}
</style>