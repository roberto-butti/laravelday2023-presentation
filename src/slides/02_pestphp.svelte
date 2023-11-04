<script lang="ts">
	import { Notes, Slide, Code } from '@components'
	import Subheadline from './components/subheadline.svelte'
	import Item from './components/item.svelte'
	import Fit from '@lib/components/fit.svelte'
	import Cover from './components/cover.svelte'
	import Quote from './components/quote.svelte'
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
	<img src="public/teams.png" alt="Tipologie di teams"/>
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
	<Fit>Architettura del Software</Fit>
	<Quote>L'architettura del software si riferisce alla struttura organizzativa e al design fondamentale di un sistema software, che comprende componenti, moduli, interfacce e le relazioni tra di essi.</Quote>
	<p class="text-sm">https://pestphp.com/docs/arch-testing</p>
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
