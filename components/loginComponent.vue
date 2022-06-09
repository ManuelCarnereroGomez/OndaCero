<template>

    <!-- Primera pagina, iniciar sesion-->

    <div class="login__main">
        <div class="login__header">
            <img> <!-- LOgo ?? -->
        </div>

        <div class="login__register">
            <span class="register__connect--span">CONECTARSE</span>
            <span>Todavia no tienes una cuenta en OndaCero</span>
            <span><a href="" class="register__connect--link">Registrate</a></span>

            <div class="login__icons">
                <v-icon>mdi-google</v-icon>
                <v-icon>mdi-facebook</v-icon>
                <v-icon>mdi-apple</v-icon>
            </div>
        </div>

        <form class="login__session" method="post" @submit.stop.prevent="loginUser">
            <div class="login__inputs--div">
                <input class="login__input" type="email" name="email" id="email_input" v-model.trim="email_input" />
                <input class="login__input" type="password" name="password" id="password_input"
                    v-model="password_input" />
                <span>{{loginError}}</span>
                <input class="login_submit" type="submit" value="INICIAR SESIÓN"  />
            </div>


            <div class="login__forget">
                <span><a>¿Olvidaste tu contraseña?</a></span>
                <span>O<a>¿Prefieres entrar sin iniciar sesión?</a></span>
            </div>
        </form>


    </div>


</template>

<script>

export default {
    name: 'loginComponent',
    data() {
        return {
            email_input: '',
            password_input: '',
            loginError: ''
        }
    },
    methods: {
        loginUser() {
            const email = this.email_input;
            const password = this.password_input;

            /* userArray.forEach(user => {
                if (user.email === email && user.password === password) {
                    this.$router.push("/principal");
                }
            }) `prueba rellenar campos de la contraseña */

            if(email !== '' && password !== ''){
                this.$router.push("/principal");
                this.setUserLocal(email);
            }else {
                this.loginError = 'Rellena los campos'
            }
        },

        setUserLocal(email){
            localStorage.setItem('user', email.split('@')[0]);
        }
    }
}


/* const userArray = [{
    email: 'prueba@prueba.com',
    password: '123456'
}]; */

</script>

<style>
.login__main {
    height: 85vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.login__header {}

.login__register {
    width: 35%;
    height: 30%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
}

.register__connect--span {
    font-weight: bold;
    font-size: 1.5rem;
}

.register__connect--link {
    text-decoration: none;
    font-weight: bold;
    text-transform: uppercase;
}

.login__icons {
    width: 35%;
    display: flex;
    justify-content: space-around;
}

.v-icon {
    color: black !important;
}

.login__session {
    width: 50%;
    height: 50%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
}

.login__inputs--div {
    width: 100%;
    height: 50%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
}

.login__input {
    width: 50%;
    border: 1px solid #ccc;
}

.login_submit {
    border: 1px solid #ccc;
    width: 30%;
    font-weight: bold;
    text-transform: uppercase;
    background-color: #f1f1f1;
}

.login__forget {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.login__forget a {
    text-decoration: none;
    font-weight: bold;
    text-transform: uppercase;
}
</style>