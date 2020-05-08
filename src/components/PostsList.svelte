<script>
  import { onMount } from "svelte";
  let posts = [];
  onMount(async () => {
    const response = await fetch(
      "http://localhost:8080/db/site/grace_chapel_container",
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

<ul>
  {#each posts as post}
    <li>{post['@name']}</li>
  {/each}
</ul>
