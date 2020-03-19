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
      class: "myBtn_blue"
    },
    red: {
      class: "myBtn_red"
    }
  };
</script>

<style lang="scss">
  @import "../../styles/common.scss";
  .myBtn{
    &_blue{
      background-color: $COLOR_BLUE;
    }

    &_red{
      background-color: $COLOR_RED;
    }
  }
</style>

<input
  type="button"
  class={colors[color].class}
  on:click={handleClick}
  {value} />
