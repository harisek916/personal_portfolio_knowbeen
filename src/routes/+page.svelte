<script lang="ts">
  let pages = 1;
  let complexity = "basic";
  let features = 0;

  $: baseRate = 1000;
  $: total = baseRate * pages + (complexity === "advanced" ? 500 : 0) + features * 200;
</script>

<input type="number" bind:value={pages} min="1" />
<select bind:value={complexity}>
  <option value="basic">Basic</option>
  <option value="advanced">Advanced</option>
</select>
<input type="number" bind:value={features} min="0" />
<p>Total Estimated Cost: ₹{total}</p>
