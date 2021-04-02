<template>
    <div>
    <!-- Nav Bar Home and About -->
            <b-navbar>
        <template #brand>
            <b-navbar-item tag="router-link" :to="{ path: '/' }">
                <img
                    src="../assets/computer.png"
                    alt="Lightweight UI components for Vue.js based on Bulma"
                >
            </b-navbar-item>
        </template>
        <template #start>
            <b-navbar-item href="#">
                Home
            </b-navbar-item>
            <b-navbar-item href="#">
                About Me
            </b-navbar-item>

        </template>
    </b-navbar>

    <div class ="container">
        
        <!-- homepage -->
        <h1 class="title is-1"> Home Page </h1>
        <h2 class="subtitle is-3">Welcome </h2>

        <p1 class="has-text-left">
            This is Your study Tracker
        </p1>

        <!-- kolom nama dan source belajar -->
        <b-field class="has-text-left" label="Name / Subject" :label-position="labelPosition">
        <b-input v-model="formClassName"></b-input>
        </b-field>

        <b-field class="has-text-left" label="Source / Instructor name" :label-position="labelPosition">
        <b-input v-model="formInstructorName"></b-input>
        </b-field>
 
        <b-field class="has-text-left" label="Class Type"> 
        <!-- Radio field - free class or paid class -->
        <b-radio v-model="formClassType"
                native-value="Free Class">
                Free Class 
        </b-radio>
        <b-radio v-model="formClassType"
                native-value="Paid Class">
                Paid class 
        </b-radio>
        </b-field>    

         <div class="buttons">
            <b-button type="is-primary" expanded @click="addClass()">Add Class</b-button>
        </div>

<!-- memberikan horizontal ruler -->
<hr/>
        <!-- Memberikan collapse konten dan isi ke bawah -->
         <b-collapse
            class="panel"
            animation="slide"
            v-for="(ekskul, index) of ekskuls"
            :key="index"
            :open="isOpen == index"
            @open="isOpen = index">

            <template #trigger="props">
                <div
                    class="card-header"
                    role="button"
                >
                    <p class="card-header-title">
                        {{ ekskul.className }}
                    </p>
                    <a class="card-header-icon">
                        <b-icon
                            :icon="props.open ? 'menu-down' : 'menu-up'">
                        </b-icon>
                    </a>
                </div>
            </template>
            <div class="card-content">
                <div class="content">
                    Instructor: {{ ekskul.instructorName }} -- {{ekskul.classType}}
                </div>
            </div>
        </b-collapse>

    </div>

    </div>
</template>

<script>
export default {
    name:"HomePage",
    data() {
        return{ 
            formClassName: "",
            formInstructorName:"",
            formClassType:"free",
            
            ekskuls: [ //javascript array of objects
        { 
        className: "Introduction to web development",
        instructorName: "Andre Rusli",
        classType: "Paid",
        },
        {
        className: "Stock trading 101",
        instructorName: "Carolina Aprilia",
        classType: "Free",
        },
    ],        
        }
    },
    methods: { 
        addClass() {
            //add data to array in javascript
            this.ekskuls.push({
                className: this.formClassName,
                instructorName: this.formInstructorName,
                classType:this.formClassType,
            })   
        },
    }
};
</script>