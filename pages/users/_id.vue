<template>
    <div class="container">
        <div class="columns is-centered">
            <div class="column is-half">
                <nav class="panel">
                    <p class="panel-heading">
                        <b-icon
                            icon="folder"
                            type="is-black"
                            size="is-small">
                        </b-icon>
                        Albums de <strong>{{ user.username }}</strong>
                    </p>
                    <nuxt-link v-for="album in albums" :key="album.id" class="panel-block" :to="'/users/album/'+album.id">{{ album.title }}</nuxt-link>
                    <div class="panel-block">
                        <nuxt-link class="button is-link is-outlined is-fullwidth" to="/">Regresas al inicio</nuxt-link>
                    </div>
                </nav>                
            </div>
        </div>    

    </div>
</template>

<script>
    import axios from 'axios';
    import env from '../../config/env';

    export default {
        name: 'UserPage',
        layout: 'navbar',
        async asyncData({ params, erro }){
            try{
                const _user = (await axios.get(`${env.endpoint}/users/${params.id }`)).data
                const _albums = (await axios.get(`${env.endpoint}/albums?userId=${params.id }`)).data
                return {user:_user, albums:_albums}
            }catch (e){
                console.log(e);
            }
        }
    }
</script>

<style>
    .panel{
        margin: 5px 20px 5px 20px !important;
    }
</style>    

