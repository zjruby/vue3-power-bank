<template>
    <div>
        <button @click="fetchData">获取数据</button>
        <p v-if="data">{{ data.message }}</p>
    </div>
</template>
<script lang="ts">
export default {
    name: "HelloWorld",
}
</script>
<script lang="ts" setup>
import axios from 'axios'
import { ref } from 'vue'
//定义响应式类型
interface ResopnseData {
    message: string
}
//定义响应式数据
const data = ref<ResopnseData | null>()
const fetchData = async () => {
    try {
        const response = await axios.get<ResopnseData>('http://localhost:3001')
        data.value = response.data
    }
    catch (error) {
        console.error('出错', error)
    }
}
</script>