<script lang="ts">
	import { GuessCharacterColor } from "./GuessCharacter";
	import { guesses } from "./stores";
</script>

<div class="guess-grid">
	{#each $guesses as guess}
		{#each guess.characters as character}
			<div
				class="guess-cell"
				class:invalid={!guess.isValid && character.value !== ""}
				class:submitted={guess.isSubmitted}
				class:green={character.color === GuessCharacterColor.Green}
				class:yellow={character.color === GuessCharacterColor.Yellow}
			>
				{character.value}
			</div>
		{/each}
	{/each}
</div>

<style>
	.guess-cell {
		border: 2px solid var(--color-light-gray);
		border-radius: 4px;
		box-sizing: border-box;
		font-size: 32px;
		height: 64px;
		text-transform: uppercase;

		display: flex;
		align-items: center;
		justify-content: center;
	}

	.guess-grid {
		display: grid;
		grid-template-columns: repeat(5, 64px);
		gap: 4px;
	}

	.invalid {
		border-color: var(--color-red);
	}

	.submitted {
		background: var(--color-gray);
		border-color: var(--color-gray);
		color: #ffffff;
	}

	.submitted.green {
		background: var(--color-green);
		border-color: var(--color-green);
	}

	.submitted.yellow {
		background: var(--color-yellow);
		border-color: var(--color-yellow);
	}
</style>
