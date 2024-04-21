<script>
    import { createEventDispatcher } from 'svelte';
    import Alert from './alert.svelte';
    export let startGame
    let difficultyOptions = [4 , 5 , 6]
    let selectedOption = ''
    let alertNewGame = false



    const dispatch = createEventDispatcher();

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
    background-color: rgb(150, 175, 177);
    padding: 0.5rem;
    margin: 0.5rem;
    height: 10%;
    display: flex;
    font-size: 3rem;
    

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
    
}
#gameSettings{
    padding: 1rem;
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
</style>

<div id=main>

    <div id = title>Mastermind-js</div>

    <div id = gameSettings>
        <div id= difftitle>Choose difficulty</div>
        <select bind:value = {selectedOption}>
            {#each difficultyOptions as option}
                <option value = {option}> {option} </option>
            {/each}
        </select>
        <button class=check on:click={handleNewGame}>Start New Game!</button>
    </div>
</div>

