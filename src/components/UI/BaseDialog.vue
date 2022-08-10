<template>
    <div @click="$emit('close')"></div>
    <!-- Somehow this div for grabbing ::backdrop does not work? -->
    <dialog open>
        <header>
            <slot name="header">
                <h2>{{ title }}</h2>
            </slot>
        </header>
        <section>
            <slot name="sectionOne">
            </slot>
        </section>
        <menu>
            <slot name="actions">
                <base-button @click="$emit('close')">Close</base-button>
            </slot>
        </menu>
    </dialog>
</template>

<script>
export default{
    // another type of providing props option in vue script.
    props: {
        title: {
            type: String,
            required: false,
        }
    },
    emits:['close']
}
</script>

<style scoped>
dialog {
  position: fixed;
  top: 20vh;
  left: 10%;
  width: 80%;
  z-index: 100;
  border-radius: 12px;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 0;
  margin: 0;
  overflow: hidden;
}



header {
  background-color: #3a0061;
  color: white;
  width: 100%;
  padding: 1rem;
}



header h2 {
  margin: 0;
}



section {
  padding: 1rem;
}



menu {
  padding: 1rem;
  display: flex;
  justify-content: flex-end;
  margin: 0;
}



@media (min-width: 768px) {
  dialog {
    left: calc(50% - 20rem);
    width: 40rem;
  }
}

</style>