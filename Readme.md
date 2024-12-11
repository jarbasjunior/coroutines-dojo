# Dojo Coroutines



---

## Índice: 📋
- [Requisitos](#requisitos)

  - [Kotlin 1.9](#kotlin-1-9)
  - [Kotlin coroutine 1.7](#kotlin-coroutine-1-7)

- [Introdução](#intro)

  - [Técnicas de Programação Assíncrona](#async-programm)
  - [Programação Assíncrona com Kotlin](#async-program-kotlin)
  - [Coroutines X Outras Formas de Gerenciar Tarefas](#coroutines-x-other-management-tasks)

---

## <a id="requisitos"/> Requisitos: ❗ </a>

- <a id="kotlin-1-9"/> [Kotlin 1.9.0](https://github.com/JetBrains/kotlin/releases/tag/v1.9.0)

  - **Intellij** -> **Settings** -> **Build**, **Execution**, **Deployment** -> **Kotlin Compiler**. **Update Language version** e **Api version**
  - **build.gradle.kts** -> ajustar o plugin do Kotlin `kotlin("jvm") version "1.9.0"`

- <a id="kotlin-coroutine-1-7"/> [Kotlin coroutines 1.7](https://github.com/Kotlin/kotlinx.coroutines/releases/tag/1.7.0) 

  - **build.gradle.kts** -> adicionar a dependência `implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.0")`

* Após realizar as configurações acima, sincronizar o Gradle através do caminho: **Intellij** -> **Gradle** -> **Sync All Grade Project** e verificar dentro da **External Libraries**, se todas as bibiliotecas foram atualizadas com sucesso. Ou pelo comando `./gradlew dependencies`
  `
* **OBS.**
  * Considerar versões a partir das sugeridas acima. Kotlin com versões <= 1.4 e Kotlin Coroutines <= 1.0 podem apresentar inconsistências
  * Corotinas não dependedem de versão do gradle ou outras ferramentas de construção, de qualquer modo, foi utilizado o gradle 8.1

---

## <a id="introdução"/> Introdução </a>

Nesta seção serão expostas algumas técnicas de programação assíncrona utilizadas e um breve particularidade entre elas e a abordagem utilizada pelo Kotlin com Coroutine.

### <a id="async-programm"/> Técnicas de Programação Assíncrona </a>

<div style="display: flex; justify-content: center; align-items: center;">
  <img src="https://github.com/user-attachments/assets/0e6aeb6f-b752-4059-934d-9913f5e597db" width="980" height="430">
</div>

### <a id="async-program-kotlin"/> Programação Assíncrona com Kotlin</a>

Kotlin se utiliza de Corotinas para programação assíncrona, cuja abordagem tem por príncípio suspender uma funcão e retomá-la em algum outro momento com as seguintes particularidades em relação as abordagens anteriores

<p align="center">
  <img src="https://github.com/user-attachments/assets/e5edc8ee-ec0e-408a-8e27-e91b85a42f34" width="500" height="400">
</p>

### <a id="coroutines-x-other-management-tasks"/> Coroutines X Outras Formas de Gerenciar Tarefas</a>

- **Coroutines X Multi-Thread**

  - **_Multi Thread_**
    - Mais agendamento de threads maior a sobrecarga
    - Mais agendamento de corotina menor a sobrecarga (comparada a Multi-Thread)
     
    <br/>
  
    <div style="display: flex; justify-content: align-items: center;">
      <img src="https://github.com/user-attachments/assets/ccda6732-33da-4a08-a52e-eccccc3e818c" width="580" height="330">
    </div>
    
    <br/>

- **Coroutine X Virtual-Thread**

  - **_Virtual Thread_**
    - Introduzida no Java 21
    - Utilizada para resolver os problemas de bloqueio de Input/Output
    - Ainda não suportam concorrência estruturada Structured Concurrency (yet)
      
    <br/>
  
    <div style="display: flex; justify-content: align-items: center;">
      <img src="https://github.com/user-attachments/assets/1dc53551-3aaa-4c5a-92ca-2baf09ca6df8" width="580" height="330">
    </div>

    <br/>
  
- **Coroutine X Threads**

  - Threads podem ser bloqueadas
  - Coroutines são suspensas da thread, o que significa que a thread em que as coroutines estão sendo executadas estará disponível para trabalho posterior
  - Não há um mapeamento 1:1 entre threads e coroutines
  - Muitas coroutines por Thread
  - Coroutines escalam melhor
      
  <br/>
  
  <div style="display: flex; justify-content: align-items: center;">
    <img src="https://github.com/user-attachments/assets/7262e2a0-ef88-4e7f-925d-ddac9ccf5676" width="580" height="330">
  </div>

  <br/>