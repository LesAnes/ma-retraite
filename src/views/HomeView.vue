<script setup lang="ts">
import { ref } from 'vue';

const modal = ref<string | null>(null);
const handleClick = (param: string | null): void => {
  modal.value = param;
}
</script>

<template>
  <main>
    <div class="left">
      <h1>
        <span>TOUCHE</span>
        <span>PAS À MA</span>
        <span class="bold">RETRAITE !</span>
      </h1>
      
      <p>Ce simulateur est vraiment très objectif et s'appuie sur <span class="bold">une bonne foi exemplaire</span>. Il permet de donner un fabuleux exemple d'une <span class="bold">démocratie fonctionnelle</span> et pas du tout incline à tomber dans le fascisme <span class="bold">dans 7 jours.</span></p>
      <p><span class="bold">Il permet ainsi d'élever le débat et de ne pas du tout induire en erreur des potentiels électeurs soucieux de voir leur retraite baisser.</span></p>
    </div>

    <div class="right">
      <h3><span class="bold">Dimanche, vous allez plutôt voter pour...</span></h3>
      <div class="actions">
        <button @click="handleClick('re')">Renaissance</button>
        <button class="ok" @click="handleClick('nfp')">Nouveau Front Populaire</button>
        <button @click="handleClick('rn')">Rassemblement national</button>
      </div>
    </div>

    <div v-if="modal" class="overlay" @click="handleClick(null)"></div>
    <div v-if="modal" class="modal">
      <div v-if="modal === 'nfp'">
        <span class="res ok">
          <span class="bold">Bravo ! 🎉</span>
        </span>
      </div>
      <div v-else>
        <span class="res">
          <span class="bold">Gros loser ! 💩 </span>
        </span>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    display: grid;
    grid-template-columns: repeat(1, 2fr);
  }

  h1 {
    display: flex;
    flex-direction: column;
    line-height: 1.1em;
    padding-bottom: 0.5rem;
    font-size: 3.5rem;
    color: white;
  }

  h3 {
    font-size: 1.5rem;
    color: white;
  }

  p {
    color: white;
    font-size: 1rem;
    margin-bottom: 1rem;
  }

  .bold {
    font-weight: 900;
  }

  .right,
  .left {
    height: 100%;
    padding: 1rem 2rem;
    display: flex;
    flex-direction: column;
  }

  .actions {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 1rem 2rem;
  }

  button {
    background: rgba(255, 255, 255, 0.8);
    color: #EE2C17;
    text-align: center;
    font-weight: 600;
    border: none;
    padding: 1rem;
    text-transform: uppercase;
    font-size: 1.25rem;
    border-radius: 8px;
    font-weight: 900;
    cursor: pointer;
    margin-bottom: 1rem;
  }

  button.ok {
    color: #74E291
  }

  button:hover {
    opacity: 0.8;
  }

  .modal {
    display: flex;
    justify-content: center;
    position: fixed;
    background-color: white;
    width: 90%;
    height: 500px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 8px;
    padding: 2rem;
    z-index: 2;
  }

  .overlay {
    position: fixed;
    height: 100%;
    width: 100%;
    top: 0;
    left: 0;
    z-index: 1;
    opacity: 0.8;
    background-color: darkgrey;
    cursor: pointer;
  }

  .res {
    font-size: 2rem;
    color: #EE2C17;
  }

  .res.ok {
    color: #74E291
  }

  @media (min-width: 1024px) {
    main {
      grid-template-columns: repeat(2, 2fr);
    }

    .modal {
      width: 500px;
      height: 500px;
    }
  }
</style>
