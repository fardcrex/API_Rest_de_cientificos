<template>
    <div class="document">
        <div class=title>
            <h1>Consumiendo Api Zadness</h1>
            <p class=descripcion>URL: <a href="http://www.zadness.com/api">http://www.zadness.com/api/</a></p>
        </div>    
        <div class=Cientificos>
            <h2>Cientificos</h2>
            <h3>GET</h3>
            <p class=descripcion><span class=negrita><a href="http://www.zadness.com/api/cientificos">/cientificos</a></span> Obtiene la información de todos los cientificos</p>
            <p class=ok>HTTP 200 OK</p>
            <pre class="language-javascript"><code>
{
    "data": [
        {
            "_id": "5c8bd428efe4ce47d0acebcb",
            "name": "Christiaan Huygens",
            "country": {
                "_id": "5c89c984ecbd574e71f7f9e4",
                "name": "Netherlands"
            },
            "imagen": "/assets/5c840c6d0ca7a20b7c240b98.jpeg",
            "url": "https://es.wikipedia.org/wiki/Christiaan_Huygens",
            "descripcion": "Fue [...] a Royal Society.",
            "__v": 0,
            "AñoFallecimiento": 1695,
            "AñoNacimiento": 1629
        },
        [...],
        {
            "_id": "5c8bd428efe4ce47d0acebc0",
            "name": "Peter Debye",
            "country": {
                "_id": "5c89c984ecbd574e71f7fa37",
                "name": "United States"
            },
            "imagen": "/assets/5c8404970ca7a20b7c240b8d.jpg",
            "url": "https://es.wikipedia.org/wiki/Peter_Debye",
            "descripcion": "Petrus (Peter) Josephus [...] al 
            conocimiento de las estructuras
            moleculares.",
            "__v": 0,
            "AñoFallecimiento": 1695,
            "AñoNacimiento": 1629
        }
    ]
}
        </code></pre>        
        <p class=descripcion><span class=negrita><a href="http://www.zadness.com/api/cientifico/:id">/cientifico/:id</a></span> Obtiene la información de un cientifico</p>
        <p>
            <span class="llave">id:</span> Cientifico unique ID.
        </p>
        <p class=ok>HTTP 200 OK</p>
        <pre class="language-javascript"><code>
{
    "data": {
        "_id": "5c8d35bcefe4ce47d0acebd7",
        "name": "Christiaan Huygens",
        "country": {
            "_id": "5c89c984ecbd574e71f7f9e4",
            "name": "Netherlands"
        },
        "imagen": "/assets/5c840c6d0ca7a20b7c240b98.jpeg",
        "url": "https://es.wikipedia.org/wiki/Christiaan_Huygens",
        "descripcion": "Fue un astrónomo, [...] miembro de la Royal Society.",
        "__v": 0,
        "AñoFallecimiento": 1695,
        "AñoNacimiento": 1629
    }
}
        </code></pre>
        <p class=error>HTTP/ 400 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "No existen datos en el API con tus parámetros de búsqueda."
}</code></pre>
<p class=error>HTTP/ 500 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "Error interno del servidor. Cast to ObjectId failed for value
     \"[...]\" at path \"_id\" for model \"Cientifico\""
}
</code></pre>
<h3>POST</h3>
        
        <p class=descripcion><span class=negrita><a href="http://www.zadness.com/api/cientifico/:id">/cientifico</a></span> Crea un cientifico y se obtiene el cientifico creado.</p>
        
        <p>
            <span class="llave">id:</span> Cientifico unique ID.
        </p>
        <p class=descripcion>Cuerpo (body) de la petición POST</p>
        <p>
           <span class="llave">name:</span>  Nombre del cientifico. <span class=negrita>REQUIRE UNIQUE</span>          
        </p>
        <p>  <span class="llave">country:</span> ID del país de procedencia <a href="#countries">ver países </a> <span class=negrita>REQUIRE</span>  </p>
        <p> <span class="llave">imagen:</span> URL de la imagen del cientifico <span class=negrita>OPCIONAL</span>  </p>
        <p> <span class="llave">url:</span> URL de la wiki  
        <p><span class="llave">descripcion:</span>  Una descripcion sobre su vida  <span class=negrita>OPCIONAL</span>  </p>
        <p> <span class="llave">AñoFallecimiento:</span> Año de fallecimiento <span class=negrita>OPCIONAL</span>  </p>
        <p> <span class="llave">AñoNacimiento:</span> Año de nacimiento <span class=negrita>OPCIONAL</span>  </p>
        <p class=ok>HTTP 200 OK</p>
        <pre class="language-javascript"><code>
{
    "data": {        
        "name": "New Cientifico",
        "country": "5c89c984ecbd574e71f7f9e4",
        "imagen": "/assets/imagenDefault.jpg",
        "url": "https://es.wikipedia.org/wiki/New_Cientifico",
        "descripcion": "Nueva descripcion",
        "__v": 0,
        "AñoFallecimiento": 2000,
        "AñoNacimiento": 3000
    }
}
        </code></pre>
        <p class=error>HTTP/ 400 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "No existen datos en el API con tus parámetros de búsqueda."
}</code></pre>
<p class=error>HTTP/ 500 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "Error interno del servidor. "
}
</code></pre>


    <h3>PUT</h3>        
        <p class=descripcion><span class=negrita><a href="http://www.zadness.com/api/cientifico/:id">/cientifico/:id</a></span> Actualiza la información de un cientifico y se obtiene el actualizado.</p>
        <p>
            <span class="llave">id:</span> Cientifico unique ID.
        </p>
        <p class=descripcion>Cuerpo (body) de la petición PUT</p>
        <p>
           <span class="llave">name:</span>  Nombre del cientifico. <span class=negrita>REQUIRE UNIQUE</span>          
        </p>
        <p>  <span class="llave">country:</span> ID del país de procedencia <a href="#countries">ver países </a> <span class=negrita>REQUIRE</span>  </p>
        <p> <span class="llave">imagen:</span> URL de la imagen del cientifico <span class=negrita>OPCIONAL</span>  </p>
        <p> <span class="llave">url:</span> URL de la wiki  
        <p><span class="llave">descripcion:</span>  Una descripcion sobre su vida  <span class=negrita>OPCIONAL</span>  </p>
        <p> <span class="llave">AñoFallecimiento:</span> Año de fallecimiento <span class=negrita>OPCIONAL</span>  </p>
        <p> <span class="llave">AñoNacimiento:</span> Año de nacimiento <span class=negrita>OPCIONAL</span>  </p>
        <p class=ok>HTTP 200 OK</p>
        <pre class="language-javascript"><code>
{
    "data": {        
       "name": "Name Actualizado",
        "country": "5c89c984ecbd574e71f7f9e4",
        "imagen": "/assets/imagenDefault.jpg",
        "url": "https://es.wikipedia.org/wiki/New_Cientifico",
        "descripcion": "Nueva descripcion Actualizada",
        "__v": 0,
        "AñoFallecimiento": 2000,
        "AñoNacimiento": 3000
    }
}
        </code></pre>
        <p class=error>HTTP/ 400 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "No existen datos en el API con tus parámetros de búsqueda."
}</code></pre>
        <p class=error>HTTP/ 500 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "Error interno del servidor. Cast to ObjectId failed for value
     \"[...]\" at path \"_id\" for model \"Cientifico\""
}
        </code></pre>

        <h3>DELETE</h3>
                
        <p class=descripcion><span class=negrita><a href="http://www.zadness.com/api/cientifico/:id">/cientifico/:id</a></span> Elimina a un cientifico y se obtiene el borrado.</p>
        <p>
             <span class="llave">id:</span> Cientifico unique ID.
        </p>
        
        <p class=ok>HTTP 200 OK</p>
        <pre class="language-javascript"><code>
{
    "data": {        
       "name": "Name DEL CIENTIFICO ELIMINADO",
        "country": "5c89c984ecbd574e71f7f9e4",
        "imagen": "/assets/imagenDefault.jpg",
        "url": "https://es.wikipedia.org/wiki/Cientifico_OLD",
        "descripcion": "descripcion DEL CIENTIFICO ELIMINADO",
        "__v": 0,
        "AñoFallecimiento": 2000,
        "AñoNacimiento": 3000
    }
}
        </code></pre>
        <p class=error>HTTP/ 400 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "No existen datos en el API con tus parámetros de búsqueda."
}</code></pre>
<p class=error>HTTP/ 500 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "Error interno del servidor.[...]"
}
</code></pre>

</div>  
        <div class=Countries>
            <h2 id="countries">Countries</h2>
            <h3>GET</h3>
            <p class=descripcion><span class=negrita><a href="http://www.zadness.com/api/countries">/countries</a></span> Obtiene la información de todos los países</p>
            <p class=ok>HTTP 200 OK</p>
            <pre class="language-javascript"><code>
{
    "data": [
        {
            "_id": "5c89c984ecbd574e71f7f94a",
            "code": "AF",
            "name": "Afghanistan",
            "__v": 0
        },
        [...],
        {
            "_id": "5c89c984ecbd574e71f7fa43",
            "code": "AX",
            "name": "Åland",
            "__v": 0
        }
    ]
}
            </code></pre>   
            <p class=error>HTTP/ 500 Bad Response</p>
        <pre  class="language-javascript"><code>{
    "message": "Error interno del servidor.[...]"
}
</code></pre>
        </div>        
    </div>
</template>

<script>



export default {
    
}
</script>

<style lang="scss" scoped>
$cel: 540px;
$tablet: 814px;
$laptop:1025px;
$desk:1300px;

.document {
    
    margin: auto;
    margin-bottom: 15vh;
    min-height: 80vh;
    display: grid;
    width: 98%;
    justify-items: center;
    max-width: 1300px;
    grid-template-columns: 100%;
    grid-template-areas:    "title "
                            "Cientificos"
                            " Countries";

    @media screen and (min-width:$cel){
    justify-items: center;
    }
    @media screen and (min-width:$tablet){
        justify-items: center;
    }
    @media screen and (min-width:$laptop){
        justify-items: center;
            grid-template-columns: 50% 50%;
            
            grid-template-areas: "title title"
                                "Cientificos Countries"
    }
    @media screen and (min-width:$desk){
            
    }
    
  }
  .title{
        width: 100%;
        grid-area: title
    }
    .Cientificos{
         width: 97%;
        grid-area: Cientificos
    }
    .Countries{
         width: 97%;
        grid-area: Countries
    }
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
    }
    .llave{
         font-size: 1.1rem;
         color:#204e93;
          font-weight: bold;
    }
    .negrita{
        font-weight: bold;
    }
    .ok{
        font-size: 1.1rem;
        font-weight: bold;
        color: #43A047
    }
    .error{
        font-size: 1.1rem;
        font-weight: bold;
        color: #E53935
    }
    .descripcion{
        font-size: 1.2rem;
    }
 /* PrismJS 1.15.0
https://prismjs.com/download.html#themes=prism-okaidia&languages=clike+javascript+json */
/**
 * okaidia theme for JavaScript, CSS and HTML
 * Loosely based on Monokai textmate theme by http://www.monokai.nl/
 * @author ocodia
 */
code[class*="language-"],
pre[class*="language-"] {
	color: #ccc;
	background: none;
	font-family: Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace;
	font-size: 1em;
	text-align: left;
	white-space: pre;
	word-spacing: normal;
	word-break: normal;
	word-wrap: normal;
	line-height: 1.5;

	-moz-tab-size: 4;
	-o-tab-size: 4;
	tab-size: 4;

	-webkit-hyphens: none;
	-moz-hyphens: none;
	-ms-hyphens: none;
	hyphens: none;

}

/* Code blocks */
pre[class*="language-"] {
	padding: 1em;
	margin: .5em 0;
	overflow: auto;
}

:not(pre) > code[class*="language-"],
pre[class*="language-"] {
	background: #2d2d2d;
}

/* Inline code */
:not(pre) > code[class*="language-"] {
	padding: .1em;
	border-radius: .3em;
	white-space: normal;
}

.token.comment,
.token.block-comment,
.token.prolog,
.token.doctype,
.token.cdata {
	color: #999;
}

.token.punctuation {
	color: #ccc;
}

.token.tag,
.token.attr-name,
.token.namespace,
.token.deleted {
	color: #e2777a;
}

.token.function-name {
	color: #6196cc;
}

.token.boolean,
.token.number,
.token.function {
	color: #f08d49;
}

.token.property,
.token.class-name,
.token.constant,
.token.symbol {
	color: #f8c555;
}

.token.selector,
.token.important,
.token.atrule,
.token.keyword,
.token.builtin {
	color: #cc99cd;
}

.token.string,
.token.char,
.token.attr-value,
.token.regex,
.token.variable {
	color: #7ec699;
}

.token.operator,
.token.entity,
.token.url {
	color: #67cdcc;
}

.token.important,
.token.bold {
	font-weight: bold;
}
.token.italic {
	font-style: italic;
}

.token.entity {
	cursor: help;
}

.token.inserted {
	color: green;
}


</style>
