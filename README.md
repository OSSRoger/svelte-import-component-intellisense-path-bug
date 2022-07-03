# BUG: Svelte for VS Code : Intellisense for Import Nested Sibling Component

Intellisense for component import does not work if
the component is not in the same directory, a child
directory, or a parent directory.

## Repro: Intellisense to import My4thComponent into My3rdComponent.svelte does not work
1. Create a new svelte project.
2. Create a components directory under the src directory in the project.
3. Create a subcomponents directory under the components directory.
4. Create an othercomponents directory under the components directory.
5. Create a My1stComponent.svelte under the components directory.
6. Create a My2ndComponent.svelte under the components directory.
6. Create a My3rdComponent.svelte under the subcomponents directory.
7. Create a My4thComponent.svelte under the othercomponents directory.
8. Import My2ndComponent into My1stComponent.svelte and note that import intellisense is working.
9. Import My3rdComponent into My2ndComponent.svelte and note that import intellisense is working.
10. Attemp to import My4thComponent into My3rdComponent and note that import intellisense is NOT working. 
Type the following into the script block in My3rdComponent and note that intellisense never gives an option for My4thComponent
```bash
<script>
import My
</script>
```
## i.e. Directory structure where ./ is the root of the project
```bash
./src/components/My1stComponent.svelte
./src/components/My2ndComponent.svelte
./src/components/subcomponents/My3rdComponent.svelte
./src/components/othercomponents/My4thComponent.svelte
```


## Optional
BTW Running the following is optional as the issue still repros with or without typescript.
```bash
node scripts/setupTypeScript.js
```

## Note
I tried reproducing the issue with only three components. 
I eliminated the My2ndComponent and renamed My3rdComponent to My2ndComponent and My4thComponent to My3rdComponent.
When attempting to import My3rdComponent into My2ndComponent the isue didn't repro.
i.e.
```bash
./src/components/My1stComponent.svelte
./src/components/subcomponents/My2ndComponent.svelte
./src/components/othercomponents/My3rdComponent.svelte
```



## System Info
- OS: macOS Monterey 12.4, MacBook Pro, Apple M1 Pro,
- IDE: VS Code 1.68.1 (Universal)
- Node: v18.1.0
- Svelte: v3.48.0 
- Svelte for VS Code: v105.18.1
