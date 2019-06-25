<script>
	let current = 'svelte';
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
    <button
        class:active="{current === 'svelte'}"
        on:click="{() => current = 'svelte'}"
    >Svelte</button>

    <button
        class:active="{current === 'react'}"
        on:click="{() => current = 'react'}"
    >React</button>

    <button
        class:active="{current === 'vue'}"
        on:click="{() => current = 'vue'}"
    >Vue</button>

    <button
        class:active="{current === 'angular'}"
        on:click="{() => current = 'angular'}"
    >Angular</button>
</div>
