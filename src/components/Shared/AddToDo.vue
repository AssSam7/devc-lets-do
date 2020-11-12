<template>
  <form class="add__panel">
    <input type="text" class="add__input" placeholder="add details" />
    <button type="submit" class="add__btn">Add</button>
  </form>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.add {
  &__panel {
    display: flex;
    justify-content: space-between;
    align-items: stretch;
  }

  &__input {
    flex: 0 0 82%;

    border: 0;
    outline: none;
    border: 1px solid #bdbdbd;
    border-radius: 12px;
    text-indent: 1rem;
    color: #828282;

    &::placeholder {
      color: #828282;
    }
  }

  &__btn {
    padding: 2rem 5rem;
    border: 0;
    outline: none;
    background: #2f80ed;
    box-shadow: 0px 2px 6px rgba(127, 177, 243, 0.4);
    border-radius: 12px;
    font-weight: 600;
    font-size: 14px;
    line-height: 17px;

    color: #ffffff;
  }
}
</style>
