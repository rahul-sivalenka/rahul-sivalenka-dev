<script context="module" lang="ts">
import Titbit from '$lib/Titbit.svelte';

	export const prerender = true;
</script>

<section>
	<p>Hey I'm</p>

	<Titbit>
		<h1>
			Rahul
		</h1>
	</Titbit>

</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		/* Fix for mobile browser overflowing viewport when height is set to 100vh
		Ref: https://css-tricks.com/css-fix-for-100vh-in-mobile-webkit/ */
		min-height: 100vh;
		min-height: --webkit-fill-available;
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