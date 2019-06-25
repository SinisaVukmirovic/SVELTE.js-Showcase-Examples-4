<style>
	.box {
		width: 80%;
		padding: 1em;
		margin: 0 auto 1em;
		border: 1px solid #eee;
		border-radius: 2px;
		box-shadow: 2px 2px 8px rgba(255,255,255,0.4);
    }
</style>

<div class="box">
	<slot>
		<em>This is fallback slot! No content was provided</em>
	</slot>
</div>