<script context="module">
  export function preload({ host, path, params }) {
    let ogp = {}
    ogp.url = 'https://' + host + path
    ogp.type = 'article'
    ogp.title = '記事編集タイトル'
    ogp.description = '記事詳細'
    ogp.site_name = 'サイト名'
    ogp.image = 'https://placehold.jp/cc9999/993333/150x150.png'

    console.log(host)
    console.log(path)
    console.log(params)
    let { postId } = params;
    console.log('preload: postId=' + postId);
    return this.fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`)
      .then(r => r.json())
      .then(post => {
        return { post, ogp };
      });
  }
</script>
<script>
  import PageTitle from '../../../components/molecules/PageTitle.svelte'
  import Button from 'svelma/src/components/Button.svelte'
  import Input from 'svelma/src/components/Input.svelte'
  import Progress from 'svelma/src/components/Progress.svelte'
  import { Snackbar } from 'svelma'

  export let post;
  export let ogp;

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
        Snackbar.create({ message: ' 編集成功' })
        posting = false;
        })
      .catch(error => {
        console.log(error);
        posting = false;
        })
  }
</script>

<svelte:head>
  <title>Sapper project template</title>
  <meta property="og:url" content={ogp.url} />
  <meta property="og:type" content={ogp.type} />
  <meta property="og:title" content={ogp.title} />
  <meta property="og:description" content={ogp.description} />
  <meta property="og:site_name" content={ogp.site_name} />
  <meta property="og:image" content={ogp.image} />
</svelte:head>

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
    <a rel=prefetch href="post">一覧に戻る</a>
  </div>
</form>

{#if posting}
  <Progress type="is-primary" max="100"></Progress>
{/if}
