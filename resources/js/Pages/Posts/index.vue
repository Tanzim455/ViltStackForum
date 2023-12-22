<template>
 <!-- Authuser-{{user}} -->
<Navbar />
<SuccessMessage />
  <div v-for="post in posts.data" :key="post.id">

    <div class="container mx-auto p-6  bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700 space-y-3">
    <Link
    :href="route('post.show',{post:post.slug})"
    >
        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{post.title}}</h5>
    </Link>
    <div class="flex">
        <div v-if="user">
       <Link
       v-if="post.user_id===user.id && user"
        @click="destroy(post.id)"
    class="bg-red-600 text-white px-4 py-1 rounded-md"


    >Delete</Link>
    </div>
   <div v-if="user">



       <Link
        v-if="post.user_id===user.id"
       :href="route('post.edit',{post:post.slug})"
    class="bg-green-600 text-white px-4 py-1 rounded-md"


    >Edit</Link>
    </div>
    </div>
    <Link

       :href="route('user.show',{user: post.user.slug})"
       class="text-blue-600 font-serif pointer"


    >Written by-{{post.user.name}}</Link>
    <Link

       :href="route('categories.show',{category: post.category.slug})"
       class="text-blue-600 font-serif pointer"


    >Category-{{post.category.name}}</Link>



    </div>
</div>

</template>

<script setup>


import Navbar from '../../Layouts/Navbar.vue'
// import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
 import { Link,usePage,router } from '@inertiajs/vue3';
import { computed} from 'vue';
// import { Inertia } from '@inertiajs/vue3';
// import { usePage,router } from '@inertiajs/vue3';
// import { usePage,router} from "@inertiajs/vue3";
import SuccessMessage from '@/Components/SuccessMessage.vue';
// const user = computed(() => usePage().props.value.auth.user)
const user=computed(() => usePage().props.auth.user)
let props = defineProps({
  posts: Object,



});
const destroy=(id)=>{

    router.delete(route("post.destroy",id));
}

</script>

<style>
</style>
