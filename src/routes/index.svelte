<script>
  import Cards from '../components/molecules/Cards.svelte';
  import "bulma/css/bulma.css";
  let title = "Sapper project template";
</script>

<style lang="scss">

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
    text-align: center;
    margin: 0 auto;
  }

  .test{
    font-size: 1.2rem;
    color: $v-pointColor;
    text-align: center;
    padding: 10px;
    border: 1px solid #444;
    //mixin使用
    @include m-radius(5px);
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
  <meta property="og:type" content="article" />
  <meta property="og:title" content={title} />
  <meta property="og:description" content="ページの説明" />
  <meta property="og:site_name" content="サイト名" />
  <meta
    property="og:image"
    content="https://placehold.jp/cc9999/993333/150x150.png" />
</svelte:head>

<h1>Great success!</h1>
<p class="test">グローバルscssからmxinを使った場合</p>
<p class="button">グローバルscssからextendを使った場合</p>

<Cards />
