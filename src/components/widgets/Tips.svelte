<script context="module" lang="ts">
	const tips = [
		"KELİME+'ya tıklayarak veya tahtayı sağa sola kaydırarak oyun modunu değiştirebilirsiniz.",
		"Zor mod, oyun moduna özeldir. Bir oyun modunda açarsanız diğerlerinde değişmeyecektir.",
		"Tahtadaki bir kelimenin anlamını öğrenmek için üzerine çift dokunun veya sağ tıklayın.",
		"Zor mod, zor mod kurallarını henüz ihlal etmediyseniz bir oyunda etkinleştirilebilir.",
		"Önceki tüm bilgileri kullanarak orada kaç olası kelimenin oynanabileceğini görmek için bir sonraki satıra çift dokunun veya sağ tıklayın.",
		"Kelimeler rastgele olarak listeden seçildiğinden, aynı kelimeyi tekrar almak mümkündür.",
		"Sol üst köşede yenileme düğmesini gördüğünüzde, yeni bir kelimenin hazır olduğu anlamına gelir.",
		"Herkes aynı anda aynı kelimeleri alır. Sizin kelime #73'ünüz, herkesin #73'üyle aynıdır.",
		"Mümkün olan tüm 5 harfli kelimelerin seçilebileceği doğru tahminlerden daha fazla geçerli tahmin vardır.",
		"Geçmiş oyunlar istatistiklerinize dahil edilmez. Geçmiş oyunlar, belirli bir oyun numarasına bir bağlantı takip ettiğinizde ortaya çıkar.",
		"Her oyun modu için en son geçmiş oyunun verileri yalnızca kaydedilir.",
	];
</script>

<script lang="ts">
	export let change: boolean;
	let index = Math.floor(tips.length * Math.random());
	$: if (change) index = Math.floor(tips.length * Math.random());

	function nextTip() {
		index = (index + 1) % tips.length;
	}
	function previousTip() {
		index = (index - 1 + tips.length) % tips.length;
	}
</script>

<div class="outer">
	<div class="number">Tip {index + 1}/{tips.length}</div>
	<div class="tip">{tips[index]}</div>
	<svg
		class="left"
		on:click={previousTip}
		on:keydown={previousTip}
		xmlns="http://www.w3.org/2000/svg"
		viewBox="0 0 100 100"
	>
		<path d="M75,0L25,50L75,100z" />
	</svg>
	<svg
		on:click={nextTip}
		on:keypress={nextTip}
		class="right"
		xmlns="http://www.w3.org/2000/svg"
		viewBox="0 0 100 100"
	>
		<path d="M25,0L75,50L25,100z" />
	</svg>
</div>

<style lang="scss">
	.outer {
		margin: 15px auto;
		padding: 10px 20px;
		max-width: calc(0.6 * var(--game-width));
		border: solid 1px var(--border-secondary);
		background: var(--bg-secondary);
		border-radius: 4px;
		position: relative;
	}
	.number {
		text-align: center;
		font-weight: bold;
		font-size: 1.2em;
		margin-bottom: 10px;
	}
	.left,
	.right {
		cursor: pointer;
		position: absolute;
		border-radius: 4px;
		background: var(--fg-primary);
		fill: var(--bg-primary);
		height: 45px;
		padding: 10px 0;
		top: 50%;
	}
	.left {
		left: 0;
		transform: translate(-50%, -50%);
	}
	.right {
		right: 0;
		transform: translate(50%, -50%);
	}
	.tip {
		text-align: center;
		min-height: 70px;
	}
</style>
