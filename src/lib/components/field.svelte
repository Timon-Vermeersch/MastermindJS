<script>
    import { LOGONSERVER } from '$env/static/private';
    import { createEventDispatcher } from 'svelte';

    export let attempts;
    export let showResults;
    export let correctColors;
    export let difficulty
    
    
    const dispatch = createEventDispatcher();

</script>

<style>

#main{
    background-color: rgb(150, 175, 177);
    padding: 0.5rem;
    margin: 0.5rem;
    height: 70%;
    display: flex;
    flex-direction: row;
    overflow-y: scroll;

    /* glass */
    background: rgba(255, 255, 255, 0.08);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(2.5px);
    -webkit-backdrop-filter: blur(2.5px);
    border: 1px solid rgba(255, 255, 255, 0.13);
}
#playingfield{
    background-color: rgb(188, 195, 195);
    width: 80%;
    display: flex;
    flex-direction: column;
    overflow-y: scroll;
    justify-content: flex-end;
    align-items: center;
}
.attempt {
    width: 80%;
    display: flex;
    justify-content: space-around;
    border-top: 2px solid #ccc;
    padding-bottom: 0.3rem;
    
    
    
}
#check{
    background-color: aquamarine;
    width: 20%;
}
</style>

<div id=main>

    <div id="playingfield">
        {#if showResults}
            {#each attempts as attempt}
                <div class="attempt">
                    {#each attempt as color}
                        <div style="background-color: {color}; width: 50px; height: 50px; border-radius: 50%; margin-top: 10px;">
                        </div>
                    {/each}
                </div>
                
            {/each}
        {/if}
    </div>


    <div id=check>

    </div>
</div>