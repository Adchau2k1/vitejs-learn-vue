<script setup>
import { ref, reactive } from 'vue'

const input = ref('')
const counter = reactive({
    count: 0,
})
const countId = setInterval(() => counter.count++, 1000)
const list = [
    {
        id: 1,
        title: 'Item 1',
    },
    {
        id: 2,
        title: 'Item 2',
    },
    {
        id: 3,
        title: 'Item 3',
    },
]

const handleStop = (id) => clearInterval(id)
const handleChangeInput = (e) => (input.value = e.target.value)
</script>

<template>
    <p class="number">Đếm: {{ counter.count }}</p>
    <button type="button" @click="handleStop(countId)">Dừng</button>

    <input class="input" :value="input" @input="handleChangeInput" />
    <p v-if="input">Giá trị: {{ input }}</p>
    <p v-else>Input trống</p>

    <ul class="mt-10">
        <li v-for="item in list" :key="item.id">{{ item.title }}</li>
    </ul>
</template>

<style>
.number {
    font-size: 30px;
    color: green;
    font-weight: 700;
}

.input {
    display: block;
    margin-top: 20px;
}
</style>
