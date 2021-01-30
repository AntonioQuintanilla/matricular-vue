<template>
  <div class="container mw-100 px-5 vh-100">
    <b-form class="p-0">
      <b-container class="text-light mw-100">
        <b-row cols="12" cols-sm="4" class="pt-3">
          <b-col class="d-flex align-items-center justify-content-end">
            <label class="m-0" for="nombre">Escriba el nombre</label>
          </b-col>
          <b-col>
            <b-form-input
              type="text"
              v-model="nuevoNombre"
              placeholder="Nombre..."
            ></b-form-input>
          </b-col>
        </b-row>
        <b-row cols="12" cols-sm="4" class="my-2">
          <b-col class="d-flex align-items-center justify-content-end">
            <label class="m-0" for="edad">Escriba la edad</label>
          </b-col>
          <b-col>
            <b-form-input
              type="number"
              v-model="nuevaEdad"
              placeholder="20"
            ></b-form-input>
          </b-col>
        </b-row>
        <b-row cols-sm="4" class="my-2">
          <b-col class="d-flex align-items-center justify-content-end">
            <label for="edad">Seleccione el sexo</label>
          </b-col>
          <b-col class="text-left m-2">
            <b-form-radio value="m" v-model="nuevoSexo">Masculino</b-form-radio>
            <b-form-radio value="f" v-model="nuevoSexo">Femenino</b-form-radio>
          </b-col>
        </b-row>
        <b-row cols-sm="4">
          <b-col class="d-flex align-items-center justify-content-end">
            <label for="edad">Agregar materia</label>
          </b-col>
          <b-col class="text-left">
            <div class="dropdown" @click="cambiar()">
              <button
                class="btn btn-primary dropdown-toggle"
                type="button"
                id="dropdownMenu2"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Dropdown
              </button>
              <ul class="dropdown-menu" aria-labelledby="dropdownMenu2">
                <li>
                  <button id="uno" class="dropdown-item" type="button">Action</button>
                </li>
                <li>
                  <button id="dos" class="dropdown-item" type="button">
                    Another action
                  </button>
                </li>
                <li>
                  <button id="tres" class="dropdown-item" type="button">
                    Something else here
                  </button>
                </li>
              </ul>
            </div>
          </b-col>
          <b-col align-self="start" class="text-left">
            <b-button variant="outline-primary" @click="agregarDato()"
              >Agregar Dato</b-button
            >
          </b-col>
        </b-row>
      </b-container>
    </b-form>

    <!--mostrar la data en un table-->
    <!--b-table striped hover :items="arreglo"></!--b-table-->
    <!-- <div class="container"> -->
    <b-table-simple class="mt-5 table-light table-striped">
      <b-thead class="thead-dark">
        <b-th>Nombre</b-th>
        <b-th>Edad</b-th>
        <b-th>Sexo</b-th>
        <b-th>Materias</b-th>
      </b-thead>
      <b-tbody>
        <b-tr v-for="dato in arreglo" :key="dato.nombre">
          <b-td>{{ dato.nombre }}</b-td>
          <b-td
            ><b-form-input type="number" v-model="dato.edad"></b-form-input
          ></b-td>
          <b-td>{{ dato.sexo == "m" ? "Masculino" : "Femenino" }}</b-td>
          <b-td>
            <b-dropdown
              id="dropdown-left"
              text="Materias"
              variant="outline-primary"
              class="dropdown m-2"
            >
              <b-dropdown-item href="#"></b-dropdown-item>
            </b-dropdown>
          </b-td>
          <!-- <b-td><span v-if="dato.edad >= 18">Mayor de edad</span></b-td> -->
        </b-tr>
      </b-tbody>
    </b-table-simple>
  </div>

  <!-- </div> -->
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    materia: String,
  },
  data() {
    return {
      arreglo: [
        { nombre: "Nahum", edad: 20, sexo: "m", materia: "" },
        { nombre: "Jose", edad: 5, sexo: "m", materia: "" },
        { nombre: "Maritza", edad: 15, sexo: "f", materia: "" },
      ],
      nuevoNombre: "",
      nuevaEdad: "",
      nuevoSexo: "",
      nuevaMateria: "",
    };
  },
  methods: {
    agregarDato() {
      this.arreglo.push({
        nombre: this.nuevoNombre,
        edad: this.nuevaEdad,
        sexo: this.nuevoSexo,
        materia: this.nuevaMateria,
      });
    },
    cambiar() {
      const drop = document.getElementById('dropdownMenu2');
      drop.addEventListener('change', () => {

      })
      const btn = document.querySelector('#uno');
      drop.innerHTML = btn.innerHTML;

      



    },
  },
};
</script>
