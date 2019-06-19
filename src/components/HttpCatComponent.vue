<template>
    <div>
        <div>
            <h2>{{ message }}:</h2>
            <select v-model="status">
                <option v-for="item in statusList" :key="item.code" :value="item.code">
                    {{ item.code }} - {{ item.message }}
                </option>
            </select>
        </div>
        <div>
            <img :src="`https://http.cat/${status}`">
        </div>
    </div>
</template>

<script>
import http from '../http.js'
export default {
    data() {
        return {
            status: 200,
            statusList: http.statusList
        }
    },

    computed: {
        message() {
            return this.statusList.find(item => item.code === this.status).message
        }
    },
}
</script>
