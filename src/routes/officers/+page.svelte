<script>
	import { officers, siteContent } from '#lib/content.js';

	const content = siteContent.officers;
</script>

<svelte:head>
	<title>Officers · {siteContent.name}</title>
	<meta name="description" content="Meet the Furries@CMU officers. Profiles include pronouns, a photo, and a bio." />
</svelte:head>

<main class="page page--officers min-h-screen">
	<section class="officers-intro content-width" aria-labelledby="officers-title">
		<div class="page-kicker"><span>03 / PEOPLE INDEX</span><span>THE HUMANS BEHIND THE HOWLS</span></div>
		<div class="officers-intro__layout">
			<div>
				<p class="eyebrow">The club is made of people</p>
				<h1 id="officers-title">Meet the<br /><em>organizers.</em></h1>
			</div>
			<p>{content.intro} Pronouns are listed for everyone. Fursona images are optional; one profile has a placeholder slot, and the others can opt in later.</p>
		</div>
	</section>

	<div class="cut cut--orange" aria-hidden="true">
		<svg viewBox="0 0 1440 42" preserveAspectRatio="none"><path d="M0 21 52 12 105 18 158 8 211 15 264 23 317 10 370 18 423 9 476 15 529 21 582 7 635 15 688 22 741 11 794 17 847 8 900 20 953 10 1006 15 1059 24 1112 10 1165 19 1218 7 1271 15 1324 22 1377 11 1440 16v26H0Z" /></svg>
	</div>

	<section class="officer-list content-width" aria-label="Club officer profiles">
		{#each officers as officer, index}
			<article class="officer-profile officer-profile--{index + 1}">
				<div class="officer-profile__portrait">
					{#if officer.portrait}
						<img src={officer.portrait} alt="Portrait of {officer.name}" />
					{:else}
						<div class="portrait-placeholder" role="img" aria-label="Replaceable portrait placeholder">
							<span class="portrait-placeholder__id">PORTRAIT<br />0{index + 1}</span>
							<span class="portrait-placeholder__big">PHOTO<br />GOES<br />HERE</span>
							<span class="portrait-placeholder__caption">{officer.name}</span>
						</div>
					{/if}
					<span class="portrait-note">image slot / replace me</span>
				</div>
				<div class="officer-profile__copy">
					<div class="officer-role"><span>OFFICER 0{index + 1}</span><span>{officer.role}</span></div>
					<h2>{officer.name}</h2>
					<p class="officer-pronouns">{officer.pronouns}</p>
					<p class="officer-bio">{officer.bio}</p>
					{#if officer.fursona}
						<div class="fursona-slot">
							<div class="fursona-slot__art" role="img" aria-label="Optional fursona image placeholder"><span>OPTIONAL<br />CHARACTER<br />IMAGE</span></div>
							<div><span class="eyebrow">Optional / if they want</span><p>{officer.fursona.copy}</p></div>
						</div>
					{:else}
						<p class="fursona-note">Fursona image: optional. Nothing to add unless this person wants to.</p>
					{/if}
				</div>
				<span class="officer-profile__seal" aria-hidden="true">F@C<br />✳</span>
			</article>
		{/each}
	</section>
</main>
