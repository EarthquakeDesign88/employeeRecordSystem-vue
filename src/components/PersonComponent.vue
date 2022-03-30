
<template>
    <CardComponent>
        <template v-slot:card-header>
           <h1 class="child-component">ชื่อ : {{name}} </h1>
        </template>

        <template v-slot:card-content>
            <transition name="fade">
                <p>เพศ : {{gender}} เงินเดือน : {{salary}} บาท ตำแหน่ง : {{department}} ทักษะด้านภาษา : {{skill}}</p>
                <!-- <p>ตำแหน่ง : {{department}}</p>
                <p>ทักษะด้านภาษา : {{skill}}</p> -->
            </transition>
        </template>
        
    </CardComponent>
</template>

<script>
import CardComponent from './CardComponent.vue';
export default {
    name: "PersonComponent",
    components: {
        CardComponent
    },
    props: {
        name: {
            type: String,
            required: true
        },
        salary: {
            type: Number,
            default: 15000
        },
        department: {
            type: String,
            required: true
        },
        gender: {
            type: String,
        },
        skill: {
            type: Array,
        }
    }

}
</script>

<style scoped>
    h1 {
        color: #000;
    }
    p {
        color: #000;
    }
    button {
        font: inherit;
        cursor: pointer;
        border: 1px solid #ff0077;
        background: #ff0077;
        color: #fff;
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
    }
    button:hover {
        border: 1px solid #4edafa;
        background: #4edafa;
    }
    .fade-enter-from {
        opacity: 0;
    }
    .fade-enter-active {
        transition: all 0.5s linear;
    }
</style>