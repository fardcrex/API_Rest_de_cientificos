<template>

  <div class="about">
    <h1>This is an about page</h1>
    <h2>{{$route.params.idd}}</h2>
    <h3>{{persona.name}}   :  {{persona.id}}---{{persona.two.apellido}} </h3>
    
     
     <div  v-bind:key="cienti.img" v-for="(cienti ) in cientificosIma" >
    <p>{{cienti.name}}</p>
       <router-link :to="'/about/'+cienti.name"> 
    <button class="btn waves-effect waves-light  light-blue darken-1" type="submit" name="action">demo
        <i class="material-icons right">send</i>
    </button>
   </router-link>
     </div>
  </div>
</template>
<script>
 
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
     if(!this.$route.params.idd){
       this.persona= {
      name:"pedrño",
      id:"asdasdasdasdf342fse",
      two:{apellido:"sasas"}
     }
     }else{
       
      
this.persona= {
      name:"juan",
      id:this.$route.params.idd,
      two:{apellido:"conislla"}

     }
      
       
     }

   }
}
</script>
<style lang="scss" scoped>
  .about {
    min-height: 80vh;
  }
</style>
