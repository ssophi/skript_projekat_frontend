<template>
<NavBarLoggedIn/>
  <div class="userhome">
    <h2>Forma za zakazivanje treninga</h2>
  </div>

  <div>
      <b>Ponedeljak</b> <br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_ponedeljak">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>

      <b>Utorak</b><br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_utorak">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>

      <b>Sreda</b><br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_sreda">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>

      <b>Cetvrtak</b><br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_cetvrtak">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>

      <b>Petak</b><br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_petak">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>

      <b>Subota</b><br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_subota">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>

      <b>Nedelja</b><br>
      <div v-bind:key="trening.id" v-for="trening in treninzi_nedelja">
        <UserReserveWorkoutItem v-bind:trening="trening"  />
        <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
      </div> <br>
  </div>
</template>

<script>
import axios from 'axios'
import UserReserveWorkoutItem from './UserReserveWorkoutItem.vue'
import NavBarLoggedIn from './NavBarLoggedIn.vue'

export default {
  name: "UserReserveWorkout",
  components: {
     UserReserveWorkoutItem,
     NavBarLoggedIn
  },

  data(){
    return {
      treninzi_ponedeljak: [
      
      ], treninzi_utorak: [
        
      ], treninzi_sreda: [
        
      ], treninzi_cetvrtak: [
        
      ], treninzi__petak: [
        
      ], treninzi_subota: [
        
      ], treninzi_nedelja: [
        
      ],
      form:{
          
      }
    }
  },

  created(){
    const token = localStorage.getItem('jwt')
    const username = localStorage.getItem('username')
    console.log('Bearer ', token)
    console.log('username: ', username)
    axios.get('http://localhost:5000/termin/st/1', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => {this.treninzi_ponedeljak = res.data
      console.log("username: ", localStorage.getItem('username'))})
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/st/2', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => this.treninzi_utorak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/st/3', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => this.treninzi_sreda = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/st/4', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => this.treninzi_cetvrtak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/st/5', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => this.treninzi_petak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/st/6', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => this.treninzi_subota = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/st/7', {
      headers:{
        'Authorization': 'Bearer '+ token
      }
    })
    .then(res => this.treninzi_nedelja = res.data)
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
