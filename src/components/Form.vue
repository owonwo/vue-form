<template>
    <div class="Form">
        <div class="Form-Head align-self">
            <p class="poppins-bold text-center text-white">Try it for free 7 days <span class="poppins-reg">then $20/mo. thereafter</span></p>
        </div>

        <div class="Form-Body">
            <form action="#">
                <label for="" class="newLb">
                    <input type="text" placeholder="First Name" 
                    v-model="form.firstName" 
                    :class="error.line">  
                    <p class="mb-10 text-right text-red err">{{error.firstName}}</p>
                    <p class="errIcon" :class="error.icon"></p>
                </label>
                <label for="" class="newLb">
                    <input type="text" placeholder="Last Name" v-model="form.lastName" :class="error.line">
                    <p class="mb-10 text-right text-red err">{{error.lastName}}</p>
                    <p class="errIcon" :class="error.icon"></p>
                </label>
                <label for="" class="newLb">
                    <input type="email" placeholder="Email Address" v-model="form.emailAdd" :class="error.line">
                    <p class="mb-10 text-right text-red err">{{error.emailAdd}}</p>
                    <p class="errIcon" :class="error.icon"></p>
                </label>
                <label for="" class="newLb">
                    <input type="password" placeholder="Password" v-model="form.password" :class="error.line">
                    <p class="mb-10 text-right text-red err">{{error.password}}</p>
                    <p class="errIcon" :class="error.icon"></p>
                </label>

                <button @click.prevent="showModal" class="text-white poppins-reg cursor-point" type="submit">claim your free trial</button>
            </form>
            <p class="Form-Footer poppins-bold">By clicking the button, you are arguing to our <span class="Form-Terms">Terms and Services</span></p>
        </div>
    </div>
</template>


<script>
    export default{
        name: 'Form',
        props: ["form", "error"],
        methods:{
            showModal(){
                this.$emit('nowShow')
            }
        }
    }
</script>

<style>
    .Form{
        width: 500px;
    }

    .Form-Head{
        height: 60px;
        line-height: 60px;
        background:hsl(248, 32%, 49%);
        border-radius: 8px;
        box-shadow: 0 10px hsla(249, 10%, 26%, 0.2)
    }

    .Form-Head p{
        font-size: 15px;
    }

    .Form-Body{
        padding: 38px;
        background: #fff;
        margin-top: 32px;
        border-radius: 8px;
        box-shadow: 0 6px hsla(249, 10%, 26%, 0.15)
    }


    .Form-Body form input::placeholder{
        font-family: 'Poppins-Bold';
        color: hsla(249, 10%, 26%, 0.6)
    }

    .Form-Body form button{
        width: 100%;
        background: hsl(154, 59%, 51%);
        letter-spacing: 3px;
        margin-top: 13px;
        box-shadow: 0 4px hsla(154, 59%, 51%, 0.7);
    }

    .Form-Body form button:active{
        box-shadow: 0 2px;
        transform: translateY(2px)
    }

    .Form-Footer{
        color:hsl(246, 25%, 77%);
        font-size: 11px;
        text-align: center;
        margin-top: 20px
    }

    .Form-Terms{
        color:hsl(0, 100%, 74%)
    }

    .err{
        font-size: 13px;
        font-style: italic;
        font-family: 'Poppins-regular';
        margin-top: 4px;
    }

    .newLb{
        position: relative;
        z-index: 0
    }

    .red-border{
        border: 1.7px solid hsl(0, 100%, 74%);
    }

    .no-red-border{
        border: 1.43px solid hsl(246, 25%, 77%);
    }

    .errIcon{
        position: absolute;
        top: 0px;
        right: 10px;
        font-size: 22px;
        color: hsl(0, 100%, 74%)
    }
</style>