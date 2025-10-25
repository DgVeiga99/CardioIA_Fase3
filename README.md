# 🩺 CardioIA - Fase 3: IoT em Saúde Digital – Edge & Cloud Computing com ESP32

## 💡 Ideia do Projeto

O projeto **CardioIA – Fase 3: IoT em Saúde Digital – Edge & Cloud Computing com ESP32** tem como proposta o desenvolvimento de um **protótipo funcional de sistema vestível para monitoramento cardíaco**, capaz de **coletar sinais vitais**, **armazená-los localmente** e **transmiti-los para a nuvem** em tempo real.  

A iniciativa explora o uso de **tecnologias IoT aplicadas à saúde**, simulando um sistema que monitora continuamente parâmetros fisiológicos como **batimentos cardíacos**, **temperatura corporal**, **umidade** e **movimento**. O objetivo é demonstrar como o **ESP32** pode atuar como um **nó de borda (edge device)** em uma arquitetura distribuída, processando dados localmente e garantindo operação contínua mesmo em condições de conectividade limitada.  

Na **Parte 1 (Edge Computing)**, o foco é o armazenamento e a resiliência local. O ESP32 coleta dados dos sensores, registra as leituras no **SPIFFS** e garante que as informações não sejam perdidas durante falhas de rede, sincronizando-as automaticamente assim que a conexão é restabelecida.  

Na **Parte 2 (Fog/Cloud Computing)**, a proposta é transmitir os dados para a nuvem via **protocolo MQTT**, permitindo a integração com dashboards desenvolvidos no **Node-RED** para visualização em tempo real.  
Esses dashboards podem conter **gráficos**, **medidores (gauges)** e **indicadores de alerta**, simulando um sistema médico inteligente capaz de detectar anomalias, como febre ou taquicardia.  

⚠️ **Nota:** devido às limitações do ambiente de simulação **Wokwi** e à ausência de hardware físico, **não foi possível realizar a integração prática com o Node-RED e o envio real via MQTT**.  
No entanto, todo o código e a arquitetura foram estruturados de forma compatível, bastando configurar um broker MQTT e importar o fluxo Node-RED para concluir a integração.  

Este projeto reforça princípios de **eficiência, segurança e boas práticas em IoT médica**, apresentando uma solução 100% aplicável a contextos reais de monitoramento remoto de pacientes.

---

## 📘 Visão Geral

Este projeto foi desenvolvido como parte da **Fase 3 da Global Solution – IoT em Saúde Digital** do curso de **Inteligência Artificial (FIAP)**.  
A proposta envolve a construção de um ecossistema completo que demonstra a aplicação das tecnologias de **Edge** e **Cloud Computing** em um cenário de **saúde digital conectada**.

---

## 🧩 Estrutura do Projeto

| Parte | Tema | Descrição |
|:------:|------|------------|
| **1** | **Edge Computing – Armazenamento e Processamento Local** | Coleta de dados de sensores, armazenamento em SPIFFS, simulação de conectividade e resiliência offline. |
| **2** | **Fog/Cloud Computing – Transmissão e Integração com a Nuvem** | Transmissão de dados via MQTT (simulada) e arquitetura pronta para integração com Node-RED. |

---

## ⚙️ Parte 1 – Armazenamento e Processamento Local (Edge Computing)

📁 **Local:** `/code/parte1`  
📂 **Relatório:** `/code/docs`

Nesta primeira etapa, foi desenvolvido um nó de **Edge Computing** com o **ESP32**, responsável por coletar dados de dois sensores distintos — o **DHT22** (temperatura e umidade) e um **potenciômetro** (simulando um sinal fisiológico, como oxigenação).  
As leituras são armazenadas localmente no sistema de arquivos **SPIFFS** e, ao detectar reconexão Wi-Fi (simulada por chave lógica), os dados são **sincronizados** via `Serial.println()` e o buffer é limpo após o envio.  

O sistema adota uma **política de armazenamento limitado (300 KB)**, simulando um *ring buffer* que mantém apenas as amostras mais recentes, característica comum em dispositivos IoT com pouca memória.  

📷 **Circuito desenvolvido no Wokwi:**

<img width="629" height="390" alt="image" src="https://github.com/user-attachments/assets/d6d79d2d-6d0a-4e46-af22-bee3b40f1a5e" />

🔗 [Simulação Online no Wokwi](https://wokwi.com/projects/445704978329638913)


---

## ☁️ Parte 2 – Transmissão e Visualização em Nuvem (Fog/Cloud Computing)

📁 **Local:** `/code/parte2`  
📂 **Relatório:** `/code/docs`

Na segunda etapa, o projeto foi planejado para a **transmissão dos dados coletados pelo ESP32 para a nuvem**, utilizando o **protocolo MQTT** e integração com o **Node-RED**.  
Essa camada de *Fog/Cloud* tem como objetivo receber as informações enviadas do dispositivo, processá-las e exibi-las em um painel de monitoramento.

⚠️ **Nota importante:**  
Por limitações do ambiente de simulação e disponibilidade de tempo, **não foi possível realizar a integração completa com o Node-RED nem a simulação MQTT** conforme previsto na atividade.  
Entretanto, o código do ESP32 e a estrutura do projeto já foram construídos para suportar essa integração, bastando inserir as credenciais do broker e importar o fluxo Node-RED.  

---

## 🧠 Conclusões Gerais

As duas etapas deste projeto demonstram, de forma integrada, a aplicação prática dos conceitos de **Edge Computing** e **Cloud Computing** em um contexto de **IoT médico**.  
Na borda, o ESP32 atua como um nó inteligente capaz de **coletar, analisar e armazenar dados localmente**, garantindo operação contínua e segura.  
Na nuvem, a arquitetura planejada possibilita a **visualização, análise e emissão de alertas** em tempo real, quando plenamente integrada.

A proposta consolida os aprendizados de **resiliência offline**, **processamento distribuído**, **transmissão MQTT** e **boas práticas de segurança em IoT**, reforçando como dispositivos de baixo custo podem contribuir para **soluções reais de monitoramento de saúde digital**.

