<template>
  <q-page class="column">
    <div class="q-ma-md" style="max-width: 400px">
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <q-input filled v-model="username" label="Username" />
        <q-input filled v-model="password" label="Password" type="password" />

        <!-- <q-toggle v-model="accept" label="I accept the license and terms" /> -->

        <div>
          <q-btn label="Login" type="submit" color="primary" />
          <!-- <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" /> -->
        </div>
      </q-form>

      <q-form @submit="atten" @reset="onReset" class="q-gutter-md">
        <div>
          <q-btn label="Mark Attendance" type="submit" color="primary" />
          <!-- <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" /> -->
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { useQuasar } from 'quasar';
import { ref } from 'vue';

export default {
  setup() {
    const $q = useQuasar();

    const username = ref('baghdad__raza');
    const password = ref('Rz4sjX86RCgjHPA');

    return {
      username,
      password,

      async onSubmit() {
        const myHeaders = new Headers();
        myHeaders.append('Content-Type', 'application/json');
        myHeaders.append('Accept', 'application/json');

        myHeaders.append(
          'Access-Control-Allow-Origin',
          'http://localhost:3000'
        );
        myHeaders.append('Access-Control-Allow-Credentials', 'true');

        myHeaders.append('GET', 'POST', 'OPTIONS');

        const raw = JSON.stringify({
          username: 'asd',
          password: 'qwe',
        });

        const requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          // redirect: 'follow',
          credentials: 'include',
          mode: 'cors',
        };

        fetch('https://flask-hello-world-ktjt.vercel.app/login', requestOptions)
          .then((response) => response.text())
          .then((result) => console.log(result))
          .catch((error) => console.error(error));
        // try {
        //   const response = await fetch(
        //     'https://flask-hello-world-ktjt.vercel.app/login',
        //     {
        //       method: 'POST',
        //       headers: {
        //         'Content-Type': 'application/json',
        //         Accept: 'application/json',
        //       },
        //       body: JSON.stringify({
        //         username: username.value,
        //         password: password.value,
        //       }),
        //     }
        //   );

        //   if (!response.ok) {
        //     console.log(reponse);
        //     throw new Error('Login failed');
        //   }

        //   const data = response;
        //   const token = data;

        //   // Store the token in local storage
        //   localStorage.setItem('token', token);
        //   // Redirect to the protected page
        //   // window.location.href = '/protected-page';
        // } catch (error) {
        //   // messageElement.textContent = 'Login failed: ' + error.message;
        //   console.log(error.message);
        // }

        // const myHeaders = new Headers();
        // myHeaders.append(
        //   'Accept',
        //   'application/json, text/javascript, */*; q=0.01'
        // );
        // myHeaders.append('Accept-Language', 'en-US,en;q=0.9');
        // // myHeaders.append('Cache-Control', 'no-cache');
        // myHeaders.append('Connection', 'keep-alive');
        // myHeaders.append(
        //   'Content-Type',
        //   'application/x-www-form-urlencoded; charset=UTF-8'
        // );
        // myHeaders.append('DNT', '1');
        // myHeaders.append('Origin', 'https://eureka.ilmversity.net');
        // myHeaders.append(
        //   'Referer',
        //   'https://eureka.ilmversity.net/school/site/login'
        // );
        // myHeaders.append('Sec-Fetch-Dest', 'empty');
        // myHeaders.append('Sec-Fetch-Mode', 'cors');
        // myHeaders.append('Sec-Fetch-Site', 'same-origin');
        // myHeaders.append('X-Requested-With', 'XMLHttpRequest');

        // const raw = `LoginForm%5Busername%5D=${username.value}&LoginForm%5Bpassword%5D=${password.value}&LoginForm%5BrememberMe%5D=1`;

        // const requestOptions = {
        //   method: 'POST',
        //   headers: myHeaders,
        //   body: raw,
        //   mode: 'cors',
        //   //credentials: 'same-origin',
        //   //credentials: 'include',
        // };

        // const url = 'https://eureka.ilmversity.net/school/site/login';
        // fetch(new Request(url, { redirect: 'manual' }), requestOptions)
        //   .then((response) => {
        //     return response;
        //   })
        //   .then((result) => console.log(result))
        //   .catch((error) => console.error(error));
      },

      onReset() {
        username.value = null;
        password.value = null;
      },

      atten() {
        const myHeaders = new Headers();
        myHeaders.append(
          'Accept',
          'application/json, text/javascript, */*; q=0.01'
        );
        myHeaders.append('Accept-Language', 'en-US,en;q=0.9,ur;q=0.8');
        myHeaders.append('Connection', 'keep-alive');
        myHeaders.append(
          'Content-Type',
          'application/x-www-form-urlencoded; charset=UTF-8'
        );
        myHeaders.append('DNT', '1');
        myHeaders.append('Origin', 'https://eureka.ilmversity.net');
        myHeaders.append(
          'Referer',
          'https://eureka.ilmversity.net/school/attendance/student'
        );
        myHeaders.append('Sec-Fetch-Dest', 'empty');
        myHeaders.append('Sec-Fetch-Mode', 'cors');
        myHeaders.append('Sec-Fetch-Site', 'same-origin');
        myHeaders.append('X-Requested-With', 'XMLHttpRequest');

        const raw = 'attenVal=1&id=option_4478&dateVal=2024-09-01';

        const requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          mode: 'cors',
          redirect: 'follow',
        };

        const url =
          'https://eureka.ilmversity.net/school/attendance/singleattendance';
        fetch(new Request(url, { redirect: 'manual' }), requestOptions)
          .then((response) => {
            console.log(response);
          })
          .then((result) => console.log(result))
          .catch((error) => console.error(error));
      },
    };
  },
};
</script>
