<script>
	import { discordInviteUrl, recentEvents, siteContent } from '#lib/content.js';

	const content = siteContent.events;
</script>

<svelte:head>
	<title>Events · {siteContent.name}</title>
	<meta name="description" content="Monthly Howling at the Moon meetups and recent Furries@CMU event notes." />
</svelte:head>

<main class="page page--events min-h-screen">
	<section class="events-intro content-width">
		<div class="page-kicker"><span>02 / EVENT LOG</span><span>MONTHLY, AFTER DARK</span></div>
		<p class="eyebrow">Our recurring ritual</p>
		<p class="events-intro__lede">A walk, a howl, a movie, a pile of snacks.</p>
		<p class="events-intro__small">The date shifts. The plan is simple. The moon does its part.</p>
	</section>

	<section class="moon-bleed" aria-labelledby="events-title">
		<div class="moon-field">
			<div class="moon-poster content-width">
				<div class="moon-copy">
					<p class="eyebrow eyebrow--light">Furries@CMU presents / once a month</p>
					<h1 id="events-title">Howling<br /><span>at the</span><br />Moon</h1>
					<p class="moon-copy__intro">{content.copy}</p>
					<ol class="moon-route">
						<li><span>01</span><strong>Walk to Walking to the Sky</strong></li>
						<li><span>02</span><strong>Movie + snacks</strong></li>
					</ol>
				</div>

				<figure class="moon-art">
					<svg viewBox="0 0 480 420" role="img" aria-labelledby="moon-svg-title moon-svg-desc">
						<title id="moon-svg-title">Pixel moon over a hill</title>
						<desc id="moon-svg-desc">A blocky cream moon and pixel stars sit over a simple red-orange landscape.</desc>
						<rect width="480" height="420" fill="#2468c0" />
						<g fill="#f1e4d4">
							<rect x="70" y="42" width="12" height="12" /><rect x="118" y="79" width="8" height="8" /><rect x="370" y="43" width="11" height="11" />
							<rect x="418" y="107" width="8" height="8" /><rect x="51" y="164" width="9" height="9" /><rect x="399" y="202" width="12" height="12" />
							<rect x="320" y="90" width="8" height="8" /><rect x="159" y="48" width="7" height="7" />
						</g>
						<path d="M237 50h40v18h26v21h19v27h17v41h-17v25h-20v20h-27v18h-43v-18h-28v-20h-18v-25h-18v-40h18v-29h20V87h29z" fill="#f1e4d4" />
						<g fill="#e5b992"><rect x="259" y="95" width="14" height="14" /><rect x="300" y="132" width="10" height="10" /><rect x="225" y="150" width="12" height="12" /><rect x="270" y="174" width="9" height="9" /></g>
						<path d="M0 296h75l24-21h52l22 17h63l20-30h43l32 23h66l25-21h58v156H0z" fill="#8c0101" />
						<path d="M0 348h92l19-17h64l21 20h46l27-17h60l21 16h49l20-19h61v89H0z" fill="#c03415" />
						<g fill="#4c251e"><rect x="82" y="312" width="12" height="12" /><rect x="375" y="300" width="12" height="12" /><rect x="220" y="360" width="9" height="9" /><rect x="28" y="376" width="14" height="14" /></g>
					</svg>
					<figcaption>the moon is real / the art is not a schedule</figcaption>
				</figure>

				<div class="date-slip">
					<span class="date-slip__asterisk">✳</span>
					<p class="date-slip__label">Next gathering</p>
					<strong>Check Discord<br />for the date</strong>
					{#if discordInviteUrl}
						<a href={discordInviteUrl} target="_blank" rel="noreferrer">Find the club ↗</a>
					{:else}
					<span>Invite link goes here</span>
					{/if}
				</div>
			</div>
		</div>
	</section>

	<div class="cut cut--red" aria-hidden="true">
		<svg viewBox="0 0 1440 44" preserveAspectRatio="none"><path d="M0 12 54 18 109 7 164 19 218 13 273 21 327 9 382 17 436 11 491 22 545 8 600 15 655 21 709 10 764 18 818 7 873 16 927 22 982 11 1036 18 1091 9 1145 20 1200 13 1255 22 1309 8 1364 17 1440 12v32H0Z" /></svg>
	</div>

	<section class="recent-section content-width" aria-labelledby="recent-title">
		<div class="recent-heading">
			<p class="eyebrow">The paper trail / sample entries</p>
			<h2 id="recent-title">Recent<br /><em>gatherings.</em></h2>
			<p>{content.recentIntro}</p>
		</div>
		<div class="event-clippings">
			{#each recentEvents as event, index}
				<article class="event-clipping event-clipping--{index + 1}">
					<div class="event-clipping__meta"><span>DATE TO ADD</span><span>SAMPLE 0{index + 1}</span></div>
					<p class="event-clipping__kind">{event.category}</p>
					<h3>{event.title}</h3>
					<p>{event.copy}</p>
					{#if index === 0}<span class="event-clipping__sticker">A NOTE<br />FROM THE CLUB</span>{/if}
				</article>
			{/each}
		</div>
		<p class="recent-foot">Dates, recaps, and photos are intentionally placeholders until real updates are ready.</p>
	</section>
</main>
