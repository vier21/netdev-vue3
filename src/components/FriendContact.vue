<template>
    <div>
        <li>
            <h2>{{ nama }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
            <button @click="toggleFavorite">Toggle Favorite</button>
            <button @click="toggleDetail">{{ detailVisible ? 'Hide' : 'Show' }} Details</button>
            <ul v-if="detailVisible">
                <li><strong>Phone:</strong>{{ phoneNumber }}</li>
                <li><strong>Email:</strong>{{ emailAddress }}</li>
            </ul>
            <button @click="deleteContact">Delete</button>    
        </li>
    </div>
</template>

<script>

export default {
    props: {
        id: {
            type: String,
            required: true
        },  
        nama: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String
        },
        emailAddress: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false,
        }
    },
    //emits: {}
    emits: ['toggle-favorite','delete-contact'],
    data() {
        return {
            detailVisible: false,
        }
    },

    methods: {
        toggleDetail() {
            this.detailVisible = !this.detailVisible;
        },
        toggleFavorite() {
           this.$emit('toggle-favorite', this.id)
        },
        deleteContact() {
           this.$emit('delete-contact', this.id);
        }
    },
}
</script>

