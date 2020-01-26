<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  function handleClick(e) {
    dispatch("message", { text: "Hello" });
  }
  export let value = "送信";
  export let color;
  let colors = {
    none: {
      class: "myBtn"
    },
    blue: {
      class: "myBtn blue"
    },
    red: {
      class: "myBtn red"
    }
  };
</script>

<style lang="scss">
  @import "../../styles/button.scss";
</style>

<input
  type="button"
  class={colors[color].class}
  on:click={handleClick}
  {value} />
