<script>
  import 'bulma/css/bulma.css'

  export let title = '未指定';
  export let subTitle = '未指定';
</script>

<style>
  .pageTitle-title {
    padding: 1rem;
  }
</style>

<section class="hero is-info">
  <div class="hero-body pageTitle-title">
    <div class="container">
      <h1 class="title">
        {title}
      </h1>
      <h2 class="subtitle">
        {subTitle}
      </h2>
    </div>
  </div>
</section>