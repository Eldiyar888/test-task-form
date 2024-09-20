<script>
  export let label;
  export let required = false;
  export let value;
  export let errorMessage = "";
  export let type = "text";

  let inputElement;

  $: inputElement && (inputElement.type = type);
</script>

<div class="wrapper">
  <label>{label}{required ? '*' : ''}</label>
  <input bind:this={inputElement} bind:value={value} required={required} />
  {#if errorMessage}
    <span class="error">{errorMessage}</span>
  {/if}
</div>

<style>
  .error {
    color: red;
    font-size: 0.8rem;
  }

  .wrapper {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  label {
    font-weight: 300;
    font-size: 15px;
    line-height: 18px;
    color: rgba(121, 126, 163, 1);
  }

  input {
    border: none; 
    border-bottom: 1px solid rgba(63, 67, 99, 1);
    padding: 0 0 6px 0; 
    font-size: 16px; 
    outline: none; 
    background-color: transparent;
    color: #fff;
  }

  input:focus {
    border-bottom: 1px solid rgba(255, 255, 255, 1);
  }

  .wrapper:focus-within label {
    color: rgba(255, 255, 255, 1);
  }
</style>