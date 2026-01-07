<script>
// Source - https://stackoverflow.com/a
// Posted by pasta64
// Retrieved 2025-12-17, License - CC BY-SA 4.0
import '@fortawesome/fontawesome-free/css/all.min.css'
import { writable } from 'svelte/store';
import { browser } from '$app/environment';

export const isDarkMode = writable(
    browser ? localStorage.getItem('theme') !== 'light' : true
)

function toggleTheme() {
    isDarkMode.update(dark => {
        const newValue = !dark;
        if (browser) {
            localStorage.setItem('theme', newValue ? 'dark' : 'light');
            document.documentElement.classList.toggle('light-mode', !newValue);
        }
        return newValue;
    })
}

if (browser) {
    const isLight = localStorage.getItem('theme') === 'light';
    document.documentElement.classList.toggle('light-mode', isLight);
}
</script>

<div class="p-6 w-full flex justify-between">
    <h1 class="text-xl cursor-pointer"><a href="/">Tanish Khadse</a></h1>
    <div>
        <ul class="flex flex-row text-lg space-x-4 ">
            <!-- Theme Toggle Button -->
            <li>
                <button 
                    on:click={toggleTheme}
                    class="cursor-pointer text-xl hover:opacity-80 transition"
                    title={$isDarkMode ? "Switch to light mode" : "Switch to dark mode"}
                    aria-label="Toggle theme"
                >
                    {#if $isDarkMode}
                        <i class="fa-solid fa-sun"></i>
                    {:else}
                        <i class="fa-regular fa-moon"></i>
                    {/if}
                </button>
            </li>
            <li>
                <a href="/compiler" title="blog" class="transition hover:border-b">
                    blog
                </a>
            </li>
            <li>
                <a href="https://www.linkedin.com/in/tkhadse/" title="linkedin">
                    <i class="fa-brands fa-linkedin cursor-pointer text-2xl"></i>
                </a>
            </li>
            <li>
                <a href="https://github.com/tkhdse" title="github">
                    <i class="fa-brands fa-github cursor-pointer text-2xl"></i>
                </a>
            </li>
        </ul>
    </div>
</div>