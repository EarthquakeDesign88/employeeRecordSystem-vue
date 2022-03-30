
<template>
    <h1 class="child-component">{{message}}</h1>
    <form @submit.prevent="submitForm">
        <div class="form-control">
            <label for="emp-name">ชื่อพนักงาน</label>
            <input type="text" v-model.trim="employee.name">
        </div>
        <div class="form-control">
                <label for="emp-salary">เงินเดือน</label>
                <input type="number" v-model="employee.salary">
            </div> 
        <div class="form-control">
            <label for="emp-department">ตำแหน่งงาน</label>
            <select v-model="employee.department">
                <option value="โปรแกรมเมอร์">โปรแกรมเมอร์</option>
                <option value="ฝ่ายการตลาด">ฝ่ายการตลาด</option>
                <option value="ฝ่ายการขาย">ฝ่ายการขาย</option>
                <option value="ฝ่ายการเงิน">ฝ่ายการเงิน</option>
            </select>
        </div> 
        <div class="form-control">
            <h2>เพศ</h2>
            <div>
                <input type="radio" value="ชาย" v-model="employee.gender"> 
                <label for="Gender">ชาย</label>
            </div>
            <div>
                <input type="radio" value="หญิง" v-model="employee.gender"> 
                <label for="Gender">หญิง</label>
            </div> 
        </div> 
        <div class="form-control">
            <h2>ทักษะด้านภาษา</h2>
            <div>
                <input type="checkbox" value="ไทย" v-model="employee.skill"> 
                <label for="Skill">ไทย</label>
            </div>
            <div>
                <input type="checkbox" value="อังกฤษ" v-model="employee.skill"> 
                <label for="Skill">อังกฤษ</label>
            </div> 
            <div>
                <input type="checkbox" value="จีน" v-model="employee.skill"> 
                <label for="Skill">จีน</label>
            </div> 
        </div> 
        <div>
            <button>บันทึกข้อมูล</button>
        </div>
        <!-- {{ JSON.stringify(employee) }} -->
    </form>
</template>

<script>
export default {
    name: "FormComponent",
    data() {
        return {
            message: "แบบฟอร์มบันทึกข้อมูลพนักงาน",
            employee: {
                name: "",
                salary: 0,
                department: "โปรแกรมเมอร์",
                gender: "",
                skill: []
            }
        }
    },
    methods: {
        submitForm() {
            const newEmployee = {
                name: this.employee.name,
                salary: this.employee.salary,
                department: this.employee.department,
                gender: this.employee.gender,
                skill: this.employee.skill
            }
            this.$emit("save", newEmployee);
            this.resetForm();
        },
        resetForm() {
            this.employee.name = "";
            this.employee.salary = 0;
            this.employee.department = "โปรแกรมเมอร์";
            this.employee.gender = "";
            this.employee.skill = [];
        }
    }
}
</script>

<style scoped>
    h1 {
        text-align: center;
    }
    form {
        margin: 2rem auto;
        max-width: 40rem;
        border-radius: 12px;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
        background: #fff;
    }
    .form-control {
        padding: 5px 15px;
        margin: 0.5rem 0;
    }
    label {
        font-weight: bold;
    }
    input,select {
        display: block;
        width: 100%;
        font: inherit;
        margin-top: 0.5rem;
    }
    button {
        font:inherit;
        background: #fac532;
        border: 1px solid #fabd17;
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
        color: #fff;
        cursor: pointer;
        padding: 0.5rem 1rem;
        border-radius: 15px;
        margin: 0 0 15px 15px;
    }
    input[type="radio"], 
    input[type="checkbox"] 
    {
        display: inline-block;
        width: auto;
        margin-right: 1rem;
    }
    input[type="radio"] + label,
    input[type="checkbox"] + label {
        font-weight: normal;
    }
    h2 {
        font-size: 1rem;
        margin: 0.5rem 0;
    }
    button:hover {
        border: 1px solid #4edafa;
        background: #4edafa;
    }

</style>