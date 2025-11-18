# **SYMβIOTE — IoT para o Futuro do Trabalho**

### Global Solution 2025 — FIAP

---

## **Integrantes**

* Vinicius Mafra Paiva — RM565916
* Kaike Correia de Sousa — RM561623
* Nduarda de Castro Coutinho dos Santos — RM562184

---

# 1. **Descrição do Problema**

O futuro do trabalho exige profissionais capazes de aprender rapidamente, manter foco em ambientes híbridos e adaptar-se às mudanças constantes.
Entretanto, muitos usuários enfrentam dificuldades como:

* Ambientes inadequados (calor, baixa luminosidade, distrações)
* Falta de indicadores sobre produtividade
* Baixa integração entre ferramentas físicas e digitais
* Dificuldade em monitorar sua própria evolução

Tais fatores prejudicam aprendizado, saúde e eficiência no trabalho.

---

# 2. **A Solução – SYMβIOTE IoT**

O SYMβIOTE é uma plataforma inteligente para desenvolvimento contínuo de habilidades.
Neste projeto, desenvolvemos um dispositivo físico que conecta o ambiente real ao contexto digital:

# **Symbiote Context Button — Dispositivo IoT com ESP32**

Ele atua em três frentes principais.

---

## 2.1 Monitoramento Ambiental

O dispositivo mede em tempo real:

* Temperatura (DS18B20)
* Luminosidade (LDR)

Isso permite avaliar as condições do ambiente e melhorar foco e bem-estar.

![hardware-esp32](images/hardware.png)
---

## 2.2 Detecção de Modo de Contexto

O botão físico alterna entre três modos de uso:

* **Study**
* **Work**
* **Pause**

Com LEDs indicativos para cada modo:

* Azul: Study
* Verde: Work
* Vermelho: Pause

![funcionamento-sistema](images/funcionamento_projeto.png)
---

## 2.3 Envio de Dados via MQTT

O ESP32 envia mensagens automaticamente:

* A cada **5 segundos**
* Sempre que o botão muda o modo

O envio acontece no formato JSON.

![Mosquitto](images/mosquitto.png)
---

# 3. **Arquitetura do Sistema**

Fluxo geral da solução:

```
[ ESP32 ]
     ↓ (MQTT Publish)
[ Broker MQTT - HiveMQ / Mosquitto ]
     ↓
[ Node-RED ] → Dashboard + Regras + Integração Symbiote
```
![Node-RED-dashboard](images/node-red-dashboards.png)
---

# 4. **Comunicação MQTT — Parte Técnica**

### Tópico utilizado

```
symbiote/context
```

### Exemplo de JSON enviado

```json
{
  "deviceId": "symbiote-btn-01",
  "event": "periodic_update",
  "mode": "study",
  "temperature": 24.8,
  "lux": 310.2,
  "timestamp": 1731888861
}
```

### Tipos de eventos

| Evento          | Descrição                                 |
| --------------- | ----------------------------------------- |
| periodic_update | Enviado automaticamente a cada 5 segundos |
| context_change  | Enviado quando o botão muda o modo        |

### Broker utilizado

* Endereço: **broker.hivemq.com**
* Porta: **1883**

---

# 5. **Reprodução Local do Projeto**

## Requisitos

* Node.js e Node-RED
* Broker MQTT (HiveMQ, Mosquitto, AWS EC2 etc.)
* Arduino IDE
* Wokwi ou ESP32 físico

---

## 5.1 Configuração da AWS 

**Criação da instância:**
![AWS Instância](images/aws_instancia.png)

**Regras de segurança configuradas:**
![AWS Regras](images/aws_regras.png)
---

## 5.2 Conexão via SSH (Putty)

![Putty](images/putty.png)
---

# 6. **Simulação Wokwi**

Simulação completa disponível:
**[link-wokwi](https://wokwi.com/projects/447869522108655617)**

### Passos:

1. Abrir o link do projeto
2. Clicar em Start Simulation
3. Abrir o Serial Monitor
4. Verificar leituras de sensores
5. Conferir envio MQTT no Node-RED

---

# 7. **Node-RED – Fluxo e Dashboard**

O Node-RED exibe:

* Temperatura
* Luminosidade
* Modo atual
* Eventos recebidos
* JSONs publicados

E inclui lógica para alertas e recomendações.

**Imagem do Dashboard / Fluxo:**

![Node-RED](images/node-red.png)
---

# 8. **Código-Fonte**

O repositório inclui:

* Código ESP32: `main.ino`
* Fluxo Node-RED
* Configuração MQTT

---

# 9. **Tecnologias Utilizadas**

### Hardware

* ESP32
* DS18B20
* LDR
* LEDs
* Botão tátil

### Software

* Arduino IDE
* Wokwi
* Node-RED
* Mosquitto / HiveMQ
* AWS EC2
* ArduinoJson
* DallasTemperature

---

# 10. **Vídeo Demonstrativo**

O vídeo apresenta:

* Explicação do problema
* Arquitetura da solução
* Funcionamento no Wokwi
* Envio MQTT
* Dashboard Node-RED

Inserir link do vídeo:
**INSERIR_LINK_AQUI**

---

# 11. **Impacto no Futuro do Trabalho**

O SYMβIOTE IoT cria uma ponte entre:

* Ambiente físico
* Inteligência artificial
* Rotina de estudo e trabalho

Permitindo:

* Ajustes de ambiente
* Redução de distrações
* Entendimento do contexto em tempo real
* Evolução profissional baseada em dados
