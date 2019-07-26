<template>
    <div id="preview">
        <h1>{{resume.profile.name || '请填写名称'}}</h1>
        <p>{{resume.profile.city || '请填写城市'}} | {{resume.profile.birth || '请填写出生日期'}}</p>
        <hr>
        <section v-if="filter(resume.Projects).length > 0">
            <h2>项目</h2>
            <ul>
                <li v-for="project in filter(resume.Projects)">
                    {{project.name}}
                    {{project.content}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.workHistory).length > 0">
            <h2>工作经历</h2>
            <ul>
                <li v-for="work in filter(resume.workHistory)">
                    {{work.company}}
                    {{work.content}}
                </li>
            </ul>
        </section>
         <section v-if="filter(resume.studyHistory).length > 0">
            <h2>学习经历</h2>
            <ul>
                <li v-for="study in filter(resume.studyHistory)">
                    {{study.school}}
                    {{study.duration}}
                    {{study.degree}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.awards).length > 0">
            <h2>获奖情况</h2>
            <ul>
                <li v-for="award in filter(resume.awards)">
                    {{award.name}}
                </li>
            </ul>
        </section>

<section v-if="filter(resume.contacts).length > 0">
            <h2>联系方式</h2>
            <ul>
                <li v-for="contact in filter(resume.contacts)">
                    {{contact.qq}}
                    {{contact.wechat}}
                    {{contact.email}}
                    {{contact.phone}}                    
                </li>
            </ul>
        </section>
    </div>
</template>


<script>
export default {
    props: ['resume'],
    methods: {
        filter(array) { // 找出非空对象
            return array.filter( item=> !this.isEmpty(item))
        },
        isEmpty(object) { //只要有一个 value 不是 false ， 就返回 false
            let empty = true;
            for (let key in object) {
                if (object[key]) {
                    empty = false;
                    break;
                }
            }
            return empty;
        }
    }
};
</script>

<style>
#preview {
    display: flex;
    flex-direction: column;
    align-items: center;
    
}

</style>
