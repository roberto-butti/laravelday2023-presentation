<script>
    /**
	 * @type {string}
	 */
    export let banner;
    /**
	 * @type {string}
	 */
     export let icon;
    /**
	 * @type {string}
	 */
     export let headline;
    /**
	 * @type {string}
	 */
     export let subheadline;
    /**
	 * @type {string}
	 */
     export let title;
     /**
	 * @type {string}
	 */
     export let subtitle;


</script>
<div
		class="dark:!bg-navy-800 shadow-shadow-500 shadow-3xl rounded-primary relative mx-auto flex h-full w-full flex-col items-center bg-cover bg-clip-border p-[16px] dark:text-white dark:shadow-none"
	>
		<div
			class="relative mt-1 flex h-32 w-full justify-center rounded-xl bg-cover"
			style="
			background-image: url({ banner } );
			background-image2: url('https://i.ibb.co/FWggPq1/banner.png');">
			<div
				class="absolute -bottom-12 flex h-[88px] w-[88px] items-center justify-center rounded-full border-[4px] border-white bg-blue-400"
			>
				<img
					class="h-full w-full rounded-full"
					src="{icon}"
					alt=""
				/>
			</div>
		</div>
		<div class="mt-16 flex flex-col items-center">
			<p class="text-gray-900 text-6xl font-bold">{ headline }</p>
			<p class="text-gray-800 text-3xl font-normal">
				{ subheadline }
			</p>
		</div>
		<div class="mt-6 mb-3 flex gap-4 md:!gap-14">
			<div class="flex flex-col items-center justify-center">
				<p class="text-red-600 text-6xl font-bold">
					{ title }
				</p>
				<p class="text-gray-700 text-sm font-normal">
					{ subtitle }
				</p>
			</div>
		</div>
	</div>