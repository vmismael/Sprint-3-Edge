# Sprint-3-Edge

## 🗒️ Integrantes

Danilo Wendler - RM556602  
Renato Luiz - RM556403  
Pedro Muzel - RM555983  
Vitor Ismael RM-556027  
Guilherme Cezarino RM-557724  

## Descrição
O projeto em desenvolvimento foi solicitado na disciplina de Edge Computing, pelo curso de Engenharia de Software - FIAP. <br> 
Link do projeto no Wokwi: [Projeto no Wokwi](https://wokwi.com/projects/410468304224276481)

## Visão Geral do Projeto

Este projeto simula um sistema de telemetria em tempo real para um carro de Fórmula E utilizando tecnologias de IoT (Internet das Coisas). A solução agora é baseada na plataforma ESP32, que se conecta ao Node-RED via MQTT. O sistema integra um sensor de temperatura DHT22 e um acelerômetro/giroscópio MPU6050 para monitorar a temperatura do motor e a aceleração longitudinal do carro. Os dados de telemetria são enviados em formato JSON.

### Conexão MQTT

A comunicação entre o ESP32 e o Node-RED é feita via protocolo MQTT, usando o servidor público **test.mosquitto.org**. O ESP32 envia os dados de telemetria (temperatura, aceleração e velocidade) para o Node-RED, que organiza e exibe os dados em um painel em tempo real.

## Funcionalidades

- **Monitoramento da Temperatura do Motor**: Utilizando o sensor DHT22 para medir a temperatura do motor.
- **Monitoramento da Aceleração Longitudinal**: Utilizando o acelerômetro MPU6050 para medir a aceleração no eixo X.
- **Cálculo da Velocidade**: A velocidade é calculada com base nos dados de aceleração, com um limite máximo de 322 km/h e sem permitir velocidades negativas.
- **Telemetria em Tempo Real**: Os dados de telemetria são transmitidos via MQTT no formato JSON, facilitando o monitoramento e análise.

## Arquitetura do Sistema

### Dispositivo IoT (ESP32)
- **ESP32**: Controla a coleta de dados dos sensores e envia os dados para o Node-RED via MQTT.
- **DHT22**: Sensor de temperatura utilizado para monitorar a temperatura do motor.
- **MPU6050**: Acelerômetro usado para coletar dados de aceleração no eixo X e calcular a velocidade.

### Node-RED
Node-RED é utilizado para processar os dados recebidos via MQTT e exibi-los em um painel. Os dados são manipulados e exibidos em gráficos de aceleração, velocidade e indicadores de temperatura em tempo real.

## Fluxo de Dados

### Coleta de Dados (ESP32)
O ESP32 lê os valores do sensor DHT22 (temperatura) e do MPU6050 (aceleração no eixo X). Com base na aceleração, o ESP32 calcula a velocidade do carro, garantindo que a velocidade não ultrapasse 322 km/h e que não fique negativa. Os dados são formatados em JSON e enviados para o Node-RED via MQTT.

### Processamento de Dados (Node-RED)
O Node-RED recebe os dados via MQTT, processa as informações e organiza os dados de telemetria. O painel do Node-RED exibe as leituras de temperatura, aceleração e velocidade em tempo real.

### Visualização (Dashboard Node-RED)
Um painel gráfico exibe a telemetria, incluindo gráficos de aceleração e velocidade ao longo do tempo, além de indicadores para a temperatura do motor.

## Recursos Necessários

### Dispositivos IoT (Hardware)
- ESP32: Microcontrolador que captura e processa os dados dos sensores.
- Sensor DHT22: Mede a temperatura do motor.
- Sensor MPU6050: Coleta os dados de aceleração no eixo X.

### Software
- **Node-RED**: Ferramenta visual para conectar dispositivos e criar fluxos de dados. Node-RED será utilizado para receber os dados do ESP32 via MQTT e exibi-los.
- **Arduino IDE**: Para programar o ESP32 e carregar o código necessário.
- **Broker MQTT**: test.mosquitto.org será utilizado como servidor MQTT para a comunicação entre o ESP32 e o Node-RED.

### Bibliotecas Arduino:
- **WiFi**: Para conexão do ESP32 à rede Wi-Fi.
- **PubSubClient**: Para comunicação via MQTT.
- **ArduinoJson**: Para formatar os dados como JSON.
- **DHT**: Para o sensor DHT22.
- **MPU6050_light**: Para o sensor MPU6050.

## Dependências
- **WiFi.h**: Para conectar o ESP32 ao Wi-Fi.
- **PubSubClient.h**: Para configurar a comunicação MQTT.
- **ArduinoJson**: Para formatar os dados de telemetria como JSON.
- **DHT.h**: Para interação com o sensor de temperatura DHT22.
- **MPU6050_light.h**: Para leitura dos dados de aceleração do MPU6050.
