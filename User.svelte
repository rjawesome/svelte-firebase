<script>
  export let firebase
  export let user = undefined
  firebase.auth().onAuthStateChanged(u => {
    user = u;
  })
</script>

{#if user === undefined}
  <slot name="loading"></slot>
{:else if user === null}
  <slot name="signed-out"></slot>
{:else}
  <slot user={user}></slot>
{/if}
