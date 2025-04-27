<script>
	import Showcase from '$lib/Showcase.svelte';
	import { EMAIL } from '$lib/social';
</script>

<svelte:head>
	<title>Anil Kumar</title>
</svelte:head>

<section>
	<div>
		<p class="greet">Hey there! 👋 I Am,</p>
		<p class="name">Anil Kumar</p>
		<p>Indie self-taught developer</p>
		<p class="short-info">
			I specialize in developing secure and robust web applications and websites.
		</p>
		<a  aria-label="Send an email to Anil Kumar" class="btn" href={`mailto:${EMAIL}`}>Drop a Message</a>
	</div>
</section>

<section>
	<h2>About</h2>
	<hr />
	<div class="container">
		<span>
			I'm a developer who <span title="Just my principles and a desire for perfection"
				>loves building things that are secure, functional, and truly meaningful</span
			>. I primarily work with <b title="My love for JavaScript">TypeScript</b>,
			<b title="Not just another React follower!">SvelteKit</b>, and
			<b title="Wait, what? Go is awesome!">Go</b>
			— but I never limit myself to one stack. I'm passionate about
			<span title="No, no Bitcoins involved!">cryptography</span>,
			<span title="Got your back, hackers!">data security</span>, and
			<span title="Crafting like it's Minecraft!">crafting</span>
			experiences where privacy is the top priority.
			<span title="You don't call me a nerd!"
				>I love breaking things just to rebuild them better. Open-source, <b
					title="Who said Windows!?">Linux</b
				>, and doing things the hard way are key to how I learn and grow.</span
			>
			<span title="I won't abandon it, I promise!"
				>Right now, I'm building PassGuard, an encrypted vault for notes, passwords, and files —
				pure privacy at its core.</span
			>
			<span title="The mountains are calling, but I'll be back soon :)"
				>Always exploring, always building, always learning.</span
			>
		</span>
	</div>
</section>

<Showcase />

<style>
	section {
		padding: 2rem 1.2rem;
		padding-bottom: 0;
		display: grid;
	}

	p {
		font-size: 1.125rem;
		line-height: 1.75rem;
	}

	.short-info {
		font-size: 16px;
		letter-spacing: -0.025em;
		line-height: normal;
		margin-top: 0.5rem;
	}

	.name {
		font-size: 2.25rem;
		font-weight: 800;
		line-height: 1.375;
	}

	.name + p {
		font-weight: 500;
	}

	.btn {
		background: rgb(var(--primary-rgb), 0.75);
		padding: 0.4rem 0.75rem;
		border-radius: 6px;
		display: inline-block;
		margin-top: 1rem;
		font-size: 0.875rem;
		line-height: 1.25rem;
		font-weight: 500;
		transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
		border: 2px solid rgb(var(--primary-rgb));
	}

	.btn:hover {
		border-radius: 99px;
		background-color: transparent;
	}

	section .container {
		font-size: 1rem;
		line-height: 1.5rem;
	}
</style>
