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
Entretanto, muitos usuários enfrentam problemas como:

* Ambientes inadequados (calor, baixa luminosidade, distrações)
* Falta de indicadores sobre produtividade
* Baixa integração entre ferramentas físicas e digitais
* Dificuldade em monitorar sua própria evolução

Tais fatores prejudicam aprendizado, saúde e eficiência no trabalho.

---

# 2. **A Solução – SYMβIOTE IoT**

O SYMβIOTE é uma plataforma inteligente para desenvolvimento contínuo de habilidades.
Neste projeto, foi desenvolvido um dispositivo físico que conecta o ambiente real ao contexto digital:

# **Symbiote Context Button — Dispositivo IoT com ESP32**

Ele atua em três frentes principais:

---

## 2.1 Monitoramento Ambiental

O dispositivo utiliza sensores para medir:

* Temperatura (DS18B20)
* Luminosidade (LDR)

Essas informações ajudam a analisar o ambiente e garantir condições adequadas ao foco e ao aprendizado.

(Local para inserir imagem do circuito e sensores)

---

## 2.2 Detecção de Modo de Contexto

Um botão físico permite alterar entre três modos:

* Study
* Work
* Pause

LEDs indicam o modo selecionado:

* Azul: Study
* Verde: Work
* Vermelho: Pause

(Local para inserir imagem do botão e LEDs)

---

## 2.3 Envio de Dados via MQTT

O ESP32 envia dados automaticamente:

* A cada 5 segundos
* Sempre que o modo muda

O envio é feito no formato JSON para o broker MQTT.

(Local para inserir captura do MQTT Explorer ou HiveMQ Client)

---

# 3. **Arquitetura do Sistema**

Representação do fluxo:

```
[ ESP32 ]
     ↓ (MQTT Publish)
[ Broker MQTT - HiveMQ ]
     ↓
[ Node-RED ] → Dashboard, lógica e integração com a plataforma Symbiote
```

(Local para inserir o diagrama da arquitetura registrado)

---

# 4. **Comunicação MQTT — Parte Técnica**

### Tópico utilizado

```
symbiote/context
```

### Formato JSON enviado

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

* Endereço: broker.hivemq.com
* Porta: 1883

(Local para inserir captura da interface do HiveMQ Websocket)

---

# 5. **Reprodução Local do Projeto**

## Requisitos

* Node.js e Node-RED
* Broker MQTT (HiveMQ, Mosquitto ou similar)
* Arduino IDE
* Simulação Wokwi ou dispositivo ESP32
* Conexão Wi-Fi

---

# 6. **Simulação Wokwi**

O projeto pode ser testado integralmente no Wokwi.

Link da simulação:
INSERIR_LINK_AQUI

### Passo a passo

1. Abrir o link do projeto
2. Clicar em Start Simulation
3. Abrir o Serial Monitor
4. Verificar leituras de sensores e JSON enviado
5. Visualizar dados no Node-RED

(Local para inserir imagem da simulação em funcionamento)

---

# 7. **Node-RED – Fluxo e Dashboard**

O Node-RED recebe os dados do MQTT e exibe:

* Temperatura em tempo real
* Luminosidade
* Modo atual
* Histórico de eventos
* JSON recebido

O fluxo também pode disparar lógicas personalizadas, como alertas ou recomendações.

(Local para inserir imagem do dashboard)
(Local para inserir imagem do fluxo)

---

# 8. **Código-Fonte**

O repositório contém:

* Código completo do ESP32 (main.ino)
* Fluxo Node-RED (arquivo .json)
* Scripts auxiliares
* Comentários explicativos em todos os pontos importantes

(Local para inserir captura de partes importantes do código)

---

# 9. **Tecnologias Utilizadas**

### Hardware

* ESP32
* Sensor DS18B20
* Sensor LDR
* LEDs
* Botão tátil

### Software

* Arduino IDE
* Wokwi
* Node-RED
* HiveMQ MQTT Broker
* ArduinoJson
* DallasTemperature
* OneWire

---

# 10. **Vídeo Demonstrativo**

O vídeo apresenta:

* O problema
* A arquitetura
* Funcionamento da simulação
* Comunicação MQTT
* Dashboard do Node-RED
* Integração com a plataforma Symbiote

Inserir link do vídeo:
INSERIR_LINK_AQUI

(Local para inserir imagem do vídeo)

---

# 11. **Impacto no Futuro do Trabalho**

O SYMβIOTE IoT cria uma ponte entre o ambiente físico e o digital, permitindo:

* Melhor controle do ambiente em tempo real
* Redução de distrações e aumento de foco
* Aprendizado guiado por métricas reais
* Integração natural do usuário com a IA
* Evolução contínua baseada em contexto

Essa abordagem combina tecnologia, ambiente e inteligência para transformar a forma como as pessoas aprendem e trabalham.

---

# 12. **Conclusão**

O Symbiote Context Button demonstra como o ESP32 pode se tornar uma interface física poderosa entre o usuário e o ecossistema digital do futuro.
A solução propõe uma nova forma de estudar e trabalhar, unindo ambiente, comportamento e IA em um único fluxo contínuo de evolução.

