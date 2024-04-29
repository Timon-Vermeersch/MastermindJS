<script>
    import { createEventDispatcher } from 'svelte';
    import Alert from './alert.svelte';
    export let startGame
    // let difficultyOptions = [4 , 5 , 6]
    let selectedOption = ''
    let alertNewGame = false



    const dispatch = createEventDispatcher();
    const difficulty = {
        Easy: 4,
        Medium: 5,
        Hard: 6
    };
    function handleNewGame() {
    if (selectedOption) {
        // dispatch('newGame', { detail: { difficulty: selectedOption } });
        dispatch('newGame', { difficulty: selectedOption });
        console.log(`${selectedOption} starting new game`);
        dispatch('alertNewGame0');
    } else {
        dispatch('alertNewGame1');
    }
}


    
</script>
<style>

#main{
    background-color: #ABE4A1;
    padding: 0.5rem;
    margin: 0.5rem;
    height: 10%;
    display: flex;
    font-size: clamp(3rem);
    font-family: "JetBrains Mono",monospace;
    

    /* glass */
    background: rgba(255, 255, 255, 0.08);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(2.5px);
    -webkit-backdrop-filter: blur(2.5px);
    border: 1px solid rgba(255, 255, 255, 0.13);

}

#title{
    padding: 1rem;
    display: flex;
    
    width: 80%;
    justify-content: space-around;
    align-items: center;
    
}
#gameSettings{
    padding: 0.2rem;
    display: flex;
    width: 20%;
    font-size: 1rem;
    flex-direction: column;
    flex-wrap: nowrap;
    align-content: space-around;
    align-items: stretch;
    justify-content: space-evenly;
}

#difftitle{
    display: flex;
    justify-content: center;
}
.check{
  align-items: center;
  background-color: #8390dc39;
  border-radius: 4px;
  box-sizing: border-box;
  cursor: pointer;
  display: inline-flex;
  font-family: "JetBrains Mono",monospace;
  justify-content: center;
  line-height: 1;
  overflow: hidden;
  padding-left: 1rem;
  padding-right: 1rem;
  position: relative;
  text-align: left;
  transition: box-shadow .15s,transform .15s;
  
  height: 4rem;
  

}
  
  
</style>

<div id=main>

    <div id = title>Mastermind-js</div>

    <div id = gameSettings>
        <div id= difftitle>Choose difficulty</div>
        <select  class=check bind:value = {selectedOption}>
            <option value="" selected disabled hidden>Easy</option>
            {#each Object.entries(difficulty) as [key,value]}
                <option value = {value}> {key} </option>
            {/each}
        </select>
        <button class=check on:click={handleNewGame}>Start New Game!</button>
    </div>




</div>
