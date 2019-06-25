<script>
    let language = 'english';
    let framework = 'svelte';

    const translations = {
		english: {
			tooltip: "Switch Languages",
		},
		latin: {
			tooltip: "Itchsway Anguageslay",
		}
    };
    
    const descriptions = {
		svelte: {
			tooltip: "is Amazing!",
		},
		react: {
			tooltip: "is not reactive!",
		}
    };

	function tooltip(node, text) {
		const tooltip = document.createElement('div');
		tooltip.textContent = text;

		Object.assign(tooltip.style, {
			position: 'absolute',
			background: '#eee',
			color: '#333',
			padding: '0.5em 1em',
			fontSize: '12px',
			pointerEvents: 'none',
            transform: 'translate(-50%, 100%)',
            border: '2px solid cornflowerblue',
			borderRadius: '2px',
			transition: 'opacity 0.4s'
		});

		function position() {
			const { top, right, bottom } = node.getBoundingClientRect();
			tooltip.style.top = `${(top + bottom) / 2}px`;
			tooltip.style.left = `${right}px`;
		}

		function append() {
			document.body.appendChild(tooltip);
			tooltip.style.opacity = 0;
			setTimeout(() => tooltip.style.opacity = 1);
			position();
		}

		function remove() {
			tooltip.remove();
		}

		node.addEventListener('mouseenter', append);
		node.addEventListener('mouseleave', remove);

		return {
			update(text) {
				tooltip.textContent = text;
				position();
			},

			destroy() {
				tooltip.remove();
				node.removeEventListener('mouseenter', append);
				node.removeEventListener('mouseleave', remove);
			}
		};
	}
    
    function toggleLangBtn() {
        language = language === 'english' ? 'latin' : 'english';
	}
    function toggleFrameBtn() {
        framework = framework === 'svelte' ? 'react' : 'svelte';
	}
</script>

<!-- ======================================= -->

<style>
	.btn-container {
		display: flex;
		justify-content: space-evenly;
	}
</style>
<!-- ======================================= -->

<div class="btn-container">
	<button on:click={toggleLangBtn} use:tooltip={translations[language].tooltip}>
		{language}
	</button>

	<button on:click={toggleFrameBtn} use:tooltip={descriptions[framework].tooltip}>
		{framework}
	</button>
</div>
