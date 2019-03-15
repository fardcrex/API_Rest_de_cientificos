<template>

  <div class="about">
    <h1>This is an about page</h1>
    <h2>{{$route.params.id}}</h2>
    <h3>{{persona.name}}   :  {{persona.id}}---{{persona.two.apellido}} </h3>
    
     
     <div  v-bind:key="cienti.img" v-for="(cienti ) in cientificosIma" >
       <img :src="'/img/'+cienti.img" alt=""><p>{{cienti.img}}</p>
       <router-link :to="'/about/'+cienti.name"> 
    <button class="btn waves-effect waves-light  light-blue darken-1" type="submit" name="action">demo
        <i class="material-icons right">send</i>
    </button>
   </router-link>
     </div>
  </div>
</template>
<script>
 import { setTimeout } from 'timers';
export default {
 
   data() {
     return {
        cientificosIma:[{name:"5c8405c00ca7a20b7c240b8f", img:"5c8405c00ca7a20b7c240b8f.jpg"},
      {name:"5c8406fc0ca7a20b7c240b91", img:"5c8406fc0ca7a20b7c240b91.jpg",
      },
      {name:"5c8407bc0ca7a20b7c240b92", img:"5c8407bc0ca7a20b7c240b92.034d5a11.jpg"},
      {name:"5c8408740ca7a20b7c240b93", img:"5c8408740ca7a20b7c240b93.034d5a11.jpg"}],
    persona:{
      name:"cargando",
      id:"cargando ID",
      two:{apellido:"cargando apellido"}
     }
     }
     
   },
   created(){
     if(!this.$route.params.id){
       this.persona= {
      name:"pedrño",
      id:"asdasdasdasdf342fse",
      two:{apellido:"sasas"}
     }
     }else{
       
       setTimeout(()=>{
this.persona= {
      name:"juan",
      id:this.$route.params.id,
      two:{apellido:"conislla"}

     }
       },3000)
       
     }

   }
}
</script>