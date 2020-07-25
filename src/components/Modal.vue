<template>
    <div v-if="modal" class="Modal dc-flex j-center align-items">
        <span class="material-icons large text-white Modal-close cursor-point" style="font-size: 40px" @click="closeModal">close</span>
        <div class="Modal-content">
            <h2 class="text-center poppins-bold">Edit your details</h2>
            <form action="#">
                <label for="first name">
                    First name
                    <input type="text" :disabled ="disableState" :value="form.firstName" class="mb-10">
                </label>
                <label for="last name">
                    Last name
                    <input type="text" :disabled ="disableState" :value="form.lastName" class="mb-10">
                </label>
                <label for="email">
                    Email address
                    <input type="email" :disabled ="disableState" :value="form.emailAdd" class="mb-10">
                </label>
                <label for="password">
                    Password
                    <input type="password" :disabled ="disableState" :value="form.password" class="mb-10">
                </label>
                <div class="mt-10">
                    <button class="edit poppins-bold" @click.prevent="editForm">click to Edit</button>
                    <button type="submit" class="save poppins-bold" @click.prevent="showSuccess">Save & Finish</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>

    export default{
        name: 'Modal',
        data(){
            return{
                disableState: true
            }
        },
        props:["modal", "form"],
        methods:{
            closeModal(){
                this.$emit('nowClose')
            },
            editForm(){
                this.disableState = false
            }, 
            showSuccess(){
                this.$emit('showSuccessModal')
            }
        }
    }
</script>

<style scoped>
    .Modal{
        position: fixed;
        height: 100%;
        width: 100%;
        top: 0;
        left:0;
        z-index: 60;
        background: hsla(248, 32%, 49%, 0.7);
        backdrop-filter: blur(2px);
        transition: all .3s ease-in-out;
    }

    .Modal-close{
        position: absolute;
        top: 55px;
        right: 85px;
    }

    .Modal-content{
        width: 350px;
        background: #fff;
        border-radius: 6px;
        padding: 25px 35px;
        box-shadow: 0 6px hsla(249, 10%, 26%, 0.15)
    }

    .Modal-content h2{
        color: hsl(248, 32%, 49%);
        margin-bottom: 18px;
    }

    .Modal-content form label{
        font-family: 'poppins-regular';
        font-size: 16px;
    }

    .Modal-content form button{
        width: 48%;
        color: #fff;
    }

    .Modal-content form button:active{
        box-shadow: 0 2px;
        transform: translateY(2px)
    }

    .edit{
        background: hsl(248, 32%, 49%);
        box-shadow: 0 4px hsla(248, 32%, 49%, 0.4)
    }

    .save{
        float: right;
        background: hsl(154, 59%, 51%);
        box-shadow: 0 4px hsla(154, 59%, 51%, 0.7);
    }
</style>