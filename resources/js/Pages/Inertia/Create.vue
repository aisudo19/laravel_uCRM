<script setup>
import { reactive } from 'vue'
// import { Inertia } from '@inertiajs/inertia'
import { router } from '@inertiajs/vue3'

defineProps({
    errors: Object
})
const form = reactive({
    title: null,
    content: null,
})

//storeメソッド呼ぶ
function submitFunction() {
    router.post('/inertia', form)
}

</script>

<template>
<!-- フォームの遷移を防ぐ -->
    <form @submit.prevent="submitFunction">
        <input name="title" type="text" v-model="form.title"><br>
        <div v-if="errors.title">{{ errors.title }}</div>
        <input name="content" type="text" v-model="form.content"><br>
        <div v-if="errors.content">{{ errors.content }}</div>
        <button>送信</button>
    </form>
</template>
