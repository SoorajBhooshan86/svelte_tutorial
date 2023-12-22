<script>
    export let showModal = false;
    let isPromo = false;
    export let text = "It's me the default text";
</script>

{#if showModal}
    <div class="backdrop" on:click>
        <div class="modal" class:promo={isPromo}>{text}</div>
    </div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background-color: rgba(0, 0, 0, 0.8);
    }

    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        text-align: center;
        margin: 10% auto;
        background: white;
    }
    .promo {
        background: red;
        color: white;
    }
</style>
