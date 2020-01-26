<script>
  import Button from "./Button.svelte";
  export let value;
</script>

<Button color="red" on:message {value} />
