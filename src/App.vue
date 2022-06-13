<template>
  <div id="app">
    <div v-if='$store.state.user'>
        <headers></headers>
        <menu></menu>
          <router-view />
    </div>
    <div v-else>
        <login ></login>
    </div>
  </div>
</template>
<script type="text/javascript">
  
import headers from './components/header.vue'
import menu from './components/menu.vue'
import login from './components/login.vue'

export default {
  data(){
    return{
    }
  },
  components: {
      headers,
      menu,
      login
  },
  methods:{

  },
  mounted() {
    var user = JSON.parse(localStorage.getItem('user'))
    if (user) {
      this.$store.state.user = user
    }
  },
    watch: {
    '$store.state.user': {
      deep: true,
      handler(new_val){
        if (new_val) {
          localStorage.setItem('user', JSON.stringify(new_val))
        } else {
          localStorage.removeItem('user')
        }
                
      }
    }
  },
};
</script>

<style src="">

</style>
