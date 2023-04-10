# grua_esp32_tft_lcd
Controle e visualização do posicionamento de grua em display com ESP32

## Componentes Fisícos

![image](https://user-images.githubusercontent.com/50549048/230969561-1447cf24-667f-4433-8fed-da2bd0bc41f2.png)

Joystick HW504: Dispositivo físico que é conectado ao ESP32 NODEMCU-32S por meio de fios. O joystick pode é um pequeno dispositivo com uma alça que pode ser movida em diferentes direções. Possúi tanto deslocamento em X e Y assim como um botão Z para propósito geral. É conectado a uma fonte, utilizada a saída de 3.3V do ESP32 e um terra, também conectado ao terra do ESP32. 

ESP32 NODEMCU-32S: Trata-se de uma pequena placa microcontroladora que possui pinos e conectores para conectar outros dispositivos. O ESP32 pode ser conectado a um computador ou fonte de energia usando um cabo USB. Também pode ser conectado a uma placa de ensaio ou outra placa de prototipagem para teste, que é por meio dessa que será conectado aos demais dispositivos do projeto.

Display ILI9341: Pequeno módulo de display que pode ser montado em uma protoboard ou outra placa de prototipagem. O monitor é uma tela pequena com resolução de 320 x 240 pixels. Também pode ter pinos ou conectores para conectar ao ESP32 usando fios. Será responsavél por receber os dados e exibir em sua tela a grua e sua movimentação.

## Visão Lógica do Sistema

![image](https://user-images.githubusercontent.com/50549048/230970318-8acd03a2-3a6b-4198-ab6a-b3af2d9f5751.png)

O sistema irá funcionar baseado em uma lógica de interface, lógica de negócios e dados. 

### Interface com o Usuário

![image](https://user-images.githubusercontent.com/50549048/230971363-cf8e0a68-2726-44d6-8a1f-437d6b7cf16b.png)

A interface com o usuário se trata da movimentação da grua. Nela o usário pode interagir com o Joystick o movendo no eixo X e Y ou pressionando o botão Z. O eixo X pode ser alternado entre movimentação da grua em "eixo" para a esquerda ou direita e também, quando pressinado o botão Z para alternar a função, o eixo X se torna referente ao ajuste da posição do angulo "teta". O eixo Y do Joystick irá representar a "altura" da grua.

### Lógica de Negócios

O sistema possuí uma lógica baseada na movimentação do usário. Para simular uma grua real com sua movimentação fisica, o sistema irá receber a movimentação do joystick e tentar movimentar a grua de acordo a movimentação do joystick. Então toda vez que o usuário mexer na "altura", será identificado a movimentação da grua e ela será movimentada um valor para cima ou para baixo, assim como o eixo ou angulo, de acordo a escolha feita com o z. O sistema irá identificar a movimentação e então calcular a nova posição do dipositivo. O joystick não movimenta diretamenta a grua para uma posição, apenas serve para acionar uma movimentação, respeitando assim os aspector fisícos do dispositivo. Após calcular a nova posição da grua os valores são atualizados e enviados para o display. 
sel=1 (x=angulo, y=altura)

### Dados

#COLOCAR AQUI IMAGEM DAS VISÕES DA GRUA

Os dados recebidos da lógica de negócios são enviados para o display. O display conta com a exibição da grua em duas visões. Uma superior, aonde é possível visualizar o angulo de ajuste e uma lateral aonde pode ser conferido o deslocamento do eixo e da altura. 
