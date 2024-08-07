<script setup>
    import { ref } from 'vue'; 
    const items = ref([
    {
      id: 1,
      name: '珍珠奶茶',
      des: '香濃奶茶搭配QQ珍珠',
      price : 50,
      stock : 20,
    },
    {
      id: 2,
      name: '冬瓜檸檬',
      des: '清新冬瓜配上新鮮檸檬',
      price : 45,
      stock : 15,
    },
    {
      id: 3,
      name: '翡翠檸檬',
      des: '綠茶與檸檬的完美結合',
      price : 55,
      stock : 30,
    },
    {
      id: 4,
      name: '四季春茶',
      des: '香醇四季春茶，回甘無比',
      price : 45,
      stock : 10,
    },
    {
      id: 5,
      name: '阿薩姆奶茶',
      des: '阿薩姆紅茶搭配香醇鮮奶',
      price : 50,
      stock : 25,
    },
    {
      id: 6,
      name: '檸檬冰茶',
      des: '檸檬與冰茶的清新組合',
      price : 45,
      stock : 20,
    },
    {
      id: 7,
      name: '芒果綠茶',
      des: '芒果與綠茶的獨特風味',
      price : 55,
      stock : 18,
    },
    {
      id: 8,
      name: '抹茶拿鐵',
      des: '抹茶與鮮奶的絕配',
      price : 60,
      stock : 20,
    }
  ])
    const add = (item) =>{
        item.stock++
    }
    const sub = (item) =>{
        if (item.stock > 0)
        item.stock--
    }

    const editingIndex = ref(0)
    const editingName = ref('')
    const comfirm = (item) => {
        if(editingName.value.length>0)
            item.name = editingName.value
        editingIndex.value = 0
    }
    const cancel = () => {
        editingIndex.value = 0
    }
    const edit = (index, item) => {
        editingIndex.value = index
        editingName.value = item
    }
</script>

<template>
    <table>
        <thead>
            <tr>
            <th scope="col">品項</th>
            <th scope="col">描述</th>
            <th scope="col">價格</th>
            <th scope="col">庫存</th>
            </tr>
        </thead>  
        <tbody>
            <tr v-for="item in items" v-bind:key="item.id">
                <div v-if="editingIndex === item.id">
                    <input v-model="editingName" />
                </div>
                <div v-else>{{ item.name }}</div>
                <td><small>{{ item.des }}</small></td>
                <td>{{ item.price}}</td>
                <td><button type="button" @click="sub(item)">-</button>{{item.stock}}
                    <button type="button" @click="add(item)">+</button>
                </td>
                <div v-if="editingIndex === item.id">
                    <button @click="comfirm(item)">儲存</button>
                    <button @click="cancel">取消</button>
                </div>
                <div v-else>
                    <button @click="edit(item.id, item.name)">編輯</button>
                </div>
            </tr>
        </tbody>
    </table>
</template>
 
<style>
</style>  