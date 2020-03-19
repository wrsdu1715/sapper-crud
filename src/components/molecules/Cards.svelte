<script>
  import Card from '../atoms/Card.svelte';
</script>

<style lang="scss">
@import "../../styles/common.scss";
  .cards{
    border: 1px solid $v-pointColor ;
    padding: 10px;
    display: flex;
  }
</style>


<ul class="cards">
  <Card />
  <Card />
  <p>親コンポーネント</p>
</ul>