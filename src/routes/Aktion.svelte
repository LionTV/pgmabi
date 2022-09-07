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

        let innerWidth = 0
	    let innerHeight = 0
</script>
<svelte:window bind:innerWidth bind:innerHeight />
    <div id="main">
    
      <div id="content" class="text-center"> 

        <h1 class="m-8 text-white text-3xl">Abi Aktion 2023</h1>

        {#if innerWidth < 600}
            <img src="https://i.ibb.co/4d4W94W/abiaktion.jpg" alt="" class="m-auto h-96">
            <img src="https://i.ibb.co/XyYgNv9/294955511-416196253881110-3827850152430602030-n.jpg" alt="" class="m-auto h-96">
        {/if}

        {#if innerWidth > 600}
        <div class="inline-flex">
            <img src="https://i.ibb.co/4d4W94W/abiaktion.jpg" alt="" class="m-auto h-96">
            <img src="https://i.ibb.co/XyYgNv9/294955511-416196253881110-3827850152430602030-n.jpg" alt="" class="m-auto h-96">
        </div>
        {/if}

        <div class="m-4">
            <p>Das ist unser Abiaktionsteam 2023.
                Die Abiaktion 2023 spendet an den Kinderschutzbund im Ahrtal. Dieser hat zahlreiche Angebote für Kinder, beispielsweise Waldausflüge, Spielnachmittage, aber auch einige erlebnispädagogische Angebote. Auch die Eltern bekommen in Form von einigen Workshops (zum Beispiel Notfallpädagogik) und Elterntreffs Unterstützung von unserer Institution.
                Wir, das Abiaktionsteam, dürfen natürlich entscheiden für was unsere Spenden benutzt werden sollen. Wir haben uns dazu entschieden, dass ein Teil unseres Geldes in Sachspenden investiert werden soll und der andere Teil in die Organisation selbst, damit weiterhin Aktionen in so einer großen Menge statt finden können. Denn Kinder, sowie auch die Eltern sollen die Möglichkeit haben, kurz aus ihrem Alltag heraus zukommen und vorallem auch Dinge erleben, und neue Skills erlernen dürfen.<br> <br>
                
                Wir haben uns für diese Aktion entschieden, da der ,,Alltag" für die Familien nach der Flutkatastrophe im Sommer 2021 stehts herausfordernd bleibt.
                Kindergärten und Schulen werden auf lange Sicht nur in veränderter Form und oft nur an Ausweichstandorten geöffnet sein. Die traumatischen Ereignisse haben bei Groß und Klein eindeutige Spuren hinterlassen, teilweise auch in Form von schweren psychischen Belastungen. <br> <br>
                
                All diese Menschen sollen auch noch nach längerer Zeit unterstützt werden und auf keinen Fall vergessen werden, da immernoch jede Menge Hilfe täglich benötigt wird.
                
                Der Kinderschutzbund hilft nicht nur mit materialistischen Spenden, sondern kümmert sich vielmehr darum, dass Familien die vergangenen Erlebnisse verarbeiten können und dass vorallem Kinder in diesen harten Zeiten Wärme, Geborgenheit und Empathie erfahren.</p>
        </div>
    
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

    #main {
        display: flex;
        min-height: 100vh;
        flex-direction: column;
    }

    #content {
        flex: 1;
    }
</style>