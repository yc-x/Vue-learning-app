<template>
    <base-dialog v-if="inputIsInvalid" title="Input is invalid" @close="resetValid">
        <template #sectionOne>
            <p>Input is invalid, please check!</p>
            <p>lorem ipsum</p>
        </template>
        <!-- <template #actions>
            <base-button @click="resetValid">Got it</base-button>
        </template> -->
    </base-dialog>
    <base-card>
        <form @submit.prevent="submitResources">
            <div class="form-control">
                <label for="title">Title</label>
                <input id="title" name="title" type="text" ref="titleInput"/>
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea id="description" name="description" rows="3" ref="descriptionInput"></textarea>
            </div>
            <div class="form-control">
                <label for="link">Link</label>
                <input id="link" name="link" type="url" ref="linkInput"/>
            </div>
            <div>
                <base-button type="sbumit" >Add Resource</base-button>
            </div>
        </form>
    </base-card>
</template>

<script>
export default{
    inject:['addResource'],
    data(){
        return {
            inputIsInvalid: false,
        };
    },
    methods: {
        submitResources(){
            var enteredTitle = this.$refs.titleInput.value;
            var enteredDesc = this.$refs.descriptionInput.value;
            var enteredLink = this.$refs.linkInput.value;
            if(enteredTitle.trim() === '' || enteredDesc.trim() === '' || enteredLink.trim() === ''){
                this.inputIsInvalid = true;
                return;
            }
            //this.inputIsInvalid = false;
            //this.resetValid();
            this.addResource(enteredTitle, enteredDesc, enteredLink);
        },
        resetValid(){
            this.inputIsInvalid = false;
        }
    }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}



input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}



input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}



.form-control {
  margin: 1rem 0;
}
</style>