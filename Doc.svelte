<script>
  export let firebase
  export let path
  export let doc = undefined
  export let id = undefined
  firebase.firestore().doc(path).onSnapshot(document => {
    if (!document.exists) doc = null
    else {
      doc = document.data()
      id = document.id
    }
  },
  error => {
    doc = null
  })
</script>

{#if doc === undefined}
  <slot name="loading"></slot>
{:else if doc === null}
  <slot name="fallback"></slot>
{:else}
  <slot id={id} doc={doc}></slot>
{/if}
