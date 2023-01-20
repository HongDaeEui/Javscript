<script setup>
const search = ref("")
const names = ref(['aa', 'bb', 'cc', 'dd'])

const matchingNames = computed(() => {
    return names.value.filter(name => name.includes(search.value))
})

watch(search, () => {
    "search 값이 바뀔 때 마다 실행되는 함수";
})

watchEffect(() => {
    console.log(
        "search value가 정의됬기에 search가 바뀔때마다 실행된다",
        search.value,
    )
})


</script>


<template>
    <div class="about">

        <h1>unplugin-auto-import 사용</h1>
        <input type="text" v-model="search"/>
        <p>{{ search }}</p>
        <div v-for="name in matchingNames" :key="name">
            {{ name }}
        </div>
    </div>
</template>

<style>
@media (min-width: 1024px) {
    .about {
        min-height: 100vh;
        display: flex;
        align-items: center;
    }
}
</style>