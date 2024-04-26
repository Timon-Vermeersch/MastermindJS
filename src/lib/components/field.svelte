<script>
   
    import { createEventDispatcher } from 'svelte';
    import Checkmark from './checkmark.svelte';
    import QuestionMark from './questionMark.svelte';
    import Cross from './cross.svelte';
    

    export let attempts;
    export let showResults;
    export let correctColors;
    export let difficulty


    
    
    const dispatch = createEventDispatcher();

    function transformGuess (attempt,solution,difficulty) {
    let checked = Array(difficulty).fill('');
    for (let i = 0; i < attempt.length; i++) {
        if(solution.includes(attempt[i]) && attempt[i] !== solution[i]){
            checked[i] = 'vraagteken'
        }
        else if(solution.includes(attempt[i]) && attempt[i] === solution[i]){
            checked[i] = 'checkmark'
        }
        else if(!solution.includes(attempt[i])){
            checked[i] = 'kruisje'
        }

    }
    console.log('checked',checked)
    return checked
}

</script>

<style>

#main{
    background-color: #DB6324;
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
    background-color: #ABE4A1;
    background-image: url(../static/woodpattern.png);
    width: 80%;
    display: flex;
    flex-direction: column;
    overflow-y: scroll;
    justify-content: flex-end;
    align-items: center;
    border-radius: inherit;

}
.attempt {
    width: 100%;
    display: flex;
    justify-content: space-around;
    border-top: 2px solid #ccc;
    padding-bottom: 0.3rem;
    
    
    
    
}
#check{
    background-color: #ABE4A1;
    width: 20%;
    
    border-top-right-radius: inherit;
    border-bottom-right-radius: inherit;

}
.flex{
    display: flex;
    flex-direction: column;
    justify-content: flex-end;

}

.flexrow{
    display: flex;
    flex-direction: row;
    gap: 1rem;
    padding:1.42rem;
    justify-content: center;
    border-top: rgb(113, 112, 112) solid 1px
    


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


        <div id=check class='flex'>
            {#each attempts as attempt}
            <div class='flexrow'>
                {#each transformGuess(attempt,correctColors,difficulty) as transformedGuess}
                        {#if transformedGuess === 'vraagteken'}   
                            <span><QuestionMark/></span>
                        {/if}
                        {#if transformedGuess === 'kruisje'}   
                            <span><Cross/></span>
                        {/if}
                        {#if transformedGuess === 'checkmark'}   
                            <span><Checkmark/></span>
                        {/if}

                        
                        
                    {/each}
                </div>
            {/each}
        </div>
</div>