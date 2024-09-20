<script>
  export let label;
  export let bindChecked;
</script>

<label>
  <input class="custom-checkbox" id="myCheckbox" type="checkbox" bind:checked={bindChecked} />
    <label for="myCheckbox">
        {label}
    </label>
</label>

<style>
    .custom-checkbox {
        position: absolute;
        z-index: -1;
        opacity: 0;
    }

    .custom-checkbox + label {
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
      font-weight: 300;
    font-size: 15px;
    line-height: 18px;
    color: rgba(121, 126, 163, 1);
}
.custom-checkbox + label::before {
  content: '';
  display: inline-block;
  width: 30px;
  height: 30px;
  flex-shrink: 0;
  flex-grow: 0;
  border: 1.7px solid rgba(63, 67, 99, 1);
  border-radius: 8px;
  margin-right: 0.5em;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: 50% 50%;
  box-sizing: border-box;
}

  .custom-checkbox:checked + label::before {
    background-color: rgba(63, 67, 99, 1);
    background-image: url('/Vector.svg');
  }

</style>