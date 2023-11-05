<script lang="ts">
	import { Slide, Code } from '@components'
	import Subheadline from './components/subheadline.svelte'
	import Item from './components/item.svelte'
	import Fit from '@lib/components/fit.svelte'
	//import Cover from './components/cover.svelte'
	import Quote from './components/quote.svelte'
	import Image from './components/image.svelte'
	import Quotesmall from './components/quotesmall.svelte'
	import Text from './components/text.svelte'
</script>

<Slide animate>
    <Subheadline>Come fare refactor in maniera serena?</Subheadline>
    <Text>

Rector è uno strumento per il refactoring automatico del codice PHP. Consente di apportare modifiche strutturali al codice sorgente in modo automatico, risparmiando tempo e riducendo il rischio di errori umani durante il processo di refactoring.
</Text>

<Subheadline>Puó essere utilizzato in due contesti</Subheadline>
<Text>

<ul class="text-align-left">
    <li>Aggiornamenti: Rector ora supporta gli aggiornamenti da PHP 5.3 a 8.2 e i principali progetti open-source come Symfony, PHPUnit e Doctrine. Volete essere sempre aggiornati all'ultima versione di PHP e Framework, senza alcuno sforzo?</li>
    <li>Rifattorizzazione automatica</li>
</ul>
</Text>
</Slide>

<Slide animate>
<Subheadline>Refactor con Rector</Subheadline>
    <Text>Nel file di configurazione rector.php vengono impostate le regole da seguire</Text>
    	<div>
		<Code  lang="shell">
			{`
composer require rector/rector --dev
vendor/bin/rector init
            `}
		</Code>
	</div>
	<div>
		<Code  lang="php">
			{`
    $rectorConfig->sets([
        LevelSetList::UP_TO_PHP_81,
        SetList::DEAD_CODE,
        SetList::CODE_QUALITY,
        SetList::EARLY_RETURN,
        SetList::TYPE_DECLARATION,
        // SetList::PRIVATIZATION
    ]);
            `}
		</Code>
	</div>
</Slide>

<Slide animate>
<Subheadline>Refactor con Rector</Subheadline>

	<div>
		<Code  lang="shell">
			{`
vendor/bin/rector process --dry-run
            `}
		</Code>
	</div>
	<div>
		<Code  lang="php">
			{`
$rectorConfig->sets([
    LevelSetList::UP_TO_PHP_80
]);
            `}
		</Code>
	</div>
<Image src="rector.png" alt="Esecuzione di rector" />
</Slide>

<Slide animate>
<Subheadline>Refactor con Rector</Subheadline>
    <Text>Esiste un progetto che definisce regole specifiche per Laravel da utilizzare con Rector: <a href="https://github.com/driftingly/rector-laravel">https://github.com/driftingly/rector-laravel</a></Text>
	<div>
		<Code  lang="shell">
			{`
composer require driftingly/rector-laravel --dev
            `}
		</Code>
	</div>
	<div>
		<Code  lang="php">
			{`
$rectorConfig->sets([
    LaravelSetList::LARAVEL_100
]);
            `}
		</Code>
	</div>

</Slide>
