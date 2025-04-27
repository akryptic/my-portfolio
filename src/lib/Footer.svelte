<script>
	import { GithubLogo, InstagramLogo, LinkedinLogo, XLogo } from 'phosphor-svelte';
	import { GITHUB_USERNAME, INSTAGRAM_USERNAME, LINKEDIN_USERNAME, X_USERNAME } from './social';
</script>

<footer>
	<div class="social-links">
		<a aria-label="GitHub Profile" target="_blank" href="https://github.com/{GITHUB_USERNAME}"
			><GithubLogo weight="fill" /></a
		>
		<a
			aria-label="Instagram Profile"
			target="_blank"
			href="https://instagram.com/{INSTAGRAM_USERNAME}"><InstagramLogo weight="fill" /></a
		>
		<a aria-label="X Profile" target="_blank" href="https://x.com/{X_USERNAME}"
			><XLogo weight="fill" /></a
		>
		<a
			aria-label="Linked-In Profile"
			target="_blank"
			href="https://linkedin.com/in/{LINKEDIN_USERNAME}"><LinkedinLogo weight="fill" /></a
		>
	</div>

	<div>
		<p>Built with <a target="_blank" href="https://svelte.dev/">Sveltekit</a></p>
	</div>
</footer>

<style>
	footer {
		background-color: rgba(var(--surface-rgb), 0.1);
		border-top: 1px solid rgba(var(--surface-rgb));
		display: flex;
		justify-content: space-evenly;
		padding: 0.8rem;
        z-index: 999;
		align-items: center;
	}

	.social-links {
		display: flex;
		gap: 0.8rem;
	}

	.social-links a {
		font-size: 1.6rem;
	}

	p > a {
		text-decoration: underline;
	}
</style>
