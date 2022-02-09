<template>
<NavBarNotLoggedIn />
  <div class="home">
    <h2>Svi treninzi u ponudi</h2>

    <!-- <ul id="array-with-index">
      <li v-for="trening in treninzi" :key="trening.id">
        {{ trening.tip }} - {{ trening.termini }}
      </li>
    </ul>

    <h2>Sve masaze u ponudi</h2>
    <ul id="array-with-index">
      <li v-for="masaza in masaze" :key="masaza.id">
        {{ masaza.tip }} - {{ masaza.termini }}
      </li>
    </ul> -->

    <div v-bind:key="trening.id" v-for="trening in treninzi">
        <WorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div>
    <h2>Sve masaze u ponudi</h2>
    <div v-bind:key="masaza.id" v-for="masaza in masaze">
        <MasageItem v-bind:masaza="masaza"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div>
  </div>
</template>

<script>

import WorkoutItem from './WorkoutItem.vue'
import MasageItem from './MasageItem.vue'
import NavBarNotLoggedIn from './NavBarNotLoggedIn.vue'
import axios from 'axios'

export default {
  
  name: 'Home',
  components: {
     WorkoutItem,
     MasageItem,
     NavBarNotLoggedIn
  },
  
  data(){
    return {
      treninzi: [
        
      ],
      masaze: [
        
      ]
    }
  },

  created(){
    axios.get('http://localhost:5000/trening')
    .then(res => this.treninzi = res.data)
    .catch(err => console.log(err))

    console.log("treninzi ", this.treninzi)

    axios.get('http://localhost:5000/masaza')
    .then(res => this.masaze = res.data)
    .catch(err => console.log(err))
  }
}
</script>

<style scoped>
th, td {
  border-bottom: 1px solid #ddd;
}
table {
  width: 100%;
}
</style>
