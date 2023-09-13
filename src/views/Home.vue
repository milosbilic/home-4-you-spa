<template>
    <div class="container mt-5 text-center">
        <h3>Home 4 You: Where Happiness Finds Its Perfect Address</h3>
        <h3>{{ message }}</h3>
    </div>
</template>

<script lang="ts">
    import { ref } from "vue";
    
    export default {
        name: "Home",
        setup() {
            const message = ref('You are not logged in');

            // onMounted()

            return {
                message
            }
        }
    }
</script>