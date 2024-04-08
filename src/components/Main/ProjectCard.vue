<template>
    <div class="col">
        <figure>
            <router-link :to="{ name: 'single-project', params: { slug: propsElement.slug } }">
                <img :src="'http://127.0.0.1:8000/storage/' + propsElement.cover_image" alt="">
            </router-link>
            
        </figure>
        <div class="info">
             <router-link :to="{ name: 'single-project', params: { slug: propsElement.slug } }" class="no-decoration">
                 <h3>{{ propsElement.title }}</h3>

             </router-link>
            <p>{{ propsElement.description }}</p>
            <span v-if="propsElement.type">Type: {{ propsElement.type.type }}</span>
            <p v-if="propsElement.technologies.length > 0">
                Technologies:
                <span v-for="(item, index) in propsElement.technologies" :key="item.id">
                    {{ item.name + ', ' }}
                </span>
            </p>

        </div>
    </div>
</template>

<script>
export default {
    name: "ProjectCard",
    props: [
        "propsElement"
    ],
    data() {

        return {}
    }
}
</script>

<style lang="scss" scoped>
@use "../../styles/partials/variables" as*;

.col {
    width: calc(100% / 5 - 20px + (20px / 5));

    figure {

        img {
            max-height: 200px;
        }
    }

    .info {
        background-color: #F9FCFB;
        padding: 20px;
        min-height: 200px;
        text-align: center;
        display: flex;
        flex-direction: column;
        gap: 10px;
        align-items: center;

        h3 {
            color: #f9a300;
            text-transform: uppercase;
            font-size: 20px;
            font-weight: bold;
        }

        p {
            text-transform: capitalize;
            font-size: 14px;
            letter-spacing: 1px;
        }

        span {
            text-transform: capitalize;
            font-size: 14px;
            letter-spacing: 1px;
            margin-block: 10px;
        }
    }
}
</style>