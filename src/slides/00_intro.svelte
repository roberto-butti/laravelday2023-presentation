<script lang="ts">
	import { Notes, Slide, Code } from '@components'
	import Bio from './components/bio.svelte'
	import Fit from '@lib/components/fit.svelte'
	import Quote from './components/quote.svelte'
	import Cover from './components/cover.svelte'
</script>

<Slide>
	<Cover
		banner="https://pestphp.com/www/assets/bg-head.webp"
		icon="https://a.storyblok.com/f/88751/166x166/38baa7f7ab/roberto-butti.png"
		headline="Roberto Butti"
		subheadline="Developer Relations Engineer"
		title="Vivere serenamente con Laravel"
		subtitle="Un viaggio nella Developer eXperience dell'ecosistema di Laravel">

	</Cover>
	<Notes>
		<b>Avoid eye contact.</b>
	</Notes>
</Slide>
<Slide animate>
	<div>
		<Code lang="php" lines="2-5|6|8-10|13-15|18-20|23-29|30-37">
			{`
<?php
$bio = [
    "name" => "Roberto Butti",
    "role" => "Developer Relations Engineer",
    "company" => "Storyblok",
    "conferences" => [
        [
            "name" => "PHPday Grusp Edition",
            "year" => 2022,
            "topic" => "Perché PHP"
        ],
        [
            "name" => "Laravel Day",
            "year" => 2022,
            "topic" => "Laravel Octane"
        ],
        [
            "name" => "Laracon EU",
            "year" => 2023,
            "topic" => "Laravel Octane"
        ]
    ],
    "opensource_projects" => [
        [
            "name" => "Some Drops of PHP",
            "url" => "https://drops-of-php.hi-folks.dev/"
            "description" => "The opensoruce book"
        ],
    ],
    "books" => [
        [
            "title" => "High Performance with Laravel Octane",
            "publication_year" => 2023,
            "author" => "Roberto Butti",
            "publisher" => "Packt"
        ],
    ]
];

        `}
		</Code>
	</div>
</Slide>
<Slide animate>
	<Fit>Developer eXperience</Fit>
</Slide>

<Slide animate>
	<Fit>Developer eXperience</Fit>
	<Quote>
		é la sensazione, é quel feeling, che come Developers proviamo con l'utilizzo
		di uno strumento
	</Quote>
</Slide>
