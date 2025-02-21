<script>
    let { children } = $props();
    import "../app.css";
    import Tab from "$lib/components/Tab.svelte";
</script>

<div class="flex items-center justify-center min-h-screen px-4">
    <div style="background: linear-gradient(to bottom, #0B0B0F, #1A1A22E5, #211A1A, #212127);" class="max-w-[400px] w-full mx-auto p-4  border border-[var(--color-general)] rounded-2xl flex flex-col gap-4 shadow-[0_4px_10px_rgba(0,0,0,0.16)]">
        <Tab /> 
    </div>
</div>

