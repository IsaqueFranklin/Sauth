<script>
	import { authStore } from './../../stores/authStore.js';

    let email;
    authStore.subscribe((curr) => {
        email = curr?.currentUser?.email
    })
</script>

{#if $authStore.currentUser}
    <div class="flex flex-col justify-center items-center my-auto">
        <h1 class="text-xl font-light text-center">Current user: {email}</h1>
        <form>
            
        </form>
    </div>
{:else}
    <div class="flex flex-col justify-center items-center my-auto">
        <h1 class="text-xl font-semibold text-center">Loading...</h1>
    </div>
{/if}