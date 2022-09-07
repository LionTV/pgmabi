<script>
    import { browser } from "$app/env";
    import { fade } from 'svelte/transition';
    
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
    
    
      import Hamburger  from 'svelte-hamburger';
      import Menu from '../components/Menu.svelte';
    
      let open = false;
    </script>
    
    <div id="main">
    
      <div id="content"> 

        <h1 class="m-8">Home Page</h1>
    
      </div>
    
      <Footer />
    </div>

    <style>
      #main {
        display: flex;
        min-height: 100vh;
        flex-direction: column;
      }
    
      #content {
        flex: 1;
      }
</style>