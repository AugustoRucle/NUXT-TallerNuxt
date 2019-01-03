<template>
    <div class="box box-photographer">
        <article class="media">
            <div class="media-left">
                <figure class="image is-128x128 image-photographer">
                  <img src="https://bulma.io/images/placeholders/128x128.png" alt="Image">
                </figure>
            </div>
            <div class="media-content">
                <div class="subtitle title-photographe">
                    <b-icon
                        icon="account"
                        size="is-medium">
                    </b-icon>
                    <strong>{{ photographer.username }}</strong>
                </div><br>
                <div class="subtitle subtitle-photographer">
                    <b-icon
                        icon="email"
                        size="is-small">
                    </b-icon>
                    <p>{{ photographer.email }}</p>
                </div><br>
                <div class="subtitle subtitle-photographer">
                    <b-icon
                        icon="web"
                        type="is-black"
                        size="is-small">
                    </b-icon>
                    <p>{{ photographer.website }}</p> 
                </div>
            </div>
        </article>
        <nuxt-link :to="'/users/'+photographer.id" class="button is-black is-medium is-fullwidth">Albums</nuxt-link>
    </div>
</template>

<script>
export default {
    name:"BoxProfile",
    props:{
        photographer: Object
    }
}
</script>

<style>
    .box-photographer{
        margin: 10px 10px 0px 10px !important;
        padding: 30px 20px 15px 30px;
    }

    .subtitle-photographer, .title-photographer{
        display: inline-flex;
        font-size: 18px;
        margin: 5px 5px 10px 2px !important;
    }
    .media-content{
        min-height: 200px;
    }

    .subtitle-photographer p{
        margin-left: 20px;
    }

    .title-photographe{
        margin: 0px !important;
    }

    .title-photographe strong{
        font-size: 23px !important;
        margin: 0px !important;
    }
</style>
