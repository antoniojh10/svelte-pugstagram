<script>
  import { onMount } from "svelte";
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import TimeLine from "../components/TimeLine.svelte";
  import Sidebar from "../components/Sidebar.svelte";

  let data = {};
  const API = "https://us-central1-pugstagram-co.cloudfunctions.net/data";

  const myUser = {
    name: "Antonio Hernández",
    nickname: "antoniojh10",
    avatar:
      "https://static.platzi.com/media/avatars/avatars/antoniojh10_9d913909-e6e6-479a-a8ac-b80c0ddc263c.jpg"
  };

  onMount(async () => {
    const response = await fetch(API);
    data = await response.json();
  });
</script>

<div class="main">
  <Header />
  <Main>
    <TimeLine posts={data.posts} />
    <Sidebar {...myUser} />
  </Main>
</div>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap");
  @import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");
  :global(body) {
    background-color: #fafafa;
    color: rgba(38, 38, 38, 0.7);
    font-family: "Lato", sans-serif;
    margin: 0;
    padding: 0;
  }

  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }
</style>
