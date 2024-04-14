<script>
	import { authStore, authHandlers } from './../../stores/authStore.js';
    import AuthReset from '../../components/AuthReset.svelte'

    let email;
    authStore.subscribe((curr) => {
        email = curr?.currentUser?.email
    })
</script>

{#if $authStore.currentUser}
    <div class="flex flex-col justify-center items-center my-auto">
        <h1 class="text-xl font-light text-center">Current user: {email}</h1>
        <AuthReset />
        <button class="mt-4 px-2 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white" on:click={authHandlers.logout}>Logout</button>
    </div>
{:else}
    <div class="flex flex-col justify-center items-center my-auto">
        <h1 class="text-xl font-semibold text-center">Loading...</h1>
    </div>
{/if}