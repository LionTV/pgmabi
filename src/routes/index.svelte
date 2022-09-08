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