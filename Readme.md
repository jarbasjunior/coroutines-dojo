# Dojo Coroutines



---

## Índice: 📋
- [Requisitos](#requisitos)

  - [Kotlin 1.9](#kotlin-1-9)
  - [Kotlin coroutine 1.7](#kotlin-coroutine-1-7)

- [Introdução](#intro)

  - [Técnicas de Programação Assíncrona](#async-programm)
  - [Programação Assíncrona com Kotlin](#async-program-kotlin)

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

