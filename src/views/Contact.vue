<template>
<NavBarNotLoggedIn />
  <div class="home">
    <h1>Contact page</h1>
  </div>
</template>

<script>
import NavBarNotLoggedIn from './NavBarNotLoggedIn.vue'

export default {
  name: 'Contact',
  components: {
    NavBarNotLoggedIn
  }
}
</script>