<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import * as d3 from "d3";
  import ScrollyVideo from "scrolly-video/dist/ScrollyVideo.svelte";

  /* Componentes */
  import Taquilla from "./components/Taquilla.svelte";
  import Marcas from "./components/Marcas.svelte";
  import Online from "./components/Online.svelte";
  import Presupuesto from "./components/Presupuesto.svelte";
  import Mattel from "./components/Mattel.svelte";

  let currentPage = "home";

 
</script>

<main>
  {#if currentPage === "home"}
  <div class="header" id="top">
    <h1 class="titulo">El Fenomeno Barbie</h1>
    <p class="bajada">La película Barbie fue un fenómeno global, superó los mil millones de dólares en taquilla y revitalizó la franquicia, impactando moda y redes sociales. 
    ¡Entrá a la casa de Barbie y descubrí más!</p>
    <img src="/images/estrella1.png" alt="estrella1" class="estrella1" width="40px" style="top:25%; left: 16%;">
    <img src="/images/estrella2.png" alt="estrella2" class="estrella2" width="40px" style="top:7%; right: 16%;">
  </div>

  <div class="imagen-con-botones">
    <img class="casa" src="/images/svgs/casa.svg" width="600" alt="Casa" />
    <button class="boton" style="top: 49%; left: 55%;" on:click={() => (currentPage = "Marcas")}>Marcas</button>
    <button class="boton" style="top: 75%; left: 62%;" on:click={() => (currentPage = "Mattel")}>Mattel</button>
    <button class="boton" style="top: 49%; left: 45%;" on:click={() => (currentPage = "Presupuesto")}>Presupuesto</button> 
    <button class="boton" style="top: 75%; left: 42%;" on:click={() => (currentPage = "Online")}>Online</button>
    <button class="boton" style="top: 25%; left: 50%;" on:click={() => (currentPage = "Taquilla")}>Taquilla</button>
  </div>
<!-- Parte final del condicional --> 

  {:else if currentPage === "Mattel"}
    <Mattel goHome={(home) => (currentPage = home)} />
  {:else if currentPage === "Online"}
    <Online goHome={(home) => (currentPage = home)} />
  {:else if currentPage === "Taquilla"}
    <Taquilla goHome={(home) => (currentPage = home)} />
  {/if}
  <!-- Termina el condicional sin <Presupuesto> y <Marcas> -->
  
  <!-- Sacamos la lógica para Presupuesto y Marcas (hack) -->
  <div style="display: {currentPage === 'Presupuesto' ? 'block' : 'none'};">
    <Presupuesto goHome={(home) => (currentPage = home)} />
  </div>

  <div style="display: {currentPage === 'Marcas' ? 'block' : 'none'};">
    <Marcas goHome={(home) => (currentPage = home)} />
  </div>
</main>



<style>
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-bottom: 10px;
    text-align: center;
    padding: 0 10px;
    position: relative;
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

  .titulo {
    padding-top: 20px;
    font-family: "Bartex";
    font-size: clamp(3rem, 8vw, 7em); /* Escala entre 3rem y 7em */
    margin: 0;
    color: #ffffff;
    font-weight: 600;
    text-shadow: 3px 5px 0px #E81D8D;
  }

  .bajada {
    font-family: "Helvetica";
    font-size: 1em;
    margin: 20px auto;
    max-width: 50%; /* Ajusta el ancho para pantallas pequeñas */
    color: #710A43;
    text-align: center;
  }

  .imagen-con-botones {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding-bottom: 35px;
   
  }

  .casa {
    height: auto;
    max-width: 90%; 
    object-fit: contain;
  }

  .boton {
    position: absolute;
    padding: 10px 20px;
    background-color: #E81D8D;
    border: none;
    border-radius: 20px;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    transform: translate(-50%, -50%);
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3);
    transition: box-shadow 0.3s ease, transform 0.3s ease;
  }

  .boton:hover {
    background-color: #710A43;
    box-shadow: 0px 6px 10px rgba(0, 0, 0, 0.4);
    transform: translate(-50%, -50%) scale(1.05);
  }

  main {
    background-image: url("/public/images/fondo_casa.png");
    background-size: cover;
    background-position: center bottom;
    background-repeat: no-repeat;
    width: 100vw;
    height: 100vh;
    background-color: #FFE3F5;
  }

  /* Media Query para pantallas pequeñas */
  @media (max-width: 768px) {
    .titulo {
      font-size: 4rem; /* Ajusta el tamaño del título */
    }

    .bajada {
      font-size: 0.9em; /* Texto más pequeño */
    }

    .boton {
      font-size: 0.9rem; /* Botones más pequeños */
      padding: 8px 15px;
    }
  }

</style>
