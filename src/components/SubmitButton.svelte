<script>
  export let text = "Send";
  export let color = "blue";
</script>

<button class="btn" style="background-color: {color};">
  {text}
</button>

<style>
    .btn {
        width: fit-content;
        display: inline-block; 
        border: none;
        border-radius: 50px;
        padding: 10px 40px;
        background-color: #2c2f47;
        color: rgba(255, 255, 255, 0.7);    
        font-weight: 400px;
        font-size: 18px;
        line-height: 21.6px;
    }
</style>