<template>
  <div>
    <h1>Superset</h1>
    <div id="superset-mount" ref="bla" />
  </div>
</template>
<script setup lang="ts">
import { embedDashboard } from '@superset-ui/embedded-sdk'
import { ref } from 'vue'

const bla = ref(null)

embedDashboard({
  id: '5d0d48f2-9b72-45f2-9a22-198ac64e6a9c', // given by the Superset embedding UI
  supersetDomain: 'https://superset.example.com',
  mountPoint: document.getElementById('superset-mount'), // any html element that can contain an iframe
  fetchGuestToken: () => fetchGuestTokenFromBackend(),
  dashboardUiConfig: {
    // dashboard UI config: hideTitle, hideTab, hideChartControls, filters.visible, filters.expanded (optional), urlParams (optional)
    hideTitle: true,
    filters: {
      expanded: true
    }
    // urlParams: {
    //   foo: 'value1',
    //   bar: 'value2',
    // ...
    // }
  }
})

const fetchGuestTokenFromBackend = () => {}
</script>
