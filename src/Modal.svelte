<script>
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
</script>

<style>
	.modal-background {
		position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
		background: rgba(0,0,0,0.6);
	}

	.modal {
		position: relative;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
		width: 480px;
        max-width: 95%;
		overflow: auto;
        padding: 1em;
        border: 1px solid #eee;
        border-radius: 0.2em;
        box-shadow: 0 0 50px #fff;
        background: #333;
        color: #eee;
	}

	button {
		display: block;
	}
</style>

<div class='modal-background' on:click='{() => dispatch("close")}'>
    <div class='modal'>
        <slot name='header'></slot>
        <hr>
        <slot></slot>
        <hr>

        <button on:click='{() => dispatch("close")}'>close modal</button>
    </div>
</div>
