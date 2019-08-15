<template>
  <el-table :data="data" v-bind="attrs" v-on="event" ref="el-table">
    <template v-for="(item, index) in columns">
      <column-plus v-if="!item.hidden" :key="index" :attrs="item"></column-plus>
    </template>
  </el-table>
</template>

<script>
import ColumnPlus from './ColumnPlus';
export default {
  props: {
    data: {
      type: Array,
      required: true
    },
    columns: {
      type: Array,
      required: true
    },
    attrs: {
      type: Object,
      default: () => ({})
    },
    event: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    _attrs() {
      //默认table 参数
      const defaultParams = {};
      return Object.assign(defaultParams, this.attrs);
    }
  },
  components: {
    ColumnPlus
  },
  methods: {
    /**
     * 使用 el-table的方法
     */
    useTableFunc(FuncName, ...params) {
      if (!this.$refs['el-table']) {
        return console.warn('访问不到el-table');
      }
      if (!FuncName) {
        return console.error('请传入tabel方法名字');
      }
      this.$refs['el-table'][FuncName](params[0]);
    }
  },
  watch: {
    data() {
      this.$nextTick(() => {
        this.useTableFunc('doLayout');
      });
    }
  }
};
</script>

<style></style>
