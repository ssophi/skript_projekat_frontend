<template>
     <div class="masage-item">
        <b>{{masaza.tip}}</b> 
        <p>satnica: od {{masaza.sati_od}} do {{masaza.sati_do}}</p>
        <!-- <p>{{trening.termini}}</p> -->
        <!-- <button @click="$emit('del-blogpost', blogpost.id)" class="del">x</button> -->
    </div>
</template>

<script>
export default {
    name:"UserReserveMassageItem",
    props:["masaza"]
}
</script>

<style scoped>
    .masage-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  /* .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  } */
</style>