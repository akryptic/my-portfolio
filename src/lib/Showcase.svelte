<script lang="ts">
	import { GithubLogo } from 'phosphor-svelte';
	import { GITHUB_USERNAME } from './social';

	interface WorkItem {
		id: string;
		title: string;
		description: string;
		time_range: [Date, Date] | [Date, null];
		href?: string;
		tags: string[];
		image_url?: string;
		github_url?: string;
		ongoing?: boolean;
	}

	const works: WorkItem[] = [
		{
			id: 'work_abcd123_001',
			title: 'Lovluk',
			description:
				'Developed and deployed Sveltekit based website for a bussiness brand about sanitary pads and baby diapers',
			time_range: [new Date('31 March 2025'), null],
			href: 'https://lovluk.com',
			tags: ['Typescript', 'Sveltekit', 'Javascript', 'Tailwindcss'],
			image_url: '/images/lovluk.webp'
		},
		{
			id: 'work_abcd123_002',
			title: 'Irrigo',
			description: 'A web application created to control ESP32 project.',
			time_range: [new Date('1 March 2025'), new Date('16 April 2025')],
			href: 'https://irrigo.pages.dev',
			tags: ['Jquery', 'HTML5', 'CSS3', 'Javascript', 'Websocket', 'PWA'],
			image_url: '/images/irrigo.webp',
			github_url: `https://github.com/${GITHUB_USERNAME}/irrigo`,
			ongoing: false
		},
		{
			id: 'work_abcd123_003',
			title: 'Passguard',
			description:
				"An platform native application, which i decided to create on a friend's birthday and is still ongoing :)",
			time_range: [new Date('1 oct 2023'), null],
			tags: ['Typescript', 'Sveltekit', 'Tauri', 'SCSS', 'Rust', 'Docker'],
			image_url: '/images/passguard.webp',
			github_url: `https://github.com/${GITHUB_USERNAME}/passguard`,
			ongoing: true
		}
	];
</script>

<section>
	<h2>Experience / My Creations</h2>
	<hr />
	<div class="container">
		{#each works as work (work.id)}
			{@const startDate = work.time_range[0]}
			{@const endDate = work.time_range[1]}
			{@const rangeTitle = `${startDate.toLocaleDateString('en-US', { dateStyle: 'long' })} - ${endDate ? endDate.toLocaleDateString('en-US', { dateStyle: 'long' }) : 'Present'}`}
			<article aria-label={work.title}>
				<header>
					<img loading="lazy" width="320" src={work.image_url} alt="Visual of {work.title}" />
					{#if work.ongoing}
						<div class="onging-badge"><i class="dot"></i><span>Ongoing </span></div>
					{/if}
				</header>
				<div class="content">
					<h4 class="title">{work.title}</h4>
					<p class="description">{work.description}</p>
					{#if work.href}
						<p class="link">
							URL: <a aria-label={`Visit ${work.title} website`} target="_blank" href={work.href}
								>{work.href}</a
							>
						</p>
					{/if}
					<div class="tags-container">
						{#each work.tags as tag}
							<span class="tag">{tag}</span>
						{/each}
					</div>

					<div class="date">
						{#if work.github_url}
							<a
								aria-label={`View ${work.title} on GitHub`}
								target="_blank"
								href={work.github_url}
								title="View on github"><GithubLogo /></a
							>
						{/if}
						<p title={rangeTitle}>{rangeTitle}</p>
					</div>
				</div>
			</article>
		{/each}
	</div>
</section>

<style>
	section h2,
	section hr {
		display: block;
	}

	section .container {
		display: grid;
		grid-template-columns: 1fr;
		place-items: center;
		gap: 1.2rem;
		padding: 0 0.5rem;
	}

	article {
		position: relative;
		border: 2px solid rgba(var(--surface-rgb));
		background: rgba(var(--surface-rgb), 0.25);
		transition: all 0.2s ease;
		border-radius: 8px;
		padding: 0.8rem;
		height: 100%;
		width: 100%;
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	article:hover {
		border: 2px solid rgba(var(--primary-rgb));
		background: rgba(var(--primary-rgb), 0.25);
		transform: scale(1.05);
	}

	img {
		width: 100%;
		aspect-ratio: 16/9;
		border-radius: 8px;
	}

	.title {
		font-size: 1.875rem;
		line-height: 1.5;
		font-weight: 600;
		text-align: center;
	}

	.description {
		line-height: 1.25rem;
		font-size: 0.875rem;
	}

	.link {
		font-weight: 500;
	}

	.link a {
		font-size: 12px;
		text-decoration: underline;
		color: lightblue;
	}

	.tags-container {
		display: flex;
		gap: 0.6rem;
		margin: 0.8rem 0;
		flex-wrap: wrap;
	}

	.tag {
		border: 1px solid rgba(var(--primary-rgb));
		background-color: rgba(var(--primary-rgb), 0.4);
		padding: 0.2rem 0.4rem;
		border-radius: 4px;
		font-size: 0.8em;
		color: rgba(var(--primary-rgb));
		font-weight: 500;
	}

	.onging-badge {
		display: inline-flex;
		align-items: center;
		gap: 0.4rem;
		font-size: 0.8rem;
		box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.5);
		background-color: rgb(var(--surface-rgb));
		padding: 0.2rem 0.4rem;
		border-radius: 4px;
		position: absolute;
		top: 0.6rem;
		right: 0.6rem;
	}

	.dot {
		display: inline-block;
		width: 0.6rem;
		height: 0.6rem;
		background-color: rgba(var(--primary-rgb));
		border-radius: 50%;
		animation: blink 1.5s infinite;
	}

	.date {
		color: rgb(151, 151, 151);
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 12px;
		margin-top: 1rem;
	}

	.date a {
		font-size: 1.4rem;
		background: rgba(0, 0, 0, 0.25);
		padding: 0.2rem;
		border-radius: 99px;
	}

	/* Blinking and fading effect */
	@keyframes blink {
		0% {
			opacity: 1;
			transform: scale(1);
		}
		50% {
			opacity: 0.3;
			transform: scale(0.8);
		}
		100% {
			opacity: 1;
			transform: scale(1);
		}
	}

	@media only screen and (min-width: 600px) {
		section {
			grid-column: span 2;
		}

		section .container {
			grid-template-columns: 1fr 1fr;
			margin-top: 0.8rem;
		}
	}
</style>
