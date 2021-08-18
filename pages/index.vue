<template>
  <div>{{ result }}</div>
</template>

<script lang="ts">
import { gql } from 'graphql-tag'
import { defineComponent } from '@nuxtjs/composition-api'
import { useQuery, useResult } from '@vue/apollo-composable/dist'

export default defineComponent({
  setup() {
    const query = useQuery(gql`
      query {
        countries(filter: { currency: { eq: "EUR" } }) {
          code
        }
      }
    `)
    const result = useResult(query.result)

    return { result }
  },
})
</script>
