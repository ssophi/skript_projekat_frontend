<template>
  <NavBarNotLoggedIn />

  <div class="home">
    <h2>Svi treninzi u ponudi</h2>
    <div v-bind:key="trening.id" v-for="trening in treninzi">
        <WorkoutItem v-bind:trening="trening"  />
    </div>
    <h2>Sve masaze u ponudi</h2>
    <div v-bind:key="masaza.id" v-for="masaza in masaze">
        <MasageItem v-bind:masaza="masaza"  />
    </div>
  </div>
</template>

<script>
import NavBarNotLoggedIn from './NavBarNotLoggedIn.vue'
import WorkoutItem from './WorkoutItem.vue'
import MasageItem from './MasageItem.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    NavBarNotLoggedIn,
     WorkoutItem,
     MasageItem,
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
  },

  methods:{
    goToLogIn(){
      this.$router.push('/login'); 
    },
    goToRegister(){
      this.$router.push('/register'); 
    }
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
