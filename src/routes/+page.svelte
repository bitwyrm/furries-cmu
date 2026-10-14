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
		<svg viewBox="0 0 1440 42" preserveAspectRatio="none"><path d="M0 17 43 10 91 14 137 7 185 17 235 8 285 15 336 6 386 13 438 9 488 18 539 11 590 15 640 7 692 16 741 10 793 19 843 8 896 14 945 7 997 17 1048 9 1098 15 1148 6 1200 14 1250 8 1301 16 1350 9 1397 14 1440 8L1440 29 1393 33 1344 27 1297 35 1246 29 1198 37 1147 30 1098 35 1048 28 999 34 949 29 899 36 848 29 799 35 749 27 699 34 648 28 598 36 548 29 498 35 448 28 398 34 348 28 298 36 248 30 198 35 149 28 99 34 49 29 0 35Z" /></svg>
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
		<svg viewBox="0 0 1440 46" preserveAspectRatio="none"><path d="M0 21C100 8 155 9 220 17S340 28 430 15 570 6 640 18 780 30 860 15 1010 4 1080 17 1220 30 1300 14 1390 8 1440 17C1360 30 1320 36 1260 31S1130 25 1060 34 930 41 860 31 720 25 640 36 500 40 430 31 290 24 220 36 80 40 0 32Z" /></svg>
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
		<svg viewBox="0 0 1440 48" preserveAspectRatio="none"><path d="M0 17 58 23 110 8 165 18 222 12 278 22 333 9 389 17 446 11 502 21 558 7 615 16 671 12 727 23 783 10 840 20 897 8 953 17 1010 10 1067 24 1124 11 1181 18 1238 7 1297 20 1353 12 1440 17L1440 34 1386 30 1331 39 1276 31 1220 38 1164 30 1108 36 1052 29 996 38 940 32 884 39 828 31 772 37 716 29 660 36 604 30 548 38 492 31 436 37 380 29 324 36 268 30 212 39 156 31 100 36 45 30 0 36Z" /></svg>
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
		<svg viewBox="0 0 1440 44" preserveAspectRatio="none"><path d="M0 20 50 8 101 16 150 11 200 24 251 13 301 21 351 8 402 14 451 18 502 7 552 20 602 12 652 21 702 10 752 18 802 12 852 23 902 9 952 17 1002 11 1052 21 1102 8 1152 16 1202 12 1252 22 1302 10 1352 18 1440 7L1440 30 1388 36 1338 29 1288 37 1237 31 1186 39 1136 30 1086 35 1035 29 985 38 934 30 884 36 833 28 783 37 732 31 681 38 631 29 580 36 529 30 479 39 428 31 377 36 327 29 276 38 225 31 175 36 124 28 73 36 0 32Z" /></svg>
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
		<svg viewBox="0 0 1440 42" preserveAspectRatio="none"><path d="M0 12 54 20 108 7 162 16 216 23 270 10 324 18 378 8 432 15 486 21 540 9 594 17 648 6 702 19 756 11 810 21 864 7 918 17 972 10 1026 22 1080 11 1134 19 1188 8 1242 17 1296 23 1350 10 1404 17 1440 9L1440 31 1380 37 1325 29 1271 36 1218 30 1164 38 1110 31 1056 37 1002 29 948 36 894 30 840 38 786 31 732 37 678 29 624 36 570 30 516 38 462 31 408 37 354 29 300 36 246 30 192 38 138 31 84 37 30 30 0 34Z" /></svg>
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
