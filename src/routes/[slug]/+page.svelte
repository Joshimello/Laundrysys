<script>
  import * as I from 'lucide-svelte'
  import { Button } from '$lib/components/ui/button'
  import { Progress } from '$lib/components/ui/progress'
  import { goto } from '$app/navigation'
  import { onMount } from 'svelte'
  import Chart from 'chart.js/auto'

  let chart
  onMount(() => {
    new Chart(chart, {
      type: 'line',
      data: {
        labels: ['8 AM', '9 AM', '10 AM', '11 AM', '12 PM', '1 PM', '2 PM'],
        datasets: [{
          label: 'usage',
          data: [0, 1, 1, 0, 1, 0, 0],
          fill: false,
          borderColor: '#000000'
        }]
      },
      options: {
        scales: {
          y: {
            ticks: {
              stepSize: 1,
              precision: 0
            },
            suggestedMax: 2
          }
        }
      }
    })
  })

</script>

<div class="p-4">
  <Button variant="secondary" class="flex items-center gap-2" on:click={() => goto('/')}>
    <I.ArrowLeft size="24" />
    <span class="text-lg">Return</span>
  </Button>
</div>

<div class="p-4 flex flex-col">
  <span class="font-bold text-3xl">F2 Washer #1</span>
  <span class="text-md text-lg text-red-600">Currently in use</span>
</div>

<div class="px-4 pt-4">
  <span class="text-xl font-bold">Progress</span>
</div>

<div class="p-4 flex items-end gap-4">
  <span class="text-5xl">23:10</span>
  <span class="text-xl">/ 30:00</span>
</div>

<div class="px-4 pb-4 flex flex-col gap-2">
  <Progress value={20} max={100} class="h-2" />
</div>

<div class="px-4 pt-4">
  <span class="text-xl font-bold">Usage</span>
</div>

<div class="p-4">
  <canvas bind:this={chart} />
</div>