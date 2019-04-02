<template>
    <div class=footer>
        
        <div class=footer-one>
            <p>
            Sigueme en twitter con tweets de las ocurrencias sobre la vida de un emprendedor, ( vue, golang, flutter, psql, mongoDB, java) pronto IA con python
            
        
        <a href="https://twitter.com/fardcrex">twitter <i class="fab fa-twitter-square"></i></a></p>
        <p v-on:click="ejemplo">Agredimientos: Alvaro Enrique por prestar su servidor para porder poner en linea este proyecto 
        <a href="https://twitter.com/AlvaroEnriqueDS">twitter <i class="fab fa-twitter-square"></i></a></p>
        <!-- <center><a href="https://www.cerotec.net/estadisticas-125883/zadness.com" title="abrir detalles"><img src="https://www.cerotec.net/contador.php?t=13&s=2&i=125883" alt="www.cerotec.net"></a> <br><a href='https://www.cerotec.net' style='font-size:12px;' >Analitics</a></center> -->
        </div>
        
        <div class=footer-dos>
            <input v-model="clave" type="text" style="color: white" placeholder="Clave Para reiniciar BD">
              <button v-on:click="reiniciar" class="btn waves-effect waves-light red darken-1" type="submit" name="action"> <span style="color: #fff">Reiniciar</span>
                <i class="material-icons right">refresh</i>
            </button> 
            {{mensaje}}
        </div>
        
    </div>
</template>

<script>
export default {   
  name: 'footerapp'  ,

  data(){
      return {
          clave:"",
          mensaje:"",
          
      }
  }
  ,methods:{
     reiniciar(){
        if(this.clave){
            fetch(`https://zadness.com/api/cientificos/${this.clave}`).then(res=>{
                this.mostrarRespuestaDelServidor(res.status)            
                this.reiniciarMensaje()
            }).catch(e=>{                   
                this.mensaje="Clave incorrecta"+e                  
                this.reiniciarMensaje()
            }
        )}else{
            this.mensaje="Inserte clave"
        }
          
      },
    mostrarRespuestaDelServidor:  function (option) {
        const options = {
            '200': ()=>{this.mensaje="Se reinicio correctamente"},
            '401': ()=>{this.mensaje="Clave key incorrecta"},
            '404': ()=>{this.mensaje="Url del Servidor está roto"},
            '500': ()=>{this.mensaje="Error en el Servidor"},
            'default': ()=>{this.mensaje="Error no calificado"},
            }   
        return (options[option] || options['default'])(); 
    },
    reiniciarMensaje: function (time = 5000) {
        setInterval(()=>{
                this.mensaje=""
                 },time)
    },
    ejemplo(){
        // eslint-disable-next-line
        true?this.$router.push({ name: 'demo', params: { id: '5ca174fc3d91e80a067f1080' } }):console.log("sad");
        
        
         console.log("si funciona")}
    
  }
}

</script>
<style lang="scss" scope>
$cel: 540px;
$tablet: 814px;
$laptop:1025px;
$desk:1300px;

 .footer{
     min-height:25vh;
     background-color: #1D2731;
     color: white;
     padding: 5%;
     display: grid;
     grid-template-columns: 1fr;
      grid-template-rows:1fr 1.2fr;
    &-one{
         align-self: center;
         justify-self: start;
    }
    &-dos{
       
         align-self: center;
         justify-self: center;
    }


@media screen and (min-width:$cel){
      
  }
  @media screen and (min-width:$tablet){
      padding:3%;
      grid-template-columns: 80% 20%;
      grid-template-rows: 1fr ;
      &-one{
         align-self: center;
         justify-self: center;
    }
    &-dos{
        padding: 1%;
         align-self: start;
         justify-self: center;
    }
  }
  @media screen and (min-width:$laptop){
       
  }
  @media screen and (min-width:$desk){
         
  }
 }
</style>
