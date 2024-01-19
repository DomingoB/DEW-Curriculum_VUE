<script setup>
import { ref } from 'vue';

defineProps({
    msg: String,
})

const persona = ref({
    nombre: 'Pedro',
    apellidos: 'Picapiedra Jurasico',
    email: 'ejemplo@gmail.com',
    direccion: 'C/Suárez, nº 24',
    tlf: '922-111-111',
    educacion: [ {
        titulo: ['Técnico Informático de Sistemas y Ciberseguridad', 'Administrativo de Gestiones Financieras'],
        anio: ['200-222', '223-226'],
        descripcion: ['Uso de aplicaciones ofimáticas, programas de seguridad, desarrollo de aplicaciones', 'Organización y gestión de recursos, análisis y control de economía'],
        }
    ],
    experiencia: [ {
        nombreEmpresa: ['Riqeak Tecnology', 'Demils Economic S.L'],
        anio: ['230-235', '240-250'],
        cargo: ['Ayudante y soporte técnico de sistemas operativos', 'Jefe administrativo del departamento de economía'],
        }
    ],
    extras: [{
        idiomas: ['Español A2', 'Francés A2', 'Inglés C2'],
        hobbies: ['Ver la tele', 'Picar piedras', 'Comer'],
        permisoConducir: ['B1', 'C1'],
        vehiculo: ['Hundai i20', 'Ferrari Roma', 'MyCamion_Piedra'],
    }]
})
</script>


<template>
    <div class="container">
        <fieldset>
            <legend><h1>Información personal</h1></legend>
            <p><strong>Nombre Completo:</strong> {{ persona.nombre }} {{ persona.apellidos }}</p>
            <p><strong>Email:</strong> {{ persona.email.charAt(0).toUpperCase() + persona.email.slice(1).toLowerCase() }}</p>
            <p><strong>Dirección:</strong> {{ persona.direccion }}</p>
            <p><strong>Teléfono:</strong> {{ persona.tlf }}</p>
        </fieldset>

        <br/>

        <fieldset>
            <legend><h2>Objetivos/Perfil profesional</h2></legend>
            <p>
            ¿Qué es Lorem Ipsum?
            Lorem Ipsum es simplemente el texto de relleno de las imprentas y archivos de texto.
            Lorem Ipsum ha sido el texto de relleno estándar de las industrias desde el año 1500,
            cuando un impresor (N. del T. persona que se dedica a la imprenta) desconocido usó una galería de textos
            y los mezcló de tal manera que logró hacer un libro de textos especimen.
            </p>
        </fieldset>
        
        <br/>

        <fieldset>
            <legend><h2>Formación Académica</h2></legend>
            <div v-for="(formacion, index) in persona.educacion" :key="index">
                <div v-for="(titulo, index) in formacion.titulo" :key="index">
                    <div class="conjunto-datos">
                        <div class="derecha">
                            <p class="anio"><span>Años:</span> {{ formacion.anio[index] }}</p>
                        </div>
                        <div class="izquierda">
                            <p class="titulo"><span>Título:</span> {{ titulo }}</p>
                            <p class="descripcion">{{ formacion.descripcion[index] }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </fieldset>

        <br/>

        <fieldset>
            <legend><h2>Experiencia Laboral</h2></legend>
            <div v-for="(exp, index) in persona.experiencia" :key="index">
                <div v-for="(nombreEmpresa, index) in exp.nombreEmpresa" :key="index">
                    <div class="conjunto-datos2">
                        <p class="empresa"><strong>Nombre de la empresa:</strong>&nbsp; {{ nombreEmpresa }}</p>
                        <p><span>Años:</span> {{ exp.anio[index] }}</p>
                    </div>
                    <p class="cargo"><span>Cargo:</span>&nbsp; {{ exp.cargo[index] }}</p>
                </div>
            </div>
        </fieldset>
        
        <br/>

        <fieldset>
            <legend><h2>Extras</h2></legend>
            <div v-for="(otros, index) in persona.extras" :key="index">
                <div class="contenedor">
                    <div class="parte1">
                        <strong>Idiomas:</strong>
                        <div v-for="(idiomas, index) in otros.idiomas" :key="index">
                            <li>{{ idiomas }}</li>
                        </div>

                        <br/>

                        <strong>Hobbies:</strong>
                        <div v-for="(hobbies, index) in otros.hobbies" :key="index">
                            <li>{{ hobbies }}</li>
                        </div>
                    </div>

                    <br/><br/>
                
                    <div class="parte2">
                        <strong>Permisos de Conducir:</strong>
                        <div v-for="(permisoConducir, index) in otros.permisoConducir" :key="index">
                            <li> {{ permisoConducir }}</li>
                        </div>

                        <b/><br/><br/>

                        <strong>Vehículos: </strong>
                        <div v-for="(vehiculo, index) in otros.vehiculo" :key="index">
                            <li> {{ vehiculo }}</li>
                        </div>
                    </div>
                </div>
            </div>
        </fieldset>
    </div>
</template>



<style>
body {
    background-image: url('img/playa.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
}

.container {
    margin: 0 auto;
    padding: 15px;
    background-color: rgb(182, 181, 181);
    width: 50%;
}

h1, h2 {
    margin: 0;
    padding: 0;
    color: blue;
}

h1:hover, h2:hover {
    color: red;
}

fieldset {
    background-color: rgb(156, 155, 155);
    border: 1px solid blue;
}

fieldset:hover {
    background-color: rgb(190, 190, 190);
    border: 1px solid red;
}




.conjunto-datos {
    display: flex;
    margin-bottom: 30px;
}

.anio, .titulo {
    font-weight: bold;
}

span {
    text-decoration: underline;
    font-size: 18px;
}

.derecha {
    justify-content: start;
}

.izquierda {
    justify-content: end;
    text-align: left;
    margin-left: 350px;
}

.descripcion {
    margin: 0;
    font-size: 0.85em;
}



.conjunto-datos2 {
    display: flex;
    justify-content: space-between;
    margin: 0;
}

.empresa {
    font-size: 19px;
}

.cargo {
    margin: 0;
    margin-bottom: 30px;
}


.contenedor {
    display: flex;
}

.parte1 {
    justify-content: flex-start;
    margin-right: 350px;
}

.parte2 {
    justify-content: flex-start;
    text-align: left;
}
</style>

