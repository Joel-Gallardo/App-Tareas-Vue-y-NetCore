<template>
    <div>
        <h1 class="display-4 text-center">Listado de Tareas</h1>
        <hr>
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <div class="card mt-4">
                    <div class="card-body">

                        <span v-if="errorMensaje" class="text-danger">{{ errorMensaje }}</span>

                        <div class="input-group mt-2">
                            <input type="text" v-model="tarea" class="form-control form-control-lg"
                                placeholder="Agregar Tarea " />
                            <div class="input-group-append">
                                <button v-on:click="agregarTarea()" class="btn btn-success btn-lg">
                                    Agregar
                                </button>
                            </div>
                        </div>
                        <br>

                        <h5 v-if="!listaTareas.length">No hay tareas, añade una nueva</h5>

                        <ul class="list-group">
                            <li v-for="(tarea, index) of listaTareas" :key="index"
                                class="list-group-item d-flex justify-content-between">
                                <span v-on:click="cambiarEstadoDeTarea(tarea, index)" class="cursor">
                                    <!-- <i v-bind:style="[ tarea.estado ? 'color: #1cab40;' : '' ]"
                                        v-bind:class="[ tarea.estado ? 'fa-solid fa-circle-check' : 'fa-regular fa-circle' ]"></i> -->

                                    <i v-if="!tarea.estado" class="fa-regular fa-circle"></i>
                                    <i v-if="tarea.estado" class="fa-solid fa-circle-check" style="color: #1cab40;"></i>
                                </span>
                                {{ tarea.nombre }}
                                <span v-on:click="eliminarTarea(index)" class="text-danger cursor">
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
    name: 'TareaComponent',
    data() {
        return {
            tarea: '',
            listaTareas: [],
            errorMensaje: ''
        }
    },
    methods: {
        agregarTarea() {

            if (!this.tarea.trim()) { // Verifica si el campo está vacío o solo contiene espacios en blanco
                this.errorMensaje = 'Por favor, ingresa una tarea antes de agregarla.';
                setTimeout(() => {
                    this.errorMensaje = ''; // Limpia el mensaje de error después de 2 segundos
                }, 6000);
                return;
            }

            const tarea = {
                nombre: this.tarea,
                estado: false
            }

            this.listaTareas.push(tarea);
            this.tarea = '';
            this.errorMensaje = '';
        },
        eliminarTarea(index) {
            this.listaTareas.splice(index, 1);
        },
        cambiarEstadoDeTarea(tarea, index) {
            this.listaTareas[ index ].estado = !tarea.estado
            // const tarea = document.querySelector('.cursor')
            // tarea.appendChild('I')
            // tarea.
        }
    }
}
</script>

<style scoped>
.cursor {
    cursor: pointer;
}
</style>