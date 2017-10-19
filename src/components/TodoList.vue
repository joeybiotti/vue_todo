<template>
<div>
  <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
  <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
  <todo v-for="todo in todos" v-bind:todo="todo"></todo>
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
};
