<template>
  <div class="userhome">
    <h2>My Page</h2>
  </div>

  <div>
    <form @submit.prevent="addBlogPost">
      <b class="Same">Ime: </b> <p class="Same">{{user.ime}}</p><br>
      <b class="Same">Prezime: </b> <p class="Same">Izvuci iz baze koje je prezime</p><br>
      <b class="Same">Username: </b> <p class="Same">Izvuci iz baze koje je username</p><br>
      <b class="Same">Email: </b> <p class="Same">Izvuci iz baze koje je email</p><br>
      <input type="submit" value="Change" class="btn">
    </form>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  
  name: 'UserHome',
  components: {
    
  },
  data(){
    return {
      user: {
        username:'',
        ime:'',
        prezime:'',
        email:''
      }
    }
  },

  created(){
    axios.get('http://localhost:5000/user/', localStorage.getItem('username')) //vrednost username-a ce biti uzeta iz localStorage
    .then(res => {this.user = res.data
      console.log(user)})
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
.Same{
  display:inline-block;
}
</style>
