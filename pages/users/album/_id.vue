<template>
    <div class="container">
        <div class="columns is-centered">
            <div class="column is-four-fifths">
                <nav class="panel">
                    <p class="panel-heading has-text-centered">
                        <b-icon
                            icon="folder"
                            type="is-black"
                            size="is-small">
                        </b-icon>
                        Fotos del album <strong>{{ album.title }}</strong> de <strong>{{ user.username }}</strong>
                    </p>
                </nav>                
            </div>
        </div>    
        <div class="columns is-multiline is-centered">
            <div class="column is-6" v-for="photo in photos" :key="photo.id">
                <div class="card">
                        <div class="card-image">
                            <figure class="image is-5by4">
                                <img :src="photo.url" alt="Placeholder image">
                            </figure>
                        </div>
                        <div class="card-content">
                            <div class="content has-text-centered">{{ photo.title }}</div>
                        </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    import env from '../../../config/env'

    export default {
        name: 'AlbumUserPage',
        layout: 'navbar',
        async asyncData({ params, erro }){
            try{
                const Album = (await axios.get(`${env.endpoint}/albums/${params.id }`)).data
                const Photos = (await axios.get(`${env.endpoint}/photos?albumId=${params.id }`)).data
                const User = (await axios.get(`${env.endpoint}/users/${ Album.userId }`)).data
                return { album:Album, photos:Photos, user:User }
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
