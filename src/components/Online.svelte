<script>
  import Scroller from "@sveltejs/svelte-scroller";

  export let goHome;

  
</script>

<main>
  <div class="text-container">
    <h1>Barbie online</h1>
    <p>La película tuvo un impacto muy grande en los medios. Todo lo relacionado a Barbie se volvía tendencia y eso se puedo ver en diferentes ámbitos. Explora la computadora de Barbie y entérate de todo lo que paso. </p>
    <img src="/images/estrella1.png" alt="estrella1" class="estrella1" width="40px" style="top:25%; left: 16%;">
    <img src="/images/estrella2.png" alt="estrella2" class="estrella2" width="40px" style="top:87%; right: 16%;">
  </div>

  <div class="button-container">
    <button on:click={() => goHome("home")}>
      <img src="/images/casacuartos/casaonline.png" alt="Casa" class="casa-image">
  </button>
  </div>


  <div class="scrollytelling">
    <img src="/images/online/barbieonline1.svg" alt="fotos" class="fotos">
    <img src="/images/online/barbieonline2.svg" alt="fotos" class="fotos">
    <img src="/images/online/barbieonline3.svg" alt="fotos" class="fotos">
  </div>



</main>

<style>

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

.scrollytelling {
  display: flex;
  max-height: 100%;
  flex-wrap: wrap;
  background-color: #FFE3F5;
  justify-content: center;
}

.fotos{
  margin-bottom: 20px;
  height: 600px;
  width: 80%;
  justify-content: center;
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
  height: 150px; /* Ajusta la altura del contenedor */
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

main{background-color: #FFE3F5;}






</style>


