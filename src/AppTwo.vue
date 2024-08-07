<script setup>
  import {ref } from 'vue';
    const text = ref('卡斯柏')
    const num = ref(0)
    const add = () =>{
        num.value++
    }
    const imgS = ref('https://images.unsplash.com/photo-1471922694854-ff1b63b20054?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTl8fG9jZWFufGVufDB8fDB8fHww')

    const todos = ref([
    {
      id: 1,
      nname: '購買雜貨',
      dueDate: '2024-07-30',
      complete : true,
    },
    {
      id: 2,
      nname: '完成報告',
      dueDate: '2024-08-01',
      complete : false,
    },
    {
      id: 3,
      nname: '清理房間',
      dueDate: '2024-07-28',
      complete : true,
    },
    {
      id: 4,
      nname: '計劃假期',
      dueDate: '2024-08-05',
      complete : false,
    },
    {
      id: 5,
      nname: '處理稅務',
      dueDate: '2024-08-10',
      complete : false,
    }
  ])

</script>
<template>
    123
    <h1>{{ text }}</h1>
    <input type="text" v-model="text">
    <h2>{{ num }}</h2>
    <button v-on:click="add">點我</button>
    <!--屬性-->
    <img v-bind:src="imgS" alt="">
    <div>
        <div v-for="todo in todos" v-bind:key="todo.id">
            {{ todo.nname }} <br>
            {{ todo.dueDate }} <br>
            {{ todo.complete?'是':'否' }} <input type="checkbox" v-model="todo.complete">
            <button @click="todo.complete = !todo.complete">切換</button>
            <hr>
        </div>
    </div>
    
    <!--{{  }}可以加入JS Expression-->
</template>

<style>
</style>  