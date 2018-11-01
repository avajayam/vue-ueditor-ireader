<template>
    <div>
        <script :id=id type="text/plain"></script>
    </div>
</template>
<style>
    @import './static/themes/default/css/ueditor.css';
    @import './static/themes/iframe.css';

    .v-modal { z-index: 999 !important }
    .el-dialog__wrapper { z-index: 1000 !important }
</style>
<script>
import './static/ueditor.config.js'
import './static/ueditor.all.js'
import './static/zh-cn.js'
import './static/ueditor.parse.js'

export default {
    name: 'ue',
    data () {
        return {
            editor: null
        }
    },
    model: {
        prop: 'ueContent',
        event: 'change'
    },
    props: {
        ueContent: {
            type: String
        },
        config: {
            type: Object
        },
        id: {
            type: String
        },
    },
    watch: {
        ueContent() {
            this.editor.setContent(this.ueContent)
        }
    },
    mounted() {
        const _this = this;
        this.editor = UE.getEditor(this.id, this.config);
        this.editor.addListener('ready', function () {
            _this.editor.setContent(_this.ueContent)
        });

        // 监听内容区变化
        // 并实时修改ueContent值
        this.editor.addListener('contentChange', function () {
            _this.$emit('change', _this.editor.getContent())
        })
    },
    methods: {
      // 获取内容
      getUEContent() {
          return this.editor.getContent()
      }
    },
    destroyed() {
      this.editor.destroy();
    }
}
</script>
