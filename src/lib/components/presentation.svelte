<script lang="ts">
	import { onMount } from 'svelte'
	import Reveal from 'reveal.js'

	import '@styles/theme.css'
	import 'reveal.js/dist/reveal.css'


	// themestyle for code
	//import '@styles/code.css'
	//import 'reveal.js/plugin/highlight/zenburn.css'
	import '@styles/code/github.css'

	// theme
	//import 'reveal.js/dist/theme/white-contrast.css'
	import '@styles/theme/white-contrast.scss'
	//import '@styles/black-contrast.css'


	import { navigation } from '@stores/navigation'
	import options from '@config'

	onMount(() => {
		const deck = new Reveal(options)

		// keep track of current slide
		deck.on('slidechanged', (event: CustomEvent) => {
			// update navigation store
			updateSlideStore(deck)
		})

		deck.initialize().then(() => {
			// update navigation store
			updateSlideStore(deck)

			// we pass the language to the `<Code>` block
			// and higlight code blocks after initialization
			highlightCodeBlocks(deck)
		})

		// reload page after update to avoid HMR issues
		reloadPageAfterUpdate()
	})

	function updateSlideStore(deck: Reveal.Api) {
		$navigation = {
			hash: window.location.hash,
			currentSlide: deck.getSlidePastCount(),
			indices: deck.getIndices(),
			availableRoutes: deck.availableRoutes(),
		}
	}

	function updateHash() {
		$navigation.hash = window.location.hash
	}

	function highlightCodeBlocks(deck: Reveal.Api) {
		const highlight = deck.getPlugin('highlight')
		const codeBlocks = [...document.querySelectorAll('code')]
		codeBlocks.forEach((block) => {
			// @ts-ignore
			highlight.highlightBlock(block)
		})
	}

	function reloadPageAfterUpdate() {
		if (import.meta.hot) {
			import.meta.hot.on('vite:afterUpdate', () => {
				location.reload()
			})
		}
	}
</script>

<svelte:window on:hashchange={updateHash} />

<div class="reveal antialiased">
	<div class="slides">
		<slot />
	</div>
	<div class="p-4 w-full text-base">
		<img class="w-24"  src="https://www.grusp.org/wp-content/uploads/2021/04/2.png" alt="Laravelday 2023"  />
	</div>


</div>
