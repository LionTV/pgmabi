<script>
	import { createEventDispatcher, onDestroy } from 'svelte';

	let comp;
	const dispatch = createEventDispatcher();
	export const close = () => {
		//save data from modal
		dispatch('close');
	};

	// @ts-ignore
	let modal;

	// @ts-ignore
	const handle_keydown = e => {
		if (e.key === 'Escape') {
			close();
			return;
		}

		if (e.key === 'Tab') {
			// trap focus
			// @ts-ignore
			const nodes = modal.querySelectorAll('*');
			const tabbable = Array.from(nodes).filter(n => n.tabIndex >= 0);

			let index = tabbable.indexOf(document.activeElement);
			if (index === -1 && e.shiftKey) index = 0;

			index += tabbable.length + (e.shiftKey ? -1 : 1);
			index %= tabbable.length;

			tabbable[index].focus();
			e.preventDefault();
		}
	};
</script>

<svelte:window on:keydown={handle_keydown}/>

<div class="modal-background" on:click={close}></div>

<div class="modal rounded" role="dialog" aria-modal="true" bind:this={modal}>
	<slot name="header"></slot>
	<hr>
	<slot></slot>
	<hr>
	<slot name="footer"></slot>
	<!-- svelte-ignore a11y-autofocus -->
	<button class="text-white bg-gray-500 mt-2 rounded" autofocus on:click={close} id="closebutton">Schließen</button>
</div>

<style>
	.modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,0.3);
	}

	.modal {
		position: absolute;
		left: 50%;
		top: 50%;
		width: calc(100vw - 4em);
		max-width: 32em;
		max-height: calc(100vh - 4em);
		overflow: auto;
		transform: translate(-50%,-50%);
		padding: 1em;
		border-radius: 0.2em;
		background: rgb(30, 41, 59);
	}

	#closebutton {
		display: block;
		outline: none;
		padding: 4px;
	}
</style>