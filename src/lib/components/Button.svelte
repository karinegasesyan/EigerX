<div class="relative mt-3 mb-3">
    <button 
        type="submit" 
        aria-label="Send us a message" 
        class="relative flex flex-col w-full px-4 md:px-5 py-3 md:py-4 rounded-[10px] gap-2 bg-transparent border border-[var(--color-primary)] transition-all duration-300 group cursor-pointer focus:outline-none focus:ring-2 focus:ring-[var(--color-primary)]"
    >
        <p class="font-inter text-sm md:text-base font-semibold text-[var(--color-white)] leading-[14px] group-hover:text-[var(--color-white)]">
            Send us a message
        </p>
        <span class="font-inter text-sm md:text-base font-normal text-[var(--color-gray)] leading-[14px] group-hover:text-[var(--color-white)]">
            We typically reply within a day
        </span>
        
        <!-- Positioned Image with Hover Animation -->
        <div class="absolute right-5 top-1/2 transform -translate-y-1/2 transition-transform duration-300 group-hover:translate-x-2 group-hover:scale-110">
            <img src="src/images/send.svg" alt="Send Icon" class="object-contain" loading="lazy">
        </div>
    </button>
</div>
