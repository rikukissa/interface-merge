<script lang="ts">
  const defaultInterface = `interface Foo {
  bar: Bar
}

interface Bar {
  hello: string;
}
`;

  import { mergeInterfaces } from "./mergeInterfaces";

  let initialValue = location.hash
    ? decodeURIComponent(location.hash.substr(1))
    : defaultInterface;

  let merged = "";
  merged = mergeInterfaces(initialValue);

  function onInterfacesChanged(event: Event) {
    const value = (event.target as HTMLTextAreaElement).value;
    location.hash = value;
    merged = mergeInterfaces(value);
  }
</script>

<main>
  <textarea value={initialValue} on:change={onInterfacesChanged} />
  <textarea>{merged}</textarea>
</main>

<style>
  main {
    height: 100%;
    padding: 1rem;
    background: #ccc;
    display: flex;
    box-sizing: border-box;
    flex-direction: column;
    gap: 1rem;
  }
  textarea {
    flex-grow: 1;
    margin: 0;
    padding: 0;
    border: 0;
    box-sizing: border-box;
    padding: 5px;
  }
</style>
