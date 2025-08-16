<script>
import Ul from '../components/Ul.svelte'
import SingleBox from '../components/SingleBox.svelte'

const structure = [
  {
    title: 'first node',
    gender: 'm',
    spouse: {title: 'first node spouse', gender: 'f'},
    children: [
      {
        title: 'A node',
        gender: 'f',
        spouse: {title: 'A node spouse', gender: 'm'},
        children: [
          {
            title: 'third node child',
            gender: 'f',
            children: []
          }
        ]
      },
      {
        title: 'B node 2',
        gender: 'm',
        children: [
          {
            title: 'B node child',
            gender: 'm',
            children: []
          },
          {
            title: 'B node child',
            gender: 'm',
            children: []
          },
          {
            title: 'B node child',
            gender: 'm',
            children: []
          },
          {
            title: 'B node child',
            gender: 'f',
            spouse: {title: 'A node spouse', gender: 'm'},
            children: []
          },
          {
            title: 'B node child',
            gender: 'm',
            children: []
          }
        ]
      }
    ]
  }
]
</script>

<h1 class="text-4xl text-center p-4">FT</h1>

<div class="flex justify-center overflow-scroll max-h-svh max-w-svw">
  <ul class="tree">
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
</div>
