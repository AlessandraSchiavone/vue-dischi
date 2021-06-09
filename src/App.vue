<template>
  <div id="app">
   <Header/>
   <main>
      <DisksList />
    </main>
  </div>
</template>

<script>
import Header from './components/Header';
import DisksList from './components/DisksList';

export default {
  name: 'App',
  components: {
    Header,
    DisksList
    
  }
}
</script>

<style lang="scss">
@import './style/general';
</style>
