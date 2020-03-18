<template>
  <div class="login">
    <h1>{{ title }}</h1>
    <div id="wrapper">

        <!-- the google signin button -->
        <div class="g-signin2 g-button" data-width=300% data-onsuccess="onSignIn"></div>

        <a class="button" href="#" v-on:click="signout">Sign out</a>
    </div>
    <div id="name"></div>
  </div>
</template>


<script>
export default {
  name: 'Login',
  data () {
    return {
      title: 'My "Login with Google" Page',
    }
  },

  methods: {
    signout: function() {
      var auth2 = gapi.auth2.getAuthInstance();
      auth2.signOut().then(function () {
        console.log('User signed out.');
      });

      // change the "name" element to be blank when user signs out
      document.getElementById("name").innerHTML = ""
    },
  }
}
</script>


<style scoped>
.button {
  background-color: black; 
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 50px;
}

#wrapper {
    width: 50%;
    margin-left: 25%;
    margin-top: 50px;
    margin-bottom: 50px;
}
.g-button {
  padding-left: 33%;
}

#name {
    font-weight: bold;
    font-size: 30pt;
}
</style>
