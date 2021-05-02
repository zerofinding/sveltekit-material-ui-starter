<script>
  import { setContext } from 'svelte'

  import TopAppBar from '$lib/components/TopAppBar.svelte'
  import Drawer from '$lib/components/Drawer.svelte'

  let open = false
  const toggleNavigation = () => {
    open = !open
  }

  let theme = 'light'
  const handleTheme = () => {
    const html = document.querySelector('html')
    if(html.dataset.theme === 'light'){
      html.dataset.theme = 'dark'
    }else{
      html.dataset.theme = 'light'
    }
  }

  setContext('open', open)
  setContext('toggleNavigation', toggleNavigation)
  setContext('handleTheme', handleTheme)
</script>

<div
class="top-app-bar-container"
on:click={(event) => event.stopPropagation()}>
  <TopAppBar
  on:toggleNavigation={toggleNavigation} />

  <div
  class="drawer-container"
  on:click={(event) => event.stopPropagation()}
  style="padding-top: 55px">
    <Drawer
    {open}
    on:toggleNavigation={toggleNavigation} />

    <slot />
  </div>
</div>

<style>
.top-app-bar-container {
  width: 100%;
  border: 0px solid var(--mdc-theme-text-hint-on-background, rgba(0, 0, 0, 0.1));
  margin: 0;
  overflow: auto;
}

@media (max-width: 480px) {
  .top-app-bar-container {
    margin-right: 0;
  }
}
.drawer-container {
  position: relative;
  display: flex;
  min-height: 768px;
  border: 1px solid var(--mdc-theme-text-hint-on-background, rgba(0, 0, 0, 0.1));
  overflow: hidden;
  z-index: 0;
}
</style>