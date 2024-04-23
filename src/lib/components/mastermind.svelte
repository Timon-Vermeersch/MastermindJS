<script >
import { flip } from 'svelte/animate';
import Field from '$lib/components/field.svelte';
import Input from '$lib/components/input.svelte';
import Header from '$lib/components/header.svelte';
import Alert from './alert.svelte';
import YouWin from './youWin.svelte';

let newGameBool = false
let attempts = [];
let selectedColors = Array(4).fill('');
let colors = ['red', 'blue', 'green', 'yellow', 'purple', 'orange'];
let difficulty = 5;
let showResults = false;
let correctColors = [];
let showAlert = false
let alertMessage = ''
let youWin = false

$: if (newGameBool) {
    setTimeout(() => {
      newGameBool = false;
    }, 3000); // Change '3000' to however many milliseconds you want
  }

function newGameAlert(){
    
    newGameBool = true;
    alertMessage = 'Fresh Game Started 101';
    
}

function newCorrectColors(difficulty) {
    correctColors = []; 
    while (correctColors.length < difficulty) { 
        let randomIndex = Math.floor(Math.random() * colors.length);
        let color = colors[randomIndex];
        if(!correctColors.includes(color)){
            correctColors = [color, ...correctColors]; // Use correctColors to store the new random color
        }
        
    }
    console.log(correctColors);
}
function newWin(){
    
    let difficultyLevel = 4
    console.log(difficultyLevel)
    console.log(`Starting new game with difficulty: ${difficultyLevel}`);
    difficulty = difficultyLevel;
    showResults = false;
    showAlert = false;
    alertMessage = '';
    newCorrectColors(difficultyLevel);
    selectedColors = Array(difficultyLevel).fill('');
    

     

}

function newGame(event){
    console.log(event)
    let difficultyLevel = event.detail.difficulty;
    console.log(difficultyLevel)
    console.log(`Starting new game with difficulty: ${difficultyLevel}`);
    attempts = [];
    difficulty = difficultyLevel;
    showResults = false;
    showAlert = false;
    alertMessage = '';
    newCorrectColors(difficultyLevel)
    selectedColors = Array(difficultyLevel).fill('');
    newGameAlert()
    

    
     

}
function handleCheck() {
    if (selectedColors[0] == '' || selectedColors[1] == '' || selectedColors[2] == '' || selectedColors[3] == '') {
        showAlert = true;
        alertMessage = '1 or more inputs need to be filled';
    } else if (arraysEqual(selectedColors, correctColors)) {
        const newAttempt = [...selectedColors];
        console.log(selectedColors);
        console.log(correctColors);
        attempts = [newAttempt, ...attempts];
        showResults = true;
        console.log('you win');
        youWin = true
        


    } else {
        const newAttempt = [...selectedColors];
        console.log(selectedColors);
        console.log(correctColors);
        attempts = [newAttempt, ...attempts];
        showResults = true;
        selectedColors.fill('');
        console.log(attempts);
        showAlert = false;
        newGameBool = false
    }
}




function arraysEqual(a, b) {
    if (a.length !== b.length) return false;
    for (let i = 0; i < a.length; i++) {
        if (a[i] !== b[i]) return false;
    }
    return true;
}


</script>
<style>
    #main{
        background-color: #24bddb;
        height: 90vh;
        width: 65vw;
        border-radius: 16px;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
        backdrop-filter: blur(2.5px);
        -webkit-backdrop-filter: blur(2.5px);
        border: 1px solid rgba(255, 255, 255, 0.13);
        display: flex;
        flex-direction: column;
        overflow: hidden;
    }
</style>

<div id=main>
    <Header 
    on:alertNewGame1={() => {showAlert = true;alertMessage = 'Choose Difficulty'}}
    on:alertNewGame0={() => {showAlert = false;alertMessage = ''}}
    on:newGame={newGame}/>
    <Field {attempts} {showResults} {correctColors} {difficulty}/>
    <Input {colors} {selectedColors} on:check={handleCheck}/>
    
    {#if youWin}
    <YouWin close={() => youWin = false}/>
    {/if}


</div>

{#if showAlert}
<Alert message={alertMessage}/>
{/if}


{#if newGameBool}
<Alert message={'fresh game started'}/>
{/if}









