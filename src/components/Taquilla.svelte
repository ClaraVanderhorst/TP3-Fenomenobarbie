<script>
  import Scroller from "@sveltejs/svelte-scroller";

  export let goHome;

  let count, index, offset, progress;

  // Lista de imágenes para cada sección
  const images = [
      "/images/BarbieVsOp/guerra1.svg",
      "/images/BarbieVsOp/guerra2.svg",
      "/images/BarbieVsOp/guerra3.svg",
      "/images/BarbieVsOp/guerra4.svg",
  ];

  const bajadas = {
    1: "Barbie tomo la delantera en esta semana, todos de rosa en el cine.",
    2: "Oppenheimer no se dio por vencido y en esta semana logro derrotar a Barbie.",
    3: "Esta guerra no tiene final, la lucha ardua sigue y ninguno se da por vencido.",
    4: "Barbie logro remontar lo perdido en las semanas anteriores y lidero esta última  semana",
  };

  const recaudacion = {
    1: "536",
    2: "638",
    3: "406",
    4: "270",
  };
  
</script>

<main>
  <div class="text-container">
    <h1>Barb<span class="span-titulo">enheimer</span></h1>
    <p>El término "Barbenheimer", una fusión ingeniosa de "Barbie" y "Oppenheimer", encapsula perfectamente la dualidad de la experiencia cinematográfica ofrecida ese día. Por un lado, teníamos a "Barbie", una explosión de color, música y mensajes feministas que busca empoderar a su audiencia.Por el otro, "Oppenheimer" nos sumergía en la complejidad ética y científica que rodeó la creación de la bomba atómica, una historia contada con la intensidad y el dramatismo que el tema merece.</p>
    <img src="/images/estrella1.png" alt="estrella1" class="estrella1" width="40px" style="top:25%; left: 16%;">
    <img src="/images/estrella3.png" alt="estrella3" class="estrella3" width="40px" style="top:87%; right: 16%;">
  </div>

  <div class="button-container">
    <button on:click={() => goHome("home")}>
      <img src="/images/casacuartos/casataquilla.png" alt="Casa" class="casa-image">
  </button>
  </div>


<h2 class="intro">Las primeras semanas fueron definitoria para esta guerra</h2>

  <div class="scrollytelling">


    
      <div class="fixed-left">
          {#if index >= 0 && index < images.length}
              <img src={images[index]} alt={`Imagen ${index + 1}`} class="scroll-image" />
          {/if}
      </div>

      

      <Scroller bind:count={count} bind:index={index} bind:offset={offset} bind:progress={progress}>
          <div slot="foreground" class="content">
            
              {#each images as _, i}
                  <section class="step {i === index ? 'active' : ''}">
                      <h2 class="semana">Semana {i + 1}</h2>
                      <p class="total"><span class="span-total">Total:</span> {recaudacion[i+1]} millones</p>
                      <p class="bajada">{bajadas[i+1]}</p> 
                  </section>
              {/each}
          </div>
      </Scroller>
  </div>

  <div class="text-container2">
    <h3>Tercera Guerra Mundial</h3>
    <p>Se disputo una guerra entre Barbie y Oppenheimer. <br>¿Quién gano en cada país y cuantos millones recaudaron?</p>
  </div>

  <div class="mapa">
    <iframe src='https://flo.uri.sh/visualisation/20498099/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/visualisation/20498099/?utm_source=embed&utm_campaign=visualisation/20498099' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
  </div>
</main>

<style>

.fixed-left {
  position: sticky; 
  top: 220px; 
  left: 0;
  width: 60%; 
  height: 100vh; 
  background-color: #FFE3F5;
  overflow-y: auto; /* Permite scroll si hay demasiadas imágenes */
  padding: 20px;
  margin-top: 20px;
}

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

  .estrella3{
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


.span-titulo{
  color: black;
}

.scroll-image {
  max-width: 80%;
  height: auto;
  object-fit: contain;
}

.scrollytelling {
  display: flex;
  min-height: 100vh;
}

.content {
    font-family: "Helvetica";
    width: 100%;
    padding: 0 20px;
    color: #710A43;
    font-size: 1em;
  }

  .semana{
    font-weight: 900;
  }

  .span-total{font-weight: 900;}

  .bajada{font-weight: 100;}

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

.intro{
  font-family: "Helvetica";
    font-size: 1.3em;
    margin: 20px auto;
    max-width: 50%; /* Ajusta el ancho para pantallas pequeñas */
    color: #710A43;
    text-align: center;
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

.text-container2 {
    width: 100%;
    text-align: center;
    padding: 20px 0;
    background-color: #FFE3F5;
}
  
.text-container2 h3 {
    font-family: "Bartex";
    font-size: 7em;
    margin: 0;
    color: #ffffff;
    font-weight: 600;
    text-shadow: 3px 5px 0px #E81D8D;
}


  
.text-container2 p {
    font-family: "Helvetica";
    font-size: 1em;
    margin: 20px 200px;
    color: #710A43;
}

.intro{
  justify-content: center;
  align-items: center;
  display: flex;
}

main{background-color: #FFE3F5;}

</style>
