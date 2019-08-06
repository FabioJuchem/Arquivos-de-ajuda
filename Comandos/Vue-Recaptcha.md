## Guia para implantação do Vue-Recaptcha Google



#### Chave Para Google Recaptcha



Para utilizar o Recaptcha você deve acessar o site



https://www.google.com/recaptcha



e criar uma conta



## adicionar um dominio valido



Caso seja dominio de testes adicionar 



localHost 

e adiocionar tambem

127.0.0.1



### Chave para teste

6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI



### Install



#### NPM 



```shell
$ npm install --save vue-recaptcha
```



### YARN 



```shell
$ yarn add vue-recaptcha
```



### Adicionar os seguintes trechos ao arquivo INDEX.HTML

```html
<script src="https://unpkg.com/vue-recaptcha@latest/dist/vue-recaptcha.js"></script>

<script src="https://unpkg.com/vue-recaptcha@latest/dist/vue-recaptcha.min.js"></script>
```





### Aplicação ao template



```vue
<template>
  <vue-recaptcha sitekey="Your key here"></vue-recaptcha>
</template>

<script>
  import VueRecaptcha from 'vue-recaptcha';
  export default {
    ...
    components: { VueRecaptcha }
  };
</script>
```



### Aplicar o desafio Captcha a um Botão



```vue
<template>
  <vue-recaptcha sitekey="Your key here">
    <button>Click me</button>
  </vue-recaptcha>
</template>

<script>
  import VueRecaptcha from 'vue-recaptcha';
  export default {
    ...
    components: { VueRecaptcha }
  };
</script>
```





## Forma implementada 

```vue
<template>
  <vue-recaptcha
    ref="recaptcha"
    @verify="onVerify"
    @expired="onExpired"
    sitekey="6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI"
  ></vue-recaptcha>
</template>
<script lang="ts">
import { Vue, Prop, Component } from "vue-property-decorator";
import VueRecaptcha from "vue-recaptcha";

@Component({
  components: { VueRecaptcha }
})
export default class doubtComponent extends Vue {
  onVerify(response: any) {
    console.log("Verify: " + response);
    if (response != null) {
      this.$emit("isHuman");
    }
  }

  onExpired(response: any){
      this.$emit("expired");
    }
}

</script>
<style lang="sass" scoped>

</style>



```









