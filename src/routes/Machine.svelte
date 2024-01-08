<script>
  import * as I from 'lucide-svelte'
  import * as Card from '$lib/components/ui/card'
  import { Progress } from '$lib/components/ui/progress'
  import { Button } from '$lib/components/ui/button'
  import { goto } from '$app/navigation'
  export let time, name, progress
</script>

<Card.Root class="p-2 pl-4 flex gap-4">
  <div class="flex flex-col gap-1 w-full">
    <span class="text-lg">
      {#if time == 'vacant'}
      <span class="text-green-600">Vacant</span>
      {:else}
      <span class="text-red-600">{time}</span>
      {/if}
       - {name}
     </span>
    <Progress value={progress} max={100} class="h-2" />
  </div>
  <div>
    <Button size="icon" variant="secondary" on:click={() => goto('/'+name)}>
      <I.ArrowUpRight strokeWidth={1} />
    </Button>
  </div>
</Card.Root>