<template>
    <main class="form-signin w-100 m-auto">
        <form @submit.prevent="submit">
            <h1 class="h3 mb-3 fw-normal">Sign up to Home 4 You</h1>

            <div class="form-floating">
                <input v-model="data.email" type="email" class="form-control" id="email" placeholder="name@example.com">
                <label for="email">Email address</label>
            </div>
            <div class="form-floating">
                <input v-model="data.firstName" class="form-control" placeholder="name@example.com">
                <label for="firstName">First name</label>
            </div>
            <div class="form-floating">
                <input v-model="data.lastName" class="form-control" placeholder="name@example.com">
                <label for="lastName">Last name</label>
            </div>
            <div class="form-floating">
                <input v-model="data.phone" class="form-control" placeholder="name@example.com">
                <label for="phone">Phone</label>
            </div>
            <div class="form-floating">
                <input v-model="data.password" type="password" class="form-control" id="floatingPassword"
                    placeholder="Password">
                <label for="floatingPassword">Password</label>
            </div>
            <div class="form-floating">
                <input v-model="data.repeatedPassword" type="password" class="form-control" id="floatingPassword"
                    placeholder="Password">
                <label for="floatingPassword">Repeat password</label>
            </div>

            <button class="w-100 btn btn-lg btn-primary" type="submit">Sign in</button>
        </form>
    </main>
</template>

<script>
import { reactive } from "vue";
import axios from 'axios';
import { useRouter } from "vue-router";
export default {
    name: "Register",
    setup() {
        const data = reactive({
            firstName: '',
            lastName: '',
            email:'',
            phone: '',
            password: '',
            repeatedPassword: '',
            role: 'ROLE_USER'
        });

        const router = useRouter();

        const submit = async() => {
            await axios.post("http://localhost:8000/api/users", data);

            await router.push('/login');
        }

        return {
            data,
            submit
        }
    }
}
</script>