Internacionalização com NPM

Intalação 

npm install vue-i18n

Configuração

Arquivo Main

import VueI18n from 'vue-i18n';
import { languages, defaultLocale } from './plugins/i18n/configI18n';

Vue.use(VueI18n);

e adicionar i18n no new vue 

Criar arquivo i18n e dentro dele o arquivo locales

dentro do arquivo i18n criar configi18n.ts  com as seguintes configurações

import pt from './locales/pt.json';
import en from './locales/en.json';
 
export const defaultLocale = 'en';
 
export const languages = {
 pt,
 en,
};

caso o import não funcione utilizar 

var pt = require('./locales/pt.json');
console.log("Json data : ", JSON.stringify(pt));
var en = require('./locales/en.json');
console.log("Json data : ", JSON.stringify(en));

dentro de locales criar dois arquivos json  en.json e pt.json onde seram adicionados os comandos em jason para a tradução

para utilizar é só criar a variavel no texto desejado

ex: {{$t('canal')}}

caso ocorra erro no json 
Adicionar linha "src/**/*.json"
no arquivo tscondig.json na seção  "INCLUDE"