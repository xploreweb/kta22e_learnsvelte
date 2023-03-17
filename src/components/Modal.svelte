<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    export let active;
</script>

<div class="modal" class:is-active={active}>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="modal-background" on:click={()=>{dispatch('close')}}></div>
    <div class="modal-content">
      <p class="image is-4by3">
        <img src="https://bulma.io/images/placeholders/1280x960.png" alt="">
      </p>
    </div>
    <button class="modal-close is-large" aria-label="close" on:click={()=>{active=false;}}></button>
  </div>