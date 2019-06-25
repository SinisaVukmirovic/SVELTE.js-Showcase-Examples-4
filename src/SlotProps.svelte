<script>
	let hovering;

	function enter() {
		hovering = true;
	}

	function leave() {
		hovering = false;
	}
</script>

<section on:mouseenter={enter} on:mouseleave={leave}>
	<slot hovering={hovering}></slot>
</section>