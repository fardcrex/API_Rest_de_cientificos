<template>

  <div class="about">
   <div class=title>
     <h1>Acerca del Proyecto</h1>
      
        
     <h2  class="header">Sobre el desarrollador</h2>
     <div v-show="cardAvatar" class="row">
      <div class="col s12">
        <div class="card">
          <div class="card-image">
            <img class="img" src="../../assets/jair.jpg">
            <span class="card-title">Jair Conislla</span>
          </div>
          <div class="card-content">
            <span class="desc">Estudiante de Ingeniería de Software de la Universidad Tecnológica del Perú y de la carrera de Física de la Universidad Nacional Mayor de San Marcos. Con interés de trabajar en las áreas de programación, sistemas, informática. Me considero una persona autodidacta, analítica y con excelentes habilidades interpersonales.</span>
          </div>
          <div class="card-action">
            <a href="https://github.com/fardcrex">gitgub</a>
          </div>
        </div>
      </div>
    </div>
     <div v-show="!cardAvatar" class="col s12 m7">   
      <div class="card horizontal">
        <div class="card-image">
          <img class=foto2
          src="../../assets/jair.jpg">
        </div>
        <div class="card-stacked">
          <div class="card-content">
            <span  class="desc">Estudiante de Ingeniería de Software de la Universidad Tecnológica del Perú y de la carrera de Física de la Universidad Nacional Mayor de San Marcos. Con interés de trabajar en las áreas de programación, sistemas, informática. Me considero una persona autodidacta, analítica y con excelentes habilidades interpersonales.</span>
          </div>
          <div class="card-action">
            <a href="https://github.com/fardcrex">gitgub</a>
          </div>
        </div>
      </div>
    </div>
   </div>
   <div class="frotend-container">
     <h2>Tecnologias Frontend</h2>
     <img class=img width="650" src="../../assets/Imagen de iOS (1).jpg" alt="Escritorio">
     <ul class="collection">
        <li class="collection-item avatar">
          <img src="../../assets/node.png" alt="" class="circle">
          <span class="title">Servidor Web</span>
          <p>Node.js <br>
           8.10.0
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img src="../../assets/express.png" alt="" class="circle">
          <span class="title">Framework Backend</span>
          <p>Express<br>
            4.16.3
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img src="../../assets/mongo.png" alt="" class="circle">
          <p>Mongo DB <br>
            3.6.3
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img src="../../assets/mongoose.jpg" alt="" class="circle">
          <span class="title">Object Modeling</span>
          <p>Mongoose<br>
            5.2.6
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
      </ul>
   </div>
   <div class="backend-container">
     <h2>Tecnologias Backend</h2>
     <img class=img src="../../assets/Backend.jpg" alt="Escritorio">
     <ul class="collection">
        <li class="collection-item avatar">
          <img src="../../assets/logo.png" alt="" class="circle">
          <span class="title">Framework Javascript</span>
          <p>Vue<br>
            2.6.6
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img src="../../assets/materialize.png" alt="" class="circle">
          <span class="title">Framework Web</span>
          <p>Materialize CSS <br>
            1.0.0
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img src="../../assets/prismjs.png" alt="" class="circle">
          <span class="title">Syntax Highlighter</span>
          <p>Prism.js <br>
            1.15.0
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img src="../../assets/nginx-wp.jpg" alt="" class="circle">
          <span class="title">Servidor Web</span>
          <p>Nginx <br>
            1.14.0 
          </p>
          <a href="#!" class="secondary-content"><i class="material-icons">grade</i></a>
        </li>        
      </ul>

   </div>
  </div>
</template>
<script>

export default {
 
   data() {
     return {
       cardAvatar:true
     }
     
   },
   created(){
    const mediumBp = window.matchMedia('(max-width: 814px)');
    console.log(mediumBp)
    if(mediumBp.matches){
      this.cardAvatar= true
    }else{
      this.cardAvatar= false
    }
   }
}
</script>
<style lang="scss" >
  $cel: 540px;
  $tablet: 814px;
  $laptop:1025px;
  $desk:1300px;
h1{
        font-size: 3rem;
        font-family: Merriweather;
        text-align: center;
        @media screen and (min-width:$tablet){
        font-size: 3.5rem;
    }
    }
    h2{
        font-size: 2.8rem;
        font-family: Merriweather;
        font-weight: bold;
    }
    h3{
        font-size: 2.5rem;
        font-style: italic;
        font-family: Merriweather;
    }
    p{
        
        font-family:  'Open Sans', sans-serif;
        font-size: 1rem;
        
    }
  .desc{
    font-size: 1.6rem;
     @media screen and (min-width:$tablet){
         font-size: 2.5rem;}
  }
  .about {
    margin: auto;
    min-height: 90vh;
    display: grid;
    width: 98%;
    justify-items: center;
    max-width: 1300px;
    grid-template-columns: 100%;
    grid-template-areas: "title"
                          "frotend"
                          "backend";
     @media screen and (min-width:$cel){
    justify-items: center;
    }
    @media screen and (min-width:$tablet){
         justify-items: center;
            grid-template-columns: 50% 50%;
            grid-template-rows: auto 1fr;
            grid-template-areas: "title title"
                                "frotend backend"
    }
    @media screen and (min-width:$laptop){
       
    }
    @media screen and (min-width:$desk){
            
    }

  }
  .title{
    
    width: 90%;
    grid-area: title;

  }
  .frotend-container{
    width: 95%;
    grid-area:  frotend;
    &>img{
      width: 100%;
    }
  }
  .backend-container{
    width: 95%;
    grid-area: backend;
    &>img{
      width: 100%;
    }
  }
  img{
    max-height: 60vh
  }
  
</style>
