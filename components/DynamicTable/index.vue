<template>
    <el-table :data="data" v-bind="attrs" v-on="event">
        <column-plus
            v-for="(item, index) in columns"
            :key="index"
            :attrs="item"
        ></column-plus>
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
            return Object.assign(this.attrs, defaultParams);
        }
    },
    components: {
        ColumnPlus
    }
};
</script>

<style></style>
