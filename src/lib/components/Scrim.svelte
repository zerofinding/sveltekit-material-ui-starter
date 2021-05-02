<script>
  import { getContext } from 'svelte'

	import {
    Scrim,
  } from '@smui/drawer'

  const toggleNavigation = getContext('toggleNavigation')
</script>

<Scrim
fixed={false}
on:click={(event) => event.stopPropagation()}
on:mouseup={toggleNavigation} />