<script>
	import { fade } from 'svelte/transition';
	import LoadingCard from './LoadingCard.svelte';
	
	/**
	 * @type {{title: string, description: string}}
	 */
	export let recommendation;

</script>

<div>
	{#if recommendation.description}
		<div in:fade class="relative flex flex-col md:flex-row bg-neutral-800/70 shadow-md p-6">
			<div
				class="md:hidden z-10 absolute inset-0 bg-cover bg-center"
				style={`background-image: url(${recommendation.poster})`}
			>
				<div class="w-full h-full bg-black/80 bg-blur-sm" />
			</div>

			<div class="z-40 flex flex-col justify-between md:ml-6 pt-32 md:pt-0">
				<div>
					<div class="flex items-end mb-4">
						<div class="font-bold text-slate-200 text-3xl">
							{recommendation.title}
							<span class="font-bold text-slate-200/60 text-xl ml-2">{recommendation.year}</span>
						</div>
					</div>
					<div class="text-slate-200/90 mb-4">
						{recommendation.description}
					</div>
					<div class="text-slate-200/50 mb-4">
						Starring: {recommendation.actors}
					</div>
				</div>
				<div class="flex items-center">
					<div class="mr-4 py-1 px-2 rounded-full text-pink-600 border border-pink-600 text-xs">
						{recommendation.rated}
					</div>
				</div>
			</div>
		</div>
	{:else}
		<div in:fade class="relative flex flex-col md:flex-row bg-neutral-800/70 shadow-md p-6">
			<div
				class="text-white/50 flex items-center justify-center h-[250px] flex-none w-1/5 bg-neutral-900"
			>
				<svg
					width="35"
					height="35"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						fill-rule="evenodd"
						clip-rule="evenodd"
						d="M0.75 2.25C0.75 1.42157 1.42157 0.75 2.25 0.75H21.75C22.5784 0.75 23.25 1.42157 23.25 2.25V21.75C23.25 22.5784 22.5784 23.25 21.75 23.25H2.25C1.42157 23.25 0.75 22.5784 0.75 21.75V2.25Z"
						stroke="currentColor"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
					<path
