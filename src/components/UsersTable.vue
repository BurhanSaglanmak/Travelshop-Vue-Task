<template>
    <div>
      <div class="container"    >
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Ana Sayfa</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        
       
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Filter
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Action</a></li>
           

            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          
          </ul>
        </li>
       
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
</div>
        <div class="container"    >
        <table class="table" >
  <thead>
    <tr v-if="width > widthNum">
      <th scope="col">ID</th>
      <th scope="col">Name</th>
      <th scope="col">Photo</th>
      <th scope="col">Username</th>
      <th scope="col">Email</th>
      <th scope="col">Phone</th>
      <th scope="col">Website</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="user in users" :key="user.id">
        <div id="containerUser">
      <th  v-if="width < widthNum" scope="col">ID</th>
      <th scope="row">{{user.id}}</th>
    </div>
    <div id="containerUser">
      <th scope="col" v-if="width < widthNum">Name</th>
      <td>{{user.name}}</td>
    </div>
      <div id="containerUser">
      <th  scope="col" v-if="width < widthNum">Username</th>
      <td >
      <img id="image" :src="`https://avatars.dicebear.com/v2/avataaars/${user.username}.svg?options[mood][]=happy`" alt="..."/>
      </td>
    </div>
    <div id="containerUser">
      <th  scope="col" v-if="width < widthNum">Username</th>
      <td >
        {{user.username}}</td>
    </div>
      <div id="containerUser">
      <th scope="col" v-if="width < widthNum">Email</th>
      <td>{{user.email}}</td>
    </div>  
    <div id="containerUser">
      <th scope="col" v-if="width < widthNum">Phone</th>
      <td>{{user.phone}}</td>
    </div>
      <div id="containerUser">
      <th scope="col" v-if="width < widthNum">Website</th>
      <td>{{user.website}}</td>
    </div>
    <hr />
    </tr>
   
  </tbody>
</table>
    </div>
</div>

</template>

<script>
import axios from "axios"
export default {
    name:"containerUser",
    data (){
        return {
            users:null,
            width: document.documentElement.clientWidth,
            widthNum: 785,
        }
    },
    created: function(){
        axios.get("https://jsonplaceholder.typicode.com/users").then((item)=>{
            this.users = item.data;
      console.log(this.width);  

        })
    } ,
    mounted() {
    window.addEventListener('resize', this.getDimensions);
  },
  unmounted() {
    window.removeEventListener('resize', this.getDimensions);
  },
  methods: {
    getDimensions() {
      this.width = document.documentElement.clientWidth;
    }
  } 
   
}
</script>

<style>
#containerUser{
    display: contents;
    flex-direction: column;  
}
#image{
  display: inline-flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
 width: 40px;
 height: 40px;
  border-radius: 50px;
  transition: 0.3s;
  background-color: rgb(241, 181, 181);
}
#image:hover{
  display: inline-flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
 width: 80px;
 height: 80px;
  border-radius: 50px;
  transition: 0.3s;
  background-color:brown;

}
@media screen and (max-width: 785px) {
    tr,tbody{
    font-size:large;
    margin: 0;
    padding: 0;
    display: flex;
    align-items:initial;
    justify-content: center;
    flex-direction: column;    
}
td{
    display: flex;
    align-items: center;
    justify-content: center;
}
#containerUser{
    display: inline-flex;
    justify-content:space-between;
    align-items: center;
    flex-direction: row;   
}
}

</style>