<script setup>
 //這是ESModules 的運用(import匯入一個元件去使用)
  import VueComponent from "./components/VueComponent.vue";

  //js可以直接渲染到畫面
  const text = '一句話';

  //vue可以雙向綁定  
  import {ref } from 'vue';
  const text2 = ref('一兩句話');  //定義vue的資料使用

  //關注點分離, 要把資料抽出來, 由資料驅動畫面
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

  //Reactivet的用法跟缺點
  import { reactive } from 'vue';
  let test = reactive({
    name :'卡斯柏'
  })
  //1. 不能使用純值 (value cannot be made reactive)
  //const test2 = reactive('123')
  //2. 不能重新被賦值
  //AJAX
  test = {
    name:'杰倫'
  }

  //ref的用法跟缺點,存取值都要加上.value
  const num = ref(0)
  //setInterval(() => {
  //  num.value+=1
  //}, 100);
  console.log(todos.value);
  console.log(todos.value[0].nname);
</script>
<template>
  <h1>目前是App.vue</h1>
  <div>----------------------------------------------------------------</div>
  <div>js可以直接渲染到畫面</div>
  <h2>{{text}}</h2>
  <div>----------------------------------------------------------------</div>
  <div>vue可以雙向綁定</div>
  <h2>{{text2}}</h2>
  <input type="text" v-model="text2">
  <div>----------------------------------------------------------------</div>
  <VueComponent></VueComponent>
  <div>----------------------------------------------------------------</div>
  <div>一般table範例</div>
  <table>
  <thead>
    <tr>
      <th>代辦事項名稱</th>
      <th>到期日</th>
      <th>是否已完成</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>購買雜貨</td>
      <td>2024-07-30</td>
      <td>是</td>
    </tr>
    <tr>
      <td>完成報告</td>
      <td>2024-08-01</td>
      <td>否</td>
    </tr>
    <tr>
      <td>清理房間</td>
      <td>2024-07-28</td>
      <td>是</td>
    </tr>
    <tr>
      <td>計劃假期</td>
      <td>2024-08-05</td>
      <td>否</td>
    </tr>
    <tr>
      <td>處理稅務</td>
      <td>2024-08-10</td>
      <td>否</td>
    </tr>
  </tbody>
  </table>
  <br>
  <div>----------------------------------------------------------------</div>
  <div>關注點分離範例</div>
  <table>
  <thead>
    <tr>
      <th>代辦事項名稱</th>
      <th>到期日</th>
      <th>是否已完成</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="todo in todos" :key="todo.id">
      <td>{{todo.nname}}</td>
      <td>{{todo.dueDate}}</td>
      <td>{{todo.complete ? '是': '否'}}</td>
    </tr>
  </tbody>
  </table>
  <div>----------------------------------------------------------------</div>
  <div>Reactivet範例</div>
  <h2>{{test.name}}</h2>
  <input type="text" v-model="test.name">
  <div>----------------------------------------------------------------</div>
  <div>Ref範例</div>
  {{ num }} - <input type="number" v-model="num">

</template>

<style>
</style>   