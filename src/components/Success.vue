<template>
    <div v-if="success" class="Success slideInUp d-flex j-center align-items">
        <p class="poppins-reg text-white">You Have Successfully Claimed Your Spot! 👏🏻👏🏻</p>
    </div>
</template>

<script>
export default{
    name: 'Success',
    props: ["success"]   
}
</script>

<style>
    .Success{
        position: absolute;
        transform: translate(-50%, -50%);
        top: 35px;
        right: 0;
        width: 600px;
        padding: 6px 25px;
        font-size: 17px;
        margin-bottom: 35px;
        border-radius: 6px;
        background: hsl(154, 59%, 51%);
        box-shadow: 0 4px hsla(154, 59%, 51%, 0.7);
    }


</style>