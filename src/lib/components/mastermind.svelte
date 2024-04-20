<script>
import Field from '$lib/components/field.svelte';
import Input from '$lib/components/input.svelte';
import Header from '$lib/components/header.svelte';


let difficulty = 5;
let colors = ['red', 'blue', 'green', 'yellow', 'purple', 'orange'];


</script>
<style>
    #main{
        background-color: rgb(236, 170, 170);
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
    <Header/>
    <Field/>
    <Input {colors}/>
</div>