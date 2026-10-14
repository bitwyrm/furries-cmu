<script>
	import '../app.css';
	import { page } from '$app/state';
	import { discordInviteUrl, siteContent } from '#lib/content.js';
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600;700&family=Silkscreen:wght@400;700&display=swap" rel="stylesheet" />
</svelte:head>

<div class="site-frame">
	<div class="top-scribble" aria-hidden="true"><span>♥</span> FURRY IS A VERB <span>✳</span> MAKE SOMETHING TOGETHER <span>♥</span> FURRY IS A VERB <span>✳</span></div>
	<header class="site-header">
		<a class="site-brand" href="/" aria-label="Furries at CMU home">
			<span class="site-brand__name">Furries<span>@CMU</span></span>
			<span class="site-brand__tag">a club thing / Pittsburgh, PA</span>
		</a>
		<nav class="main-nav" aria-label="Main navigation">
			{#each siteContent.navigation as item, i}
				<a href={item.href} aria-current={page.url.pathname === item.href ? 'page' : undefined}>
					<span class="main-nav__number">0{i + 1}</span>{item.label}
				</a>
			{/each}
		</nav>
		{#if discordInviteUrl}
			<a class="header-discord" href={discordInviteUrl} target="_blank" rel="noreferrer">Discord <span>↗</span></a>
		{:else}
			<span class="header-discord header-discord--pending">Discord invite pending <span>↗</span></span>
		{/if}
	</header>

	<slot />

	<footer class="site-footer">
		<div class="site-footer__inner">
			<a href="/" class="footer-mark">F@C<span>✳</span></a>
			<p>Made of people, paper, pixels, and snacks.<br /><span>Furries@CMU · Carnegie Mellon University</span></p>
			<nav aria-label="Footer navigation">
				{#each siteContent.navigation as item}
					<a href={item.href}>{item.label}</a>
				{/each}
			</nav>
		</div>
		<div class="footer-bottom"><span>Current status: making it up as we go</span><span>✳ NO ONE NEEDS A COSTUME TO BELONG ✳</span></div>
	</footer>
</div>
