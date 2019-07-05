<template>
  <div class="app">
    <dynamic-table
      :columns="columns2"
      :data="data"
      :attrs="tableAttr"
      :event="tableEvent"
    ></dynamic-table>
  </div>
</template>

<script>
import DynamicTable from "./components/DynamicTable";
export default {
  name: "App",
  data() {
    return {
      //table
      tableAttr: {
        height: `400px`,
        stripe: false,
        border: true,
        fit: true
      },
      tableEvent: {
        "selection-change": val => {
          console.log(val);
        }
      },
      columns2: [
        {
          type: "selection",
          width: "55"
        },
        {
          label: "City",
          prop: "city",
          width: 100
        },

        {
          label: "Address",
          prop: "address",
          width: 300
        },
        {
          label: "Postcode",
          prop: "zip",
          width: 200,
          sortable: true,
          "sort-method": function(a, b) {
            return b.zip - a.zip;
          }
        },
        {
          label: "Action",
          fixed: "right",
          width: "300",
          render: (h, params) => {
            return h("div", [
              h(
                "el-button",
                {
                  props: {
                    type: "primary",
                    size: "mini"
                  },
                  on: {
                    click() {
                      console.log(params);
                    }
                  }
                },
                "查看"
              ),
              h(
                "el-button",
                {
                  props: {
                    type: "primary",
                    size: "mini"
                  }
                },
                "删除"
              )
            ]);
          }
        }
      ],
      data: [
        {
          name: "John Brown",
          age: 18,
          address: "New York No. 1 Lake Park",
          province: "America",
          city: "New York",
          zip: 100010
        },
        {
          name: "Jim Green",
          age: 24,
          address: "Washington, D.C. No. 1 Lake Park",
          province: "America",
          city: "Washington, D.C.",
          zip: 100002
        },
        {
          name: "Joe Black",
          age: 30,
          address: "Sydney No. 1 Lake Park",
          province: "Australian",
          city: "Sydney",
          zip: 100007
        }
      ]
    };
  },
  components: {
    DynamicTable
  }
};
</script>
