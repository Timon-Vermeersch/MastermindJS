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
/* font-family: "JetBrains Mono",monospace; */
#main{
    background-color: rgb(150, 175, 177);
    padding: 0.5rem;
    margin: 0.5rem;
    height: 15%;
    display: flex;
    justify-content: space-around;
    

    /* glass */
    background: rgba(252, 252, 252, 0.08);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(2.5px);
    -webkit-backdrop-filter: blur(2.5px);
    border: 1px solid rgba(255, 255, 255, 0.13);
    
}
.check{
  align-items: center;
  background-color: #8391dc;
  border-radius: 4px;
  box-sizing: border-box;
  cursor: pointer;
  display: inline-flex;
  font-family: "JetBrains Mono",monospace;
  justify-content: center;
  line-height: 1;
  overflow: hidden;
  padding-left: 16px;
  padding-right: 16px;
  position: relative;
  text-align: left;
  transition: box-shadow .15s,transform .15s;
  font-size: clamp(1rem);
  width: 7rem;
  height: 7rem;
  
  
}
select {
    width: auto; 
    padding: 8px;
    margin: 1px;
    border: 1px solid #ccc; 
    border-radius: 4px; 
    background-color: white; 
    cursor: pointer; 
    font-family: Arial, sans-serif; 
    font-size: clamp(14px); 
    height: 80%;
  }
  select:focus {
    outline: none; 
    border-color: #0056b3; 
    
  }
  option {
    display: flex;

    padding: 8px; 
    background-color: #f8f9fa; 
  }
  #input{
    display: flex;
    align-items: center;
  }
</style>

<div id="main">
    {#each selectedColors as color, index}
      <div id="input">
            <select style = "background-color: {selectedColors[index]}"bind:value={selectedColors[index]} on:change={() => setColor(index, selectedColors[index])}>
            <option value="">Select a color</option>
            {#each colors as color}
                <option value={color}>{color}</option>
            {/each}
            </select>
            <!-- <div style="background-color: {selectedColors[index]}; max-width: 50px; height: 50px; border-radius: 50%; margin-top: 10px;"></div> -->
      </div>
    {/each}
    <button class=check on:click={handleCheck}>check!</button>
</div>