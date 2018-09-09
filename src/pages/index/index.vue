<template>
    <div>
        <i-button type="primary">这是一个按钮</i-button>
        <i-row>
            <i-col span="8" class="col-class">
                <i-button type="error">col-8</i-button>
            </i-col>
            <i-col span="8" class="col-class">
                col-8
            </i-col>
            <i-col span="8" class="col-class">
                <i-button type="error">col-8</i-button>
            </i-col>
        </i-row>
        <i-grid>
            <i-grid-item>
                <div style="background: #ccc;height: 200px;word-wrap: break-word;word-break: break-all;">aaaaaaaaaaaaaaaaaaaaaaaaaa</div>
            </i-grid-item>
            <i-grid-item>
                <div style="background: #ccc;height: 200px;word-wrap: break-word;word-break: break-all;">aaaaaaaaaaaaaaaaaaaaaaaaaa</div>
            </i-grid-item>
            <i-grid-item>Grid</i-grid-item>
            <i-grid-item>Grid</i-grid-item>
        </i-grid>
        <i-panel title="标题">
            <view style="padding: 15px;">PANEL 内容区域</view>
        </i-panel>
        <i-cell-group>
            <i-cell title="只显示箭头" is-link></i-cell>
            <i-cell title="跳转到首页" is-link url="/pages/dashboard/index">
                <span slot="footer">详情</span>
            </i-cell>
            <i-cell title="只有 footer 点击有效" is-link url="/pages/dashboard/index" only-tap-footer></i-cell>
            <i-cell title="开关" label="label">
                <switch slot="footer" checked />
            </i-cell>
        </i-cell-group>
        <i-button type="default" @click="toastHandle()">测试toast组件</i-button>
        <i-button type="default" @click="messageHandle()">测试message组件</i-button>
        <i-toast id="toast" />
        <i-message id="message" />
    </div>
</template>

<script>
    import { $Toast, $Message } from "../../../static/iview/base/index";
    export default {
        data () {
            return {};
        },
        mounted () {
            wx.login({
                success: function (res) {
                    if (res.code) {
                        console.log(res);
                    } else {
                        console.log("获取用户登录态失败！" + res.errMsg);
                    }
                }
            });
        },
        methods: {
            messageHandle () {
                $Message({
                    content: "测试message组件",
                    type: "success",
                    selector: "#message"
                });
            },
            toastHandle () {
                $Toast({
                    content: "测试toast组件",
                    type: "success",
                    selector: "#toast"
                });
            }
        }
    };
</script>

<style scoped>
    .col-class {
        text-align: center;
    }
</style>