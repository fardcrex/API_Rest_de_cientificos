<template>
    <div class=footer>
        <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odio fugit eius quod eum natus perspiciatis molestias dignissimos laborum sequi nam explicabo, sit minus nisi labore ex doloremque iusto illo ullam?
        </p>
        
        
        <div>
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
          fetch(`http://zadness.com/api/cientificos/${this.clave}`).then(res=>{       this.mostrarRespuestaDelServidor(res.status)            
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
    }
  }
}

</script>
<style lang="scss">
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
    &>div{
         align-self: center;
         justify-self: start;
    }
    &>p{
       
         align-self: center;
         justify-self: center;
    }


@media screen and (min-width:$cel){
      
  }
  @media screen and (min-width:$tablet){
      padding:3%;
      grid-template-columns: 80% 20%;
      grid-template-rows: 1fr ;
      &>div{
         align-self: center;
         justify-self: center;
    }
    &>p{
        padding: 1%;
         align-self: center;
         justify-self: center;
    }
  }
  @media screen and (min-width:$laptop){
       
  }
  @media screen and (min-width:$desk){
         
  }
 }
</style>
