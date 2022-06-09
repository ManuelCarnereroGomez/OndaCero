<template>
    <div class="content">
        <div>
            <img class="tamanioimg" v-bind:src="albun" />
        </div>

        <div class="text">
            <template v-if="name.length > 17">
                <MARQUEE BEHAVIOR=ALTERNATE SCROLLDELAY =400>
                    <h1 class="tittle">{{name}}</h1>
                </MARQUEE>
            </template>

            <template v-if="name.length <= 17">
                <h1 class="tittle">{{name}}</h1>
            </template>
            
            <h2 class="subtittle">{{subName}}</h2>
        </div>
    </div>
</template>

<style>
.content {
    background-color: green;
    display: flex;
    border-radius: 15px;
    margin: 1% 1%;
}
.flex{
    display: flex;
}

.tamanioimg {
    width: 50px;
    height: 50px;
    padding: 2%;
    margin: 7% 1% -1% 9%;
    border-radius: 100%;
}

.text {
    margin-left: 5%;
    color: white;
    display: block;
}

.tittle {
    margin-top: 1%;
    font-weight: bold;
    width: 200px;
    font-size: 17px;

}

.subtittle {
    margin-top: -1%;
    font-size: 12px;
}
</style>

<script>
export default {
    name: 'radioComponets',
    props: {
        name: String,
        subName: String,
        albun: String
    }
}

</script>
