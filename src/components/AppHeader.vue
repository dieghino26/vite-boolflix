<script>
export default {
    name: "AppHeader",
    data: () => ({ term: "" }),
    emits: ["form-submit"]
}
</script>

<template>
    <header>
        <h1>Boolflix</h1>
        <form @submit.prevent="$emit(`form-submit`, term)">
            <input type="text" v-model.trim="term">
            <button>Cerca</button>
        </form>
    </header>
</template>