<script>
  import Button from "./Button.svelte";
  export let value;
</script>

<style lang="scss">
  @import "../../styles/button.scss";
</style>

<Button color="blue" {value} />
