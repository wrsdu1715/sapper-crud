<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`https://jsonplaceholder.typicode.com/posts`)
      .then(r => r.json())
      .then(posts => {
        console.log(`prefetch: ${posts.length}件`)
        return { posts };
      });
  }
</script>
<script>
  import PageTitle from '../../components/molecules/PageTitle.svelte'
  import IconTrash from '../../components/atoms/IconTrash.svelte'
  import Button from 'svelma/src/components/Button.svelte'
  import { Dialog, Toast } from 'svelma'

  export let posts = [];
  let loading = false;

  function onDelete(post) {
    if (post === null) { return }
    Dialog.confirm({
          message: "以下の記事を本当に削除しますか？<br>" + post.title,
          title: "削除",
          type: 'is-danger',
          icon: 'trash.svg'
        })
        .then(isDelete => {
          if (isDelete) {deletePost(post)}
        })
  }

  function deletePost(post) {
    if (post === null) { return }
    return fetch(`https://jsonplaceholder.typicode.com/posts/${post.id}`, {
        method: 'DELETE'
      })
      .then(r => {
        posts = posts.filter(p => p.id !== post.id);
        Toast.create({
          message: r.ok ? '削除成功' : '削除失敗',
          type: r.ok ? 'is-success' : 'is-danger'
        })
      });
  }
</script>

<PageTitle title="記事一覧" subTitle="CRUD機能つき"></PageTitle>

<p>
  <a rel=prefetch href="post/create">新規作成</a>
</p>

<table class="table is-fullwidth">
  <thead>
    <tr>
      <th>id</th>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    {#each posts as post (post.id)}
      <tr>
        <td>{post.id}</td>
        <td><a rel=prefetch href="post/edit/{post.id}">{post.title}</a></td>
        <td><a on:click={() => onDelete(post)} href="javascript:void(0)"><IconTrash /></a></td>
      </tr>
    {:else}
      {#if !loading}
        <tr>
          <td colspan="3">
            <section class="section">
              <div class="content has-text-grey has-text-centered">
                <p><i class="far fa-3x fa-brown"></i></p>
                <p>データなし</p>
              </div>
            </section>
          </td>
        </tr>
      {/if}
    {/each}
  </tbody>
</table>

Icons made by <a href="https://www.flaticon.com/authors/kiranshastry" title="Kiranshastry">Kiranshastry</a> from <a href="https://www.flaticon.com/" title="Flaticon"> www.flaticon.com</a>