<template>
    <header class="header">
        <div class="logo-container">
            <h1 class="logo">
                BOOLFIX
            </h1>
        </div>
        <div class="avatar flex">
            <div class="flex center gap">

                <input @keyup.enter="$emit('onSearch')" type="text" v-model="store.search"
                    placeholder="Cerca il nome del film " class="cerca">
                <div>
                    <button @click="$emit('onSearch')" class="cerca-2">
                        🔍

                    </button>
                </div>

            </div>

            <img src="https://banner2.cleanpng.com/20180623/iqh/kisspng-computer-icons-avatar-social-media-blog-font-aweso-avatar-icon-5b2e99c40ce333.6524068515297806760528.jpg"
                alt="Avatar" />
        </div>
    </header>
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
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 80px;
    color: white;
    padding: 0 20px;
}

.logo {
    color: red;

}

.logo:hover {
    transform: scale(1.3);
}

.avatar img {
    height: 50px;
    border-radius: 50%;
    aspect-ratio: 1;
    object-fit: cover;
}

.avatar {
    gap: 45px;
}

.logo-container {

    transform: scale(1);
    transition: transform 0.2s ease-in-out;
}

.cerca {
    border-radius: 10px;
    height: 30px;
    text-align: center;

}

.cerca-2 {

    border-radius: 6px;
    padding: 4px;


}

.cerca-2:hover {
    transform: scale(1.3);
}

.center {
    align-items: center;
}

.gap {
    gap: 10px;
}
</style>