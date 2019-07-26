<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i }" v-on:click="currentTab = i">
                    <svg class="icon">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>

                </li>

            </ol>
        </nav>
        <ol class="panes">

            <li v-bind:class="{active: currentTab === 0}">
                <ProfileEditor v-bind:profile="resume.profile" />
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                <ArrayEditor v-bind:items="resume.workHistory"
                 v-bind:labels="{company:'公司' ,content:'工作内容'}" title="工作经历" />
            </li>
            <li v-bind:class="{active: currentTab === 2}">      
                <ArrayEditor v-bind:items="resume.studyHistory" 
                v-bind:labels="{school:'学校' ,duration:'时间',degree:'学位'}" title="学习经历"/>                        
            </li>
            <li v-bind:class="{active: currentTab === 3}">
                <ArrayEditor v-bind:items="resume.Projects"
                 v-bind:labels="{name:'项目名称' ,content:'项目内容'}"  title="项目"/>  
            </li>
            <li v-bind:class="{active: currentTab === 4}">
                <ArrayEditor v-bind:items="resume.awards" 
                v-bind:labels="{name:'获奖详情'}" title="获奖情况"/>                  
            </li>
            <li v-bind:class="{active: currentTab === 5}">
                 <ArrayEditor v-bind:items="resume.contacts" 
                v-bind:labels="{qq:'QQ',wechat:'微信',email:'邮箱',phone:'手机号码'}" title="联系方式"/> 

            </li>
        </ol>
    </div>
</template>

<script>
import ProfileEditor from "./ProfileEditor";
import ArrayEditor from "./ArrayEditor";
export default {
    components: { ProfileEditor, ArrayEditor},
    props:['resume'],
    data() {
        return {
            currentTab: 0,
            icons: [
                "shenfenzheng",
                "work",
                "book",
                "Heart",
                "jiangbei",
                "weibiaoti-"
            ],
        };
    },
    methods: {},
    created() {}
};
</script>


<style lang="less">
#editor {
    min-height: 100px;
    display: flex;
    > nav {
        background: black;
        width: 80px;
        > ol > li {
            padding: 16px 0;
            text-align: center;
            > .icon {
                width: 24px;
                height: 24px;
                fill: white;
            }
            &.active {
                background: white;
                > .icon {
                    fill: black;
                }
            }
        }
    }
    > .panes {
        flex: 1;
        .container {
            position: relative;
            .el-icon-delete{
                position: absolute;
                right: 50px;
                top: -30px;
            }
        }
        > li {
            display: none;
            padding: 32px;
            height: 100%;
            width: 100%;
            overflow: auto;
            &.active {
                display: block;
            }
        }
    }
}
</style>
