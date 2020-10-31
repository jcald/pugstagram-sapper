<script context="module">
  export async function preload() {
    let data = {};
    const response = await this.fetch(
      `https://us-central1-pugstagram-co.cloudfunctions.net/data`
    );
    data = await response.json();
    // console.log('Antes:',data);
    data.user.name='Noemi Medina';
    data.user.nickname='Noe';
    // console.log('Despues:', data)
    return { data };
  }
</script>

<script>
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import Sidebar from "../components/Sidebar.svelte";
  import TimeLine from "../components/TimeLine.svelte";
  export let data;
</script>

<svelte:head>
  <title>Pugstagram</title>
</svelte:head>

<Main>
  <TimeLine posts={data.posts} />
  <Sidebar {...data.user} />
</Main>
