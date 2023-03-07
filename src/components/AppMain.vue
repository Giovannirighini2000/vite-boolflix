<template>
    <div class="container ">
        <div class="flex center gap">
            <p>
                Inserisci il nome del film che desideri cercare
            </p>
            <div class="freccia-effetto">
                →

            </div>
            <input @keyup.enter="$emit('onSearch')" type="text" v-model="store.search" placeholder="Cerca il nome del film "
                class="cerca">
        </div>


    </div>
</template>
  
<script>
import store from '../store'
export default {
    data() {
        return {
            store,
        }
    },

}
</script>
  
<style lang="scss" scoped>
.cerca {
    border: 1px solid rgb(77, 55, 16);
    width: 185px;
    height: 30px;
    border-radius: 8px;
    color: #9595d1;
}

.center {
    justify-content: center;
}

.gap {
    gap: 10px;
}

.freccia-effetto {
    font-size: 24px;
    color: #070fe7;
    position: relative;
    display: inline-block;
    transition: all 0.2s ease-in-out;
}

.freccia-effetto::before {
    content: '';
    position: absolute;
    width: 0;
    height: 100%;
    top: 0;
    right: 100%;
    background-color: #3a3ae7;
    transition: all 0.2s ease-in-out;
}

.freccia-effetto:hover {
    transform: translateX(8px);
}

.freccia-effetto:hover::before {
    width: 8px;
}
</style>