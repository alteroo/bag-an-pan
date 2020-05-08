<script>
  import { onMount } from "svelte";
  let posts = [];
  onMount(async () => {
    const response = await fetch(
      "http://localhost:8080/db/grace_chapel_container",
      {
        headers: {
          "Content-Type": "application/json",
          Authorization: "Basic cm9vdDpyb290"
        }
      }
    );
    const json = await response.json();
    posts = json.items;

    console.log(posts);
  });
</script>

<style>
  li {
    border: 1px solid #ccc;
    background-color: khaki;
    padding: 16px 32px;
    margin: 8px;
    list-style: none;
  }
</style>

<ul>
  {#each posts as post}
    <li>{post['@name']}</li>
  {/each}
</ul>
