<script>
/**
 * 动态渲染 el-table-column
 */
export default {
    name: 'ColumnPlus',
    props: {
        attrs: {
            type: Object,
            default: () => ({}),
            required: true
        }
    },
    render: function(h) {
        let attrs = this.attrs;
        let scopedSlots = {};
        if (attrs.render) {
            scopedSlots.default = scope => attrs.render(h, scope);
        }
        return h('el-table-column', {
            attrs,
            scopedSlots
        });
    }
};
</script>
