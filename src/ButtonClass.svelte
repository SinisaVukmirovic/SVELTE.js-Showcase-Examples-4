<script>
	const frames = [
		{ frame: 'Svelte' },
		{ frame: 'React' },
		{ frame: 'Vue' },
		{ frame: 'Angular' }
	];
	
	let current = frames[0];
</script>

<style>
    .btns-container {
        display: flex;
        justify-content: space-between;
    }

	button {
        width: 8rem;
	}

	.active {
		background-color: #ff3e00;
		color: white;
    }

	@media screen and (max-width: 768px) {
        .btns-container {
            justify-content: center;
        }
        button {
            width: 7rem;
        }
	}
</style>

<div class="btns-container">
    {#each frames as frame}
        <button
            class:active={current === frame}
            on:click={() => current = frame}
        >{frame.frame}</button>
    {/each}
</div>
