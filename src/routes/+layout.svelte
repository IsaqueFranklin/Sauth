<script>
    import {onMount} from 'svelte';
    import {auth} from '../lib/firebase/firebase.client';
    import {authStore} from '../stores/authStore';
    import "../app.css";
    import { browser } from '$app/environment';

    onMount(() => {
        const unsubscribe = auth.onAuthStateChanged(user => {
            console.log(user)
            authStore.update((curr) => {
                return {...curr, isLoading: false, currentUser: user};
            })

            if (browser && !$authStore?.currentUser && !$authStore.isLoading && window.location.pathname !== '/'){
                window.location.href = '/';
            }
        })
        return unsubscribe;
    })
</script>

<main class="min-h-screen flex flex-col">
    <slot />
</main>