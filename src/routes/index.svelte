<script context="module" lang="ts">
	export const prerender = true;
</script>

<section>
	<p>Hey I'm</p>
	<h1>
		Rahul
	</h1>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
		background-color: burlywood;
	}

	h1, p {
		margin: 0;
	}

	p {
		transform: translateX(-100%);
		font-size: 1.5rem;
		font-style: italic;
	}
	
	h1 {
		font-size: 4rem;
		font-weight: bold;
	}
</style>