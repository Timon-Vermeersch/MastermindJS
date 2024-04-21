<script>
    import { createEventDispatcher } from 'svelte';
    
    export let colors;
    export let selectedColors

    const dispatch = createEventDispatcher();

    let name = '';

    function setColor(index, color){
      selectedColors[index] = color;
  }
    function handleCheck(){
      dispatch('check');
  }
</script>
<style>

#main{
    background-color: rgb(150, 175, 177);
    padding: 0.5rem;
    margin: 0.5rem;
    height: 15%;
    display: flex;
    justify-content: space-between;

    /* glass */
    background: rgba(252, 252, 252, 0.08);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(2.5px);
    -webkit-backdrop-filter: blur(2.5px);
    border: 1px solid rgba(255, 255, 255, 0.13);
    
}

</style>

<div id="main">
    {#each selectedColors as color, index}
      <div>
            <select bind:value={selectedColors[index]} on:change={() => setColor(index, selectedColors[index])}>
            <option value="">Select a color</option>
            {#each colors as color}
                <option value={color}>{color}</option>
            {/each}
            </select>
            <div style="background-color: {selectedColors[index]}; max-width: 50px; height: 50px; border-radius: 50%; margin-top: 10px;"></div>
      </div>
    {/each}
    <button class=check on:click={handleCheck}>check!</button>
</div>