<script lang="ts">
	import OverviewCards from '$lib/components/OverviewCards.svelte';
	import AboutSection from '$lib/components/AboutSection.svelte';
	import TechStack from '$lib/components/TechStack.svelte';
	import Reveal from '$lib/components/Reveal.svelte';
	import ScrollReveal from '$lib/components/ScrollReveal.svelte';
	import ScrollColorBar from '$lib/components/ScrollColorBar.svelte';
	import ContactForm from '$lib/components/ContactForm.svelte';

	let { data } = $props();
	let projects = data.projects;

	function getImageUrl(imageUrl: string | undefined): string | undefined {
		if (!imageUrl) return undefined;
		if (imageUrl.startsWith('http://') || imageUrl.startsWith('https://')) {
			return imageUrl;
		}
		return `/api/images${imageUrl.startsWith('/') ? imageUrl : '/' + imageUrl}`;
	}

	const socials = [
		{ href: 'https://github.com/Jerasaurus', label: 'GitHub', icon: 'github' },
		{ href: 'https://www.linkedin.com/', label: 'LinkedIn', icon: 'linkedin' }
	];

	function Icon({ name }: { name: string }) {
		if (name === 'github') {
			return `<svg viewBox="0 0 16 16" preserveAspectRatio="xMidYMid meet" fill="currentColor" aria-hidden="true" class="h-6 w-6" xmlns="http://www.w3.org/2000/svg"><path d="M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z"/></svg>`;
		}
		if (name === 'x') {
			return `<svg viewBox="0 0 24 24" fill="currentColor" aria-hidden="true" class="h-6 w-6"><path d="M18.36 2H21l-6.5 7.43L22 22h-6.8l-4.7-6.1L4.9 22H2.25l7.05-8.06L2 2h6.9l4.22 5.6L18.36 2Zm-1.19 18h1.89L7.01 4h-1.9L17.17 20Z"/></svg>`;
		}
		return `<svg viewBox="0 0 72 72" aria-hidden="true" class="h-6 w-6" xmlns="http://www.w3.org/2000/svg"><path fill="currentColor" fill-rule="evenodd" d="M8 0 H64 a8 8 0 0 1 8 8 V64 a8 8 0 0 1 -8 8 H8 a8 8 0 0 1 -8 -8 V8 a8 8 0 0 1 8 -8 Z M62,62 L51.315625,62 L51.315625,43.8021149 C51.315625,38.8127542 49.4197917,36.0245323 45.4707031,36.0245323 C41.1746094,36.0245323 38.9300781,38.9261103 38.9300781,43.8021149 L38.9300781,62 L28.6333333,62 L28.6333333,27.3333333 L38.9300781,27.3333333 L38.9300781,32.0029283 C38.9300781,32.0029283 42.0260417,26.2742151 49.3825521,26.2742151 C56.7356771,26.2742151 62,30.7644705 62,40.051212 L62,62 Z M16.349349,22.7940133 C12.8420573,22.7940133 10,19.9296567 10,16.3970067 C10,12.8643566 12.8420573,10 16.349349,10 C19.8566406,10 22.6970052,12.8643566 22.6970052,16.3970067 C22.6970052,19.9296567 19.8566406,22.7940133 16.349349,22.7940133 Z M11.0325521,62 L21.769401,62 L21.769401,27.3333333 L11.0325521,27.3333333 L11.0325521,62 Z"/></svg>`;
	}
</script>

<section class="relative mx-auto max-w-6xl px-6 py-28 sm:py-36">
	<div class="grid items-center gap-12 lg:grid-cols-2">
		<Reveal>
			<div
				class="inline-flex items-center gap-2 rounded-full border border-white/10 bg-white/5 px-4 py-1.5 backdrop-blur"
			>
				<span class="relative flex h-2.5 w-2.5">
					<span
						class="absolute inline-flex h-full w-full animate-ping rounded-full bg-emerald-400 opacity-60"
					></span>
					<span class="relative inline-flex h-2.5 w-2.5 rounded-full bg-emerald-400"></span>
				</span>
				<span class="text-sm text-white/80">Available for work</span>
			</div>

			<h1 class="mt-6 text-5xl font-extrabold tracking-tight sm:text-7xl">Hi, I'm Jeremy</h1>
			<p class="mt-6 max-w-2xl text-lg leading-8 text-white/70">
				Full-stack developer and embedded systems engineer studying Mechanical Engineering and CS at
				Stanford, bringing hardware and software together.
			</p>

			<div class="mt-10 flex items-center gap-3">
				{#each socials as s}
					<a
						class="group inline-flex h-12 w-12 items-center justify-center rounded-xl border border-white/10 bg-white/5 text-white/80 backdrop-blur transition hover:text-white hover:border-white/20"
						href={s.href}
						target="_blank"
						rel="noreferrer"
						aria-label={s.label}
					>
						{@html Icon({ name: s.icon })}
					</a>
				{/each}
				<a href="#overview" class="ml-2 text-white/60 hover:text-white" aria-label="Scroll down">
					<svg
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="1.5"
						class="h-6 w-6 animate-bounce"
						style="animation-delay: 5s"><path d="M12 5v14m0 0l-5-5m5 5l5-5" /></svg
					>
				</a>
			</div>
		</Reveal>

		<Reveal delay={120}>
			<div class="flex justify-center lg:justify-end">
				<div
					class="relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 shadow-xl ring-1 ring-white/10 backdrop-blur"
				>
					<img
						src="/nice.jpg"
						alt="Portrait of Jeremy"
						class="h-72 w-72 object-cover object-[50%_10%] sm:h-80 sm:w-80 md:h-96 md:w-96"
						loading="lazy"
						decoding="async"
					/>
				</div>
			</div>
		</Reveal>
	</div>
</section>

<!-- Space for gradient to fade -->
<!-- <div class="h sm:h-48"></div> -->

<!-- About/Philosophy section -->
<div id="about">
	<AboutSection />
</div>

<!-- More space before cards -->
<div class="h-24"></div>

<!-- overview cards -->
<div id="overview" class="min-h-[300px]">
	<OverviewCards />
</div>

<!-- Tech Stack section -->
<div id="skills">
	<TechStack />
</div>

<!-- Scroll-triggered Color Bar -->
<ScrollColorBar />

<!-- Projects Section - Grand Showcase -->
<section id="projects" class="relative mx-auto mt-24 px-6">
	<ScrollReveal delay={100}>
		<!-- Decorative Background Elements -->
		<div class="absolute inset-0 pointer-events-none overflow-visible">
			<div class="absolute -top-24 left-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl"></div>
			<div
				class="absolute -bottom-24 right-1/4 w-96 h-96 bg-blue-500/10 rounded-full blur-3xl"
			></div>
		</div>

		<!-- Section Header -->
		<div class="relative text-center mb-16 max-w-4xl mx-auto">
			<div
				class="inline-flex items-center gap-2 rounded-full border border-white/10 bg-white/5 px-4 py-1.5 backdrop-blur mb-6"
			>
				<span class="text-sm text-white/60">Featured Work</span>
			</div>

			<h2 class="text-3xl sm:text-4xl font-bold text-white/90 mb-6">
				<span> Things I've </span>
				<span class="bg-gradient-to-r from-purple-400 to-blue-400 bg-clip-text text-transparent">
					{' Built'}
				</span>
			</h2>

			<p class="max-w-2xl mx-auto text-lg text-white/70 leading-relaxed">
				Some projects I'm excited about! From tinkering with hardware to building web apps, I love
				diving into new challenges and learning something new along the way.
			</p>
		</div>

		<!-- Featured Projects Showcase -->
		{#if projects && projects.length > 0}
			{#each projects as project, index}
				<div class="relative max-w-7xl mx-auto mb-16">
					<a
						href="/projects/{project.id}"
						class="group block relative overflow-hidden rounded-3xl border border-white/10 bg-gradient-to-br from-purple-600/5 via-transparent to-blue-600/5 backdrop-blur-sm transition-all duration-500 hover:border-purple-500/30 hover:shadow-2xl hover:shadow-purple-500/20 hover:-translate-y-2"
					>
						<div class="grid lg:grid-cols-2 min-h-[500px]">
							<!-- Image Side -->
							<div
								class="relative overflow-hidden bg-gradient-to-br from-purple-600/20 to-blue-600/20"
							>
								{#if getImageUrl(project.cover?.url || project.heroimage?.url)}
									<img
										src={getImageUrl(project.cover?.url || project.heroimage?.url)}
										alt={project.cover?.alternativeText ||
											project.heroimage?.alternativeText ||
											project.name}
										class="absolute inset-0 h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
										loading="lazy"
									/>
								{:else}
									<div class="absolute inset-0 flex items-center justify-center">
										<div class="text-white/10">
											<svg
												xmlns="http://www.w3.org/2000/svg"
												class="h-32 w-32"
												fill="none"
												viewBox="0 0 24 24"
												stroke="currentColor"
											>
												<path
													stroke-linecap="round"
													stroke-linejoin="round"
													stroke-width="1"
													d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-6l-2-2H5a2 2 0 00-2 2z"
												/>
											</svg>
										</div>
									</div>
								{/if}
								<div
									class="absolute inset-0 bg-gradient-to-t from-gray-900 via-transparent to-transparent opacity-60"
								></div>
							</div>

							<!-- Content Side -->
							<div class="relative p-10 lg:p-12 flex flex-col justify-center">
								{#if project.tags && project.tags.length > 0}
									<div class="flex flex-wrap gap-2 mb-6 max-w-full">
										{#each project.tags
											.filter((t) => t.toLowerCase() !== 'featured')
											.slice(0, 6) as tag}
											<span
												class="px-3 py-1 text-xs font-medium bg-purple-500/10 text-purple-300 rounded-full border border-purple-500/20"
											>
												{tag}
											</span>
										{/each}
									</div>
								{/if}

								<h3
									class="text-3xl lg:text-4xl font-bold mb-4 bg-gradient-to-r from-white to-white/80 bg-clip-text text-transparent group-hover:from-purple-300 group-hover:to-blue-300 transition-all duration-300"
								>
									{project.name}
								</h3>

								{#if project.description}
									<p class="text-white/60 text-base mb-6">
										{project.description}
									</p>
								{/if}

								<div
									class="flex items-center gap-2 text-purple-300 group-hover:text-purple-400 transition-colors"
								>
									<span class="font-medium">Explore Project</span>
									<svg
										xmlns="http://www.w3.org/2000/svg"
										class="h-5 w-5 transition-transform group-hover:translate-x-1"
										fill="none"
										viewBox="0 0 24 24"
										stroke="currentColor"
									>
										<path
											stroke-linecap="round"
											stroke-linejoin="round"
											stroke-width="2"
											d="M13 7l5 5m0 0l-5 5m5-5H6"
										/>
									</svg>
								</div>
							</div>
						</div>
					</a>
				</div>
				<!-- Add margin between featured projects if there are multiple -->
				{#if index < projects.length - 1}
					<div class="mb-12"></div>
				{/if}
			{/each}

			<!-- View All Button -->
			<div class="text-center">
				<a
					href="/projects"
					class="inline-flex items-center gap-3 rounded-full bg-gradient-to-r from-purple-600 to-blue-600 px-8 py-4 text-sm font-semibold text-white shadow-lg shadow-purple-500/25 transition-all duration-300 hover:shadow-xl hover:shadow-purple-500/40 hover:-translate-y-0.5"
				>
					<span>Explore All Projects</span>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M17 8l4 4m0 0l-4 4m4-4H3"
						/>
					</svg>
				</a>
			</div>
		{:else}
			<!-- Empty State -->
			<div class="max-w-4xl mx-auto">
				<div
					class="relative overflow-hidden rounded-3xl border border-white/10 bg-gradient-to-br from-purple-600/10 to-blue-600/10 p-16 text-center backdrop-blur-sm"
				>
					<div class="absolute inset-0 bg-gradient-to-br from-purple-600/5 to-blue-600/5"></div>
					<div class="relative">
						<div
							class="inline-flex h-20 w-20 items-center justify-center rounded-full bg-gradient-to-br from-purple-500/20 to-blue-500/20 mb-6"
						>
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-10 w-10 text-purple-400"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"
								/>
							</svg>
						</div>
						<h3 class="text-2xl font-bold text-white mb-3">Projects Loading...</h3>
						<p class="text-white/60 text-lg">Amazing creations are on their way!</p>
					</div>
				</div>
			</div>
		{/if}
	</ScrollReveal>
</section>

<section id="contact" class="mx-auto mt-24 mb-24 max-w-6xl px-6">
	<ScrollReveal delay={200}>
		<div class="max-w-2xl mx-auto">
			<!-- Section Header -->
			<div class="text-center mb-12">
				<div
					class="inline-flex items-center gap-2 rounded-full border border-white/10 bg-white/5 px-4 py-1.5 backdrop-blur mb-6"
				>
					<span class="text-sm text-white/60">Get in Touch</span>
				</div>

				<h2 class="text-3xl sm:text-4xl font-bold text-white/90 mb-4">Let's Work Together</h2>

				<p class="text-white/70 text-lg">
					I'd love to hear from you. Send me a message and I'll get back to you within a few days!
					This form notifies my devices instantly.
				</p>
			</div>

			<!-- Contact Form -->
			<div class="rounded-3xl border border-white/10 bg-white/5 backdrop-blur p-8">
				<ContactForm />
			</div>
		</div>
	</ScrollReveal>
</section>

<style>
	.line-clamp-2 {
		display: -webkit-box;
		-webkit-line-clamp: 2;
		line-clamp: 2;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}

	.line-clamp-3 {
		display: -webkit-box;
		-webkit-line-clamp: 3;
		line-clamp: 3;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}
</style>
