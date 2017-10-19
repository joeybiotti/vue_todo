<template>
<div>
  <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
  <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
  <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo"></todo>
  <div class='ui centered card' v-for="todo in todos">
    <div class='content'>
      <div class='header'>
        {{ todo.title }}
      </div>
      <div class='meta'>
        {{ todo.project }}
      </div>
      <div class='extra content'>
        <span class='right floated edit icon'>
            <i class='edit icon'></i>
          </span>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="todo.done">
      Completed
    </div>
    <div class='ui bottom attached red basic button' v-show="!todo.done">
      Complete
    </div>
  </div>
</div>
</template>

<script type = "text/javascript" >

import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(){
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
  },
    completeTodo() {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  },
};
