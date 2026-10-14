<script>
	import PhotoSlideshow from '#lib/components/PhotoSlideshow.svelte';
	import ZineDivider from '#lib/components/ZineDivider.svelte';
	import { discordInviteUrl, faqs, offerings, siteContent } from '#lib/content.js';

	const content = siteContent.home;
</script>

<svelte:head>
	<title>Drop In · {siteContent.name}</title>
	<meta name="description" content="A campus club for furry, furry-adjacent, and curious people. No fursuit or fursona needed." />
</svelte:head>

<main class="page page--home min-h-screen">
	<section class="home-hero content-width" aria-labelledby="home-title">
		<div class="hero-issue"><span>CMU / STUDENT LIFE</span><span>A VERY FURRY FIELD GUIDE · NO. 01</span></div>
		<div class="hero-layout">
			<div class="hero-copy">
				<p class="eyebrow"><span class="pixel-star">✳</span> For the furry, the furry-adjacent, and the curious</p>
				<h1 id="home-title" class="hero-title"><span>Furries</span><span class="hero-title__second"><i>@</i>CMU</span></h1>
				<p class="hero-intro">A safe, welcoming corner of campus for furry, furry-adjacent, and curious people to make things, share snacks, trade materials, and find their people.</p>
				<div class="hero-reassurance">
					<span>No fursuit needed</span><span>No fursona needed</span>
				</div>
				<p class="hero-more">Come as you are. You can love the art, wear a suit, make a character, or just want to know what all this is about.</p>
			</div>
			<div class="logo-sticker" role="img" aria-label="Replaceable club logo placeholder">
				<div class="logo-sticker__tape"></div>
				<span class="logo-sticker__small">OFFICIAL CLUB LOGO</span>
				<div class="logo-sticker__mark">YOUR<br />LOGO<br /><i>HERE</i></div>
				<span class="logo-sticker__foot">swap in the real mark</span>
				<span class="logo-sticker__registration" aria-hidden="true">✳</span>
			</div>
		</div>
	</section>

	<ZineDivider from="var(--color-cream)" to="var(--color-terracotta)" accent="var(--color-orange)" shape="torn" />

	<section class="definition" aria-labelledby="definition-title">
		<div class="definition__inner content-width">
			<div class="definition-number">01<span>/</span></div>
			<div class="definition-main">
				<p class="eyebrow">First things first</p>
				<h2 id="definition-title">So, what’s<br /><em>furry?</em></h2>
			</div>
			<div class="definition-copy">
				<p>{content.definition}</p>
				<p class="margin-note">Anthropomorphic: animal characters with human traits. Art, craft, stories, and community grow out from there.</p>
			</div>
		</div>
	</section>

	<ZineDivider from="var(--color-terracotta)" to="var(--color-cream)" accent="var(--color-raspberry)" shape="wave" />

	<section class="activities-bleed" aria-labelledby="activities-title">
		<div class="activities-field">
			<div class="activities-inner">
				<div class="activities-heading">
					<p class="eyebrow eyebrow--light">Things we make room for / 02</p>
					<h2 id="activities-title">Not one<br /><span>kind of club.</span></h2>
					<p class="activities-aside">A few good reasons to show up. Bring one, find another.</p>
				</div>
				<ol class="activity-list">
					{#each offerings as offering, index}
						<li class="activity-item activity-item--{index + 1}">
							<span class="activity-index">0{index + 1}</span>
							<div>
								<h3>{offering.title}</h3>
								<p>{offering.copy}</p>
							</div>
							<span class="activity-mark" aria-hidden="true">{offering.mark}</span>
						</li>
					{/each}
				</ol>
			</div>
		</div>
	</section>

	<div class="photo-section-divider photo-section-divider--top">
		<ZineDivider from="var(--color-cream)" to="var(--color-electric-blue)" accent="var(--color-raspberry)" shape="wave" />
	</div>
	<section class="photo-section" aria-labelledby="photo-title">
		<div class="photo-section__inner content-width">
			<div class="photo-section__heading">
				<div><p class="eyebrow">Paw prints, projects, and snack crumbs</p><h2 id="photo-title">Proof of life<span class="red-dot">.</span></h2></div>
				<p>A little gallery space for real club photos. Nothing is auto-playing; flip through when you feel like it.</p>
			</div>
			<PhotoSlideshow />
		</div>
	</section>
	<div class="photo-section-divider photo-section-divider--bottom">
		<ZineDivider from="var(--color-electric-blue)" to="var(--color-cream)" accent="var(--color-raspberry)" shape="wave" />
	</div>

	<section class="faq-section content-width" aria-labelledby="faq-title">
		<div class="faq-heading">
			<p class="eyebrow">Asked before / answered plainly</p>
			<h2 id="faq-title">Good questions.</h2>
			<p>{content.faqIntro}</p>
		</div>
		<div class="faq-list">
			{#each faqs as faq, index}
				<details class="faq-row">
					<summary>
						<span class="faq-number">{String(index + 1).padStart(2, '0')}</span>
						<span class="faq-question">{faq.question}</span>
						<span class="faq-toggle" aria-hidden="true">+</span>
					</summary>
					<div class="faq-answer"><p>{faq.answer}</p></div>
				</details>
			{/each}
		</div>
		<p class="faq-foot">Still curious? <a href={discordInviteUrl} target="_blank" rel="noopener noreferrer">Give us a howl on Discord ↗</a></p>
	</section>

	<ZineDivider from="var(--color-cream)" to="var(--color-coral)" accent="var(--color-indigo)" shape="wave" />

	<div class="join-transition">
		<section class="join-section" aria-labelledby="join-title">
			<div class="join-inner content-width">
				<div class="join-copy">
					<p class="eyebrow">Your next tab</p>
					<h2 id="join-title">Find us on<br /><span>Discord.</span></h2>
					<p>{content.joinCopy} Howling at the Moon dates land there, too.</p>
				</div>
				<a class="discord-button" href={discordInviteUrl} target="_blank" rel="noopener noreferrer">Join the club <span>↗</span></a>
				<p class="join-stamp">bring your paws<br />find your pack</p>
			</div>
		</section>
		<ZineDivider from="var(--color-coral)" to="var(--color-plum)" accent="var(--color-electric-blue)" shape="cut" />
	</div>
</main>
