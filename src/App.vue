<template>
  <div id="app">
    <Header />
    <Table />
  </div>
</template>

<script>
import Header from '@/components/Header'
import Table from '@/components/Table'
export default {
  name: 'App',
  components: {
    Header,
    Table
   
  }
}
</script>