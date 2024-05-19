3. Clique em "OK" para salvar.

### Instalar a Placa NodeMCU ESP8266:

1. Navegue até "Ferramentas" > "Placa:" > "Gerenciador de Placas...".
2. Na janela do Gerenciador de Placas, digite "ESP8266" na barra de pesquisa.
3. Encontre o pacote chamado "esp8266 by ESP8266 Community" e clique em "Instalar".

### Selecionar a Placa NodeMCU ESP8266:

Após a instalação, vá para "Ferramentas" > "Placa:" e selecione "NodeMCU 1.0 (ESP-12E Module)".

## Conectar e Carregar um Sketch

### Conectar o NodeMCU ao Computador:

Use um cabo micro USB para conectar o NodeMCU à porta USB do seu computador.

### Selecionar a Porta COM:

Vá para "Ferramentas" > "Porta" e selecione a porta COM que aparece com o nome do seu NodeMCU. Se você não tem certeza de qual porta selecionar, desconecte a placa, abra o menu novamente para ver as portas listadas, reconecte a placa e veja qual nova porta aparece.


## Modelo de Montagem

O sensor de som KY-037 é conectado ao microcontrolador NodeMCU ESP8266, que irá processar os dados dos níveis de som. Os cabos de alimentação do sensor de som são conectados às entradas de 3,3V e GND do NodeMCU, enquanto o sinal de saída do sensor é conectado ao pino analógico A0. Este sistema pode ser alimentado por uma fonte de 3,7V, adequada para a operação dos componentes eletrônicos envolvidos, ou através de um cabo USB direto de um computador.

![Protótipo Montado](![20240518_152536](https://github.com/Piruca93/medidor-de-decibeis/assets/119772189/b6f27c6a-f9d4-4030-93d0-35637a8af990)) <!-- Note: Replace with actual image URL -->
*Figura 1: Protótipo completo montado, mostrando o NodeMCU, o sensor de som KY-037 e os jumpers conectados.*

## Configurando o MQTT Explorer

1. Baixe e instale o MQTT Explorer a partir do site oficial: [MQTT Explorer](http://mqtt-explorer.com/).
2. Configure uma conexão com o broker MQTT:
- Endereço do broker: `test.mosquitto.org`
- Porta: `1883`
3. Crie um tópico chamado `sound_data` para visualizar os dados publicados pelo NodeMCU.

## Funcionamento

- **NodeMCU ESP8266:** Processa os dados do sensor de som e verifica os níveis de som.
- **Sensor de Som KY-037:** Captura os níveis de som ambiente e envia para o NodeMCU.
- **Comunicação MQTT:** Configuração do NodeMCU para enviar dados dos níveis de som via protocolo MQTT para a ferramenta MQTT Explorer, permitindo monitoramento remoto.

## Vídeo-demonstração

[Assista ao vídeo-demonstração no YouTube](https://youtu.be/H3eee4xpNDw)

## Dados obtidos via MQTT no MQTT Explorer

### Gráfico de Leitura no MQTT Explorer:

No contexto do projeto de monitoramento de som utilizando o NodeMCU e o sensor KY-037, implementei um filtro de média móvel para suavizar os sinais de entrada do sensor. Esta implementação especificamente utiliza uma média móvel simples, onde o valor atual do sensor é combinado com o último valor filtrado. O fator de 0.5 para ambos os valores atuais e anteriores equilibra a contribuição de cada um, oferecendo uma suavização efetiva sem atrasar demais a resposta a mudanças reais no sinal.


*Figura 2: Gráfico de leitura no MQTT Explorer mostrando os dados de som coletados e suavizados pelo filtro de média móvel.*

## Referências

- IoT – Project Ideas. About Arduino based Decibel meter with Sound Sensor. Disponível em: <https://iot-projects-ideas.com/arduino-based-decibel-meter-with-sound-sensor>. Acesso em: 18 maio 2024.
- SENADO FEDERAL. Poluição sonora prejudica a saúde e preocupa especialistas. Disponível em: <https://www12.senado.leg.br/noticias/especiais/especial-cidadania/poluicao-sonora-prejudica-a-saude-e-preocupa-especialistas/poluicao-sonora-prejudica-a-saude-e-preocupa-especialistas>. Acesso em: 9 ago. 2023.
- Toda Matéria. Poluição Sonora. Disponível em: <https://www.todamateria.com.br/poluicao-sonora/>. Acesso em: 18/05/2024.
- Brasil Escola. Poluição Sonora. Disponível em: <https://brasilescola.uol.com.br/biologia/poluicao-sonora.htm>. Acesso em: 18/05/2023.
- AVM Faculdade Integrada. Documento sem título. Disponível em: <http://www.avm.edu.br/docpdf/monografias_publicadas/T205720.pdf>. Acesso em: 18/05/2024.
- CAP Sistema. Guia de Conexão do Potenciômetro ao Arduino. CAP Sistema, 26 de abril de 2021. Disponível em: <https://www.capsistema.com.br/guia-de-conexao-do-potenciometro-ao-arduino>. Acesso em: 18/05/2024.
- Comunicando-se via MQTT com o ESP32 (MIC404). Disponível em: <https://newtoncbraga.com.br/index.php/microcontrolador-esp32/17087-mic404>. Acesso em: 18/05/2024.
- ESP32 - Sound Sensor. Disponível em: <https://www.esp32io.com/tutorials/esp32-sound-sensor>. Acesso em: 18/05/2021.
