<script>
	import PhotoSlideshow from '#lib/components/PhotoSlideshow.svelte';
	import { discordInviteUrl, faqs, offerings, siteContent } from '#lib/content.js';

	const content = siteContent.home;
</script>

<svelte:head>
	<title>Drop In · {siteContent.name}</title>
	<meta name="description" content="A campus club for furry, furry-adjacent, and curious people. No fursuit or fursona needed." />
</svelte:head>

<main class="page page--home min-h-screen">
	<section class="home-hero content-width" aria-labelledby="home-title">
		<div class="hero-issue"><span>CMU / STUDENT LIFE</span><span>INDEPENDENT CLUB ZINE · NO. 01</span></div>
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
		<div class="hero-bottomline"><span>Not a prerequisite list.</span><span>Just a place to start.</span><span class="hero-bottomline__arrow">↓</span></div>
	</section>

	<div class="cut cut--orange" aria-hidden="true">
		<svg viewBox="0 0 1440 42" preserveAspectRatio="none"><path d="M0 19 48 14 93 18 141 9 193 15 251 8 304 16 362 12 420 19 476 7 532 13 586 11 643 17 700 6 759 12 821 15 877 8 930 14 987 7 1044 18 1105 11 1159 17 1218 6 1275 13 1332 9 1380 15 1440 10v32H0Z" /></svg>
	</div>

	<section class="definition content-width" aria-labelledby="definition-title">
		<div class="definition-number">01<span>/</span></div>
		<div class="definition-main">
			<p class="eyebrow">First things first</p>
			<h2 id="definition-title">So, what’s<br /><em>furry?</em></h2>
		</div>
		<div class="definition-copy">
			<p>{content.definition}</p>
			<p class="margin-note">Anthropomorphic: animal characters with human traits. Art, craft, stories, and community grow out from there.</p>
		</div>
	</section>

	<div class="cut cut--red" aria-hidden="true">
		<svg viewBox="0 0 1440 46" preserveAspectRatio="none"><path d="M0 29c51-18 76 3 128-11s73-6 123 3 74-14 127-9 72 17 124 4 81-12 133-3 72-1 124 8 81-14 131-12 82 18 132 9 79-10 132-14 85 9 133 12 68-7 123-11v39H0Z" /></svg>
	</div>

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
						<div><h3>{offering.title}</h3><p>{offering.copy}</p></div>
						<span class="activity-mark" aria-hidden="true">{['✳', '✦', '▧', '↗'][index]}</span>
						</li>
					{/each}
				</ol>
				<div class="activities-colophon">shared freely <span>·</span> learned together <span>·</span> always in progress</div>
			</div>
		</div>
	</section>

	<div class="cut cut--cream" aria-hidden="true">
		<svg viewBox="0 0 1440 48" preserveAspectRatio="none"><path d="M0 15 59 21 109 9 167 18 223 13 278 23 334 10 391 18 446 12 503 20 559 8 615 16 671 13 727 23 784 12 841 20 898 8 953 17 1012 11 1068 24 1126 12 1182 17 1240 9 1299 21 1356 13 1440 18v30H0Z" /></svg>
	</div>

	<section class="photo-section content-width" aria-labelledby="photo-title">
		<div class="photo-section__heading">
			<div><p class="eyebrow">The people, the projects, the snacks</p><h2 id="photo-title">Proof of life<span class="red-dot">.</span></h2></div>
			<p>A little gallery space for real club photos. Nothing is auto-playing; flip through when you feel like it.</p>
		</div>
		<PhotoSlideshow />
		<p class="photo-footnote"><span>✳</span> Placeholder frames only. Add approved photos and captions when ready.</p>
	</section>

	<div class="cut cut--blue" aria-hidden="true">
		<svg viewBox="0 0 1440 44" preserveAspectRatio="none"><path d="M0 20 50 8 101 16 150 11 200 24 251 13 301 21 351 8 402 14 451 18 502 7 552 20 602 12 652 21 702 10 752 18 802 12 852 23 902 9 952 17 1002 11 1052 21 1102 8 1152 16 1202 12 1252 22 1302 10 1352 18 1440 7v37H0Z" /></svg>
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
						{#if faq.placeholder}<span class="faq-sample">sample</span>{/if}
						<span class="faq-toggle" aria-hidden="true">+</span>
					</summary>
					<div class="faq-answer"><p>{faq.answer}</p></div>
				</details>
			{/each}
		</div>
		<p class="faq-foot">Ten questions, some still in pencil. <span>Tell us what we forgot.</span></p>
	</section>

	<div class="cut cut--dark" aria-hidden="true">
		<svg viewBox="0 0 1440 42" preserveAspectRatio="none"><path d="M0 10 53 18 105 7 159 15 212 22 265 11 318 18 371 8 424 14 477 22 530 10 583 16 636 7 689 19 742 11 795 20 848 8 901 17 954 10 1007 22 1060 12 1113 18 1166 8 1219 16 1272 22 1325 10 1378 17 1440 9v33H0Z" /></svg>
	</div>

	<section class="join-section" aria-labelledby="join-title">
		<div class="join-inner content-width">
			<div class="join-copy">
				<p class="eyebrow">Your next tab</p>
				<h2 id="join-title">Find us on<br /><span>Discord.</span></h2>
				<p>{content.joinCopy} Howling at the Moon dates land there, too.</p>
			</div>
			{#if discordInviteUrl}
				<a class="discord-button" href={discordInviteUrl} target="_blank" rel="noreferrer">Join the club <span>↗</span></a>
			{:else}
				<div class="discord-button discord-button--pending" aria-label="Discord invite pending">Discord invite pending <span>↗</span></div>
			{/if}
			<p class="join-stamp">bring yourself<br />and maybe a snack</p>
		</div>
	</section>
</main>
