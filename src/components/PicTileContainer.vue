<template>
<div class='col-md-4'>
   <ul>
     <PicTile 
      v-for="pic in pics"
      :pic="pic"
      :key="pic.title"
      @picSelect="onPicSelect"
     />
   </ul>
</div>
</template>

<script>
import PicTile from './PicTile';

export default {
  name: 'PicTileContainer',
  components: {
    PicTile
  },
  props: {
    pics: Array
  },
  methods: {
    onPicSelect(pic){
      this.$emit('picSelect', pic);
    }
  }
}
</script>