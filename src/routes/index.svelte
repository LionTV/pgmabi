<script>
import { browser } from "$app/env";

  import Footer from "../components/Footer.svelte";
  import Modal from "../components/Modal.svelte";

  let showModal = false;
  let darkmode = true;

  function toggle() {
      window.document.body.classList.toggle('light-mode')
      darkmode = !darkmode;
      let st = window.localStorage;
      st.setItem("darkmode", darkmode.toString());
  }

  let storage;
  if (browser) {
    storage = window.localStorage;
    //darkmode
    if (storage.getItem("darkmode") === null) {
      storage.setItem("darkmode", "true");
    }else if (storage.getItem("darkmode") === "true") {
      darkmode = true;
    } else {
      darkmode = false;
      window.document.body.classList.toggle('light-mode')
    }
  }
</script>

<div id="main">

  <div id="content"> 

  </div>

  <Footer />
</div>

{#if showModal}
  <Modal on:close="{() => showModal = false}">
    <h1 slot="header" class="text-white font-bold text-xl">Settings</h1>
    <div class="flex justify-between">
      <p class="text-white font-semibold mt-2">Darkmode</p>
      <div class="mt-2 mb-4">
        <label for="toggleB" class="flex items-center cursor-pointer">
          <div class="relative">
            {#if darkmode === true}
              <input checked on:click="{() => toggle()}" type="checkbox" id="toggleB" class="sr-only">
                <div class="block bg-slate-500 w-14 h-8 rounded-full"></div>
              <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
            {:else}
              <input on:click="{() => toggle()}" type="checkbox" id="toggleB" class="sr-only">
                <div class="block bg-slate-500 w-14 h-8 rounded-full"></div>
              <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
            {/if}
            </div>
        </label>
      </div>
    </div>
  </Modal>
{/if}

<style>
  :global(body.light-mode) {
        background-color: #ffffff;
        color: white;
        transition: background-color 0.3s;
  }
  :global(body) {
      background-color: rgb(15, 23, 42);
      color: white;
  }
  input:checked ~ .dot {
    transform: translateX(100%);
    background-color: rgb(49, 46, 129);
  }
  input {
    outline: none;
  }

  #main {
    display: flex;
    min-height: 100vh;
    flex-direction: column;
  }

  #content {
    flex: 1;
  }
</style>