<script>
    export let message = ''
</script>

<style>
    #alert {
        position: fixed;
        top: 20px;
        right: 20px;
        padding: 10px;
        
        color: white;
        border-radius: 5px;
        background: rgba(255, 255, 255, 0.2);
        border-radius: 16px;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
        backdrop-filter: blur(5px);
        -webkit-backdrop-filter: blur(5px);
        border: 1px solid rgba(255, 255, 255, 0.3);
    }
</style>
{#if message}
<div id = alert >
    {message}
</div>
{/if}