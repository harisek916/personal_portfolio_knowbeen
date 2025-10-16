


<script lang="ts">
  let skills = ['SvelteKit', 'Angular', 'React', 'Django', 'Python','ASP.NET'];
  let pages = 1;
  let complexity = 'basic';
  let urgency = 'normal';
  let error = '';

  $: error = pages < 1 ? 'Number of pages must be at least 1' : '';

  $: cost = error
    ? 0
    : 100 + pages * 20 + (complexity === 'advanced' ? 200 : 100) + (urgency === 'urgent' ? 150 : 0);

</script>

<div class="p-6">
  <h1 class="text-3xl font-bold mb-4">About Me</h1>
  <p class="mb-4">Hi, I'm Muhammed Haris, a fullstack developer...</p>
  <h2 class="text-xl font-semibold mb-2">Skills</h2>
  <ul class="grid grid-cols-2 gap-2">
    {#each skills as skill}
      <li class="bg-gray-100 p-2 rounded">{skill}</li>
    {/each}
  </ul>
</div>



<div class="p-6 ">
  <h1 class="text-2xl font-bold mb-4">Service Cost Calculator</h1>

  <label for="pages" >Number of Pages:</label>
  <input id="pages" type="number" bind:value={pages} class="border p-2 mb-2" />

  <label for="complexity">Complexity:</label>
  <select id="complexity" bind:value={complexity} class="border p-2 mb-2">
    <option value="basic">Basic</option>
    <option value="advanced">Advanced</option>
  </select>

  <label for="urgency" >Urgency:</label>
  <select id="urgency" bind:value={urgency} class="border p-2 mb-2">
    <option value="normal">Normal</option>
    <option value="urgent">Urgent</option>
  </select>

  {#if error}
    <p class="text-red-500">{error}</p>
  {/if}

  <p class="mt-4 font-semibold">Estimated Cost: ₹{cost}</p>
</div>