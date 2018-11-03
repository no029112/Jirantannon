<template>
    <div>
        <form @submit.prevent="" class="form-horizontal">
            <fieldset>
                <p>
                    {{recipe}}
                </p>
                <!-- Form Name -->
                <legend>Form Name</legend>

                <!-- Text input-->
                <div class="form-group">
                    <label class="col-md-4 control-label" for="title">Title</label>
                    <div class="col-md-4">
                        <input id="title" name="title"  type="text" placeholder="" class="form-control input-md"  v-model="recipe.title" >

                    </div>
                </div>

                <!-- Text input-->
                <div class="form-group">
                    <label class="col-md-4 control-label" for="imageurl">Image URL</label>
                    <div class="col-md-4">
                        <input id="imageurl" name="imageurl" type="text" placeholder="" class="form-control input-md" v-model="recipe.imageurl">

                    </div>
                </div>
                <div class="row">
                    <div class="col-md-12">
                        <button class="btn btn-primary" @click="addIngredient">
                            <i class="fa fa-plus-circle"></i> more Ingredient
                        </button>
                    </div>
                </div>
                <!-- Text input-->
                <div class="form-group">
                    <label class="col-md-4 control-label" for="ingredient">ingredient</label>
                    <div class="col-md-4">
                        <div v-for="(ingredient,index) in recipe.ingredient" :key="index">
                        <input  v-model="recipe.ingredient[index]"
                         type="text" placeholder="" class="form-control input-md" >
                        </div>
                    </div>
                </div>

                <!-- Text input-->
                <div class="form-group">
                    <label class="col-md-4 control-label" for="description">Description</label>
                    <div class="col-md-4">
                        <input id="description" name="description" type="text" placeholder="" class="form-control input-md" v-model="recipe.descriptin">

                    </div>
                </div>

                <!-- Button (Double) -->
                <div class="form-group">
                    <label class="col-md-4 control-label" for="button1id"></label>
                    <div class="col-md-8">
                        <button id="button1id" name="button1id" class="btn btn-success">Submit</button>
                        <button id="button2id" name="button2id" class="btn btn-danger" @click="save">Cancel</button>
                    </div>
                </div>

            </fieldset>
        </form>
    </div>
</template>

<script>
export default {
        data(){
            return{
                recipe: {
                    title:'',
                    description:'',
                    image:'',
                    ingredient:['']

                } 

            }
        },  
        methods:{
            addIngredient () {
                this.recipe.ingredient.push('')
            },
            save () {
                this.$emit('saveRecipe', this.recipe)
            }
        }   
        
    }
</script>

<style scoped>
</style>