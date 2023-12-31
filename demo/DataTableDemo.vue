<template>
  <h3>Data Table</h3>
  <p>Data Table is used to display data in a table.</p>
  <h5>Demo:</h5>
  <div class="demo-wrapper">
    <DataTable :table-props="tableProps" />
    <DataTable :table-props="tablePropsGuide"></DataTable>
  </div>
  <h5>Usage:</h5>
  <h6>Insert component:</h6>
  <highlightjs language="html" :code="insertCode" />
  <h6>Import:</h6>
  <highlightjs language="js" :code="importCode" />
  <h6>Apply in template：</h6>
  <highlightjs language="js" :code="templateCode" />
  <FooterMessage />
</template>

<script>
import { computed } from "vue";
import { DataTable } from "../src";
import FooterMessage from "./common/FooterMessage.vue";
export default {
  name: "DataTableDemo",
  components: { DataTable, FooterMessage },
  setup() {
    const insertCode = computed(() => {
      return `
<DataTable :table-props="tableProps" />
      `;
    });
    const importCode = computed(() => {
      return `
import { DataTable } from "air-vue";
      `;
    });
    const templateCode = computed(() => {
      return `
const tableProps = computed(() => {
return {
  title: "Demo Data Table Title", //optional
  tableHead: [
    {
      label: "Product Name",
      field: "name",
    },
    {
      label: "Price($)",
      field: "price",
    },
    {
      label: "Weight(kg)",
      field: "weight",
    },
    {
      label: "Dimensions(w x h x d)",
      field: "dimensions",
    },
  ],
  tableBody: [
    { name: "Apple", price: "1.00", weight: "1.23", dimensions: "3x2x3" },
    ...
  ],
};
});
      `;
    });
    const tableProps = computed(() => {
      return {
        title: "Demo Data Table Title", //optional
        tableHead: [
          {
            label: "Product Name",
            field: "name",
          },
          {
            label: "Price($)",
            field: "price",
          },
          {
            label: "Weight(kg)",
            field: "weight",
          },
          {
            label: "Dimensions(w x h x d)",
            field: "dimensions",
          },
        ],
        tableBody: [
          { name: "Apple", price: "1.00", weight: "1.23", dimensions: "3x2x3" },
          { name: "Pear", price: "2.00", weight: "2.10", dimensions: "4x3x3" },
          {
            name: "Banana",
            price: "0.50",
            weight: "0.76",
            dimensions: "3x8x3",
          },
        ],
      };
    });
    const tablePropsGuide = computed(() => {
      return {
        title: "Props/Events Guide", //optional
        tableHead: [
          {
            label: "Name",
            field: "name",
          },
          {
            label: "Type",
            field: "type",
          },
          {
            label: "Required",
            field: "required",
          },
          {
            label: "Default",
            field: "default",
          },
          {
            label: "Description",
            field: "description",
          },
        ],
        tableBody: [
          {
            name: "table-props",
            type: "Object",
            required: "true",
            default: "-",
            description: "table head and content",
          },
        ],
      };
    });

    return {
      insertCode,
      importCode,
      templateCode,
      tableProps,
      tablePropsGuide,
    };
  },
};
</script>

<style lang="scss">
.demo-wrapper {
  > * {
    display: inline-block;
    margin-right: 50px;
  }
}
</style>
