<script>
  import "../app.css";
  import Hamburger  from 'svelte-hamburger';
  import Menu from '../components/Menu.svelte';
  
  let open = false;
</script>

<div id="navbar" class="bg-slate-700">
  <a href="/Home">
      <img alt="" class="w-14 absolute m-2" src="https://www.gymnasium-marienstatt.de/typo3conf/ext/dg_bootstrap/Resources/Public/Theme/images/logo.png">
  </a>
  <Hamburger --line-width="3px" {open} on:click={() => open = !open} class="float-right m-6"/>
</div>
<Menu bind:open />

<slot />