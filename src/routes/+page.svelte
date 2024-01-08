<script>
  import * as I from 'lucide-svelte'
  import * as Card from '$lib/components/ui/card'
  import { Button } from '$lib/components/ui/button'
  import Machine from './Machine.svelte'
  import machines from '$lib/machines'

  let tab = 'Washers'
</script>

<div class="p-4 flex flex-col">
  <span class="font-bold text-3xl">Hello, Justin</span>
  <span class="text-md text-lg">Time for laundry?</span>
</div>

<div class="p-4 flex gap-2">
  {#each [['Washers', I.WashingMachine], ['Dryers', I.DiscAlbum]] as [item, icon]}
  <Button variant="outline" class="p-4 w-full flex flex-col justify-between items-start h-24" on:click={() => tab = item}>
    <svelte:component this={icon} size="24" strokeWidth="1.5" />
    <span class="text-lg">{item}</span>
  </Button>
  {/each}
</div>

<div class="px-4 pt-4">
  <span class="text-xl font-bold">{tab} near you</span>
</div>

<div class="p-4 flex flex-col gap-2">
  {#each machines[tab.toLowerCase()] as { time, name, progress, near }}
  {#if near}
  <Machine {time} {name} {progress} />
  {/if}
  {/each}
</div>

<div class="px-4 pt-4">
  <span class="text-xl font-bold">Other {tab.toLowerCase()}</span>
</div>

<div class="p-4 flex flex-col gap-2">
  {#each machines[tab.toLowerCase()] as { time, name, progress, near }}
  {#if !near}
  <Machine {time} {name} {progress} />
  {/if}
  {/each}
</div>