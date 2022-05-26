<template>
  <main>
      <div class="loaddingMask" v-if="$store.state.isLoading"> Loading...</div>
    <Header class="header"></Header>
    <div class="container">
      <div class="todoListArea">
        <ToDoList></ToDoList>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  components: {
    ToDoList: () => import("../components/ToDoList"),
    Header: () => import("../components/Header"),
  },
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    isLoading() {
        console.log($store.state.isLoading)
    },
  },
};
</script>
<style>
main {
  background-color: #f8f8f8;
}

.loaddingMask{
    width:100%;
    height:100%;
    position: fixed;
    top:0;
    z-index: 10;
    background: gray;
    display: flex;
    justify-content: center;
    align-items:center;
    opacity: 0.5;
    font-size: 3rem;
}

.header {
  position: fixed;
  top: 0;
}

.container {
     position: fixed;
    top: 5rem;
    background-color: #f8f8f8;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.todoListArea{
    height: calc(90vh - 5rem);
    width:80%;
}

</style>
