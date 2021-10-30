<script context="module">
	import { browser, dev } from '$app/env';

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	export const hydrate = dev;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	export const router = browser;

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;
</script>

<svelte:head>
	<title>About</title>
</svelte:head>

<div class="content">
	<h1>About Me</h1>

	<p>
		Hey! I am <b>Phani Rahul Sivalenka</b> (or simply <b>Rahul</b>).
	</p>

	<p>I'm a former electrical engineer and a current full stack developer from Hyderabad, India.</p>

	<p>
		Currently working on ReactJS. Although, I am interested to learn anything web related. My work
		so far involved this major stack: Angular, ReactJS, .Net and NodeJS.
	</p>

	<p>On the way to learn Svelte and Java.</p>

	<p>
		I love to explore and experiment with any new tech and am constantly on the look out for new
		updates in the industry.
	</p>

	<p>I love to teach. My teaching as of now is limited to co-workers and friends.</p>
</div>

<style>
	.content {
		width: 100%;
		max-width: var(--column-width);
		margin: var(--column-margin-top) auto 0 auto;
	}
</style>
