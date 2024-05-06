<template>
  <div>
    <h1>Superset</h1>
    <div id="superset-mount" ref="bla" />
  </div>
</template>
<script setup lang="ts">
import { embedDashboard } from '@superset-ui/embedded-sdk'
import { onMounted, ref } from 'vue'

const bla = ref(null)

const fetchGuestTokenFromBackend = async () => {
  // const response = await fetch('http://localhost:8088/api/v1/security/guest_token/', {
  //   method: 'POST',
  //   mode: 'no-cors',
  //   headers: new Headers([['Authentication', 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmcmVzaCI6dHJ1ZSwiaWF0IjoxNzE0OTk1NDM0LCJqdGkiOiI0MWQ2NWU5Zi1mMmZhLTRjZjQtOGRlYS1mMjc2MjNkZTAzOGIiLCJ0eXBlIjoiYWNjZXNzIiwic3ViIjoxLCJuYmYiOjE3MTQ5OTU0MzQsImV4cCI6MTcxNDk5NjMzNH0.Cz8VJqxtzlJ92AXm-BV6tS0DxrjWAlcEhKhnY11woFU']]),
  //   body: JSON.stringify({
  //     resources: [
  //       {
  //         id: '5d0d48f2-9b72-45f2-9a22-198ac64e6a9c',
  //         type: 'dashboard'
  //       }
  //     ],
  //     rls: [
  //       {
  //         clause: 'string',
  //         dataset: 0
  //       }
  //     ],
  //     user: {
  //       first_name: 'Superset',
  //       last_name: 'Admin',
  //       username: 'admin'
  //     }
  //   })
  // })
  // console.log('response', response);
  // const json = (await response.json()) as { token: string }
  // console.log('json', json);
  return "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjp7ImZpcnN0X25hbWUiOiJTdXBlcnNldCIsInVzZXJuYW1lIjoiYWRtaW4iLCJsYXN0X25hbWUiOiJBZG1pbiJ9LCJyZXNvdXJjZXMiOlt7ImlkIjoiMSIsInR5cGUiOiJkYXNoYm9hcmQifV0sInJsc19ydWxlcyI6W10sImlhdCI6MTcxNDk5OTk2Mi4wMDAwODksImV4cCI6MTcxNTAwMDI2Mi4wMDAwODksImF1ZCI6Imh0dHA6Ly9zdXBlcnNldDo4MDg4LyIsInR5cGUiOiJndWVzdCJ9.eoQ0VXw5pFFtGP9GG9H7NI0JAsajpnpBBKz-9l_PxxQ"
}

onMounted(() => {
  embedDashboard({
    id: '5d0d48f2-9b72-45f2-9a22-198ac64e6a9c',
    supersetDomain: 'http://localhost:8088',
    mountPoint: document.getElementById('superset-mount') as HTMLElement, // any html element that can contain an iframe
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
})

const guestToken = await fetchGuestTokenFromBackend()

console.log('guestToken', guestToken);
</script>
