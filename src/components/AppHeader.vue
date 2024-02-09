<script>
import { store } from "../data/store"
export default {
    name: "AppHeader",
    data: () => ({ store }),
    emits: ["form-submit"]
}
</script>

<template>
    <header>
        <h1>Boolflix</h1>
        <div>
            <input v-model="store.searchText" type="text" placeholder="Cerca il tuo film preferito"
                @keyup.enter="$emit('form-submit')">
            <button @click="$emit('form-submit')">
                Cerca
            </button>
        </div>
    </header>
</template>