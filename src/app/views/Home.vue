<template>
  <div class="fondo">
    <div class="satelite" id=box><img  src="../../assets/satellite2.png" alt="" ></div>
    <div class="logo">
        <h1>Zadness</h1>
        <img class=imgr src="../../assets/atom2515.png" alt="" >
    </div>
    <h2 class="text">
        API RESTful de 
        grandes científicos de la historia por <strong>Jair Conislla</strong>
    </h2>
   
    <div class=btn-grid>
        <router-link to="/demo"> 
    <button class="btn waves-effect waves-light  light-blue darken-1" type="submit" name="action">demo
        <i class="material-icons right">send</i>
    </button>
   </router-link>
    </div>    
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'home',
  mounted: function () {
    let velMedio = 1.2,velLados=0.7
      var pos = 0; 
	//our box element
    var box = document.getElementById('box');
    var ida = true
	setInterval(()=>{
     
        if(ida){
            if(pos<=14){
                        pos +=velLados
                        box.style.left = pos + "px"
            }
                else if(pos >= 14 && pos <= 64){
                            pos += velMedio
                    box.style.left = pos+'px';
                }
                else if(pos >= 64 && pos <= 76){
                    pos += velLados
                    box.style.left = pos+'px';
                }
                else if(pos>=76){
                    
                    ida=false
                    
                }
                }else{
                if(pos >= 64){
                        pos -= velLados
                        box.style.left = pos + "px"
            }
                else if(pos >= 14 && pos <= 64){
                            pos -= velMedio
                    box.style.left = pos+'px';
                }
                else if(pos >= 0 && pos <= 14){
                    pos -=velLados
                    box.style.left = pos+'px';
                }
                else if(pos<=0){
                    
                    ida = true
                } 
		}}, 10);
  
  },
  components: {
    
  }
  
}
</script>
<style scoped lang="scss">
$cel: 540px;
$tablet: 814px;
$laptop:1025px;
$desk:1300px;
    .fondo{
        background-image: url('../../assets/fondo.jpg');
        background-repeat: no-repeat;
        background-size: cover;
        background-attachment: fixed;
        min-height: calc(85vh - 64px);
        display: grid;
        grid-template-columns: 1fr ;
        grid-template-rows: 1fr 2fr 2fr 1fr;
        grid-template-areas: " tittle"
                            "Satelite "
                            " Contendido"
                            " boton";
        @media screen and (min-width:$cel){
             grid-template-rows: 2fr auto 2fr 2fr;
        }
        @media screen and (min-width:$tablet){
            grid-template-columns: 1fr 1fr;
        grid-template-rows: 0.8fr 1fr 0.7fr;
           grid-template-areas: "Satelite tittle"
                                "Satelite Contendido"
                                "Satelite boton";
        }
        @media screen and (min-width:$laptop){
               
        }
        @media screen and (min-width:$desk){
               
        }
    }
    .satelite{
        margin-right: 26%;
        grid-area:Satelite;
        position: relative;
    justify-self: center;
    align-self: center;
     width: 78% ;
    &>img{
      width: 100% ;
      margin: auto
    }
     @media screen and (min-width:$cel){
   margin-right: 20%;
   }
     @media screen and (min-width:$tablet){
   margin-right: 17%;
   }
    @media screen and (min-width:$laptop){
    margin-right: 14%;
    }
     
    }
    .logo{
        grid-area:tittle;
        align-self: center;
        justify-self: center;
        display: flex;
        
        &>h1{
            font-family: 'Merriweather', serif;
    font-size:3rem;
    margin: 0;
            
        }
        &>img{
              height: 60px ;
              margin-left: 2rem;
              margin-top: -0.6rem;
             
        }
        @media screen and (min-width:$cel){
            &>h1{  font-size:4.5rem }
            &>img{
              height: 85px ;
              margin-left: 2rem;
              margin-top: -0.6rem;
        }
        }
        @media screen and (min-width:$tablet){
             justify-self: start;
             &>h1{  font-size:4.5rem }
            &>img{
              height: 90px ;
              margin-left: 2rem;
              margin-top: -0.6rem;
        }
           }
        @media screen and (min-width:$laptop){
               
          &>h1{  font-size:5rem }
        &>img{
              height: 95px ;
              margin-left: 2rem;
              margin-top: -0.6rem;
        } }
        @media screen and (min-width:$desk){
              &>h1{  font-size:5.5rem }
        &>img{
              height: 100px ;
              margin-left: 2rem;
              margin-top: -0.6rem;
        }
        }
    }
    .btn{
        width: 100%;
        
    }
    .btn-grid{
        width: 70%;
        grid-area:boton;
        justify-self: center;
        align-self: center;
        padding: 2vh 2vh 2vh 0;
         @media screen and (min-width:$cel){
           width: 50%;
        }
        @media screen and (min-width:$tablet){
             width: 40%;
            justify-self: start;
            align-self: center;
        }
    }
    .text{
        grid-area:Contendido;
        margin:0;
        padding: 1vh;
        font-size: 2.8rem;
        align-self: center;
        justify-self: center;
        font-family: 'Open Sans', sans-serif;
        width: 90%;
        @media screen and (min-width:$tablet){
             width: 80%;
            justify-self: start;
            padding: 0;
        }
         @media screen and (min-width:$laptop){
             width: 75%;
            justify-self: start;
            padding: 0;
        }
    }
    @keyframes rotate {from {transform: rotate(0deg);}
    to {transform: rotate(360deg);}}
@-webkit-keyframes rotate {from {-webkit-transform: rotate(0deg);}
  to {-webkit-transform: rotate(360deg);}}
.imgr{
    -webkit-animation: 4s rotate linear infinite;
    animation: 4s rotate linear infinite;
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
}
</style>