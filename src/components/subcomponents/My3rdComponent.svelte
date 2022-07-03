<script lang="ts">
  // Bug: Intellisense for component import does not work if
  // the component is not in the same directory, a child
  // directory, or a parent directory.
  // i.e. Intellisense to import My4thComponent.svelte from My3rdComponent.svelte does not work
  //
  // components/subcomponents/My3rdComponent.svelte
  // components/othercomponents/My4thComponent.svelte

  // Attempt to use intellisense to import My4thComponent
  // Type the following and wait for intellisense
  // import My

  // import My4thComponent from '../othercomponents/My4thComponent.svelte';
</script>

<h3>My3rdComponent</h3>
<My4thComponent />
