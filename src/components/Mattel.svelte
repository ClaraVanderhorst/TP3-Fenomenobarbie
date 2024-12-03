<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import ventas from "/src/data/ventas_mattel.json";
  
  export let goHome;
  
  let count, index, offset, progress;

  // Objeto con las bajadas para cada año
  const bajadas = {
    2013: "El comienzo de la década: Barbie lidera, pero Hot Wheels pisa el acelerador.",
    2014: "Nuevas estrategias, mismas caras: Barbie y Hot Wheels mantienen su lucha.",
    2015: "¿Quién lleva la delantera? Las muñecas emergentes buscan su lugar.",
    2016: "Hot Wheels en la curva: su velocidad comienza a notarse en las ventas.",
    2017: "Barbie renueva su imagen: diversidad y modernidad le dan un impulso.",
    2018: "El ascenso de la muñeca nueva: sorpresas en el podio.",
    2019: "Hot Wheels acelera mientras Barbie redefine su estilo.",
    2020: "Pandemia y ventas: los juguetes reconquistan hogares.",
    2021: "Competencia feroz: la diversidad de productos redefine la batalla.",
    2022: "Reinvención y estrategia: Barbie apuesta a mantenerse en el juego.",
    2023: "El boom de la película: Barbie redefine el éxito, rompiendo récords y marcando tendencia."
  };

  // Función para generar un array según la cantidad
  function generateImages(item, key) {
    const cantidad = Math.floor(item[key] / 10); // Divide entre 10 y redondea hacia abajo
    return Array(cantidad).fill(`/images/${key}.png`); // Ruta a las imágenes
  }
</script>

<main>
  <div class="text-container">
    <h1>Mattel</h1>
    <p>Durante la última década, los tres juguetes más vendidos de Mattel compitieron ferozmente por ocupar el primer lugar. El podio fue cambiando con el paso de los años, pero eventos significativos, como el estreno de la película de Barbie, provocaron grandes transformaciones en las ventas.</p>
    <img src="/images/estrella1.png" alt="estrella1" class="estrella1" width="40px" style="top:25%; left: 16%;">
    <img src="/images/estrella2.png" alt="estrella2" class="estrella2" width="40px" style="top:87%; right: 16%;">
  </div>

  <div class="button-container">
    <button on:click={() => goHome("home")}>
      <img src="/images/casacuartos/casamattel.png" alt="Casa" class="casa-image">
    </button>
  </div>

  <div class="scrollytelling">
    <div class="fixed-left">
      <div class="images-container">
        {#if index >= 0}
          {#each generateImages(ventas[index], "barbies") as img}
            <img src="/images/ventasMattel/Juguete1.svg" alt="Barbie" class="toy-image" />
          {/each}
          {#each generateImages(ventas[index], "hot_wheels") as img}
            <img src="/images/ventasMattel/Juguete2.svg" alt="Hot Wheels" class="toy-image" />
          {/each}
          {#each generateImages(ventas[index], "fisher_price") as img}
            <img src="/images/ventasMattel/Juguete3.svg" alt="Fisher Price" class="toy-image" />
          {/each}
        {/if}
      </div>
    </div>
    
    <Scroller bind:count={count} bind:index={index} bind:offset={offset} bind:progress={progress}>
      <div slot="foreground" class="content">
        {#each ventas as item, i}
          <section class="step {i === index ? 'active' : ''}">
            <h2 class="año">{item.año}</h2>
            <p class="total"><span class="span-total">Total:</span> {item.total} millones de unidades</p>
            <p class="bajada">{bajadas[item.año]}</p> 
          </section>
        {/each}
      </div>
    </Scroller>
  </div>
</main>

<style>
  .fixed-left {
    position: sticky; 
    top: 170px; 
    left: 0;
    width: 60%; 
    height: 100vh; 
    background-color: #FFE3F5;
    overflow-y: auto;
    padding: 20px;
    margin-top: 20px;
  }

  .scrollytelling {
    display: flex;
    min-height: 100vh; 
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

  .casa-image {
    max-width: 100%;
    max-height: 100%;
    width: auto;
    height: auto;
  }

  .images-container {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .toy-image {
    width: 60px;
    height: 60px;
    object-fit: contain;
  }

  .content {
    font-family: "Helvetica";
    width: 100%;
    padding: 0 20px;
    color: #710A43;
    font-size: 1em;
  }

  .año{
    font-weight: 900;
  }

  .span-total{font-weight: 900;}

  .bajada{font-weight: 100;}


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

  .step {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    opacity: 0.3;
    transform: translateY(20px);
    transition: opacity 0.5s, transform 0.5s;
  }

  .step.active {
    opacity: 1;
    transform: translateY(0);
  }

  .step h2 {
    font-size: 2.5em;
    margin: 0;
  }

  .step p {
    font-size: 1.2em;
    margin: 10px 0;
  }

  main {
    background-color: #FFE3F5;
  }
</style>
