<script>
    import {onMount} from 'svelte';
    import {auth} from '../lib/firebase/firebase.client';
    import {authStore} from '../stores/authStore';
    import "../app.css";

    onMount(() => {
        const unsubscribe = auth.onAuthStateChanged(user => {
            console.log(user)
            authStore.update((curr) => {
                return {...curr, isLoading: false, currentUser: user};
            })
        })
    })
</script>

<main class="min-h-screen flex flex-col">
    <slot />
</main>