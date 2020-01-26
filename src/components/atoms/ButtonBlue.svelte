<script>
  import Button from "./Button.svelte";
  export let value;
</script>

<Button color="blue" on:message {value} />
