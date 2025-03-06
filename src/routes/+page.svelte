<script>
  
  let numberList = $state([1,2,3,4,5,6,7,8,9,10])
  let selectedNumber = $state(0)
  let screens = ['landing', 'selecting']
  let whichScreen = $derived(selectedNumber === 0 ? screens[0] : screens[1])

  let standardMultiples = Array.from(Array(21).keys()).slice(1)

  const moreNumbers = () => {
    numberList = numberList.map(number => number + 10)
  }
  const lessNumbers = () => {
    numberList = numberList.map(number => number - 10)
  }

</script>
<div class="hero min-h-screen bg-teal-100/75">
{#if whichScreen === 'landing' }
<div class="hero-content text-center prose grid gap-8 card bg-base-100 shadow-sm">
  <div class="grid gap-4 grid-cols-5">
    {#each numberList as number, i}
    <button class="btn rounded-full w-12 h-12" onclick={() => {
      selectedNumber = number
      }} >{number}</button>
    {/each}
  </div>
  <div class="flex gap-2">
    <button onclick={moreNumbers} class="btn bg-transparent border-transparent text-2xl" disabled={numberList[numberList.length - 1] >= 50}>
      More
    </button>
    <button onclick={lessNumbers} class="btn bg-transparent border-transparent text-2xl" disabled={numberList[0] === 1}>
      Less
    </button>
    {selectedNumber}
  </div>
</div>
{:else}
  <div>
    <span>{selectedNumber}</span> x <span>{standardMultiples[0]}</span> = <span>?</span>
  </div>
{/if}
</div>