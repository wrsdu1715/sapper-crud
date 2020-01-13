<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<script>
import 'bulma/css/bulma.css'
import Button from 'svelma/src/components/Button.svelte'
let title = "Sapper project template"
</script>

<svelte:head>
	<title>Sapper project template</title>
  <meta property="og:type" content="article" />
  <meta property="og:title" content="{title}" />
  <meta property="og:description" content="ページの説明" />
  <meta property="og:site_name" content="サイト名" />
  <meta property="og:image" content="https://placehold.jp/cc9999/993333/150x150.png" />
</svelte:head>

<h1>Great success!</h1>
<Button type="is-primary">I'm a Button!</Button>

<figure>
	<img alt='Borat' src='great-success.png'>
	<figcaption>HIGH FIVE!</figcaption>
</figure>

<p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p>
