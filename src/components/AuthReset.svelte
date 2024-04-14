<script>
	import { authHandlers, authStore } from './../stores/authStore.js';
    let action = '';
    let newEmail = '';
    let newPass = '';

    async function handleSubmit() {
        if (!action) {
            return
        }

        if (action === 'updatePass'){
            return await authHandlers.updatePassword(newPass);
        }

        if (action === 'updateEmail'){
            console.log(newEmail)
            return await authHandlers.updateEmail(newEmail);
        }
    }
</script>

<div class="flex flex-col items-center justify-center my-auto">
    <div class="my-4">
        <button class="px-2 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white" on:click={() => {
            action = 'updateEmail'
        }}>Update email</button>
        <button class="px-2 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white" on:click={() => {
            action = 'updatePass'
        }}>Update password</button>
    </div>
    {#if action === 'updateEmail'}
        <form class="flex flex-col">
            <label class="mb-4">
                <input bind:value={newEmail} class="px-2 py-2 border border-gray-800" type="email" placeholder="New Email" />
            </label>
            <button on:click={handleSubmit} class="px-1 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white">Submit</button>
        </form> 
    {/if}

    {#if action === 'updatePass'}
        <form class="flex flex-col">
            <label class="mb-4">
                <input bind:value={newPass} class="px-2 py-2 border border-gray-800" type="password" placeholder="New Password" />
            </label>
            <button on:click={handleSubmit} class="px-1 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white">Submit</button>
        </form> 
    {/if}
</div>