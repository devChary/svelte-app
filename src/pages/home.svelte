<script>
  import { onMount } from "svelte";
  import PostForm from '../components/postForm.svelte';

  const apiBaseUrl =
    "https://ndb99xkpdk.execute-api.eu-west-2.amazonaws.com/dev";
  let posts = [];

  onMount(async () => {
    const res = await fetch(apiBaseUrl + "/posts");
    posts = await res.json();
  });

  function editPost(post) {
      console.log(post)
  }

  function deletePost(id) {
      console.log(id)
  }
</script>

<style>
  .delete-btn {
    color: red !important;
  }

  .card .card-content .card-title {
    margin-bottom: 0;
  }

  .card .card-content p.timestamp {
    color: #999;
    margin-bottom: 10px;
  }
</style>


<div class="row">
    <div class="col s6">

    </div>
</div>

<div class="row">
  {#if posts.length === 0}
    <h3>Loading posts...</h3>
  {:else}
    {#each posts as post}
      <div class="col s6">
        <div class="card">
          <div class="card-content">
            <p class="card-title">{post.title}</p>
            <p class="timestamp">{post.createdAt}</p>
            <p>{post.body}</p>
          </div>
          <div class="card-action">
            <a on:click={() => editPost(post)}>Edit</a>
            <a on:click={() => deletePost(post.id)} class="delete-btn">Delete</a>
          </div>
        </div>
      </div>
    {/each}
  {/if}
</div>
