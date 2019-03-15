<template>

  <div id="app" class=app>
     <nav>
            <div class="nav-wrapper light-blue darken-1">
              
                <div class="brand-logo"><router-link to="/" >Zadness</router-link></div>
     <a href="#" data-target="mobile-demo" class="sidenav-trigger"><i class="material-icons">menu</i></a>
            <ul id="nav-mobile" class="right hide-on-med-and-down">
                <li><router-link to="/documentación">Documentación</router-link></li>
                <li><router-link to="/about">About</router-link></li>
                <li><a href="collapsible.html">GitHub</a></li>
            </ul>
            </div>
        </nav>  
        <ul class="sidenav" id="mobile-demo">
    <li><router-link to="/documentación">Documentación</router-link></li>
    <li><router-link to="/about">About</router-link></li>
    <li><router-link to="/demo">Demo</router-link></li>
    <li><a href="collapsible.html">GitHub <i class="material-icons right">link</i></a></li>
   
  </ul>  

    <router-view/>

    <footerapp>
    </footerapp>

  </div>
</template>


<script>

import footerapp from './components/footerapp.vue'
import { setTimeout } from 'timers';
 
export default {
  name: 'home',
  created() {
      
      
      
    },
    mounted(){
      this.crearCDN("iconFont","link","https://fonts.googleapis.com/icon?family=Material+Icons")
      this.crearCDN("fontGoogle","link","https://fonts.googleapis.com/css?family=Merriweather|Open+Sans")
      this.crearCDN("materializeCSS","link","https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css")
      this.crearCDN("materializeJS","script","https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js")
      setTimeout(()=>{var elems = document.querySelectorAll('.sidenav');
    var instances = M.Sidenav.init(elems);},800)
    
    },
    methods:{
    crearCDN: function (id ="",tipo="",urlDelCDN="") {
       if (!document.getElementById(id)){ // was already loaded
      let element = document.createElement(tipo);
      element.id = id;
      if(tipo ==="link"){
        element.href = urlDelCDN;       
        element.rel = "stylesheet"}
      else if (tipo ==="script"){
        element.src =urlDelCDN;
      }else{
        console.log("tipo equivocado")
      }
      document.getElementsByTagName('head')[0].appendChild(element);}
    }
    },
components: {
    footerapp
  }}
</script>



<style lang="scss">
$cel: 540px;
$tablet: 814px;
$laptop:1025px;
$desk:1300px;
.brand-logo{
   margin-left: 0;
@media screen and (min-width:$tablet){
        margin-left: 2rem;
  }
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983 !important
    }
  }
}
.app{
  background-color: #EFEFEF
}
</style>
