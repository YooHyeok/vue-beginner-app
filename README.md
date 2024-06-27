# *Vue Cli*
## *Install & Run*
<details>
<summary>펼치기/접기</summary>
<br>

- **Vue Cli 설치**
    
    ```bash
    npm install -g @vue/cli
    ```
    
- **Vue Version**
    
    ```bash
    vue -V
    ```
    
- **Vue 프로젝트 생성**
    
    ```bash
    vue create 프로젝트명
    ```
    
- **Vue3 선택 및 NPM/YARN중 택1**
    
    ```bash
    ? Please pick a preset
    > Default ([Vue 3] babel, eslint)
      Default ([Vue 3] babel, eslint)
    Manually select features
    ```
    ```bash
    ? Pick the pacage manager to user when installing dependencies:
    > NPM
    YARN
    Manually select features
    ```
- **vetur 플러그인 설치**  
  - VSCode IDE 좌측 extentions 탭에서 vetur 검색 후 설치

  - `jsconfig.json`  
    reference : https://vuejs.github.io/vetur/guide/
    ```json
    {
      "compilerOptions": {
        "target": "es2015",
        "module": "esnext",
        "baseUrl": "./",
        "paths": {
          "@/*": ["components/*"]
        }
      },
      "include": [
        "src/**/*.vue",
        "src/**/*.js"
      ]
    }
    ```
- **실행**
    ```bash
    npm run serve
    ```
</details>

