<template>

  <div class="about">
    <div class=title>
      <h1>Acerca del Proyecto</h1>

      <h2 class="header">Sobre el desarrollador</h2>
      <div
        v-show="cardAvatar"
        class="row"
      >
        <div class="col s12">
          <div class="card">
            <div class="card-image">
              <img
                class="img"
                src="../../assets/jair.jpg"
              >
              <span class="card-title">Jair Conislla</span>
            </div>
            <div class="card-content">
              <span class="desc">Estudiante de Ingeniería de Software de la Universidad Tecnológica del Perú y de la carrera de Física en la Universidad Nacional Mayor de San Marcos. Con experiencia básica en el de desarrollo de servicios web (APIs RESTful). Me considero una persona autodidacta con habilidades de comunicación, analítico al momento de diseñar modelos y/o resolver problemas y con excelentes habilidades interpersonales.</span>
            </div>
            <div class="card-action">
              <a
                target="_black"
                href="https://github.com/fardcrex"
              >gitgub </a>
              <a
                target="_black"
                href="https://www.linkedin.com/in/jair-pool-conislla-bocangel-a6931579/"
              >Linkedin</a>
            </div>
          </div>
        </div>
      </div>
      <div
        v-show="!cardAvatar"
        class="col s12 m7"
      >
        <div class="card horizontal">
          <div class="card-image">
            <img
              loading="lazy"
              class=foto2
              src="../../assets/jair.jpg"
            >
          </div>
          <div class="card-stacked">
            <div class="card-content">
              <h2>Jair Conislla</h2>
              <p>jair.conislla@ibernel.com</p>
              <span class="desc">Estudiante de Ingeniería de Software de la Universidad Tecnológica del Perú y de la carrera de Física en la Universidad Nacional Mayor de San Marcos. Con experiencia básica en el de desarrollo de servicios web (APIs RESTful). Me considero una persona autodidacta con habilidades de comunicación, analítico al momento de diseñar modelos y/o resolver problemas y con excelentes habilidades interpersonales.</span>
            </div>
            <div class="card-action">
              <a
                target="_black"
                href="https://github.com/fardcrex"
              >gitgub</a>
              <a
                target="_black"
                href="https://www.linkedin.com/in/jair-pool-conislla-bocangel-a6931579/"
              >Linkedin</a>
            </div>

          </div>
        </div>
      </div>
    </div>
    <div class="frotend-container">
      <h2>Tecnologias Frontend</h2>
      <img
        loading="lazy"
        class=img
        width="650"
        src="../../assets/frontend.jpg"
        alt="Escritorio"
      >
      <ul class="collection">
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/logo.png"
            alt=""
            class="circle"
          >
          <span class="title">Framework Javascript</span>
          <p>Vue<br>
            2.6.6
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/materialize.png"
            alt=""
            class="circle"
          >
          <span class="title">Framework Web</span>
          <p>Materialize CSS <br>
            1.0.0
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/prismjs.png"
            alt=""
            class="circle"
          >
          <span class="title">Syntax Highlighter</span>
          <p>Prism.js <br>
            1.15.0
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/github.png"
            alt=""
            class="circle"
          >
          <span class="title">Servidor Web</span>
          <p>GitHub Pages <br>
            actions
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
      </ul>

    </div>
    <div class="backend-container">
      <h2>Tecnologias Backend</h2>
      <img
        loading="lazy"
        class=img
        src="../../assets/backend.jpg"
        alt="Escritorio"
      >
      <ul class="collection">
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/node.png"
            alt=""
            class="circle"
          >
          <span class="title">Servidor Web</span>
          <p>Node.js <br>
            8.10.0
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/express.png"
            alt=""
            class="circle"
          >
          <span class="title">Framework Backend</span>
          <p>Express<br>
            4.16.3
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/mongo.png"
            alt=""
            class="circle"
          >
          <span class="title">Base de Datos</span>
          <p>Mongo DB <br>
            3.6.3
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
        <li class="collection-item avatar">
          <img
            loading="lazy"
            src="../../assets/mongoose.jpg"
            alt=""
            class="circle"
          >
          <span class="title">Object Modeling</span>
          <p>Mongoose<br>
            5.2.6
          </p>
          <a
            href="#!"
            class="secondary-content"
          ><i class="material-icons">grade</i></a>
        </li>
      </ul>

    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      cardAvatar: true
    };
  },
  created() {
    const mediumBp = window.matchMedia("(max-width: 814px)");
    //console.log(mediumBp)
    if (mediumBp.matches) {
      this.cardAvatar = true;
    } else {
      this.cardAvatar = false;
    }
  }
};
</script>
<style lang="scss" >
$cel: 540px;
$tablet: 814px;
$laptop: 1025px;
$desk: 1300px;
h1 {
  font-size: 3rem;
  font-family: Merriweather;
  text-align: center;
  @media screen and (min-width: $tablet) {
    font-size: 3.5rem;
    font-weight: bold;
  }
}
h2 {
  margin: 0 0 1rem 0;
  font-size: 2.8rem;
  font-family: Merriweather;
}
h3 {
  font-size: 2.5rem;
  font-style: italic;
  font-family: Merriweather;
}
p {
  font-family: "Open Sans", sans-serif;
  font-size: 1rem;
}
.desc {
  font-size: 1.2rem;
  @media screen and (min-width: $cel) {
    font-size: 1.4rem;
  }
  @media screen and (min-width: $tablet) {
    font-size: 1.4rem;
  }
  @media screen and (min-width: $laptop) {
    font-size: 1.7rem;
  }
  @media screen and (min-width: $desk) {
    font-size: 1.9rem;
  }
}
.about {
  margin: auto;
  min-height: 90vh;
  display: grid;
  width: 100%;
  justify-items: center;
  max-width: 1300px;
  grid-template-columns: 100%;
  grid-row-gap: 5vh;
  grid-template-areas:
    "title"
    "frotend"
    "backend";
  @media screen and (min-width: $cel) {
    width: 98%;
    justify-items: center;
  }
  @media screen and (min-width: $tablet) {
    justify-items: center;
    grid-template-columns: 50% 50%;
    grid-template-rows: auto 1fr;
    grid-template-areas:
      "title title"
      "frotend backend";
  }
  @media screen and (min-width: $laptop) {
  }
  @media screen and (min-width: $desk) {
  }
}
.title {
  width: 90%;
  grid-area: title;
}
.frotend-container {
  width: 95%;
  grid-area: frotend;
  & > img {
    width: 100%;
  }
}
.backend-container {
  width: 95%;
  grid-area: backend;
  & > img {
    width: 100%;
  }
}
img {
  max-height: 60vh;
}
</style>
