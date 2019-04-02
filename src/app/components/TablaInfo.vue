<template>
<div>
         
    <a v-if="!urlIdCientifico" href="#comienzo" class="btn-floating btn-large waves-effect waves-light blue" style="position: fixed;right:1rem;bottom:1rem;z-index:1000"><i class="material-icons " >arrow_upward</i></a>
    <a v-if="urlIdCientifico" href="#comienzo" class="btn-floating btn-large waves-effect waves-light blue" style="position: fixed;right:1rem;bottom:1rem;z-index:1000"><i class="material-icons " >edit</i></a>
    <form class="mainContainer " id="comienzo"  v-on:submit.prevent> 
        <div class="container__one">
            <div v-if="!entrarDatos">
                <div class="card" >
                <div class="card-image waves-effect waves-block waves-light">
              
                      <!--  -->
                        <img class="imagen" :src="urlDelServidorParaImagenes+(cientiObtenido.imagen||'/assets/imagenDefault.png')" alt=""   >
                   
                      
            
                </div>
                <div class="card-content">
                <h1  class="card-title activator grey-text text-darken-4 font-title">{{cientiObtenido.name}}</h1>
                
                <p >{{cientiObtenido.country.name}}</p>
                <p>{{cientiObtenido.AñoNacimiento || "0000"}}{{cientiObtenido.AñoFallecimiento?" - "+cientiObtenido.AñoFallecimiento:""}}</p>
                <p><a :href="cientiObtenido.url">Wiki</a></p>
                </div>            
            </div>
        </div> 
           
        <div  v-if="entrarDatos">
            <div class="row">
                <div class="input-field col s12">
                <input v-model="cientiNew.name" id="name" type="text" class="validate" required>
                <label class="active" for="name">Nombre del Cientifico</label>
                </div>
            </div>
            <div class="row">
                <div class="file-field input-field">
                <div class="btn">
                    <span>Imagen</span>
                    <input type="file" id=file>
                </div>
                <div class="file-path-wrapper">
                    <input class="file-path validate" type="text">
                </div>
                </div>
            </div>
          
            
            <div class="row">
                <div class="input-field col s10">
                <label class="active" for="pais">Nacionalidad del Cientifico</label>
                <input v-model="cientiNew.country.name" id=pais type="text" list="paises" required>
                <datalist id="paises">
                    <option :value="pais.name" v-for="pais in countries" v-bind:key="pais._id"></option>
                
                </datalist>
        
                </div>
            </div>
            <div class="column">
                <div class="input-field col s5">
                <input v-model="cientiNew.AñoNacimiento" id="nac" type="number" class="validate" placeholder="0000">
                <label class="active" for="nac">Año de Nacimiento</label>
                </div>
            </div>
            <div class="column">
                <div class="input-field col s5">
                <input v-model="cientiNew.AñoFallecimiento"  id="fall" type="number" class="validate" placeholder="2000">
                <label  class="active" for="fall">Año de Fallecimiento</label>
                </div>
            </div>
            <div class="row">
                
                <div class="row">
                    <div class="input-field col s12">
                    <textarea v-model="cientiNew.url" id="textarea1" class="materialize-textarea"></textarea>
                    <label for="textarea1">Link</label>
                    </div>
                </div>
                
            </div>
        </div>
            
        
        </div>
        <div class="container__dos">
            <h2 v-on:click="ejemplo" class=font-descripcion-title>Descripción: </h2>
            <p v-if="!entrarDatos" class=font-descripcion>{{cientiObtenido.descripcion}}</p>
          <div class="column"  v-if="entrarDatos">
          <div class="input-field col s12">
            <textarea  v-model="cientiNew.descripcion" id="textarea2" class="materialize-textarea" data-length="120"></textarea>
            <label for="textarea2">Textarea</label>
          </div>
          <div class="row">
                <div class="input-field col s12">
                <input v-model="cientiNew.usuario" id="name" type="text" class="validate">
                <label class="active" for="name">Username</label>
                </div>
            </div>
        </div>
            
            <div class=botones>
                <button  v-show="!entrarDatos" v-on:click="activarFormulario(1)" class="btn waves-effect waves-light light-blue darken-1" type="submit" name="action">Nuevo
                <i class="material-icons right">add</i>
                </button>
                <button v-on:click="postCientificos()" v-show="entrarDatos && editDatos"  class="btn waves-effect waves-light light-blue darken-1" type="submit" name="action">Enviar
                <i class="material-icons right">send</i>
                </button>
                
                <button v-show="cientiObtenido._id && !entrarDatos" v-on:click="activarFormulario(2)" class="btn waves-effect waves-light green darken-1 " type="submit" name="action">Editar
                <i class="material-icons right">edit</i>
                </button>
                <button v-on:click="putCientificos($route.params.id)" v-show="entrarDatos && cientiObtenido._id && !editDatos"  class="btn waves-effect waves-light light-blue darken-1" type="submit" name="action">Actualizar
                <i class="material-icons right">refresh</i>
                </button>
               <router-link  style="color:#fff" :to="'/demo/'"  > <button  v-on:click="deleteCientificos($route.params.id)"  v-show="$route.params.id && !entrarDatos" class="btn waves-effect waves-light red darken-1" type="submit" name="action">Eliminar
                <i style="color:#fff" class="material-icons right" >delete</i>
                </button></router-link>
                  <button  v-show="entrarDatos" v-on:click="desactivarFormulario()" class="btn waves-effect waves-light red darken-1" type="submit" name="action">Cancelar
                <i class="material-icons right">cancel</i>
                </button> 
            </div>
            <p>{{mensajeParaElUsuario}}</p>
            
        </div>
    </form>  

    <!-- /////////////Pogres//////////// -->
    <div class="caja_progres">
        <div class="progress progress_tamamo" v-show="loader">
                    <div class="indeterminate"></div>
        </div>
    </div>
    <!-- /////////////Pogres//////////// -->
    
     <div class=data>
            <div class="card"  v-for="cienti in cientificos" v-bind:key="cienti._id" >
                <div class="card-image waves-effect waves-block waves-light">
                
                        <router-link   :to="'/demo/'+cienti._id"  > 
                        <img class="imagen" :src="urlDelServidorParaImagenes+(cienti.imagen||'/assets/imagenDefault.png')" alt=""   >
                        </router-link>
                        
            
                </div>
                <div class="card-content" v-on:click="obtenerCienti(urlIdCientifico)">
                <span v-on:click="obtenerCienti(urlIdCientifico)" class="card-title activator grey-text text-darken-4 font-title"> <router-link   :to="'/demo/'+cienti._id"  > {{cienti.name}}</router-link><i v-on:click="obtenerCienti(urlIdCientifico)"  class="material-icons right">more_vert</i> </span>
               
                <p v-if="cienti.country">{{cienti.country.name}}</p>
                <p>{{cienti.AñoNacimiento || "0000"}}{{cienti.AñoFallecimiento?" - "+cienti.AñoFallecimiento:""}}</p>
                 <p><a :href="cienti.url">Wiki</a></p>
                </div>
                <div class="card-reveal" v-on:click="obtenerCienti(urlIdCientifico)" >
      <span class="card-title grey-text text-darken-4">Descripción<i class="material-icons right">close</i></span>
      <p>{{cienti.descripcion}}</p>
    </div>            
            </div>
        </div>
         
</div>
    
       
        
   
</template>

<script>
class Cientifico{

    constructor(name = "",country = {name:""},imagen = "",url = "",AñoNacimiento ,AñoFallecimiento ,descripcion = ""){
        this.name=name
        this.country=country
        this.imagen=imagen
        this.url=url
        this.AñoNacimiento=AñoNacimiento
        this.AñoFallecimiento=AñoFallecimiento
        this.descripcion=descripcion
    }
}
/* eslint-disable */

import  axios  from 'axios';
import { setTimeout } from 'timers';

export default {
    name: "TablaInfo",
    data(){
        return {
            urlDelServidorParaImagenes:"https://zadness.com"/* "http://127.0.0.1:5500" */,
            urlDelServidorApi:"https://zadness.com/api"/* http://zadness:3500/api  */,
            mensajeParaElUsuario:"",
            loader: false,
            entrarDatos:false,
            editDatos:false,
            countries:[],
            cientificos:[],
            congreso:{name:"Quinto Congreso Solvay",
                        url:"https://es.wikipedia.org/wiki/Congreso_Solvay",
                        country:{name:" Bruselas"},
                        descripcion:"Fue la conferencia más famosa y se celebró en octubre de 1927 en Bruselas. El tema principal fue Electrones y fotones, donde los mejores físicos mundiales discutieron sobre la recientemente formulada teoría cuántica, dieron un sentido a lo que no lo tenía, construyeron una nueva manera de entender el mundo y se dieron cuenta que para describir y entender a la naturaleza se tenían que abandonar gran parte de las ideas preconcebidas por el ser humano a lo largo de toda su historia.\n Fue una generación de oro de la ciencia, posiblemente como no ha habido otra en la historia. Diecisiete de los veintinueve asistentes eran o llegaron a ser ganadores de Premio Nobel, incluyendo a Marie Curie, que había ganado los premios Nobel en dos disciplinas científicas diferentes (Premios Nobel de Física y de Química). ",
                        imagen:'/assets/Solvay_conference_1927.jpg',
                        AñoNacimiento:1927
                },
            cientiObtenido:{name:"Cargando",
                    url:"",
                    country:{name:"  Cargando Pais"},
                    descripcion:"Cargando descripción",
                    imagen:'/assets/imagenDefault.png',
                    AñoNacimiento:"0000",
                    AñoFallecimiento:"0000"
            },
            
            img: '../../assets/5c7f29f1c561cf6ef0869c70.jpg',
            cientiNew: new Cientifico()
        }
    },computed:{
         countriesObj: function () {
             return convertArrayToObject(this.countries)
         },
         urlIdCientifico: function () {
             return (this.$route.params.id || 0)
         }
    },
    created(){
        this.getCountries()
        this.getCientificos()       
        ////console.log(this.$route.params.id)
        if(!this.$route.params.id){
           
            this.cientiObtenido={name:"Quinto Congreso Solvay",
                    url:"https://es.wikipedia.org/wiki/Congreso_Solvay",
                    country:{name:" Bruselas"},
                    descripcion:"Fue la conferencia más famosa y se celebró en octubre de 1927 en Bruselas. El tema principal fue Electrones y fotones, donde los mejores físicos mundiales discutieron sobre la recientemente formulada teoría cuántica, dieron un sentido a lo que no lo tenía, construyeron una nueva manera de entender el mundo y se dieron cuenta que para describir y entender a la naturaleza se tenían que abandonar gran parte de las ideas preconcebidas por el ser humano a lo largo de toda su historia.\n Fue una generación de oro de la ciencia, posiblemente como no ha habido otra en la historia. Diecisiete de los veintinueve asistentes eran o llegaron a ser ganadores de Premio Nobel, incluyendo a Marie Curie, que había ganado los premios Nobel en dos disciplinas científicas diferentes (Premios Nobel de Física y de Química). ",
                    imagen:'/assets/Solvay_conference_1927.jpg',
                    AñoNacimiento:1927
            }
        }
        else{
          //  //console.log("entro al if de created")
              this.obtenerCienti(this.$route.params.id)
        }
    },
    methods:{
        async getCientificos(){
            let datos = await axios.get(this.urlDelServidorApi+'/cientificos')
            if(datos){
                //console.log("Se obtuvo cientificos")
                //console.log(datos.data.data )
                this.cientificos=datos.data.data 
            }
        },
        async getCountries(){
            let datos = await axios.get(this.urlDelServidorApi+'/countries')
            if(datos){
             //   //console.log(datos)
                this.countries=datos.data.data
            }
            //console.log(this.countriesObj)
        },


        async deleteCientificos(id){
            this.loader=true
            try {
                let res = await axios.delete(this.urlDelServidorApi+`/cientifico/${id}`/* ,{
                method:"delete",
                headers:{
                    'Content-Type': 'application/json'
                }
            } */)
                //console.log("respuesta de DELETE")  
                //console.log(res)
            } catch (error) {
                
            }
            
            this.cientiObtenido={...this.congreso}
             this.getCientificos() 
            this.loader=false
        },



        async postCientificos(){
            this.loader=true
          //  //console.log(this.cientiNew)
            this.isPaisValido(this.cientiNew.country)
            let cientifico = new Cientifico(this.cientiNew.name,this.cientiNew.country,this.cientiNew.imagen,this.cientiNew.url,this.cientiNew.AñoNacimiento,this.cientiNew.AñoFallecimiento,this.cientiNew.descripcion)

            try {
                cientifico.country=await this.countriesObj[this.cientiNew.country.name]._id
            
            } catch (error) {
                //console.log(cientifico)
            }
                       
            let res
            try {
                res = await axios.post(this.urlDelServidorApi+`/cientifico`,           cientifico )
                //respuesta de POST//
                //console.log("respuesta de POST")
                //console.log(res)
            } catch (error) {
                Promise.reject(error)
                //console.log(error)
                res = ""
                return ""
            }
            
               
            //console.log(res)
            if(!file.files[0]){
                 res.data.data=await {...res.data.data,...{imagen:`/assets/imagenDefault.jpg`}}
                  //console.log(res.data.data)
            }else{
                let nameImagenFinal= obteniendoNameImagenConSuExtension(file.files[0].name,res.data.data._id)
                res.data.data= {...res.data.data,...{imagen:`/assets/${nameImagenFinal}`}}
                 res = await  axios.put(this.urlDelServidorApi+`/cientifico/${res.data.data._id}`,res.data.data)
                
                //console.log(nameImagenFinal)
                await this.enviarImagen(nameImagenFinal)
               
            }
            this.loader=false
            this.getCientificos() 
            this.desactivarFormulario()  
            this.mensajeParaElUsuario = ""
        },
        async putCientificos(id){
            this.loader=true
           
            // Le da un ID de pais al cientifico a enviar
             //console.log(this.cientiNew)
              this.cientiNew.country=await this.countriesObj[this.cientiNew.country.name]._id
              let nameImagenFinal
              //console.log("imagen")
              //console.log(this.cientiNew.imagen)
            if(file.files[0]){
                 this.cientiObtenido.imagen='/assets/imagenDefault.png'
                 nameImagenFinal= await obteniendoNameImagenConSuExtension(file.files[0].name,id,this.cientiNew.imagen)
                this.cientiNew=await {...this.cientiNew,...{imagen:`/assets/${nameImagenFinal}`}}                
                await this.enviarImagen(nameImagenFinal)
                this.desactivarFormulario()
            }
            try {
                let res = await axios.put(this.urlDelServidorApi+`/cientifico/${id}`,this.cientiNew)
                //console.log("respuesta de PUT")
                //console.log(res)
            } catch (error) {
                this.mensajeParaElUsuario = "Error"
            }
            
            await this.getCientificos()  
                
            await this.obtenerCienti(id)  
             this.loader=false
           //  //console.log(res)
        },

         async obtenerCienti(urlIdCientifico){
             this.loader=true
            this.desactivarFormulario()
          /*    //console.log(this.cientiObtenido)
            //console.log(cientificoSeleccionado)
            //console.log(this.cientiObtenido._id)
            //console.log(cientificoSeleccionado._id)
            if(this.cientiObtenido._id !== cientificoSeleccionado._id){
                this.cientiObtenido=cientificoSeleccionado */
            let datos
            try {
                datos = await axios.get(`${this.urlDelServidorApi}/cientifico/${urlIdCientifico}`)
            } catch (error) {
                datos=false
                setTimeout(()=>{
                    this.loader=false
                    alert("URL Cientifico inválido")
                    this.cientiObtenido={...this.congreso}
                    this.desactivarFormulario()
                },3000)
            } 
             //console.log(datos)
            if(datos){
                this.loader=false
                //console.log("Obtener cientifico GET")
                //console.log(datos.data.data)
                this.cientiObtenido=datos.data.data
            //    //console.log(this.cientiObtenido)            
            }
           
        },


    ////////Formulario///////////////
        activarFormulario(botonAMostrar){
         //   //console.log(this.countriesObj)
            this.entrarDatos=true
            if(botonAMostrar==1){
                this.editDatos=true
                this.cientiNew = new Cientifico()
            }
            if(botonAMostrar==2){
                this.editDatos=false
                this.cientiNew = {...this.cientiObtenido}
            }
        },
        desactivarFormulario(){
            this.entrarDatos=false
        },
    ////////Formulario///////////////

        async enviarImagen(name){
         //   //console.log(this.cientiNew)
            var fileField = document.querySelector("input[type='file']");
         //   //console.log(fileField)
            var formData = new FormData();
            formData.append('nombre', name);
            formData.append('file', fileField.files[0]);

            await fetch('https://zadness.com/upload', {
            method: 'post',
            body: formData
            })
            
        },


        ///////////Validaciones//////////////
        isPaisValido(pais){
            if(this.countriesObj[pais]){
                this.mensajeParaElUsuario = ""
            }else{
                this.mensajeParaElUsuario = "Pais no válido"
            }
        },
        ejemplo(){
            
            this.$router.push({ name: 'home'})
            console.log("si funciona")}
        },
    watch: {
        '$route' (to, from) {
            if(!this.$route.params.id){           
               this.cientiObtenido={...this.congreso}
            }
            else{
            //  //console.log("entro al if de created")
                this.obtenerCienti(this.$route.params.id)
            }
        }
    },
    beforeRouteUpdate (to, from, next) {
    
    next()
  }
}

let obteniendoNameImagenConSuExtension = function(name,nuevo,old=""){
    let extensionImgNew =name.split(".")[1]
    let extensionImgOld =old.split(".")[1]
    //console.log("funcion change name")
    //console.log(name)
    //console.log(nuevo)
    //console.log(old)
    
    if(extensionImgNew===extensionImgOld){
    //console.log(extensionImgNew)
    
        if(`new.${extensionImgNew}`===old.split("_")[1]){
            return `${nuevo}.${extensionImgNew}`
        }
        return `${nuevo}_new.${extensionImgNew}`
    }else{
        return `${nuevo}.${extensionImgNew}`
    }
   
    }

    function convertArrayToObject(array) {
    return array.reduce(function (obj, item) { 
        obj[item.name] = item; 
        return obj; 
    }, {});
}

</script>


<style lang="scss">
$cel: 540px;
$tablet: 814px;
$laptop:1025px;
$desk:1300px;

.mainContainer{        
    min-height:80vh;
    display: grid;
    margin: auto;
     justify-content: center;	
    grid-template-columns: 1fr;
    grid-template-rows: auto  1fr;
    @media screen and (min-width:$tablet){
        grid-template-columns: 47% 47%;
        grid-template-rows: 100%;
        height: 60vh;
        justify-content: center;	
    }    
}
    
    
.container__one,.container__dos {
    padding: 10% 10% 0 10%;
    justify-self: center;
    align-self: center;
    &>div>div>div>img{        
        max-height: 50vh ;
        
        max-width: 100%;
    }

     @media screen and (min-width:$tablet){
      padding: 10% 10% 0 10%;
      &>div>div>div>img{        
        height: 40vh ;
        
        width: 100%;
    }
  }
}
.container__dos {
         padding: 0 10% 0 10%;
    @media screen and (min-width:$tablet){
        padding: 6% 0 0 0;
    }
}

    .botones{
        display: flex;
        flex-direction: column;
        &>button{
            margin-top:  5%;
            width: 200px;
        }
         &>a>button{
            margin-top:  5%;
            width: 200px;
        }
    }
    .data{
       
       width: 80%;
       margin: auto;
        margin-top: 2.5%;
       display: grid;
       grid-template-columns: 100%;
        justify-content: center;	
        grid-column-gap: 5%;
       
  @media screen and (min-width:$cel){
    grid-template-columns: 90%;   
  }
  @media screen and (min-width:$tablet){
       grid-template-columns: 45% 45%;
  }
  @media screen and (min-width:$laptop){
          grid-template-columns:30% 30% 30%;
  }
  @media screen and (min-width:$desk){
          grid-template-columns: 30% 30% 30%;
  }
}
.font-descripcion{
       font-family: 'Open Sans', sans-serif;
       font-size: 1rem;
        padding-bottom: 2rem
       
}
.font-descripcion-title{
    font-family: 'Merriweather', serif;
       font-size: 2.5rem;
       padding-bottom: 2rem

}
.font-title{
    font-family: 'Merriweather', serif;
       

}
.progress_tamamo{
    width: 80%;
    margin: auto;
}
.caja_progres{
    min-height: 3vh;
}
</style>