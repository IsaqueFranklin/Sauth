<script>
    let register = false;
</script>

<div class="flex flex-col items-center justify-center my-auto">
    <h1 class="text-3xl font-light mb-4">Sign up</h1>
    <form class="flex flex-col">
        <label class="mb-4">
            <input class="px-2 py-2 border border-gray-800" type="text" placeholder="Email" />
        </label>
        <label class="mb-4">
            <input class="px-2 py-2 border border-gray-800" type="password" placeholder="Password" />
        </label>
        {#if register}
        <label class="mb-4">
            <input class="px-2 py-2 border border-gray-800" type="password" placeholder="Confirm password" />
        </label>
        {/if}
        <button class="px-1 py-2 border border-gray-800 hover:bg-gray-800 hover:text-white">Submit</button>
    </form>
</div>