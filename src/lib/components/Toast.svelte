<script>
    import { fly } from 'svelte/transition';
    import {alert} from '../alert';

    function alertClose() {
        alert.set({
            text: $alert.text,
            isActive: false
        })
    }

    alert.subscribe(value => {
        if (value.isActive) {
            setTimeout(alertClose, 2000)
        }
    })
</script>

{#if $alert.isActive}
    <div on:click={alertClose} transition:fly={{y: 100}} class="toast">
        <p>{$alert.text}</p>
    </div>
{/if}

<style>
    .toast {
        color: white;
        background: var(--black);
        border-radius: var(--borderRadiius);
        padding: 20px;
        box-shadow: var(--level-2);
        position: fixed;
        bottom: 10px;
        left: 10px;
        right: 10px;
    }

    .toast p {
        text-align: center;
        margin: 0;
        max-width: 100%;
    }
</style>
