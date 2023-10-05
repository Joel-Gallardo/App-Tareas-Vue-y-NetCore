<template>
    <div>
        <h1 class="display-4 text-center">Listado de Tareas</h1>
        <hr>
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <div class="card mt-4">
                    <div class="card-body">
                        <div class="input-group">
                            <input type="text" v-model="tarea" class="form-control form-control-lg"
                                placeholder="Agregar Tarea " />
                            <div class="input-group-append">
                                <button class="btn btn-success btn-lg">
                                    Agregar
                                </button>
                            </div>
                        </div>
                        <br>
                        <ul class="list-group">
                            <li class="list-group-item d-flex justify-content-between">
                                <span class="cursor">
                                    <i class="fa-regular fa-circle"></i>
                                </span>
                                Hacer la tarea
                                <span class="text-danger cursor">
                                    <i class="fa-solid fa-trash-can"></i>
                                </span>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: 'TareaComponent'
}
</script>

<style scoped>
.cursor {
    cursor: pointer;
}
</style>