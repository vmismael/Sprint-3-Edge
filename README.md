# Sprint-3-Edge

## 🗒️ integrantes

Danilo Wendler - RM556602 
Renato Luiz - RM556403
Pedro Muzel - RM555983
Vitor Ismael RM-556027
Guilherme Cezarino RM-557724

## Descrição
- O projeto em desenvolvimento foi solicitado na disciplina de Edge Computing, pelo curso de Engenharia de Software - FIAP.

## Visão Geral do Projeto

Este projeto simula um sistema de telemetria em tempo real para um carro de Fórmula E utilizando tecnologias de IoT (Internet das Coisas). A solução é baseada na plataforma Arduino Uno e integra um sensor de temperatura DHT11 e um acelerômetro/giroscópio MPU6050 para monitorar a temperatura do motor e a aceleração longitudinal do carro em tempo real. O sistema calcula a velocidade do carro, impõe limites de velocidade (simulando restrições do mundo real) e garante que a velocidade não se torne negativa. Os dados são enviados no formato JSON, facilitando a interface com serviços de back-end e front-end para monitoramento e análise em tempo real.

Todos os dados são transmitidos para o Node-RED em formato JSON, facilitando a interface com serviços de back-end e front-end para monitoramento e análise em tempo real. Isso permite que os usuários visualizem e analisem os dados em tempo real, otimizando o acompanhamento do desempenho do veículo de Fórmula E.

## Funcionalidades

- Monitoramento da Temperatura do Motor: Utilizando o sensor DHT11 para medir a temperatura do motor.
- Monitoramento da Aceleração Longitudinal: Utilizando o acelerômetro MPU6050 para medir a aceleração no eixo X.
- Cálculo da Velocidade: A velocidade é calculada com base nos dados de aceleração, com um limite máximo de 322 km/h e sem permitir velocidades negativas.
- Telemetria em Tempo Real: Os dados de telemetria (temperatura, aceleração e velocidade) são enviados via comunicação serial, formatados em um objeto JSON.

## Arquitetura do Sistema

### Visão Geral da Arquitetura
O sistema proposto é simples e baseado em duas partes principais:

### Dispositivo IoT (Arduino):

Arduino Uno: Controla a coleta de dados dos sensores e envia os dados para o Node-RED via comunicação serial.
Sensores:
DHT11: Mede a temperatura do motor.
MPU6050: Fornece dados de aceleração ao longo do eixo X, utilizados para calcular a velocidade.

### Node-RED:
Node-RED será utilizado para processar os dados recebidos do Arduino e exibi-los em um painel. Node-RED se comunica com o Arduino via conexão serial, e os dados são manipulados e organizados em um painel gráfico.

## Recursos Necessários

### Dispositivos IoT (Hardware)
Arduino Uno: Microcontrolador que captura e processa os dados dos sensores.
Sensor DHT11: Mede a temperatura do motor.
Sensor MPU6050: Coleta os dados de aceleração no eixo X.
Cabo USB: Para conectar o Arduino ao computador para comunicação serial com o Node-RED.

### Software
Node-RED: Ferramenta visual para conectar dispositivos e criar fluxos de dados. O Node-RED será utilizado para receber os dados do Arduino e exibi-los.
Arduino IDE: Para programar o Arduino e carregar o código necessário.
Bibliotecas Arduino:
DHT (para o sensor DHT11)
MPU6050_light (para o sensor MPU6050)
ArduinoJson (para formatar os dados como JSON)

## Fluxo de Dados

### Coleta de Dados (Arduino Uno):
O Arduino lê os valores do sensor DHT11 (temperatura) e do MPU6050 (aceleração no eixo X).
Com base na aceleração, o Arduino calcula a velocidade do carro, garantindo que a velocidade não ultrapasse 322 km/h e que não fique negativa.
Os dados são formatados em JSON e enviados para o Node-RED via conexão serial.

### Processamento de Dados (Node-RED):
O Node-RED recebe os dados via comunicação serial, processa as informações e organiza os dados de telemetria.
O painel do Node-RED exibe as leituras de temperatura, aceleração e velocidade em tempo real.

### Visualização (Dashboard Node-RED):
Um painel gráfico exibe a telemetria, incluindo gráficos de aceleração e velocidade ao longo do tempo, além de indicadores para a temperatura do motor.


## Dependências

ArduinoJson: Para formatar os dados de telemetria como JSON.
Biblioteca DHT da Adafruit: Para interação com o sensor de temperatura DHT11.
MPU6050_light: Para leitura dos dados de aceleração do MPU6050.
Node-RED: Para receber, processar e exibir os dados de telemetria.

