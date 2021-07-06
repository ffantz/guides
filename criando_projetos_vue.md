# Criando projeto VueJS:

- Criando projeto na versão mais atual do VueJS:
```
    npm install -g @vue/cli-init
    vue init webpack {nome_projeto}
    cd {nome_projeto}
    git init
```
- Adicionar no package.json:
```
    # dependencies:
        "@vue/cli": "^3.12.0",
        "axios": "^0.18.1",
        "core-js": "^3.6.5",
        "dotenv": "^7.0.0",
        "dotenv-expand": "^5.1.0",
        "element-ui": "^2.10.1",
        "laravel-echo": "^1.6.1",
        "socket.io-client": "^2.3.0",
        "v-currency-field": "^1.0.8",
        "v-money": "^0.8.1",
        "v-viewer": "^1.5.1",
        "vee-validate": "^2.2.13",
        "vue": "^2.6.11",
        "vue-avatar-editor-improved": "^1.0.4",
        "vue-click-outside": "^1.0.7",
        "vue-draggable-tree": "^1.1.6",
        "vue-moment": "^4.0.0",
        "vue-router": "^3.0.7",
        "vue-socket.io": "^3.0.9",
        "vue-the-mask": "^0.11.1",
        "vue-tree-navigation": "^4.0.1",
        "vuetify": "^2.1.4",
        "vuex": "^3.1.1"
    # devDependencies:
        "@vue/cli-plugin-babel": "^4.5.0",
        "@vue/cli-plugin-eslint": "^3.12.0",
        "@vue/cli-service": "^4.5.0",
        "babel-eslint": "^10.1.0",
        "babel-plugin-root-import": "^6.4.0",
        "deepmerge": "^4.2.2",
        "eslint": "^5.8.0",
        "eslint-plugin-vue": "^5.2.3",
        "eslint-loader": "2.1.2",
        "material-design-icons-iconfont": "^5.0.1",
        "optimize-css-assets-webpack-plugin": "^5.0.3",
        "sass": "^1.32.8",
        "sass-loader": "^10.1.1",
        "vue-cli-plugin-vuetify": "^2.2.2",
        "vue-template-compiler": "^2.6.11",
        "vuetify-loader": "^1.7.0",
        "webpack": "^4.41.2"
```
```
    npm install
```

# Configurações do projeto:
**A criação de um novo projeto pode ser feita espelhando os projetos existentes, mantendo os padrões da empresa.**

- Copiar a pasta `/src/assets` de um projeto existente para o novo projeto (contém todas as configurações de estilos, imagens e padrões empresta).

- Importar globalmente um plugin requere o registro do mesmo no arquivo `main.js` e a existência da sua pasta com um arquivo `.js` dentro de src. Consulte o Motor de Crédito ou Infinite Sales como parâmetro.

- Definir arquivo `router.js`, utilizando de base no Motor de Crédito. Isso implica em levar os módulos de vuex: `authenticatedUserModule.js`, `changePassword.js`, `dynamicNavigation.js`, `navBarModule.js`, `sideBarModule.js`, `snackBarModule.js`, `systemNavigatorModule.js`
    - Pode-se levar os arquivos base que utilizam esses vuex, mantendo o padrão de sistema: `AuthenticatedUser.vue`, `ChangePassword.vue`, `Content.vue`, `Crud.vue`, `EmployeeProfile.vue`, `Loading.vue`, `ModalLateral.vue`, `NavBar.vue`, `SideBar.vue`, `SnackBar.vue`, `SystemsNavigator.vue`, `TabBar.vue`

- Levar os layouts: `src/layouts` (migrar de um projeto existente)

- Inserir as validações de usuário logado no `src/router.js`
- Definir importações no `src/main.js`
- Definir Vuex no `src/store.js`
- Configurar `/.eslint.js`, para tratar os erros e warnings
- Configurar os arquivos de env (`.env.production` e `.env.development`)
- Ajustar título do sistema nos arquivos `index.html` e `src/components/Loading.vue`
- Ajustar a sigla do sistema nos arquivos `src/components/SystemsNavigator.vue`, `src/views/Login.vue`, `src/views/NotAllowed.vue` e `src/views/404.vue`
- Solicitar ao design os ícones `svg` e `favicon` para atualização no novo sistema
- Certificar que os demais arquivos de configuração estejam de acordo com o padrão nos outros projetos
    - O mais essencial é garantir que não tenha ficado nenhum resquício do projeto utilizado de base. Pesquise pelas siglas do projeto base no novo e altere tudo que pesquisar. **Não copie** todos os arquivos de uma vez, faça um por um e entenda o que está sendo feito ali. Copiar pode dar mais trabalho para corrigir do que levar um por um e ir adaptando as informações aos poucos.