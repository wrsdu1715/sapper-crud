<script context="module">
  export function preload({ params, query }) {
    let { postId } = params;
    console.log(postId);
    return this.fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`)
      .then(r => r.json())
      .then(post => {
        return { post };
      });
  }
</script>
<script>
  import PageTitle from '../../../components/molecules/PageTitle.svelte'
  import Button from 'svelma/src/components/Button.svelte'
  import Input from 'svelma/src/components/Input.svelte'
  import Progress from 'svelma/src/components/Progress.svelte'

  export let post;
  let posting = false;

  // 編集
  function editPost() {
    if (posting) { return };
    console.log({post})
    posting = true;
    fetch(`https://jsonplaceholder.typicode.com/posts/${post.id}`, {
        method: 'PUT',
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

<PageTitle title="編集" subTitle="記事を編集する"></PageTitle>

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
    <Button type="is-primary" on:click={editPost}>編集する</Button>
    <a href="post">一覧に戻る</a>
  </div>
</form>

{#if posting}
  <Progress type="is-primary" max="100"></Progress>
{/if}
