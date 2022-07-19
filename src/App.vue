<script setup>
import SignIn from './components/SignIn.vue'
import FamousPoets from './components/FamousPoets.vue'
import { createClient } from '@supabase/supabase-js'
import { SupabaseAuthClient } from '@supabase/supabase-js/dist/module/lib/SupabaseAuthClient'
</script>

<template>    
    <header>
    <img alt="Poetry" class="logo" src="./assets/logo.png" width="125" height="125" />
    <div class="wrapper" id="signOut">
      <div><SignIn msg="Poet ! Tell us who you are !" /></div>
      <label>email: </label><br>
	    <input type="email" required v-model="email" placeholder="username@domain.tld"><br>
	    <label>password: </label><br>
	    <input type="password" required v-model="passwd" ><br>
      <button v-on:click="register()">Sign Up</button>
      <button v-on:click="login()">Sign In</button>
      
    </div>
    <div class="hidden" id="addPoem">
      <div><SignIn msg="Write your poem !" /></div>
      	<label>Poem's title</label><br>
	      <input type="text" required name="title" v-model="title" placeholder="edit me"><br>
	      <label>Poem's content</label><br>
        <textarea required name="content" v-model="content" placeholder="edit me" rows="10" cols="50">Your poem here ...
        </textarea> <br>
	      <input type="checkbox" v-model="hidden" placeholder=true />
        <label>Hidden poem</label>
      <br><button v-on:click="createPoem()">Add the poem</button>
      <button v-on:click="fetchPoems()">List of poems</button>
    </div>
  </header>
  
  <main>
    <FamousPoets />
  </main>
</template>

<script>

const supabaseUrl = 'https://kqucrmtwrprlvuwfzvee.supabase.co'
const SUPABASE_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImtxdWNybXR3cnBybHZ1d2Z6dmVlIiwicm9sZSI6ImFub24iLCJpYXQiOjE2NTc2MDc2ODAsImV4cCI6MTk3MzE4MzY4MH0.udaSZ-cJrScuw3KNUJWfit3DjVWbKI7H07bFjzUXWYE'
const supabase = createClient(supabaseUrl, SUPABASE_KEY)


export default {
  data() {
    return {          
    }
  },
  methods: {  
    //this method allows to add new poem for the authenticated user (after sign in) 
    async createPoem(){
      //catch the exception
      try{
        //insert a new raw in poems' table based on the entered data : title, content and hidden status
        //P.S. the email of the author is automatically added since the email column is declarated
        //with a default value auth.email(). The user cannot associate its poem to another author !
        const { data, error } = await supabase
          .from('poems')
          .insert([
          { hidden: this.hidden, title: this.title, content: this.content }
          ])
        //detect the error
        if (error) throw error;
        //manage the error
      } catch (error) {
        alert(error.error_description || error.message);
      } 
    },
    //this method allows to extract all readable poems of the authenticated user
    //including his peoms and the not hidden poems. This policy is implemented by the supabase system 
    async fetchPoems(){
      try{
        const { data, error } = await supabase
          .from('poems')
          .select()
        if (error) throw error;
      } catch (error) {
        alert(error.error_description || error.message);
      } 
    },
    //this method allows a new user to sign up the system. Once done, the user receives an email
    //asking for account validation. Once the validation made the user is added to the system
    async register(){
      try {
        const { user, session, error } = await supabase.auth.signUp({
          email: this.email,
          password: this.passwd
        })
        if (error) throw error;
      } catch (error) {
        alert(error.error_description || error.message);
      } 
    },
    //this method allows the already registred user to log in the system.
    //only authenticated users can later add or read the poems
    async login(){
      try {
        const { user, session, error } = await supabase.auth.signIn({
          email: this.email,
          password: this.passwd
        })
        if (error) throw error;
        else {
          document.getElementById('signOut').style.visibility='hidden'
          document.getElementById('addPoem').style.visibility='visible'
        }
      } catch (error) {
        alert(error.error_description || error.message);
      } 
    }
  }
}
</script>

<style>
@import './assets/base.css';

header .hidden {
    visibility: hidden;
    overflow: hidden;
    display: flex;
    display:inline-block;
    place-items: flex-start;
    flex-wrap: wrap;
}

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: inline-block;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    display:inline-block;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
