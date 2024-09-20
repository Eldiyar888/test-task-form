<script>
  export let message = "";
  export let onClose;

  const handleClickOutside = (event) => {
    if (event.target === event.currentTarget) {
      onClose();
    }
  };

  setTimeout(onClose, 5000);
</script>

<div class="notification" on:click={handleClickOutside}>
  <p>{message}</p>
  <button on:click={onClose}>Закрыть</button>
</div>

<style>
  .notification {
    position: fixed;
    top: 20px;
    right: 20px;
    background-color: rgba(23, 25, 41, 1);
    color: white;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  }
  button {
    background: none;
    border: none;
    color: white;
    cursor: pointer;
    padding: 0;
    margin-top: 10px;
  }
</style>