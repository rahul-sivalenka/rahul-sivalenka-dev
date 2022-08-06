<script lang="ts">
	import party from 'party-js';

	function handleClick(this: HTMLSpanElement) {
		party.confetti(this);
	}
</script>

<span role="button" on:click={handleClick}>
	<slot />
</span>
