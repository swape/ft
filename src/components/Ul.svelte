<script>
import Ul from '../components/Ul.svelte';
import SingleBox from '../components/SingleBox.svelte';
export let structure = [];


</script>
<ul>
{#each structure as node}
  <li>
    <div class="box-group">
        <SingleBox node={node} />
        {#if node.spouse}<SingleBox node={node.spouse} />{/if}
    </div>
    {#if node.children && node.children.length > 0}
    <Ul structure={node.children} />
    {/if}
  </li>
  {/each}
</ul>

