<template>
  <div class="container">
    <header>
      <h1>#todo</h1>
    </header>

    <main class="content">
      <div class="buttons">
        <div class="all">
          <button class="btn btn__all">
            All
          </button>
          <hr />
        </div>
        <div class="active">
          <button class="btn btn__active">
            Active
          </button>
          <hr />
        </div>
        <div class="completed">
          <button class="btn btn__completed">
            Completed
          </button>
          <hr />
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {};
  },
  methods: {

  }
};
</script>

<style lang="scss" scoped>
h1 {
  font-family: "Raleway", sans-serif;
  font-style: normal;
  font-size: 3rem;
  font-weight: 700;
  color: #333333;
  text-align: center;
}

main {
  max-width: 70%;
  padding: 6rem 0;
  margin: auto;
}

.buttons {
  border-bottom: 1px solid #bdbdbd;

  display: flex;
  justify-content: space-around;
}

.btn {
  color: #333333;
  border: 0;
  outline: none;
  background: none;
  padding: 1rem 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Montserrat;
  font-style: normal;
  font-weight: 600;
  font-size: 1.4rem;
}

.all,
.active,
.completed {
  hr {
    height: 2px;
    color: transparent;
    background: #2f80ed;
    border-radius: 4px 4px 0px 0px;
  }
}
</style>
