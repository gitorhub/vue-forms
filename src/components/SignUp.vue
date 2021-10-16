<template lang="">
    <div class="container">
        <form class="form-group" @submit.prevent="submitForm">
            <label for="name" class="col-12">
                <input type="text" name="name" id="name" class="form-control col-12" v-model="name">
            </label>
            <label for="email" class="col-12">
                <input type="email" name="email" id="email" class="form-control col-12" v-model="email">
            </label>
            <label for="password" class="col-12" :class="{invalid: passwordError}">
                <input type="password" name="password" id="password" class="form-control col-12" v-model="password" @blur="formValidation">
                <p>{{passwordError}}</p>
            </label>
            <label for="department" class="department col-12 ">Select Department
                <select name="department" id="department" class="form-control" placeholder="Select Department"
                    v-model="department">
                    <option value="frontend">Frontend</option>
                    <option value="backend">Backend</option>
                    <option value="fullstack">Fullstack</option>
                </select>
            </label>
            <div class="langs col-12 d-flex">
                <label for="html" class="form-control">
                    <input type="checkbox" name="html" id="html" value="html" v-model="langs">
                    HTML
                </label>
                <label for="css" class="form-control">
                    <input type="checkbox" name="css" id="css" value="css" v-model="langs">
                    css
                </label>
                <label for="vue" class="form-control">
                    <input type="checkbox" name="vue" id="vue" value="vue" v-model="langs">
                    vue
                </label>
                <label for="js" class="form-control">
                    <input type="checkbox" name="js" id="js" value="js" v-model="langs">
                    js
                </label>
            </div>
            <div class="col-12 working-hour">
                <label for="remote">
                    <input type="radio" name="remote" id="remote" value="remote" v-model="working">
                    Remote
                </label>
                <label for="office">
                    <input type="radio" name="office" id="office" value="office" v-model="working">
                    Office
                </label>
            </div>
            <div class="col-12 hobby">
                <input class="form-control" placeholder="alt + ," type="text" v-model="hobby" @keyup.alt="addHobby">
            </div>
            <label for="terms" class="terms ">
                <input type="checkbox" name="terms" id="terms" v-model="terms">
                I approve Kvkk
            </label>
            <button class="btn btn-info col-12">Submit Form</button>
        </form>
        <div class="output col-12 d-flex flex-wrap">
            <p class="col-3">name: {{name}}</p>
            <p class="col-3">email: {{email}}</p>
            <p class="col-3">password: {{password}}</p>
            <p class="col-3">term: {{terms}}</p>
            <p class="col-3">department: {{department}}</p>
            <p class="col-3">langs: {{langs}}</p>
            <p class="col-3">working: {{working}}</p>
            <p class="col-3">hobby: {{hobby}}</p>
            <p class="col-12">hobbies: {{hobbies}}</p>
            <div class="col-12 d-flex flex-wrap" >
                <span class="p-2 m-3 badge badge-pill badge-secondary" v-for="hob in hobbies" :key="hob" @click="removeHobby(hob)">{{hob}}</span>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                name: "hussein",
                email: "",
                password: "",
                terms: false,
                department: "frontend",
                langs: [],
                working: "",
                hobby: "",
                hobbies: [],
                passwordError:""
            }
        },
        methods: {
            addHobby(e) {
                if (e.key == "," && this.hobby) {
                    console.log(e)
                    if (!this.hobbies.includes(this.hobby)) {
                        this.hobbies.push(this.hobby)
                    }
                    this.hobby = ""
                }
            },
            removeHobby(hob){
                this.hobbies=this.hobbies.filter(item=>{
                    return item != hob
                })
            },
            formValidation(){
                this.passwordError=this.password.length>6?"":"Password must be at least 6 chars length"

            },
            submitForm(){
                this.formValidation();
                
            }
        },
    }
</script>
<style >
.invalid input{
    border-color: #ff0000;
}
.invalid p{
    color:#ff0000;
}
</style>