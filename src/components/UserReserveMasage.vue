<template>
  <div class="userhome">
    <h2>Forma za zakazivanje masaza</h2>
  </div>

 <div>
    <b>Ponedeljak</b> <br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_ponedeljak">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>

    <b>Utorak</b><br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_utorak">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>

    <b>Sreda</b><br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_sreda">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>

    <b>Cetvrtak</b><br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_cetvrtak">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>

    <b>Petak</b><br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_petak">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>

    <b>Subota</b><br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_subota">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>

    <b>Nedelja</b><br>
    <div v-bind:key="masaza.id" v-for="masaza in masaze_nedelja">
      <UserReserveMasageItem v-bind:masaza="masaza"  />
      <!-- v-on:del-blogpost="$emit('del-blogpost', blogpost.id)" -->
    </div> <br>
  </div>
</template>

<script>
import axios from 'axios'
import UserReserveMasageItem from './UserReserveMasageItem.vue'

export default {
  name: "UserReserveWorkout",
  components: {
    UserReserveMasageItem
  },
    // props: ["blogposts"]

data(){
    return {
      masaze_ponedeljak: [
        
      ],
      masaze_utorak: [
        
      ],
      masaze_sreda: [
        
      ],
      masaze_cetvrtak: [
        
      ],masaze__petak: [
        
      ],masaze_subota: [
        
      ],masaze_nedelja: [
        
      ]
    }
  },

  created(){
    axios.get('http://localhost:5000/termin/sm/1')
    .then(res => this.masaze_ponedeljak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/sm/2')
    .then(res => this.masaze_utorak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/sm/3')
    .then(res => this.masaze_sreda = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/sm/4')
    .then(res => this.masaze_cetvrtak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/sm/5')
    .then(res => this.masaze_petak = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/sm/6')
    .then(res => this.masaze_subota = res.data)
    .catch(err => console.log(err))

    axios.get('http://localhost:5000/termin/sm/7')
    .then(res => this.masaze_nedelja = res.data)
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
