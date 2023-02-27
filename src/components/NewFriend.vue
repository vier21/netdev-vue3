<template>
    <div class="nf-container">
        <form @submit.prevent="submitForm">
            <div>
                <input type="text" placeholder="Your Name" v-model="enteredName">

            </div>
            <div>
                <input type="text" placeholder="Email Address" v-model="enteredEmail">
                
            </div>
            <div>
                <input type="text" placeholder="Phone Number" v-model="enteredPhone">

            </div>
            <div>
                <input type="submit" value="Add Friend">
                
            </div>
        </form>
    </div>
</template>

<script>
export default {
    emits: {
        submit: (nama,email,phone) => {
            if (nama && email && phone) {
                return true
            } else {
                alert('Name, Email, And Phone Number is required');
                return false
            }
        }
    },
    data() {
        return {
            enteredName : '',
            enteredEmail: '',
            enteredPhone: ''
        }
    },
    methods: {
        submitForm() {
           
            this.$emit('submit',this.enteredName,this.enteredEmail,this.enteredPhone);
        }
    }  
}
</script>
<style>
.nf-container {
    display: flex;
    width: 100%;
    justify-content: center;
}

.nf-container form {
    text-align: center;
}

.nf-container input {
    margin: 10px;
    padding: 12px 20px;

}
.nf-container input[type=submit] {
    margin: 10px;
    padding: 12px 20px;
    background-color: #58004d;
    border: 1px solid black;
    color: white;
    border-radius:5px ;
    cursor:pointer;
    transition: 0.5s ease;
}

.nf-container input[type=submit]:hover {
   color: #58004d;
    background-color: #e9e6e9;
    
}

</style>