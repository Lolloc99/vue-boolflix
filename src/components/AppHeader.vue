<template>
  <header>
    <img src="../assets/img/logo-netflix-fake.png" alt="Fakeflix" />
    <div class="searchbar">
      <input
        type="text"
        placeholder="Scrivi un titolo..."
        v-model="inputText"
      />
      <button @click="$emit('search', inputText)">Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",

  data: function () {
    return {
      inputText: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem;
  background-color: black;
  border-bottom: 1px solid lightgrey;

  h1 {
    font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS",
      sans-serif;
    color: #e2090c;
  }

  img {
    width: 10%;
  }
}

.searchbar {
  button {
    margin-left: 1rem;
    padding: 0.3rem;
    color: white;
    border: 1px solid black;
    background-color: #e2090c;
    cursor: pointer;
  }

  button:active {
    border: 1px solid #e2090c;
    background-color: black;
  }

  input {
    padding: 0.3rem;
    color: white;
    border: 2px solid #e2090c;
    background-color: black;
  }
}
</style>
