# FIAP — Challenge 2026 | Disruptive Architectures: IoT, IoB & Generative AI

## 1. Finalidade e Fonte / Prazo

* **Disciplina:** Disruptive Architectures: IoT, IoB & Generative AI

* **Projeto:** Challenge 2026 — Parceria com o Centro Tecnológico da Marinha em São Paulo (CTMSP) / Programa Nuclear da Marinha (PNM).

* **Entregável:** Documentação conceitual, especificação de arquitetura de IoT, fluxograma de dados e vídeo demonstrativo referentes à Sprint 1 (1º Semestre).

* **Fonte:** `2TDS Agosto - Marinha 2026 - 1º Semestre V2.pdf`.

* **Prazo de Entrega:** Conforme diretrizes do portal FIAP (Janela de entrega entre 01/11/2026 e 02/11/2026).

## 2. Equipe e Responsabilidade

* **Nome do Grupo / Projeto:** IoT Monitor — CTMSP Transparência Nuclear

* **Turma:** 2TDSPS (Turma de Agosto)

* **Integrantes:**

  * Alisson Kawan Evangelista Silva | RM: 567598

  * Eduardo Boni dos Santos | RM: 567236

  * Erick Ramos Santos | RM: 567837

  * Kenji Fernandes Wakabayashi | RM: 568156

  * Marcos Vinicius de Jesus Almeida | RM: 567214

## 3. Visão Geral do Projeto e Proposta Educativa

A tecnologia nuclear é frequentemente associada apenas a riscos ou aplicações militares de forma equivocada pela população. No entanto, o **Programa Nuclear da Marinha (PNM)** desenvolve pesquisas fundamentais que geram benefícios diretos para a sociedade em áreas como medicina (radiofármacos), agricultura, indústria e geração de energia limpa.

O grande desafio do projeto é **desmistificar a tecnologia nuclear e aproximá-la da sociedade por meio da transparência tecnológica**.

Nossa solução propõe um **Sistema IoT de Monitoramento Transparente para Laboratórios de Pesquisa**, demonstrando de forma prática e em tempo real como o ambiente de pesquisa é seguro, rigorosamente controlado e livre de riscos à população.

## 4. Detalhamento da Solução IoT

### 🎯 O Que Estamos Monitorando (Escopo da Solução)

Para garantir que a sociedade e os gestores acompanhem o rigor técnico das instalações do CTMSP, nosso sistema IoT realiza a medição contínua de **duas variáveis cruciais no ambiente físico dos laboratórios**:

1. **Temperatura e Umidade do Laboratório:**

   * **O que é medido:** A variação térmica em tempo real dentro da sala onde os equipamentos de pesquisa operam.

   * **Por que monitorar:** Laboratórios de alta tecnologia exigem temperatura controlada para evitar superaquecimento de equipamentos e degradação de amostras ou reagentes.

2. **Acesso e Estado das Portas Restritas:**

   * **O que é medido:** O estado físico da porta ("Porta Fechada" vs. "Porta Aberta").

   * **Por que monitorar:** Garantir a segurança patrimonial e operacional, assegurando que salas de pesquisa restritas não permaneçam abertas indevidamente ou sem autorização.

### 👥 Público-Alvo

* **Sociedade Civil e Estudantes:** Acessam os dados de forma simplificada no Dashboard para entender que os laboratórios operam sob condições seguras e estáveis.

* **Comunidade Acadêmica e Pesquisadores:** Acompanham os parâmetros de estabilidade do ambiente de trabalho.

* **Gestores do CTMSP:** Recebem alertas de contingência caso algum parâmetro saia do padrão.

### 💡 Aplicação Prática

O sistema lê continuamente a temperatura/umidade e a posição das portas através de um microcontrolador local (ESP32). Esses dados são enviados via Wi-Fi para a nuvem e exibidos em um **Dashboard Educativo Público**.

Se um cidadão acessar o portal, ele verá indicadores amigáveis como:

* *Status do Laboratório:* **SEGURO / ESTÁVEL**

* *Temperatura Atual:* **22°C (Dentro do limite seguro)**

* *Porta de Acesso:* **Fechada (Acesso controlled)**

Caso ocorra um evento fora do comum (ex: temperatura ultrapassar o limite ou porta mantida aberta por tempo excessivo), o painel altera visualmente o indicador para **"Alerta / Ajuste Necessário"**, permitindo ação imediata.

## 5. Sensores e Componentes Utilizados

Para garantir uma solução viável, de baixo custo e fácil prototipagem comercial, a arquitetura utiliza componentes padrão de mercado que também possuem suporte nativo em simuladores como o **Wokwi**:

1. **Sensor de Temperatura e Umidade (DHT22 / DHT11):**

   * *Função:* Mede continuamente o clima dentro do laboratório para garantir que os equipamentos e amostras operem em condições térmicas perfeitas.

2. **Sensor de Acesso / Porta (Sensor Magnético Reed Switch):**

   * *Função:* Monitora o estado de abertura e fechamento de portas de acesso restrito.

   * *Nota de Prototipagem:* Em ambientes de teste e simulação (como no **Wokwi**), este sensor pode ser perfeitamente simulado através de um componente prático de chave alavanca (*Slide Switch*) ou botão (*Pushbutton*), representando os estados "Porta Fechada" (Circuito Fechado) ou "Porta Aberta" (Circuito Aberto).

3. **Microcontrolador com Wi-Fi Integrado (ESP32):**

   * *Função:* Funciona como o "cérebro" local da estação de sensoriamento. Ele lê os dados dos sensores e os converte em pacotes digitais para envio sem fio.

## 6. Meio de Comunicação e Protocolos

* **Rede de Comunicação:** Conexão sem fio via **Wi-Fi** local do laboratório.

* **Protocolos de Aplicação:**

  * **MQTT (Message Queuing Telemetry Transport):** Protocolo extremamente leve e otimizado para IoT, ideal para envio contínuo de pequenos pacotes de dados de sensoriamento.

  * **HTTP / REST:** Utilizado secundariamente para integrações diretas entre APIs de backend e o painel final.

* **Ambiente de Nuvem:** Broker/Servidor responsável por receber os pacotes MQTT do ESP32, processá-los e armazená-los para consumo do Dashboard.

## 7. Fluxograma de Funcionamento (Arquitetura Visual)

O fluxograma completo da arquitetura foi desenvolvido no **Lucidchart** e demonstra a jornada contínua dos dados desde os sensores até o painel web.

🔗 **Link Interativo do Diagrama (Lucidchart):** [Acessar Fluxograma no Lucidchart](https://lucid.app/lucidchart/57d14a96-74d2-48ed-9cef-5f1bca4090e8/edit?viewport_loc=-552%2C-582%2C3248%2C1758%2C0_0&invitationId=inv_a766faec-91cd-40c2-a006-22d0ae915444)

### Diagrama Visual do Fluxo

```
[ 1. COLETA ]               [ 2. PROCESSAMENTO LOCAL ]          [ 3. TRANSMISSÃO ]            [ 4. DESTINO & AÇÃO ]
Sensores (DHT22 & Porta)  --->  Microcontrolador ESP32   --->  Wi-Fi / MQTT / Nuvem  --->  Dashboard Educativo
(Laboratório CTMSP)           (Sinais -> Dados Digitais)       (Envio de Pacotes)             (Visão Pública e Alertas)
```

### Explicação Detalhada do Fluxo:

1. **1. Coleta (Sensoriamento no Laboratório):** Os sensores físicos (Temperatura/Umidade e Sensor Magnético de Porta) captam as variáveis do ambiente de pesquisa do CTMSP e geram sinais elétricos.
2. **2. Processamento Local (ESP32):** O microcontrolador ESP32 recebe esses impulsos elétricos, interpreta os valores e os converte em dados digitais organizados.
3. **3. Transmissão de Dados (Rede e Nuvem):** Utilizando a rede Wi-Fi e os protocolos MQTT ou HTTP, o ESP32 envia os pacotes digitais para o servidor/broker na nuvem.
4. **4. Destino, Visualização e Tomada de Ação:**
   * **Dashboard Educativo:** Os dados na nuvem alimentam a interface pública, apresentando indicadores amigáveis para a sociedade sobre a segurança do laboratório.
   * **Alerta Visual (Ramificação de Contingência):** Se algum parâmetro for alterado fora dos limites estabelecidos (ex: elevação de temperatura ou porta mantida aberta), um alerta visual é acionado instantaneamente no painel.

## 8. Links de Evidências e Entregáveis

* **Repositório do Código e Documentação (GitHub):** [Acessar Repositório Público no GitHub](https://github.com/Nexo-Challenge/s1-iot-redes)

* **Fluxograma Edição/Visualização (Lucidchart):** [Acessar Fluxograma no Lucidchart](https://lucid.app/lucidchart/57d14a96-74d2-48ed-9cef-5f1bca4090e8/edit?viewport_loc=-552%2C-582%2C3248%2C1758%2C0_0&invitationId=inv_a766faec-91cd-40c2-a006-22d0ae915444)

* **Vídeo Demonstrativo (YouTube):** `[Cole aqui o Link do Vídeo Unlisted no YouTube (Aprox. 5 min)]`

  * *Conteúdo do vídeo:* Apresentação do problema, proposta da solução para a Marinha, detalhamento da tecnologia IoT/Redes e explicação didática do fluxograma.

## 9. Instruções para Prototipagem e Simulação no Wokwi

Para reproduzir ou simular esta arquitetura no simulador online **Wokwi**:

1. Acesse o [Wokwi.com](https://wokwi.com/).

2. Inicie um projeto com a placa **ESP32**.

3. Adicione o componente **DHT22** e conecte o pino de dados a uma porta digital do ESP32 (ex: `GPIO 15`).

4. Adicione um **Slide Switch** (simulando o sensor magnético de porta) e conecte a uma porta digital com resistor de pull-up (ex: `GPIO 4`).

5. Execute o código de leitura em C++/Arduino lendo os dados de temperatura e chave de porta, transmitindo as saídas via Serial Monitor ou via biblioteca MQTT `PubSubClient` conectada ao Wi-Fi virtual do Wokwi (`Wokwi-GUEST`).
