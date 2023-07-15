<script lang="ts">
	import { onMount } from 'svelte';

	let episodesList: any[] = [];
	const getEpisodeList = async () => {
		const data = await fetch('https://api.consumet.org/meta/anilist/info/11079');

		const res = await data.json();

		episodesList = res.episodes;
	};

	onMount(() => {
		getEpisodeList();
	});
</script>

<section
	class="shadow-lg relative overflow-hidden bg-white flex justify-center items-center h-[90%] w-[95%] rounded-xl"
>
	<div class="bg-yellow-200 w-12 h-full pt-12">
        <div class="rotate-90 ">
            <p class="font-extralight w-52">Anime Review</p>
        </div>
	</div>
	<div class="flex-col overflow-hidden flex justify-center items-center w-full h-full px-6">
		<nav class="flex justify-between h-fit w-full pt-4 border-b-2 items-center pb-4">
			<h1 class="title text-41xl">Kill Me Baby</h1>
		</nav>
		<div class="h-[90%] relative items-center w-full flex justify-between">
			<div class="w-[30%]">
				<p class="text-5xl pb-4">Anime Comedy Random Banget</p>
				<p>
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Qui, exercitationem voluptates
					amet esse perferendis ratione a doloribus natus! Corrupti alias nobis ex ipsam corporis. A
					suscipit veritatis optio impedit ducimus!
				</p>
			</div>
			<div class="w-[30%] h-[40%] border-2 rounded-md px-2 py-4 overflow-x-auto flex-row-reverse">
				{#each episodesList as ep, i}
					<div class="border-b-2">
						<p>Episode {i + 1} :</p>
						<p class="text-xs">{ep.title}</p>
					</div>
				{/each}
			</div>
		</div>
	</div>
	<img
		class="absolute bottom-[-40%] h-[140%]"
		src="mascott.png"
		alt="yasuna and sonya"
	/>
</section>

<style>
	.title {
		color: #ffd600;
		text-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
		font-style: normal;
		line-height: normal;
		font-weight: 700;
	}
</style>
