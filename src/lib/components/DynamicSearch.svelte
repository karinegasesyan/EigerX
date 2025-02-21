<script>
  let searchTerm = "";
  let filteredItems = [];
  let showDropdown = false;
  let selectedIndex = -1;
  let searchInput; // Reference for focusing

  const searchItems = [
    'In-game bonuses and free spins',
    'Crypto deposit still not credited?',
    'EigerX VIP program overview',
    'Achievements and awards',
    'EigerX loyalty rewards program details',
    'Upcoming events and community challenges',
    'Issues with withdrawals and payment delays?',
    'Exclusive promotions and special offers'
  ];

  function updateSearch(event) {
    searchTerm = event.target.value.trim();
    if (!searchTerm) {
      showDropdown = false;
      filteredItems = [];
    } else {
      filteredItems = searchItems.filter(item =>
        item.toLowerCase().includes(searchTerm.toLowerCase())
      );
      showDropdown = filteredItems.length > 0;
    }
    selectedIndex = -1;
  }

  function selectItem(item) {
    searchTerm = item;
    showDropdown = false;
  }

  function handleKeydown(event) {
    if (!showDropdown) return;

    if (event.key === "ArrowDown") {
      selectedIndex = (selectedIndex + 1) % filteredItems.length;
    } else if (event.key === "ArrowUp") {
      selectedIndex = (selectedIndex - 1 + filteredItems.length) % filteredItems.length;
    } else if (event.key === "Enter" && selectedIndex !== -1) {
      selectItem(filteredItems[selectedIndex]);
    }
  }
</script>

<!-- Wrapper with Auto Height -->
<div class="flex flex-col bg-[var(--color-general-black)] border-[var(--color-general)] p-2 mt-3 rounded-[10px] w-full max-w-md">
  
  <!-- Search Input -->
  <div class="relative flex items-center bg-[var(--color-dark-gray)] rounded-[8px] px-2">
    <input
      type="text"
      class="w-full border-0 bg-transparent text-[var(--color-light-gray)] font-inter text-sm font-semibold placeholder-[var(--color-light-gray)] 
      pl-10 py-2 focus:outline-none"
      style="padding: 10px 32px 10px 12px; min-height: 40px; transition: height 0.2s;"
      placeholder="Search for help"
      bind:value={searchTerm}
      bind:this={searchInput}
      on:input={updateSearch}
      on:keydown={handleKeydown}
      aria-haspopup="listbox"
      aria-expanded={showDropdown}
      aria-controls="suggestions"
      role="combobox"
    />

    <!-- Search Icon -->
    <button
      class="absolute right-2 top-1/2 transform -translate-y-1/2 transition-transform duration-300 hover:scale-125 hover:rotate-12 cursor-pointer"
      on:click={() => searchInput.focus()}  
      aria-label="Search"
    >
      <img src="/src/images/search.svg" alt="Search Icon" class="h-5 w-5 object-contain transition-transform duration-300" />
    </button>
  </div>

  <!-- Suggestions Dropdown (Animated) -->
  {#if showDropdown}
    <ul 
      id="suggestions"
      class="w-full max-h-[160px] overflow-y-auto shadow-lg py-2 mt-2 z-20
        bg-[var(--color-general-black)] border-0] 
        opacity-0 scale-95 translate-y-[-5px] transition-all duration-300 ease-out
        animate-fade-slide scrollbar-thin"
      role="listbox"
    >
      {#each filteredItems as item, index}
        <li role="option" aria-selected={selectedIndex === index} class="rounded-[8px]">
          <button
            class={`w-full flex items-center justify-between p-[10px_12px] text-left cursor-pointer font-inter text-sm font-normal text-[var(--color-light-gray)] 
              leading-[14px] transition duration-300 ease-in-out group 
              ${selectedIndex === index ? 'bg-[var(--color-primary)] text-[var(--color-white)]' : 'hover:text-[var(--color-gray)]'}`}
            on:click={() => selectItem(item)}
          >
            <span>{item}</span>
            <div class="flex-shrink-0 transform transition-transform duration-300 ease-out group-hover:translate-x-2 group-hover:opacity-80 group-focus-within:translate-x-2">
              <img src="src/images/right-arrow.svg" alt="Arrow Icon" class="object-contain" />
            </div>            
          </button>
        </li>
      {/each}
    </ul>
  {/if}
</div>

