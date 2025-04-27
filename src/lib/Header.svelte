<script lang="ts">
	import { browser } from '$app/environment';
	import { Moon, Sun } from 'phosphor-svelte';

	type Theme = 'dark' | 'light';
	let theme = $state<Theme>('dark');

	const update_theme = (new_theme: Theme, store: boolean = true): void => {
		if (!browser || !new_theme) return;
		theme = new_theme;
		const html = document.documentElement;
		html.dataset.theme = new_theme;
		if (store) localStorage.theme = new_theme;
	};

	if (browser) {
		const stored_theme = localStorage.theme;
		const prefersDarkMode = window.matchMedia('prefers-color-scheme: dark').matches;
		const prefersLightMode = window.matchMedia('prefers-color-scheme: light').matches;

		// Check theme is already present
		if (stored_theme) update_theme(stored_theme, false);

		// Otherwise, check for user preference
		if (!stored_theme && prefersDarkMode) update_theme('dark');
		if (!stored_theme && prefersLightMode) update_theme('light');

		// If nothing is set default to dark mode
		if (!stored_theme && !prefersDarkMode && !prefersLightMode) update_theme('dark');
	}
</script>

<header>
	<div class="branding">
		<span>Anil Kumar</span>
	</div>
	<button
		class="theme-toggle"
		aria-label={theme === 'dark' ? 'Switch to light theme' : 'Switch to dark theme'}
		onclick={() => (theme === 'dark' ? update_theme('light') : update_theme('dark'))}
	>
		{#if theme === 'dark'}
			<Moon size="24" />
		{:else}
			<Sun size="24" />
		{/if}
	</button>
</header>

<style lang="scss">
	header {
		padding: 0.8rem 1.2rem;
		background-color: rgba(var(--surface-rgb), 0.5);
		display: flex;
		justify-content: space-between;
		position: sticky;
		top: 0;
		backdrop-filter: blur(6px);
		z-index: 998;
	}

	header .branding {
		font-size: 1.2rem;
		font-weight: 600;
		letter-spacing: 0.05ch;
	}

	header .theme-toggle {
		transition: transform 0.15s ease;
		animation: float 2s cubic-bezier(0.25, 0.8, 0.25, 1) infinite;
	}

	header .theme-toggle:active {
		transform: scale(0.8);
	}
</style>
