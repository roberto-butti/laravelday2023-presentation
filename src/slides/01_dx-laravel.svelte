<script lang="ts">
	import { Notes, Slide, Code, Step, Stack, FitText } from '@components'
	import Quote from './components/quote.svelte'
	import Fit from '@lib/components/fit.svelte'
	import SubHeadline from './components/subheadline.svelte'
	import Item from './components/item.svelte'
	import Subheadline from './components/subheadline.svelte'
	import Image from './components/image.svelte'
</script>

<Slide animate>
	<Fit>Laravel e</Fit>
	<Fit>Developer eXperience</Fit>
	<Quote>Esistono strumenti nell'ecosistema Laravel che mi permettono di avere una
		buona esperienza di sviluppo?</Quote>
</Slide>
<Slide animate>
	<Fit>Documentazione</Fit>
	<SubHeadline>Elementi di supporto all'esperienza di sviluppo con Laravel.</SubHeadline>

	<Item>Doc: https://laravel.com/doc</Item>
	<Item>API doc: https://laravel.com/api</Item>
	<Item>Bootcamp: https://bootcamp.laravel.com/</Item>
	<Item>Laracast: https://laracasts.com/</Item>
	<Item>e molto altro</Item>
</Slide>
<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<SubHeadline>Elementi per capire quello che sta succedendo durante l'esperienza di
		sviluppo.</SubHeadline>
</Slide>

<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<SubHeadline>Telescope</SubHeadline>
	<Image
		src="https://laravel.com/img/docs/telescope-example.png"
		alt="Telescope"
		height="" />
</Slide>

<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<SubHeadline>Horizon</SubHeadline>
	<Image
		src="https://laravel.com/img/docs/horizon-example.png"
		alt="Horizon"
		height="" />
</Slide>
<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<SubHeadline>Xdebug</SubHeadline>
	<Image
		src="https://cdn.hashnode.com/res/hashnode/image/upload/v1677943557435/177269f4-0d15-4eaf-9fc6-f918602d0fdc.png?auto=compress,format&format=webp"
		alt="xdebug"
		height="" />

</Slide>

<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<p class="text-8xl">dd()</p>
</Slide>
<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<p class="text-3xl">dd()</p>
    <p class="text-8xl">ray()</p>
</Slide>
<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<p class="text-3xl">dd()</p>
    <p class="text-3xl">ray()</p>
    <p class="text-8xl">dump()</p>
</Slide>
<Slide animate>
	<Fit>Strumenti per la diagnostica</Fit>
	<p class="text-3xl">dd()</p>
    <p class="text-3xl">ray()</p>
    <p class="text-3xl">dump()</p>
    <p class="text-5xl">Pure PHP: print_r(), var_dump(), var_export()</p>
</Slide>

<Slide animate>
	<Fit>Supporto per gli ambienti</Fit>
	<p>
		Elementi per configurare un ambiente di sviluppo locale.
	</p>
</Slide>
<Slide animate>
	<Fit>Supporto per gli ambienti</Fit>
	<Item>Laravel Herd</Item>
    <Item>Laravel Valet</Item>
    <Item>Laravel Sail</Item>
    <Item>PHP Monitor (or phpmon)</Item>
    <Item>php artisan serve</Item>
    <Item>php -S</Item>
</Slide>
<Slide animate>
	<SubHeadline>e molto altro...</SubHeadline>
	<Quote>
        Questi elementi hanno l'obiettivo di migliorare o supportare
        l'esperienza di sviluppo, mentre interagiamo con gli strumenti.
	</Quote>
</Slide>
<Slide animate>
	<p>→ mentre interagiamo con gli strumenti.</p>
</Slide>
<Slide animate>
	<p class="text-sm">→ mentre interagiamo con gli strumenti.</p>
    <p class="text-green-800">→ dopo aver terminato il lavoro</p>
</Slide>
<Slide animate>

    <p class="text-green-200">→ dopo aver terminato il lavoro</p>
    <Quote>La Developer eXperience é sufficientemente buona, nell' evitare preoccupazioni in momenti di non sviluppo?</Quote>
</Slide>
<Slide animate>

    <Fit>Siete pronti per il deploy del Venerdí?</Fit>
</Slide>
<Slide animate>
    <SubHeadline>Domanda riformulata</SubHeadline>
    <Quote>Quale é il livello di fiducia, di confidenza, nello prodotto che state rilasciando?</Quote>
    <p class="text-sm">Riferito all'artefatto o anche ai processi che governano il rilascio</p>
</Slide>
<Slide animate>
    <SubHeadline>Domanda riformulata versione 2</SubHeadline>
    <Quote>Quanta tensione, energia negativa, disagio vi portate a casa dopo che avete fatto un rilascio in produzione?</Quote>
    <p class="text-sm">"Se poi non funziona chiamano me nel weekend, ed il problema é che é talmente un casino che non so nemmeno quanto tempo potrei metterci a ripristinare la situazione"<br />CIT. un mio amico</p>
</Slide>