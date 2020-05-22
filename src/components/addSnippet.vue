<template>
    <div id="add-blog">
        <h2>Add New snippet</h2>
        <form v-if="!submitted">
            <label>Blog Title:</label>
            <input type="text" v-model.lazy="blog.title" required />
            <label>Blog Content:</label>
            <textarea v-model.lazy.trim="blog.content"></textarea>
            <!-- <div id="checkboxes">
                <p>Blog Categories:</p>
                <label>Ninjas</label>
                <input type="checkbox" value="ninjas" v-model="blog.categories" />
                <label>Wizards</label>
                <input type="checkbox" value="wizards" v-model="blog.categories" />
                <label>Mario</label>
                <input type="checkbox" value="mario" v-model="blog.categories" />
                <label>Cheese</label>
                <input type="checkbox" value="cheese" v-model="blog.categories" />
            </div> -->
            <label>Tag:</label>
            <select v-model="blog.tag">
                <option v-for="tag in tags" :key="tag">{{ tag }}</option>
            </select>
            <hr />
            <button v-on:click.prevent="post" class="addBlog">Add snippet</button>
        </form>
        <div v-if="submitted">
            <h3>Thanks for adding your post on this app</h3>
        </div>
        <div id="preview">
            <h3>Preview blog</h3>
            <p>Blog title: {{ blog.title }}</p>
            <p>Blog content:</p>
            <p style="white-space: pre">{{ blog.content }}</p>
            <!--<p>Blog Categories:</p>
             <ul>
                <li v-for="category in blog.categories">{{ category }}</li>
            </ul> -->
            <p>Tag: {{ blog.tag }}</p>
        </div>
    </div>
</template>

<script>
// Imports

export default {
    data () {
        return {
            blog: {
                
                title: '',
                content: '',
                // categories: [],
                tag: ''
            },
            tags: ['VueJs', ' Angular ', 'React'],
            submitted: false
        }
    },
    methods: {
        post: function(){
            this.$http.post('https://www.forverkliga.se/JavaScript/api/api-snippets.php?', { 
                 add:"",
                title: this.blog.title,
                content: this.blog.content,
                //userId: 1
            }).then(function(data){
                console.log(data);
                this.submitted = true;
            });
        }
    }
}
</script>

<style>
#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes label{
    display: inline-block;
    margin-top: 0;
}

.addBlog{
    width: 100%;
    height: 2em;
      background-color:cornflowerblue;
}
</style>
