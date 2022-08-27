<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1>Login</h1>
    <div class="Register">
        <input type="text" v-model="userName" placeholder="Username"/>
        <input type="text" v-model="password" placeholder="Password"/>
        <input type="text" v-model="email" placeholder="Email"/>
    </div>
    <div>
      <button @click="_postToken">POST Request Token </button>
    </div>
    <div>
      <button @click="_postRegister">POST Register </button>
    </div>
    <div>
      <button @click="_getChecklist">GET checklist</button>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data () {
    return {
      userName: '',
      password: '',
      email:''
    }
  }, methods: {
    _postRegister(){
      // let data = [];
      //   data.push({
      //       email: this.email,
      //       password: this.password,
      //       username: this.userName
      //   })
        // console.log(this.password);
        // fetch("94.74.86.174:8080/api/register"),{
        //   methods:'POST', body:JSON.stringify(
        //     data
        //   ),
        //   header:{
        //     "Content-Type":"application/json: charset=UTF-8"
        //   }
        // }
        // .then(function(response){
        //   return response.json()
        // })
        // .then(function(data){
        //   console.log(data);
        // })

        //  fetch("94.74.86.174:8080/api/register",{
        //   methods:'POST', body:JSON.stringify({
        //     email: this.email,
        //     password: this.password,
        //     username: this.userName
        //   }),
        //  })
        // //  .then(res => res.json())
        // //  .then(re => console.log(re))
        // //  .catch(err => console.log(err))

        // .then(function(response){
        //   return response.json()
        // })
        // .then(function(data){
        //   console.log(data)
        // })

  //       fetch('94.74.86.174:8080/api/register', {
  // method: 'POST',
  // body: JSON.stringify({
  //   email: this.email,
  //           password: this.password,
  //           username: this.userName

  // }),
  // headers: {
  //   'Content-type': 'application/json; charset=UTF-8',
  // }
  // })
  // .then(function(response){ 
  // return response.json()})
  // .then(function(data)
  // {console.log(data)})

        const requestOptions = {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ "email": this.email,
            "password": this.password,
            "username": this.userName })
  };
  fetch("94.74.86.174:8080/api/register", requestOptions)
    .then(response => response.json())
    .then(data => (this.postId = data.id));



    },
    _postToken(){

        fetch("94.74.86.174:8080/api/login").then((response)=>console.log(response))
              
    },
    _getChecklist(){
      // console.log(this.userName)
      fetch("94.74.86.174:8080/api/checklist").then((response)=>console.log(response))
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
