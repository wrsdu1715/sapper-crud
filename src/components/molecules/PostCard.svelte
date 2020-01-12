<script>
  import { fade } from 'svelte/transition'
  const titleize = s => s.replace(/^([a-z])/, (_, r) => r.toUpperCase())
  export let post = {
    id: null,
    title: '',
    body: ''
  }
</script>
<div class="box">
  <article class="media">
    <div class="media-left">
      <figure class="image is-64x64">
        {#if post}
          <img transition:fade class="is-rounded" src="https://placehold.jp/150x150.png" alt="Profile picture" />
        {/if}
      </figure>
    </div>
    <div class="media-content">
      <div class="content">
        {#if post}
          <p transition:fade>
            <strong>{titleize(post.title)}</strong>
            <small />
            <br />
            {post.body}
          </p>
        {/if}
      </div>
      {#if post}
        <nav class="level is-mobile" transition:fade>
          <div class="level-left">
            <a href class="level-item" aria-label="reply">
              <span class="icon is-small">
                <i class="fas fa-reply" aria-hidden="true" />
              </span>
            </a>
            <a href class="level-item" aria-label="retweet">
              <span class="icon is-small">
                <i class="fas fa-retweet" aria-hidden="true" />
              </span>
            </a>
            <a href class="level-item" aria-label="like">
              <span class="icon is-small">
                <i class="fas fa-heart" aria-hidden="true" />
              </span>
            </a>
          </div>
        </nav>
      {/if}
    </div>
  </article>
</div>