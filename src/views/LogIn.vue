<template>
    <div>
        <h2>Log In</h2>
        <form id="loginForm" v-on:submit="getUserByUsername">
            <div>
                <label for="username">Username: </label>
                <input type="text" id="username" v-model="form.username" name="username" placeholder="Username" required>
            </div>
            <div>
                <label for="password">Password: </label>
                <input type="password" id="password" v-model="form.password" name="password" placeholder="Password" required>
            </div>
            <input type="submit" value="Log In" class="btn">
        </form>
    </div>
</template>

<script>
import axios from 'axios'
import UserReserveWorkout from '../components/UserReserveWorkout.vue'
// import vueJoiValidation from 'vue-joi-validation'

// Vue.use(vueJoiValidation)

export default {
  name: 'LogIn',

  components: UserReserveWorkout,
  data(){
    return {
      form:{
          username:'',
          password:''
      }
    }
  },

  methods:{
    getUserByUsername(){

        console.log('http://localhost:5000/user/login', this.form)
        axios.post('http://localhost:5000/user/login', this.form)
        .then(res => {
            console.log(res.data.token)
            localStorage.setItem('username', this.form.username)
            localStorage.setItem('jwt', res.data.token)})
            this.$router.push('user') 
        .catch(err => console.log(err))
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
.Same{
  display:inline-block;
}
</style>