<script lang="ts">
	import { Notes, Slide, Code } from '@components'
	import Subheadline from './components/subheadline.svelte'
	import Item from './components/item.svelte'
	import Fit from '@lib/components/fit.svelte'
	import Cover from './components/cover.svelte'
	import Quote from './components/quote.svelte'
	import Image from './components/image.svelte'
</script>
<Slide>
    <Subheadline>Deploy del Venerdí?</Subheadline>
	<Subheadline>Soluzioni:</Subheadline>
	<Item>💡 Vietiamo il deploy al Venerdí 💡</Item>
	<Item>💡💡 Vietiamo il deploy al pomeriggio 💡💡</Item>
	<Item>💡💡💡 Vietiamo il deploy al mattino 💡💡💡</Item>
	<Item>🤯 Ok non effettuiamo mai il deploy 🤯</Item>
</Slide>

<Slide>
    <Subheadline>Nell'ecosistema Laravel abbiamo strumenti che hanno un impatto sulla nostra serenitá?</Subheadline>
	<p class="text-sm">Strumenti che hanno un impatto positivo sull'esperienza post-sviluppo</p>
</Slide>


<Slide>
    <Fit>Testing</Fit>
	<Subheadline>Da dove iniziare</Subheadline>
	<Subheadline>Cosa testare</Subheadline>
</Slide>
<Slide>
    <Fit>Tipologie di Team</Fit>
	<Image
		src="teams.png"
		alt="Tipologie di teams"
		height="" />

</Slide>

<Slide>
    <Fit>Testing: da dove iniziare</Fit>
	<Subheadline>Unit per business logic</Subheadline>
	<Subheadline>End to End per integrazioni</Subheadline>
	<Subheadline>Funzionali per web site</Subheadline>
	<Subheadline>UAT (test di accettazione utente) per apporovazioni da utenti finali</Subheadline>
	<Subheadline>...</Subheadline>
</Slide>

<Slide>
    <Fit>Testing: cosa testare</Fit>
<Code  lang="php" lines="8|11-13">
			{`
/** @test */
public function it_can_generate_a_dump_command_with_columnstatistics()
{
    $dumpCommand = MySql::create()
        ->setDbName('dbname')
        ->setUserName('username')
        ->setPassword('password')
        ->doNotUseColumnStatistics()
        ->getDumpCommand('dump.sql', 'credentials.txt');

    $expected = '\'mysqldump\' --defaults-extra-file="credentials.txt" --skip-comments --extended-insert --column-statistics=0 dbname > "dump.sql"';

    $this->assertSame($expected, $dumpCommand);
}
`}
</Code>
<p class="pt-6 text-sm">https://github.com/spatie/db-dumper/commit/8425cbf10b9a7149018ecd8624ac83b50ecaa8b2</p>

</Slide>

<Slide>
		<Cover
		banner="https://pestphp.com/www/assets/bg-head.webp"
		icon="https://pestphp.com/www/assets/logo.svg"
		headline="PestPHP"
		subheadline="The elegant PHP testing framework"
		title=""
		subtitle="">

	</Cover>

	<Notes>
		<b>Avoid eye contact.</b>
	</Notes>
</Slide>
<Slide animate>
	    <Subheadline>PestPHP: installazione</Subheadline>
	<div>
		<Code  lang="shell" lines="1|2|3">
			{`
composer require pestphp/pest --dev --with-all-dependencies
./vendor/bin/pest --init
./vendor/bin/pest
        `}
		</Code>
	</div>
</Slide>
<Slide animate>
	<Subheadline>PestPHP: dataset</Subheadline>
	<Code  lang="php" lines="3-5|6-8">
		{`
describe('Calculating Stat operation', function () {
    it('Mean', function () {
        expect(
            Stat::mean([1, 2, 3, 4, 4])
        )->toEqual(2.8);
        expect(
            Stat::mean([-1.0, 2.5, 3.25, 5.75])
        )->toEqual(2.625);
    });
});
        `}
	</Code>
</Slide>

<Slide animate>
	<Subheadline>PestPHP: dataset</Subheadline>
	<Code  lang="php" lines="3-6">
		{`
describe('Calculating Stat operation', function () {
    it('Mean chain expect', function () {
        expect(Stat::mean([1, 2, 3, 4, 4]))
            ->toEqual(2.8)
            ->and(Stat::mean([-1.0, 2.5, 3.25, 5.75]))
            ->toEqual(2.625);
    });
});
        `}
	</Code>
</Slide>

<Slide animate>
	<Subheadline>PestPHP: dataset</Subheadline>
	<Code  lang="php" lines="5|6-9">
		{`
describe('Calculating Stat operation', function () {
    it('Mean dataset', function (
        array $input, float $result
	) {
        expect(Stat::mean($input))->toEqual($result);
    })->with([
        [[1, 2, 3, 4, 4], 2.8],
        [[-1.0, 2.5, 3.25, 5.75], 2.625],
    ]);
});
        `}
	</Code>
</Slide>

<Slide animate>
	<Subheadline>PestPHP: dataset</Subheadline>
	<Code  lang="php" lines="3-6|7-14">
		{`
describe('Calculating Stat operation', function () {
    it('Dynamic operation', function (string $methodName, array $input, float $result) {
        expect(call_user_func(
            [Stat::class, $methodName],
            $input)
        )->toEqual($result);
    })->with([
        ["mean", [1, 2, 3, 4, 4], 2.8],
        ["mean", [-1.0, 2.5, 3.25, 5.75], 2.625],
        ["median", [1, 3, 5], 3],
        ["median", [1, 3, 5, 7], 4],
        ["medianLow", [1, 3, 5], 3],
        ["medianLow", [1, 3, 5, 7], 3],
    ]);
});
        `}
	</Code>
</Slide>

<Slide animate>
	<Subheadline>PestPHP: dataset</Subheadline>
	<Code lang="php" lines="13">
		{`
describe('Calculating Stat operation', function () {
    it('Dynamic operation with external dataset',
		function (
			string $methodName,
			array $input,
			float $result ) {
        expect(
            call_user_func(
                [Stat::class, $methodName],
                $input
            )
        )->toEqual($result);
    })->with('input1');
});
        `}
	</Code>
</Slide>

<Slide animate>
	<Subheadline>PestPHP: dataset</Subheadline>
	<Code  lang="php">
		{`
dataset("input1", [
    [ "mean", [1, 2, 3, 4, 4], 2.8],
    [ "mean", [-1.0, 2.5, 3.25, 5.75], 2.625],
    [ "median", [1, 3, 5], 3],
    [ "median", [1, 3, 5, 7], 4],
    [ "medianLow", [1, 3, 5], 3],
    [ "medianLow", [1, 3, 5, 7], 3],
]);
        `}
	</Code>
</Slide>

<Slide animate>
	<Fit>PestPHP: copertura dei test</Fit>

	<Code  lang="shell">
		{`
vendor/bin/pest --coverage

        `}
	</Code>
	<Image src="coverage.png"
	alt="Test Coverage"
	height=""
	/>
</Slide>
<Slide animate>
	<Fit>Unit tests sono sufficienti?</Fit>
	<Image src="unit_vs_integration_tests.gif"
	alt="Unit tests VS integration test"
	height=""
	/>
</Slide>
<Slide animate>
	<Subheadline>Teoria</Subheadline>

	<Quote><b>Test funzionali</b>: Per verificare che il software funzioni come dovrebbe in una situazione reale e che soddisfi i requisiti dell'utente.</Quote>

	<Quote><b>Test di integrazione</b>: Per testare la funzionalità di un gruppo di moduli diversi e capire come interagiscono tra loro.</Quote>

</Slide>
<Slide animate>
	<Subheadline>Terminologia Laravel</Subheadline>

	<Quote><b>Feature tests</b>: per testare il modo in cui diversi oggetti interagiscono tra loro o persino una richiesta HTTP completa a un endpoint JSON o l'interazione con un View Component.</Quote>

	<Quote><b>Browser test</b>: per testare la funzionalita' tramite l'interazione automatizzata con un browser web (Laravel Dusk).</Quote>

</Slide>
<Slide animate>
	<Subheadline>Feature test</Subheadline>
	<Image src="https://github.com/Hi-Folks/gh-actions-yaml-generator/raw/develop/github-actions-generator-laravel.png"
	alt="Screenshot di una form molto complessa" height="h-full" />
</Slide>

<Slide animate>
	<Subheadline>Feature test</Subheadline>
	<Code  lang="php" lines="1-12|3-8|9|10">
		{`
test('form_submit_test_matrix')
    ->livewire(ConfiguratorForm())
    ->set('name', 'Test')
    ->set('manualTrigger', false)
    ->set('onPush', true)
    ->set('matrixLaravel', true)
    ->set('matrixLaravelVersions', ['8.*' => '8.*'])
    ->set('stepPhpVersions', ['8.0', '7.4'])
    ->call('submitForm')
    ->assertSee(readAsset('on-push-branches.yaml'))
    ->assertSee(readAsset('mysql-service.yaml'))
    ->assertSee(readAsset('strategy-php-8-74.yaml'));
        `}
	</Code>
</Slide>
<Slide animate>
	<Subheadline>Feature test</Subheadline>
	<Code  lang="php">
		{`
name: Test
on:
  push:
    branches:
      - main
      - develop
      - features/**
        `}
	</Code>
</Slide>

<Slide animate>


	<Fit>Architettura del Software</Fit>
	<Quote>L'architettura del software si riferisce alla struttura organizzativa e al design fondamentale di un sistema software, che comprende componenti, moduli, interfacce e le relazioni tra di essi.</Quote>
	<p class="text-sm">https://pestphp.com/docs/arch-testing</p>
</Slide>

<Slide animate>

	<Fit>PestPHP: Architecture Testing</Fit>
	<Image
	src="pest-architecture-testing.png"
	alt="Pest PHP architecture testing" />

</Slide>

<Slide animate>
	<Fit>PestPHP: Architecture Testing</Fit>
	<Subheadline>Se volessimo evitare di utilizzare funzioni di "debug" in produzione</Subheadline>

	<Code  lang="php">
		{`
test('ensures no debugging')
    ->expect(['dd', 'dump', 'echo', 'print_r'])
    ->not->toBeUsed();

        `}
	</Code>
</Slide>

<Slide animate>
	<Fit>PestPHP: Architecture Testing</Fit>
	<Subheadline>Final o Non Final, questo é il problema. (Amleto nel 2023)</Subheadline>

	<Code  lang="php">
		{`
test('to be final')
    ->expect('HiFolks\\Statistics')
    ->classes()
    ->not->toBeFinal();
        `}
	</Code>
</Slide>
<Slide animate>
	<Fit>PestPHP: Architecture Testing</Fit>
	<Subheadline>Le classi di un certo tipo hanno uno specifico metodo?</Subheadline>
	<Code  lang="php">
		{`
test('make')
    ->expect('HiFolks\\Statistics\\Statistics')
    ->toHaveMethod('make');
        `}
	</Code>
	<p class="text-sm">E' anche vero che una regola di questo tipo puo' essere risolta a livello di definizione di interfacce</p>
	<Code  lang="php">
		{`
test('make')
    ->expect('HiFolks\\Statistics\\Statistics')
    ->toImplement('HiFolks\\Statistics\\Contracts\\ShouldMake');
        `}
	</Code>

</Slide>

<Slide animate>
	<Fit>PestPHP: Architecture Testing</Fit>
	<Subheadline>Le classi di un certo tipo hanno il metodo __construct() e __destruct() ?</Subheadline>
	<Code  lang="php">
		{`
test('constructor')
    ->expect('HiFolks\\Statistics\\Statistics')
    ->toHaveConstructor()
    ->toHaveDestructor();
        `}
	</Code>

</Slide>
