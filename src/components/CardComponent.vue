<template>
  <li>
    <img src="https://cdn-icons-png.flaticon.com/512/3135/3135715.png" alt="LogoImage">
    <slot name="card-header"></slot>
    <slot name="card-content"></slot>
  </li>
</template>

<script>
export default {

}
</script>

<style scope>
    li {
        margin: 1rem 0;
        font-size: 1.25rem;
        font-weight: bold;
        background: rgb(191, 247, 169);
        padding: 0.5rem;
        color: #000;
        border-radius: 25px;
    } 

    img {
        width: 100px;
        height: 100px;
    }
</style>