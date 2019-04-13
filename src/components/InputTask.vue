<template>
  <div>
    <div>
      <input class="new-todo"
      @keyup.enter="addTask"
      v-model="taskName"
      placeholder="O que precisa ser feito?" />
    </div>
    <div>
      <ul>
        <li v-for="task in listaDeTarefas" :key="task.id">
          {{ task.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import task from '../models/task';
export default {

  name: 'InputTask',

  data() {
    return {
      taskName:'',
      listaDeTarefas: [],
      count: 0,
    };
  },
  methods: {
    addTask () {
      this.count += 1;
      const tarefa = new task(this.count, this.taskName);
      this.listaDeTarefas.push(tarefa);
    }
  }
};
</script>

<style lang="css" scoped>
.todoapp input::-webkit-input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}
.todoapp input::-moz-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}
.todoapp input::input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}
.new-todo,
.edit {
  position: relative;
  margin: 0;
  width: 100%;
  font-size: 24px;
  font-family: inherit;
  font-weight: inherit;
  line-height: 1.4em;
  border: 0;
  color: inherit;
  padding: 6px;
  border: 1px solid #999;
  box-shadow: inset 0 -1px 5px 0 rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.new-todo {
  padding: 16px 16px 16px 60px;
  border: none;
  background: rgba(0, 0, 0, 0.003);
  box-shadow: inset 0 -2px 1px rgba(0,0,0,0.03);
}
</style>
