<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Intro from './slides/00_intro.svelte'
	import DxLaravel from './slides/01_dx-laravel.svelte'
	import PestPHP from './slides/02_pestphp.svelte'
	import Codeanalysis from './slides/03_codeanalysis.svelte';
	import Refactor from './slides/04_refactor.svelte'
</script>

<Presentation>
	<Intro />
	<DxLaravel />
	<PestPHP />
	<Codeanalysis />
	<Refactor />
</Presentation>
