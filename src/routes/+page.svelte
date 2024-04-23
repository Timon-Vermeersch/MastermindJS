<script>
    import Mastermind from '$lib/components/mastermind.svelte';
    let code = [0,0,0,0]
</script>
<style>
    :global(html, body) {
        margin: 0;
        padding: 0;
        height: 100%;
        font-family: "JetBrains Mono",monospace;
    }
    #main{
        background-color: #249CDB;
        height: 100%;
        width: 100%;
        overflow: auto;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>

<div id=main>
    <Mastermind/>
</div>