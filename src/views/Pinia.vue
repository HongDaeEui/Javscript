<script setup>
import {computed, ref} from "vue";
import {useListStore} from "@/stores/list";

const text = ref("")
const list = useListStore()

const addList = () => {
    if (!text.value) return
    list.addList(text.value)
    text.value = ""
}

const getDataAll = computed(() =>
    list.getDataAll)

for (const [index, value] of [1, 2, 3, 4, 5].entries()) {
    console.log(index, value);
}



</script>


<template>
    <div>
        <input type="text" v-model="text"/>
        <button @click="addList(text)">추가</button>
        <h4>추가된 목록</h4>
        <p v-for="(item, index) in getDataAll" :key="index">
            {{ item }}
        </p>
    </div>
</template>