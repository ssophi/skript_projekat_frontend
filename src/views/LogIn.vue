<template>
    <div>
        <h2>Log In</h2>
        <form id="loginForm" v-on:submit="login">
            <div>
                <label for="username">Username:</label>
                <input type="text" id="username" v-model="username" placeholder="Username" required>
            </div>
            <div>
                <label for="password">Password</label>
                <input type="password" id="password" v-model="password" placeholder="Password" required>
            </div>
            <button type="submit">Submit</button>
        </form>
    </div>
</template>

<script>

export default {
  name: 'LogIn',
  components: {
    
  },
  data(){
    return {
      user: [
        
      ]
    }
  },

  created(){
    axios.get('http://localhost:5000/user/:username') //vrednost username-a ce biti uzeta iz localStorage
    .then(res => this.treninzi = res.data)
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