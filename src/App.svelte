<script>
	import Tooltip from './Tooltip.svelte';
	import Header from './Header.svelte';
	import ButtonClass from './ButtonClass.svelte';
	import Slots from './Slots.svelte';
	import SlotProps from './SlotProps.svelte';
	import Modal from './Modal.svelte';
	import Footer from './Footer.svelte';

	let showModal = false;
</script>

<!-- ================================================= -->
<style>
	.container {
		font-size: 1.25rem;
		width: 60%;
		margin: 1em auto;
		padding: 1em;
	}

	@media screen and (max-width: 900px) {
		.container {
			width: 80%;
		}
	}

	@media screen and (max-width: 768px) {
		.container {
			width: 90%;
		}
	}

	/* style for SlotProps */
	section {
		padding: .25em 1em;
		margin: 0 0 1em 0;
		background-color: cornflowerblue;
		color: #333;
	}

	.active {
		background-color: #ff3e00;
		color: white;
	}

</style>

<!-- ================================================= -->

<Header />

<div class="container">

	<h3>Button Tooltips on Hover</h3>

	<Tooltip/>

	<hr>
	
	<h3>Active Class on Button</h3>

	<ButtonClass/>

	<hr>

	<h3>Slots</h3>

	<Slots>
		<h3>Hello!</h3>
		<p>This is a Slot. It can contain anything.</p>
		<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum, odio natus!</p>
		<p>React is not reactive!</p>
	</Slots>

	<Slots/>

	<hr>

	<h3>Slots with Hover Properties</h3>

	<SlotProps let:hovering={active}>
		<section class:active>
			{#if active}
				<p>I am being hovered upon.</p>
			{:else}
				<p>Hover over me!</p>
			{/if}
		</section>
	</SlotProps>

	<SlotProps let:hovering={active}>
		<section class:active>
			{#if active}
				<p>React is a terrible name for React.js</p>
			{:else}
				<p>React is...</p>
			{/if}
		</section>
	</SlotProps>

	<SlotProps let:hovering={active}>
		<section class:active>
			{#if active}
				<p>React is not reactive!</p>
			{:else}
				<p>React is not...</p>
			{/if}
		</section>
	</SlotProps>

	<hr>

	<h3>Modal</h3>

	<button on:click="{() => showModal = true}">
		show modal
	</button>

	{#if showModal}
		<Modal on:close="{() => showModal = false}">
			<h2 slot="header">Svelte</h2>

			<h5>Modern JavaScript frameworks are all about reactivity. Change your application's state, and the view updates automatically. But there's a catch — tracking state changes at runtime adds overhead that eats into your bundle size and performance budgets. In this talk, we'll discover an alternative approach: moving reactivity into the language itself. Your apps have never been smaller or faster than they're about to become.</h5>

			<h6>This is the way to the future of web programming. Thank you Rich Harris!<br>
			I've watched this talk probably about 5 times now. Amazing work.<br>
			Damn, JavaScript is finally production ready.</h6>
		</Modal>
	{/if}

</div>

<Footer/>