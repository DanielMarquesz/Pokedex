
<template>
    <div>
        <h1>{{name}}</h1>
        <small>{{url}}</small>
        <h1>{{num}}</h1>
    </div>    
</template>

<script>
export default {
    props: {
        num: Number,
        name: String,
        url: String
    }
}
</script>


<style scoped>

</style>