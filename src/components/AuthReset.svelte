<script>
	import { authHandlers, authStore } from './../stores/authStore.js';
    let action = '';
    let email = '';
    let password = '';
    let confirmPassword = '';

    async function handleSubmit() {
        if (!email || !password || (register && !confirmPassword)) {
            return
        }

        if (register && password === confirmPassword) {
            try {
                await authHandlers.signup(email, password);
            } catch(err) {
                console.log(err)
            }
        } else {
            try {
                await authHandlers.login(email, password);
            } catch(err) {
                console.log(err)
            }
        }

        if ($authStore.currentUser) {
            window.location.href = '/privatedashboard';
        }
    }
</script>

<div class="flex flex-col items-center justify-center my-auto">
    <div>
        
    </div>
    <form class="flex flex-col">
        <label class="mb-4">
            <input bind:value={email} class="px-2 py-2 border border-gray-800" type="email" placeholder="Email" />
        </label>
        <label class="mb-4">
            <input bind:value={password} class="px-2 py-2 border border-gray-800" type="password" placeholder="Password" />
        </label>
        {#if register}
        <label class="mb-4">
            <input bind:value={confirmPassword} class="px-2 py-2 border border-gray-800" type="password" placeholder="Confirm password" />
        </label>
        {/if}
        <button on:click={handleSubmit} class="px-1 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white">Submit</button>
    </form> 
</div>