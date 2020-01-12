<script>
  import PageTitle from '../../../components/molecules/PageTitle.svelte'
  import Button from 'svelma/src/components/Button.svelte'
  import Input from 'svelma/src/components/Input.svelte'
  import Progress from 'svelma/src/components/Progress.svelte'
  // Identifier is expected エラーで使えない
  // import Snackbar from 'svelma/src/components/Snackbar/Snackbar.svelte'
  // import Field from 'svelma/src/components/Field.svelte'

  let post = {
    title: '',
    body: '',
    userId: 1
  }
  let posting = false;

  // 新規作成
  function createPost() {
    if (posting) { return };
    console.log({post})
    posting = true;
    fetch('https://jsonplaceholder.typicode.com/posts', {
        method: 'POST',
        body: JSON.stringify(post),
        headers: {
          "Content-type": "application/json; charset=UTF-8"
        }
      })
      .then(response => response.json())
      .then(json => {
        console.log(json);
        posting = false;
        })
      .catch(error => {
        console.log(error);
        posting = false;
        })
  }
</script>

<PageTitle title="新規作成" subTitle="新しい記事を作成する"></PageTitle>

<form name="form">
  <fieldset label="title">
    <label for="title">タイトル</label>
    <Input type="text" bind:value={post.title} id="title" name="title" />
  </fieldset>
  <fieldset label="body">
    <label for="body">内容</label>
    <Input type="text" bind:value={post.body} />
  </fieldset>
  <div>
    <Button type="is-primary" on:click={createPost}>新規登録する</Button>
    <a href="post">一覧に戻る</a>
  </div>
</form>

{#if posting}
  <Progress type="is-primary" max="100"></Progress>
{/if}

<!-- Fieldのエラーが発生するためSvelmaは使用しない -->
<!-- ../sapper-crud/node_modules/svelma/src/components/Field.svelte
Identifier is expected
 95: <style lang="scss">
 96:   .field {
 97:     &.is-grouped {
         ^
 98:       .field {
 99:         flex-shrink: 0; -->
