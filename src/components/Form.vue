<script setup>
    const props = defineProps(['adicionaTarefa',
    'estadoNovaTarefa',
    'alteraNovaTarefa',
    'alteraFiltro'
    ]);
</script>

<template>
    <form @submit.prevent="props.adicionaTarefa">
        <div class="row">
            <div class="col">
                <input
                @change="props.alteraNovaTarefa"
                :value="props.estadoNovaTarefa"
                required
                class="form-control"
                type="text"
                placeholder="Digite uma nova atividade">
            </div>
            <div class="col-md-2">
                <button
                type="submit"
                class="btn btn-primary">
                Adicionar
                </button>
            </div>
            <div
            @change="alteraFiltro"
            class="col-md-2">
                <select class="form-contorl">
                    <option value="todas">Todas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>