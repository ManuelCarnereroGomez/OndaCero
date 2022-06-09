 <!-- Hoja de card -->
 
<template>
    <main class="main__card">
        <div class="info__part">
            <span class="info__hour" >{{stHour+" - " + fnHour}}</span>
            <span class="info__title" v-text="cTitle"></span>
            <span class="info__presentator" v-text="cPresentatorName"></span>
        </div>
        <div class="presentatorimg__part">
            <v-img class="tamanio" :src="cPresentatorImg"></v-img>
        </div>
    </main>
</template>

<script>

export default {
    name: 'cardComponent',
    props: {
        stHour: String,
        fnHour: String,
        cTitle: String,
        cPresentatorName: String,
        cPresentatorImg: String

    }


}

</script>


<style>
.main__card {
    width: 26rem;
    height: 12rem;
    display: flex;
    background-color: rgb(68, 184, 68);
    position: relative;
    border-radius: 1.75rem;
    margin: 0 0.3%;
}

.info__part {
    display: flex;
    flex-direction: column;
    width: 100%;
    justify-content: space-between;
}

.info__hour {
    background-color: black;
    width: 100%;
    height: 2rem;
    display: flex;
    align-items: center;
    color: rgb(68, 184, 68);
    border-top-left-radius: 1.5rem;
    border-top-right-radius: 1.5rem;
    padding-left: 2.5rem;
}

.info__title {
    padding-left: 2.5rem;
    font-weight: bold;
    color: white;
    font-size: 1.5rem;
}

.info__presentator {
    padding-left: 2.5rem;
    color: white;
    margin-bottom: 2rem;
}

.presentatorimg__part {
    position: absolute;
    left: 50%;
}


.tamanio{
    width: 200px;
}
</style>