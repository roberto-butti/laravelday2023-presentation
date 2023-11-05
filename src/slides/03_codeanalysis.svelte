<script lang="ts">
	import { Slide, Code } from '@components'
	import Subheadline from './components/subheadline.svelte'
	import Item from './components/item.svelte'
	import Fit from '@lib/components/fit.svelte'
	//import Cover from './components/cover.svelte'
	import Quote from './components/quote.svelte'
	import Image from './components/image.svelte'
	import Text from './components/text.svelte'
</script>

<Slide animate>
	<Fit>Dal "testare" all'"analizzare"</Fit>
	<Subheadline>Static analysis VS Code analysis</Subheadline>

</Slide>
<Slide animate>
	<Fit>Analisi del codice con Larastan</Fit>
	<Item>Larastan si concentra sulla ricerca di errori nel codice. Cattura intere classi di bug anche prima che si scrivano i test per il codice.</Item>
	<Item>Larastan é un PHPStan wrapper specifico per Laravel.</Item>
	<Item>Larastan avvia il contenitore dell'applicazione, in modo da poter risolvere tipi che è possibile calcolare solo in fase di esecuzione. Ecco perché usiamo il termine "analisi del codice" invece di "analisi statica".</Item>

</Slide>

<Slide animate>
	    <Subheadline>Larastan: installazione</Subheadline>
	<div>
		<Code  lang="shell">
			{`
composer require nunomaduro/larastan:^2.0 --dev
        `}
		</Code>
	</div>

</Slide>
<Slide animate>
	    <Subheadline>Larastan: configurazione (phpstan.neon)</Subheadline>
	<div>
		<Code  lang="yaml">
			{`
includes:
    - ./vendor/nunomaduro/larastan/extension.neon
parameters:
    level: 6
    paths:
        - app
        `}
		</Code>
	</div>

</Slide>
<Slide animate>
	    <Subheadline>Larastan: i livelli</Subheadline>
<ul class="text-xl">

<li>Livello 0: controlli di base, classi sconosciute, funzioni sconosciute, metodi sconosciuti chiamati su $this, numero errato di argomenti passati a tali metodi e funzioni, variabili sempre indefinite.</li>
<li>Livello 1: variabili eventualmente non definite, metodi e proprietà magiche sconosciute su classi con __call e __get.</li>
<li>Livello 2: metodi sconosciuti controllati su tutte le espressioni (non solo su $this), validazione di PHPDoc.</li>
<li>Livello 3: controllo sui tipi di ritorno, tipi assegnati alle proprietà.</li>
<li>Livello 4: controllo del dead code di base - controlli di instanceof e di altri tipi sempre falsi, condizioni else irraggiungibili, codice irraggiungibile dopo il ritorno; ecc..</li>
<li>Livello 5: controllo i tipi di argomenti passati ai metodi e alle funzioni.</li>
<li>Livello 6: segnalazione di typehints mancanti.</li>
<li>Livello 7: segnalazione di tipi di unione parzialmente errati - se si chiama un metodo che esiste solo su alcuni tipi in un tipo di unione, il livello 7 inizia a segnalarlo; altre situazioni eventualmente errate.</li>
<li>Livello 8: segnalazione di chiamata di metodi e l'accesso a proprietà su tipi nullable.</li>
<li>Livello 9: controllo rigoroso sul tipo mixed.</li>
</ul>
</Slide>

<Slide animate>
	    <Subheadline>Larastan: esecuzione</Subheadline>
		<Image
		src="phpstan.png"
		alt="esecuzione di larastan"
		heigth="h-full" />

</Slide>

<Slide animate>
    <Subheadline>Come introdurre Larastan in un progetto esistente?</Subheadline>
    <Text>
        PHPStan consente di dichiarare l'elenco di errori attualmente riportato come "baseline" e di evitare che venga riportato nelle esecuzioni successive. Ciò consente di interessarsi alle violazioni solo nel codice nuovo o modificato.
    </Text>
</Slide>

<Slide animate>
	    <Subheadline>Larastan: generazione della baseline</Subheadline>
<Image src="phpstan-baseline.png" alt="Generazione di una baseline" height="h-full"/>


</Slide>

<Slide animate>
	    <Subheadline>Larastan: configurazione con baseline</Subheadline>
	<div>
		<Code  lang="yaml" lines="3,5">
			{`
includes:
    - ./vendor/nunomaduro/larastan/extension.neon
    - ./phpstan-baseline.neon
parameters:
    level: 7
    paths:
        - app
        `}
		</Code>
	</div>

</Slide>

<Slide animate>
	<Subheadline>Larastan: generazione della baseline</Subheadline>
    <Image src="phpstan-basseline-execution.png" alt="Esecuzione di phpstan con baseline" height="h-full"/>
</Slide>

<Slide animate>
    <Subheadline>Come introdurre Larastan in un progetto esistente?</Subheadline>
    <Text>
        Altro approccio (diverso dalla baseline): partire da livello 0 e in maniera progressiva tamite <b>refactor</b> successivi applicare nuovi livelli.
    </Text>
</Slide>
