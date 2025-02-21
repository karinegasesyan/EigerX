<div class="flex flex-col">
    <div class="flex flex-row w-full items-center pt-5 pr-5 pl-5 mb-[100px]">
        <!-- Logo -->
        <div class="w-[110px] h-[40px]">
            <img src="src/images/logo.svg" alt="Logo" class="w-full h-full object-contain">
        </div>
    
        <!-- User Avatars (Overlapping with Z-Index) -->
        <div class="flex ml-auto space-x-[-8px]">
            {#each [1, 2, 3] as user, index}
                <img src={`src/images/user-${user}.svg`} alt={`User ${user} Avatar`} 
                     class={`w-10 h-10 rounded-full border-2 border-[var(--color-general)] z-${3 - index} 
                     transition-transform duration-300 ease-in-out hover:scale-120 hover:border-[var(--color-primary)]`}>
            {/each}
        </div>
    </div>
    
    <div class="flex flex-col pr-5 pl-5 pt-0">
        <h1 class="font-sfpro-medium text-[32px] leading-[38px] tracking-[0] text-[var(--color-white)] opacity-70">
            Hello there
        </h1>
        <h1 class="font-sfpro-medium text-[32px] leading-[38px] tracking-[0] text-[var(--color-white)]">
            How can we help?
        </h1>
    </div>
</div>
