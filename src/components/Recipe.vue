<template>
    <div class="recipe">
        <div class="image-and-text">
            <img class="recipe-img" :src="recipe.imageUrl" :alt="recipe.title">
            <div class="title-and-description">
                <div class="title">
                    <h3>{{ recipe.title }}</h3>
                    <StarRating @star-click="starClick" :recipe="recipe" />
                </div>
                <p class="description">{{ recipe.description }}</p>
            </div>
        </div>
        <p class="under-text">{{ recipe.ingredients.length }} INGREDIENSER &nbsp; | &nbsp; {{ recipe.timeInMins }} MINUTER</p>
    </div>
</template>

<script>
    import StarRating from './StarRating.vue';
    export default {
        name: 'Recipe',
        props: {
            recipe: Object
        },
        components: {
            StarRating
        },
        methods: {
            starClick(id, number) {
                this.$emit('star-click', id, number)
            }
        }
    }
</script>

<style scoped>
    .recipe {
        background: #f4f4f4;
        margin: 5px 0;
        padding: 20px 20px;
        cursor: pointer;
        width: 750px;
        border-radius: 5px;
        box-sizing: border-box;
    }

    .recipe:hover {
        background: #e9e9e9;
    }

    .image-and-text {
        display: flex;
    }

    .title-and-description {
        display: flex;
        flex-direction: column;
        width: 100%;
    }

    .title {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .title h3 {
        margin: 0;
        width: 300px;
    }

    .recipe-img {
        border: 2px solid #ddd;
        border-style: outset;
        padding: 6px;
        width: 150px;
        height: 150px;
        margin-right: 25px;
        object-fit: cover;
        aspect-ratio: 1;
    }

    .description {
        color: #333;
    }

    .under-text {
        color: #555;
        margin-bottom: 0;
    }
</style>