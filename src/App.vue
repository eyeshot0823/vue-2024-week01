<script setup>
import { ref } from 'vue'
const stock = ref([
    {
        id: 1,
        name: '珍珠奶茶',
        description: '香濃奶茶搭配QQ珍珠',
        price: 50,
        stock: 20,
        edit: 1
    },
    {
        id: 2,
        name: '冬瓜檸檬',
        description: '清新冬瓜配上新鮮檸檬',
        price: 45,
        stock: 18,
        edit: 0
    },
    {
        id: 3,
        name: '翡翠檸檬',
        description: '綠茶與檸檬的完美結合',
        price: 55,
        stock: 34,
        edit: 0
    },
    {
        id: 4,
        name: '四季春茶',
        description: '香醇四季春茶，回甘無比',
        price: 45,
        stock: 10,
        edit: 0
    },
    {
        id: 5,
        name: '阿薩姆奶茶',
        description: '阿薩姆紅茶搭配香醇鮮奶',
        price: 50,
        stock: 25,
        edit: 0
    },
    {
        id: 6,
        name: '檸檬冰茶',
        description: '檸檬與冰茶的清新組合',
        price: 45,
        stock: 20,
        edit: 0
    },
    {
        id: 7,
        name: '芒果綠茶',
        description: '芒果與綠茶的獨特風味',
        price: 55,
        stock: 18,
        edit: 0
    },
    {
        id: 8,
        name: '抹茶拿鐵',
        description: '抹茶與鮮奶的絕配',
        price: 60,
        stock: 20,
        edit: 0
    }
]);

const stockUp = (id) => {
    stock.value[id - 1].stock = stock.value[id - 1].stock + 1
};
const stockDown = (id) => {
    stock.value[id - 1].stock = stock.value[id - 1].stock - 1
};

const editName = (id) => {
    const index = stock.value.findIndex(item => item.id === id);
    stock.value[index].edit = 1
}

const saveName = (id) => {
    const index = stock.value.findIndex(item => item.id === id);
    stock.value[index].edit = 0
}

</script>

<template>
    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Vue-2024-week01 - by Discode Eric0823</title>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
            integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
    </head>

    <body>
        <div class="container">
            <h1 class="mb-5">Vue-2024-week01</h1>
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th scope="col">品項</th>
                        <th scope="col">描述</th>
                        <th scope="col">價格</th>
                        <th scope="col">庫存</th>
                        <th scope="col" width="200">功能</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in stock" :key="item.id">
                        <td>{{ item.name }}</td>
                        <td><small>{{ item.description }}</small></td>
                        <td>{{ item.price }}</td>
                        <td>
                            <button type="button" class="btn btn-sm btn-outline-dark mr-2"
                                @click="stockDown(item.id)">-</button>
                            {{ item.stock }}
                            <button type="button" class="btn btn-sm btn-outline-dark ml-2"
                                @click="stockUp(item.id)">+</button>
                        </td>
                        <td>
                            <div class="input-group mb-3" v-if="item.edit">
                                <input type="text" class="form-control" placeholder="輸入品名..."
                                    aria-describedby="button-addon" v-model="item.name">
                                <div class="input-group-append">
                                    <button class="btn btn-outline-secondary" type="button" id="button-addon"
                                        @click="saveName(item.id)">修改</button>
                                </div>
                            </div>
                            <button type="button" class="btn btn-sm btn-outline-dark" v-if="item.edit == 0"
                                @click="editName(item.id)">修改品名</button>
                        </td>
                    </tr>
                </tbody>
            </table>
            <hr>
            <div class="text-right">By Discord Eric0823.</div>
        </div>

    </body>

    </html>
</template>

<style scoped>
th,
td,
h1 {
    text-align: center;
}
</style>
