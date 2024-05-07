<template>
  <div>
    <nuxt-link to="/">Back to index</nuxt-link>

    <p>The columns duplicate two by two as you can see.</p>

    <p>When this page is reloaded, the duplication doesn't happen.</p>

    <el-table :data="data" row-key="id">
      <el-table-column label="column1" min-width="150px">
        <template v-slot="{ row }">
          <a :href="row.page.url" target="_blank">{{ row.page.url }}</a>
        </template>
      </el-table-column>

      <el-table-column label="column2">
        <template v-slot="{ row }">
          {{ row.page.status }}
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>
<script>
export default defineNuxtComponent({
  async asyncData() {
    const data = [
      {
        id: 1,
        page: {
          url: "http://test1",
          status: 401,
        },
      },
      {
        id: 4,
        page: {
          url: "http://test4",
          status: 200,
        },
      },
      {
        id: 7,
        page: {
          url: "http://test7",
          status: 404,
        },
      },
      {
        id: 10,
        page: {
          url: "http://test10",
          status: 500,
        },
      },
    ];
    return {
      data,
    };
  },
});
</script>
