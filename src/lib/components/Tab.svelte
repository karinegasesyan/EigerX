<script>
  import DynamicSearch from '$lib/components/DynamicSearch.svelte';
  import Header from "$lib/components/Header.svelte";
  import Button from "$lib/components/Button.svelte";

  let activeTab = "home";
  let contentRef;

  const setActiveTab = (tab) => {
      activeTab = tab;
      contentRef?.scrollIntoView({ behavior: "smooth", block: "start" });
  };
</script>

<!-- Tab Content - Scrolls to Top on Change -->
<div class="flex-1" bind:this={contentRef}>
  {#if activeTab === 'home'}
    <Header />
    <Button />
    <DynamicSearch />
  {:else if activeTab === 'message'}
  <Header />
    <p class="flex justify-center space-x-4 text-[var(--color-white)]">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry. 
      Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
      when an unknown printer took a galley of type and scrambled it to make a type specimen book. 
      It has survived not only five centuries, but also the leap into electronic typesetting, 
      remaining essentially unchanged. It was popularised in the 1960s with the release of 
      Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing 
      software like Aldus PageMaker including versions of Lorem Ipsum.
    </p>
  {:else}
      <Header />
  <p class="flex justify-center space-x-4 text-[var(--color-white)]">
    It is a long established fact that a reader will be distracted by the readable
     content of a page when looking at its layout. The point of using 
     Lorem Ipsum is that it has a more-or-less normal distribution of letters, 
     as opposed to using 'Content here, content here', making it look like readable English. 
     Many desktop publishing packages and web page editors now use Lorem Ipsum as their default
    model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. 
    Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
  </p>
  {/if}
</div>

<!-- Tab Navigation with Background Color and Additional Styles -->
<div class="flex justify-center space-x-4 bg-[var(--color-general-black)] border-[var(--color-general)] py-2 rounded-[8px]">
  <button 
    class="flex-1 flex flex-col items-center py-2 px-6 font-inter text-sm font-normal transition-all duration-300 cursor-pointer hover:text-[var(--color-primary)] active:text-[var(--color-primary)] {activeTab === 'home' ? 'text-[var(--color-primary)]' : 'text-[var(--color-light-gray)]'}"
    on:click={() => setActiveTab("home")}
  >
    <img 
    src={activeTab === 'home' ? './src/images/home-active.svg' : './src/images/home.svg'} 
    alt="Home Icon" 
     class="mb-1 transition-all duration-300"
  />
    Home
  </button>

  <button 
    class="flex-1 flex flex-col items-center py-2 px-6 font-inter text-sm font-normal transition-all duration-300 cursor-pointer active:text-[var(--color-primary)] {activeTab === 'message' ? 'text-[var(--color-primary)]' : 'text-[var(--color-light-gray)]'}"
    on:click={() => setActiveTab("message")}
  >

    <img 
    src={activeTab === 'message' ? './src/images/message-active.svg' : './src/images/message.svg'} 
    alt="Message Icon" 
     class="mb-1 transition-all duration-300"
  />
    Message
  </button>

  <button 
    class="flex-1 flex flex-col items-center py-2 px-6 font-inter text-sm font-normal transition-all duration-300 cursor-pointer active:text-[var(--color-primary)] {activeTab === 'help' ? 'text-[var(--color-primary)]' : 'text-[var(--color-light-gray)]'}"
    on:click={() => setActiveTab("help")}
  >
  <img 
  src={activeTab === 'help' ? './src/images/help-active.svg' : './src/images/help.svg'} 
  alt="Help Icon" 
   class="mb-1 transition-all duration-300"
/>
    Help
  </button>
</div>
