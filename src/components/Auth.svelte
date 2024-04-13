<script>
    let register = false;

    for (let i = 0; i <= 10; i++) {
        register = !register
        console.log(register)
    }
    console.log(register)
    let email = '';
    let password = '';
    let confirmPassword = '';

    function handleRegister(){
        register = !register;
    }
</script>

<div class="flex flex-col items-center justify-center my-auto">
    {#if register}
        <h1 class="text-3xl font-light mb-4">Register</h1>
    {:else}
        <h1 class="text-3xl font-light mb-4">Login</h1>
    {/if}
    <form class="flex flex-col">
        <label class="mb-4">
            <input bind:value={email} class="px-2 py-2 border border-gray-800" type="text" placeholder="Email" />
        </label>
        <label class="mb-4">
            <input bind:value={password} class="px-2 py-2 border border-gray-800" type="password" placeholder="Password" />
        </label>
        {#if register}
        <label class="mb-4">
            <input bind:value={confirmPassword} class="px-2 py-2 border border-gray-800" type="password" placeholder="Confirm password" />
        </label>
        {/if}
        <button class="px-1 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white">Submit</button>
    </form>
    {#if register}
        <div class="mt-4 text-sm">Already have an account? <button on:click={handleRegister} on:keydown={() => {}}>Login</button></div>
    {:else}
        <div class="mt-4 text-sm">Don't have an account? <button on:click={handleRegister} on:keydown={() => {}}>Register</button></div>
    {/if}
</div>