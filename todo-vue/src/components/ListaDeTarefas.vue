<script setup>
    const props = defineProps(['tarefas', 'pendentes'])
</script>

<template>
    <ul v-if="props.pendentes.length > 0" class="clist-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo">{{tarefa.titulo}}</label>
        </li>
    </ul>
    <transition name="fade">
        <p v-if="pendentes.length === 0" class="alert alert-success mt-3 col-md-2" role="alert" > Você não tem pendencias </p>
    </transition>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity 0.6s ease;
    }
    .fade-enter-from, .fade-leave-to {
        opacity: 0;
    }

</style>
