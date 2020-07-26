<script>
  export let firebase
  export let path
  export let collection = undefined
  firebase.firestore().collection(path).onSnapshot(collection_result => {
    var collection = {}
    collection_result.forEach(doc => {
      collection[doc.id] = doc.data()
    })
  })
</script>

{#if collection === undefined}
  <slot name="loading"></slot>
{:else if collection === null}
  <slot name="fallback"></slot>
{:else}
  <slot collection={collection}></slot>
{/if}
