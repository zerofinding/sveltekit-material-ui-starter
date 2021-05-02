<script>
  import { getContext } from 'svelte'

  import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar'
  import IconButton from '@smui/icon-button'
  import Menu, { SelectionGroup, SelectionGroupIcon } from '@smui/menu'
  import List, { Item, Separator, Text } from '@smui/list'
  
  let prominent = false
  let dense = false
  let secondaryColor = false

  const toggleNavigation = getContext('toggleNavigation')
  const handleTheme = getContext('handleTheme')

  let menu
  let clicked = 'nothing yet'
  let selected1 = 'Red'
  let selected2 = 'Small'
</script>

<TopAppBar
variant="static"
{prominent}
{dense}
color={secondaryColor ? 'secondary' : 'primary'}
style="position: fixed;">
  <Row>
    <Section>
      <IconButton
      class="material-icons"
      on:click={toggleNavigation}>menu</IconButton>
      <Title>SvltKit Material UI</Title>
    </Section>
    <Section align="end" toolbar>
      <IconButton
      class="material-icons"
      aria-label="Download"
      on:click={handleTheme}>dark_mode</IconButton>
      <IconButton
      class="material-icons"
      aria-label="Print this page"
      on:click={(event) => event.stopPropagation()}
      on:mouseup={menu.setOpen(true)}>settings</IconButton>

      <Menu bind:this={menu} style="left:unset;right:unset;top: 60px">
        <List>
          <Item on:SMUI:action={() => (clicked = 'Save for Later')}>
            <SelectionGroupIcon>
              <i class="material-icons">account_circle</i>
            </SelectionGroupIcon>
            <Text>Account</Text>
          </Item>
          <Item on:SMUI:action={() => (clicked = 'Save for Later')}>
            <SelectionGroupIcon>
              <i class="material-icons">exit_to_app</i>
            </SelectionGroupIcon>
            <Text>Logout</Text>
          </Item>
        </List>
      </Menu>

    </Section>
  </Row>
</TopAppBar>

<style>
.flexy {
  display: flex;
  flex-wrap: wrap;
}

.flexor {
  display: inline-flex;
  flex-direction: column;
}

.flexor-content {
  flex-basis: 0;
  height: 0;
  flex-grow: 1;
  overflow: auto;
}
</style>