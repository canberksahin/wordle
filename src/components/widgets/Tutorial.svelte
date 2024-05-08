<script lang="ts">
	import { COLS, ROWS } from "../../utils";

	import { Tile } from "../board";
	export let visible: boolean;
</script>

<h3>Nasıl Oynanır</h3>
<div>Kelimeyi {ROWS} denemede <strong>KELİME</strong> etmeye çalışın.</div>
<div>Her tahmin geçerli bir {COLS} harfli kelime olmalıdır. Göndermek için enter tuşuna basın.</div>
<div>
	Her tahminden sonra, taşların rengi, tahmininizin kelimeye ne kadar yakın olduğunu göstermek için değişir.
</div>
<div class:complete={visible} class="examples">
	<div><strong>Örnekler</strong></div>
	<div class="row">
		<Tile value="k" state="🟩" />
		<Tile value="a" state="🔳" />
		<Tile value="l" state="🔳" />
		<Tile value="e" state="🔳" />
		<Tile value="m" state="🔳" />
	</div>
	<div>Harf <strong>K</strong> kelimenin içinde ve doğru yerde.</div>
	<div class="row">
		<Tile value="k" state="🔳" />
		<Tile value="i" state="🟨" />
		<Tile value="t" state="🔳" />
		<Tile value="a" state="🔳" />
		<Tile value="p" state="🔳" />
	</div>
	<div>Harf <strong>İ</strong> kelimenin içinde ancak yanlış yerde.</div>
	<div class="row">
		<Tile value="ç" state="🔳" />
		<Tile value="a" state="🔳" />
		<Tile value="t" state="🔳" />
		<Tile value="a" state="⬛" />
		<Tile value="l" state="🔳" />
	</div>
	<div>Harf <strong>A</strong> kelimenin hiçbir yerinde değil.</div>
</div>

<style lang="scss">
	div {
		margin: 14px 0;
	}
	.examples {
		border-top: 1px solid var(--border-primary);
		border-bottom: 1px solid var(--border-primary);
		:global(.row > *) {
			height: 100%;
			aspect-ratio: 1;
		}
		&:not(.complete) :global(.row .back) {
			transition-delay: 0.3s;
		}
	}
	.row {
		height: 40px;
		display: flex;
		gap: 4px;
	}
</style>