<script lang="ts">
	export let icon: string;
	export let link: string;
	export let tooltip: string;
</script>

<a href={link} title={tooltip} target="_blank">
	<img src={icon} alt={tooltip} />
</a>

<style>
	a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}

	a:hover {
		filter: invert(32%) sepia(94%) saturate(3150%) hue-rotate(357deg) brightness(103%) contrast(99%);
	}
</style>
