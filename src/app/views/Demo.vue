<template>
    <div class="demo">
        
        <tablaInfo > </tablaInfo>
  <!--       <div class=data>
            <div class="card"  v-for="cienti in cientificos" v-bind:key="cienti._id" >
                <div class="card-image waves-effect waves-block waves-light">
                <div v-on:click="obtenerCienti(cienti) ">
                        <router-link   :to="'/demo/'+cienti._id"  > 
                        <img class="imagen" v-if="cienti.imagen" :src="'http://127.0.0.1:5500'+cienti.imagen" alt=""   >
                        </router-link>
                    </div>     
            
                </div>
                <div class="card-content">
                <span v-on:click="obtenerCienti(cienti)" class="card-title activator grey-text text-darken-4">{{cienti.name}}<a href="#comienzo"  ><i class="material-icons right">edit</i></a></span>
                <p><a :href="cienti.URL">Wiki</a></p>
                <p >{{cienti.country.name}}</p>
                <p>{{cienti.AñoNacimiento || "0000"}}{{cienti.AñoFallecimiento?" - "+cienti.AñoFallecimiento:""}}</p>
                </div>            
            </div>
        </div>
         -->
           <!--  <ul> 
            <li v-for="cienti in cientificos" v-bind:key="cienti._id">
                <h2>
                    {{ "vinea" || cienti.name}}
                </h2>
                <p>
                    {{cienti.country.name}}
                    {{'http://127.0.0.1:5500'+cienti.imagen}}
                </p>
                
                <router-link :to="'/demo/'+cienti._id" > 
                    <img v-if="cienti.imagen" :src="'http://127.0.0.1:5500'+cienti.imagen" alt=""  class="activator" v-on:click="obtenerCienti(cienti._id)">
                </router-link>
               
                </li>
            </ul>
 -->
        
        
       
    </div>
</template>

<script>
import TablaInfo from "../components/TablaInfo.vue"



export default {

    data(){
        return {            
            
        }
    },
    components:{
        TablaInfo
    },
    created(){
      
       
    },
    methods:{
       
        
        async deleteCientificos(){

        },
        async reiniciarCientificos(){

        },
        async obtenerCienti(id){
             console.log(this.cienti)
            console.log(id)
            console.log(this.cienti._id)
            console.log(id._id)
            if(this.cienti._id !== id._id){
                this.cienti=id
            /*      let datos = await axios.get(`http://localhost:3000/api/cientifico/${id}`)
            if(datos){
                console.log("sadasda")
                console.log(datos)
                this.cienti=datos.data.data
                 console.log(this.cienti)
            } */
            }
           
        }
    }
}
</script>

<style lang="scss">
   .demo{
       min-height: 80vh;
       background-color: #EFEFEF
   }
   
</style>