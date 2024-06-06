<template>

    <div id="app">

        <nav>

            <ul>

                <li><a href="#">Home</a></li>

                <li><a href="#">About</a></li>

                <li><a href="#">Services</a></li>

                <li><a href="contact.vue">Contact</a></li>

            </ul>

        </nav>

        <div class="container">

            <div class="gallery">

                <!-- Primera imagen con enlace -->

                <div class="gallery-item">

                    <a href="https://example.com/link1">

                        <img src="https://www.startpage.com/av/proxy-image?piurl=https%3A%2F%2Fimages.pexels.com%2Fphotos%2F1619317%2Fpexels-photo-1619317.jpeg%3Fcs%3Dsrgb%26dl%3Dpexels-souvenirpixels-1619317.jpg%26fm%3Djpg&sp=1717530425T33f07f10526b1b2636d67c6586fccd07682a9bdb8a150b4bda8806dbd405f93f"
                            alt="Gallery Image 1">

                    </a>

                </div>

                <!-- Segunda imagen con enlace -->

                <div class="gallery-item">

                    <a href="https://example.com/link2">

                        <img src="https://www.startpage.com/av/proxy-image?piurl=https%3A%2F%2Fthumbs.dreamstime.com%2Fb%2Fpaisajes-de-yosemite-46208063.jpg&sp=1717530425Tdd779996a416be91f90544bfcab367780b4b020e2b29f2f50fbe08ae0bb5726b"
                            alt="Gallery Image 2">

                    </a>

                </div>

                <!-- Tercera imagen con enlace -->

                <div class="gallery-item">

                    <a href="https://example.com/link3">

                        <img src="https://www.startpage.com/av/proxy-image?piurl=https%3A%2F%2Fst2.depositphotos.com%2F1852625%2F5395%2Fi%2F450%2Fdepositphotos_53954927-stock-photo-beautiful-landscape-of-scottish-nature.jpg&sp=1717530425Tde37db4837647574e983de0e6d6cf7f1ec37e472eba70debdc704d97c1ed22f7"
                            alt="Gallery Image 3">

                    </a>

                </div>

                <!-- Cuarta imagen con enlace -->

                <div class="gallery-item">

                    <a href="https://example.com/link4">

                        <img src="https://www.startpage.com/av/proxy-image?piurl=https%3A%2F%2Ft4.ftcdn.net%2Fjpg%2F07%2F06%2F72%2F43%2F360_F_706724318_SilctpdLGPefFMlHGTRwxE8of2AveaIv.jpg&sp=1717530425T15b54acea5b926602e4e5e4888fd4c4f6b224075b371cde6f26e899444d75320"
                            alt="Gallery Image 4">

                    </a>

                </div>

            </div>

            <div class="form-container">

                <div class="form-box">

                    <h1>Contact Form</h1>

                    <form @submit.prevent="submitForm">

                        <div class="form-group">

                            <label for="name">Name:</label>

                            <input type="text" id="name" v-model="formData.name" required />

                        </div>

                        <div class="form-group">

                            <label for="email">Email:</label>

                            <input type="email" id="email" v-model="formData.email" required />

                        </div>

                        <div class="form-group">

                            <label for="message">Message:</label>

                            <textarea id="message" v-model="formData.message" required></textarea>

                        </div>

                        <button type="submit">Submit</button>

                    </form>

                </div>

                <p v-if="responseMessage">{{ responseMessage }}</p>

            </div>

        </div>

    </div>

</template>



<script>

import axios from 'axios';



export default {

    name: 'ContactForm',

    data() {

        return {

            formData: {

                name: '',

                email: '',

                message: ''

            },

            responseMessage: ''

        };

    },

    methods: {

        async submitForm() {

            try {

                // Realiza la petición para enviar el formulario 

                await axios.post('http://localhost:3000/submit', this.formData);

                // Actualiza el mensaje de respuesta a "Enviado" 

                this.responseMessage = "Enviado";

            } catch (error) {

                console.error('There was an error!', error);

                // Si hay un error, muestra un mensaje de error 

                this.responseMessage = "Error al enviar";

            }

        }

    }

};

</script>



<style scoped>
#app {

    font-family: Avenir, Helvetica, Arial, sans-serif;

    -webkit-font-smoothing: antialiased;

    -moz-osx-font-smoothing: grayscale;

    text-align: center;

}



nav {

    background-color: #333;

    padding: 1rem;

}



ul {

    list-style: none;

    padding: 0;

}



li {

    display: inline;

    margin-right: 1rem;

}



a {

    color: white;

    text-decoration: none;

}



a:hover {

    text-decoration: underline;

}



.container {

    display: flex;

    justify-content: space-between;

    margin: 20px;

}



.gallery {

    flex: 2;

    display: flex;

    flex-wrap: wrap;

    gap: 10px;

    margin-right: 20px;

}



.gallery-item {

    flex: 1 1 calc(50% - 10px);
    /* Cambiado para mostrar solo dos imágenes en una fila */

    box-sizing: border-box;

}



.gallery-item img {

    width: 100%;

    height: auto;

    display: block;

}



.form-container {

    flex: 1;

}



.form-box {

    border: 1px solid #ccc;

    padding: 20px;

    border-radius: 10px;

    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);

}



.form-group {

    margin-bottom: 20px;

}



label {

    display: block;

    font-weight: bold;

    margin-bottom: 5px;

}



input[type="text"],

input[type="email"],

textarea {

    width: 100%;

    padding: 10px;

    border: 1px solid #ccc;

    border-radius: 5px;

}



button {

    padding: 10px 20px;

    background-color: #007bff;

    color: white;

    border: none;

    border-radius: 5px;

    cursor: pointer;

}



button:hover {

    background-color: #0056b3;

}
</style>