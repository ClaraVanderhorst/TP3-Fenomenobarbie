<script>
    // Función para inicializar el componente de Flourish y tomar el script que nos permite hacer el scrolly gratis!
    import { onMount } from 'svelte';

  

// Array para guardar la data de cada slide. Cambiar cada uno con el epígrafe específico para cada slide.
const slides = [
  "Muchas marcas colaboraron con Barbie para crear prendas icónicas basadas e la película",
  "Ventas Millonarias: Estas prendas generaron muchos ingresos, Los números no mienten, aca  se pueden ver las marcas que rompieron récords junto a Barbie.",
  "La cantidad de millones ganados no siempre se reflejan en la cantidad de unidades vendidas",
  "La Prenda Más Deseada: La prendas que desataron una locura, se agotaron en horas y  demostraron que el estilo Barbie es irresistible.",
  "El Match Perfecto: La marca que más ganancias tuvo y más unidades vendió fue crocs. Con millones de pares vendidos y ganancias récord, Crocs x Barbie demostró que comodidad y estilo pueden caminar juntos.",
]

function loadFlourishScrolly() {
  const script = document.createElement('script')
  script.src = "https://cdn.flourish.rocks/flourish-scrolly-v3.1.0.min.js"
  script.type = "text/javascript"
  script.onload = () => initFlourishScrolly()
  document.body.appendChild(script)
}


onMount(() => {
  loadFlourishScrolly()
});
export let goHome;
</script>

<main>

  <div class="text-container">
    <h1>Colecciones Iconicas</h1>
    <p>Barbie hizo muchas colaboraciones con distintas marcas que fueron muy exitosas. Cuando Barbie se une con las grandes marcas, el resultado es un fenómeno global.</p>
    <img src="/images/estrella1.png" alt="estrella1" class="estrella1" width="40px" style="top:25%; left: 16%;">
    <img src="/images/estrella2.png" alt="estrella2" class="estrella2" width="40px" style="top:87%; right: 16%;">
  
  </div>

<div class="button-container">
  <button on:click={() => goHome("home")}>
    <img src="/images/casacuartos/casamarcas.png" alt="Casa" class="casa-image">
</button>
</div>



<div class="texto_container">
  <h2 class="subtitulo">¡Descubrí las colecciones más exitosas de Barbie!</h2>
</div>

<!-- Contenedor de la story de flourish (scrolly)-->
<div id="my-wrapper">
  <!-- Reemplazar el ID de jeemplo por el de la story propia -->
  <div class="flourish-embed" data-src="story/2739152" data-url="https://flo.uri.sh/story/2739152/embed" data-height="70vh">
    
    <!-- <script src="https://public.flourish.studio/resources/embed.js"></script> -->
  </div>

  <!-- Iteramos sobre las distintas slides del componente de Flourish -->
  {#each slides as slide, index}
    <p>
      {@html slide}
      <!-- svelte-ignore a11y-missing-content -->
      <a href={"#story/2739152/slide-" + (index + 1)}></a>
    </p>
  {/each}
</div>



</main>

<style>

main{background-color: #FFE3F5;}

.estrella1{
    position: absolute;
    animation: twinkle 1s infinite alternate;
    top: calc(var(--i) * 5%);
    left: calc(var(--i) * 7%);
    opacity: 0.5;
  }

  @keyframes twinkle {
    0% {
      opacity: 0;
      transform: scale(0.4);
    }
    100% {
      opacity: 1;
      transform: scale(1.2);
    }
  }

  .estrella2{
    position: absolute;
    animation: twinkle 1s infinite alternate;
    top: calc(var(--i) * 5%);
    left: calc(var(--i) * 7%);
    opacity: 0.5;
  }

  @keyframes twinkle {
    0% {
      opacity: 0;
      transform: scale(0.6);
    }
    100% {
      opacity: 1;
      transform: scale(1.2);
    }
  }

.text-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-bottom: 10px;
    text-align: center;
    padding: 0 10px;
    position: relative;
    background-color: #FFE3F5;
  }

  .text-container h1 {
    padding-top: 20px;
    font-family: "Bartex";
    font-size: clamp(3rem, 8vw, 7em); /* Escala entre 3rem y 7em */
    margin: 0;
    color: #ffffff;
    font-weight: 600;
    text-shadow: 3px 5px 0px #E81D8D;
  }

  .text-container p {
    font-family: "Helvetica";
    font-size: 1em;
    margin: 20px auto;
    max-width: 50%; /* Ajusta el ancho para pantallas pequeñas */
    color: #710A43;
    text-align: center;
  }

  .button-container {
  background-color: #ffe3f5;
  width: 100%;
  position: sticky;
  top: 0;
  z-index: 10;
  display: flex; /* Flexbox para centrar contenido */
  justify-content: center; /* Centra horizontalmente */
  align-items: center; /* Centra verticalmente */
  height: 100px; /* Ajusta la altura del contenedor */
}

/* Botón */
button {
  cursor: pointer;
  background-color: transparent; /* Fondo transparente */
  border: none; /* Sin bordes */
  padding: 0; /* Sin padding para ajustar al tamaño de la imagen */
  display: flex; /* Flexbox para centrar la imagen dentro del botón */
  justify-content: center;
  align-items: center;
  width: 100px; /* Ancho del botón */
  height: 100px; /* Alto del botón */
}

/* Imagen de la casa */
.casa-image {
  max-width: 100%;
  max-height: 100%;
  width: auto; /* Mantiene proporciones */
  height: auto; /* Mantiene proporciones */
}



a {
  font-weight: 500;
  color: #646cff;
  text-decoration: inherit;
}
a:hover {
  color: #535bf2;
}


#my-wrapper {
  margin: auto;
  max-width: 1280px;
}


.subtitulo {
  font-size: 1.5em;
  text-align: center;
}
.texto_container {
  max-width: 700px;
  margin: auto;
  margin-bottom: 50px;
  text-align: left;
}



</style>