<script>
    import { fade, fly } from 'svelte/transition';
    import { quintOut } from 'svelte/easing';
    export let close;
    export let win_lose = false;
</script>

<style>
    .modal {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000; 
    }
    .modal-content {
        background: white url('/YOUWIN.png') no-repeat center center;
        background-size: contain;
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        position: relative;
        width: 20rem;
        height: 20rem;
        color: #fff; 
        
    }
    .modal-content2 {
        background: white url('/YOULOSE.png') no-repeat center center;
        background-size: cover;
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        position: relative;
        width: 20rem;
        height: 20rem;
        color: #fff; 
        
    }
    #close {
        position: absolute;
        top: 10px;
        right: 10px;
        cursor: pointer;
        font-size: 1rem;
        height: 2rem;
        width: 4rem;
    }

    </style>



<div class="modal" in:fade={{ delay: 250, duration: 250 }} out:fade={{ duration: 250 }}>
    <div class={win_lose ? 'modal-content2' : 'modal-content'} in:fly={{ y: -200, delay: 250, duration: 250, easing: quintOut }}>
        <button id='close' on:click = {close}>Close</button>
        
    </div>
</div>