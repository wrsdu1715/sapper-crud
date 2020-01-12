<script>
  import PageTitle from '../../components/molecules/PageTitle.svelte'
  import Button from 'svelma/src/components/Button.svelte'

  let posts = [];
  let loading = false;
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
    </tr>
  </thead>
  <tbody>
    {#each posts as post (post.id)}
      <tr>
        <td>{post.id}</td>
        <td>{post.title}</td>
      </tr>
    {:else}
      {#if !loading}
        <tr>
          <td colspan="2">
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