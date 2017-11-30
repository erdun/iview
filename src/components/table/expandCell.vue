
<template>
    <div :class="classes">
        <span
            :style="{'padding-left': `${this.indent * this.indentSpan}px`}"
        />
        <div :class="expandCls" @click.stop="onExpand">
            <Icon type="ios-arrow-right"></Icon>
        </div>
    </div>
</template>

<script>
    import Icon from '../icon/icon.vue';

    export default {
        name: 'ExpandCell',
        components: { Icon },
        props: {
            onExpand: {
                type: Function,
                default: () => {}
            },
            prefixCls: String,
            expandable: {
                type: Boolean,
                default: false,
            },
            expanded: {
                type: Boolean,
                default: false,
            },
            indent: {
                type: Number,
                default: 0
            },
            indentSpan: {
                type: Number,
                default: 10
            }
        },
        computed: {
            expandCls () {
                return [
                    `${this.prefixCls}-cell-expand`,
                    {
                        [`${this.prefixCls}-cell-expand-expanded`]: this.expanded,
                        [`${this.prefixCls}-hidden`]: !this.expandable
                    }
                ];
            },
            classes () {
                return [
                    `${this.prefixCls}-expandcell`,
                ];
            },
        },
    };
</script>
