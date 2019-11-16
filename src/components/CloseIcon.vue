<template>
    <div class="exitWrapper" @click="$emit('closeEvent')">
        <img src="@/assets/closeIcon.png" alt="Close Icon" >
    </div>
</template>
<script>
    export default {
    }
</script>

<style scoped>
.exitWrapper {
    width: 60px;
    height: 60px;
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}
.exitWrapper img {
    width: 30px;
    height: 30px;
}
</style>
