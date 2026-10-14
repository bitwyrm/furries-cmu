<script>
	import '../app.css';
	import { page } from '$app/state';
	import { discordInviteUrl, siteContent } from '#lib/content.js';

	function relativeRouteHref(targetPath, pathname) {
		const routeSuffix = pathname.match(/\/(?:events|officers)\/?$/)?.[0];
		const basePath = routeSuffix ? pathname.slice(0, -routeSuffix.length) : pathname.replace(/\/$/, '');
		const currentSegments = pathname.split('/').filter(Boolean);
		const targetSegments = `${basePath}${targetPath}`.split('/').filter(Boolean);
		let sharedSegments = 0;

		while (
			sharedSegments < currentSegments.length &&
			sharedSegments < targetSegments.length &&
			currentSegments[sharedSegments] === targetSegments[sharedSegments]
		) {
			sharedSegments += 1;
		}

		const up = Array(currentSegments.length - sharedSegments).fill('..');
		const down = targetSegments.slice(sharedSegments);
		return `${[...up, ...down].join('/') || '.'}/`;
	}

	const navigation = $derived.by(() => {
		const pathname = page.url.pathname;
		return siteContent.navigation.map((item) => ({
			...item,
			href: relativeRouteHref(item.path, pathname)
		}));
	});
	const homeHref = $derived(relativeRouteHref('/', page.url.pathname));
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600;700&family=Silkscreen:wght@400;700&display=swap" rel="stylesheet" />
</svelte:head>

<div class="site-frame">
	<div class="top-scribble" aria-hidden="true"><span>✳</span> MAKE SOMETHING TOGETHER <span>♥</span> A PAWSE FOR THE CURIOUS <span>✳</span> MAKE SOMETHING TOGETHER <span>♥</span></div>
	<header class="site-header">
		<a class="site-brand" href={homeHref} aria-label="Furries at CMU home">
			<span class="site-brand__name">Furries<span>@CMU</span></span>
		</a>
		<nav class="main-nav" aria-label="Main navigation">
			{#each navigation as item, i}
				<a href={item.href} aria-current={item.href === './' ? 'page' : undefined}>
					<span class="main-nav__number">0{i + 1}</span>{item.label}
				</a>
			{/each}
		</nav>
		<a class="header-discord" href={discordInviteUrl} target="_blank" rel="noopener noreferrer">Discord <span>↗</span></a>
	</header>

	<slot />

	<footer class="site-footer">
		<div class="site-footer__inner">
			<a href={homeHref} class="footer-mark" aria-label="Furries at CMU home">✳</a>
			<p>Furries, furry-adjacent friends, and curious critters.<br /><span>Furries@CMU · Carnegie Mellon University</span></p>
			<nav aria-label="Footer navigation">
				{#each navigation as item}
					<a href={item.href}>{item.label}</a>
				{/each}
			</nav>
		</div>
		<div class="footer-bottom"><span>MAKE SOMETHING TOGETHER</span><span>✳ NO FURSUIT NEEDED ✳</span></div>
	</footer>
</div>
