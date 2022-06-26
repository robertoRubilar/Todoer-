<template>
   <div class="container" style="max-width: 600px">
    <h2 class="text-center mt-5">Lista De Tareas</h2>
    <div class="d-flex mt-5">
      <input type="text" v-model="tarea" placeholder="Ingrese Una Tarea" class="w-100 form-control"/>

      <button class="btn btn-warning rounded-1" @click="crearTarea"> Crear </button>
    </div>

    <br> 
    <br> 

    <table class="table">

      <thead>
        <tr>
          <th scope="col">Tarea</th>
          <th scope="col">Estado</th>
          <th scope="col"></th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(tarea, index) in tareas" :key="index">
          <td>
            <span :class="{ 'line-through': tarea.estado === 'Terminado' }">
              {{ tarea.nombre }}
            </span>
          </td>
          <td>
            <span class="btn btn-warning rounded-1" @click="cambioEstado(index)">
              {{ tarea.estado }}
           </span>
          </td>

          <td class="text-center">
            <button class="btn btn-warning rounded-1" @click="eliminarTarea(index)"> Eliminar </button>
         </td>
        </tr>
      </tbody>

    </table>
    
  </div>
</template>

<script>
export default {
  tarea: "",
  name: "ListaTareas",
  

  data() {
    return {
      tarea: "",
     
      estados: ["Pendiente", "En progreso", "Terminado"],
     
      tareas: [
        {
          nombre: "Ingrese el nombre de la tarea",
          estado: "Pendiente",
        },
        {
          nombre: "Use el boton Crear para agregar la tarea.",
          estado: "En progreso",
        },

         {
          nombre: "Oprima el estado de la tarea para cambiarlo.",
          estado: "Terminado",
        },
      ],
    };
  },

  methods: {

 crearTarea() {
  
        this.tareas.push({
          nombre: this.tarea,
          estado: "Pendiente",
        });
         
    },


 eliminarTarea(index) {
      this.tareas.splice(index, 1);
    },
  
 cambioEstado(index) {
      let nIndex = this.estados.indexOf(this.tareas[index].estado);
      if (++nIndex > 2) nIndex = 0;
      this.tareas[index].estado = this.estados[nIndex];
    },
  },
};
</script>

<style>

</style>