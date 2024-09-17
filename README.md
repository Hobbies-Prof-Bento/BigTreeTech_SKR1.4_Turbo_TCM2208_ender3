# BigTreeTech SKR1.4 Turbo + TCM2208 + ender3

Essse repositório é para quem comprou uma BigTreeTech SKR 1.4 turbo com TMC 2208 e gostaria de configurar em uma ender 3 comum, sem BLTouch, sem dois motores, com o display LCD simples.

README IN ENGLISH: LINK

Segue link do vídeo de como criei esse repositório: LINK

O repositório foi dividido para realização de dois procedimentos distintos e independentes:

- 1: Para quem quer apenas instalar o firmware sem alterar as configurações, ideal para quem tem a ender original e precisou trocar apenas a placa.
- 2: Para quem deseja mudar as configurações de acordo com as mudanças que realizou na impressora.

### Segue vídeo de como o repositório foi montado: 

## Ajustes iniciais de Hardware

### 1 - O primeiro passo é deixar os drivers no modo UART (para não precisar fazer ajuste físico no driver) assim como mostra a imagem.

![image](https://github.com/user-attachments/assets/cbe6c088-17b8-407b-bc51-223cabd694ad)

se a placa SKR 1.4 turbo for nova ela estará com quatro jumpers colocados, terá que remover para deixar igual a imagem.

### 2 - Adicionar os drivers TCM2208 na placa junto com os dissipadores

Colocar os cinco drivers nos cincos slots diponíveis para eles

![image](https://github.com/user-attachments/assets/93a567db-fc7c-425e-896f-0386e138d58b)

as cores dos compenentes ajudam na hora de encaixar, contudo cuidado para não colocar os drivers de maneira contrária.

### 3 - Plugar os outros componentes

Na plata está descrito onde vai cada componente, contudo está descrito abaixo onde plugar os componentes da ender 3.

**LEMBRE-SE DE QUE EM ALGUMAS CONEXÃO TEM O "+" E O "-", CUIDADO PARA NÃO LIGAR INVERTIDO**

![image](https://github.com/user-attachments/assets/dd5a70ec-325a-40c2-b003-b981ef68fd21)

1. **DCIN:** entrada de alimentação 24V;
2. **HB:** aquecimento da mesa;
3. **HE0:** aquecimento bico (o HE1 é para aquecer um segundo bico se tiver);
4. **FAN:** ventuinha que fica ligado direto (frontal do hotend);
5. **CNC FAN:** ventuinha para resfriamento de filamento (lateral do hotend);
6. **XM:** motor de passo eixo x;
7. **YM:** motor de passo eixo Y;
8. **ZAM:** motor de passo Z (o ZBM é para um segundo motor síncrono, se tiver);
9. **EM0:** motor extrusora (o EM1 é para uma segunda extrusora);
10. **EXP1:** display LCD padrão ender 3;
11. **TB:** sensor de temperatura da base;
12. **TH0:** sensor de temperatura do bico;
13. **X Stop:** sensor de fim de curso do eixo X (provavelmente seu plug é de dois fios, colocar conforme a caixinha verde);
14. **Y Stop:** sensor de fim de curso do eixo Y (provavelmente seu plug é de dois fios, colocar conforme a caixinha verde);
15. **Z Stop:** sensor de fim de curso do eixo Z (provavelmente seu plug é de dois fios, colocar conforme a caixinha verde).

## PROCEDIMENTO 1

Se você deseja apenas usar as configurações já compiladas e descarregar o firmware em sua ender 3, basta baixar o arquivo "firmware.bin" na pasta "firmware", salvar no cartão de memória que vai na impressora, desligar a impressora, colocar o cartão e religar a impressora. Ao religar a impressora a placa irá ler o arquivo "firmware.bin" e atualizar o firmware.

segue link direto para o arquivo: LINK

## PROCEDIMENTO 2

Se você deseja fazer alterações no firmware da impressora antes de instalar, voce deve seguir os passos seguintes.

### 1 -  Baixar ferramentas necessárias

1. VScode: baixar e instalar o visual studio code (https://code.visualstudio.com/Download);
2. platformIO IDE: baixar extensão do VScode platformIO IDE para compilação:
   
   ![image](https://github.com/user-attachments/assets/fe10a189-faae-440c-a83e-5abcf3756ce1)
4. Auto Build Marlin: baixar extensão do VScode Auto Muild Marlin:

   ![image](https://github.com/user-attachments/assets/666de9ba-0901-4790-934d-7875fb20f3a8)

### 2 - baixar repositório

As pasta do repositório podem ser obtidas de duas maneiras:

1. clonando repositório com comando: 
```
git clone https://github.com/Hobbies-Prof-Bento/BigTreeTech_SKR1.4_Turbo_TCM2208_ender3.git
```
2. clicando em "code" e depois "Download.zip" (é necessário extrair as pastas do arquivo .zip)
   ![image](https://github.com/user-attachments/assets/61a8a87b-6484-40d9-8dca-fedeffe9ad2f)

### 3 - Acessar o repositório com o VScode

1. Abrir o VScode;
2. ir em "arquivo";
3. selecionar "abrir pasta";

![image](https://github.com/user-attachments/assets/f0d4651c-0e71-438b-ba36-bb2b53f5486e)
   
4. escolher a pasta do repositório;

![image](https://github.com/user-attachments/assets/34a8b618-ea2a-4c3b-8195-6dded08b444a)
   
5. realizar as alterações.

No arquivo **Configuration.h** do Marlin, você pode fazer várias alterações que afetam o comportamento e as funcionalidades da impressora 3D:

1. Dimensões e limites da cama: Ajuste o tamanho da cama de impressão e os limites de movimento dos eixos.
2. Velocidades e acelerações: Configure as velocidades e acelerações dos eixos.
3. Corrente dos motores: Defina a corrente dos motores de passo.
4. Passos por milímetro (steps/mm): Ajuste a precisão do movimento dos eixos e extrusora.
5. Temperatura: Configure o controle de temperatura do hotend e da cama.

Você também pode ajustar funções avançadas como o uso de sensores de nível de cama (BLTouch), ativar o controle PID, configurar drivers específicos (como TMC), entre outras funcionalidades específicas da sua impressora.

No arquivo **Configuration_adv.h** do Marlin, você pode ajustar configurações mais avançadas que afetam o desempenho e as funcionalidades específicas da impressora. Algumas das principais alterações possíveis incluem:

1. Configurações de drivers (como TMC): Ajuste correntes, interpolação, e modos como StealthChop ou SpreadCycle.
2. PID Avançado: Controle de parâmetros PID mais detalhado.
3. Gerenciamento de Ventiladores: Configurar comportamento de ventiladores para resfriamento da placa e dos motores.
4. Homings e Movimentos: Configurações de sensorless homing e múltiplos motores Z.
5. Calibração automática e mesh leveling.
  
   Essas opções permitem personalizar ainda mais a experiência de impressão e o desempenho da impressora.

## Compilando alterações

Apos realizar as alterações necessário, clique em "Auto Build Marlin" e depois selecione "Show ABM Painel"
![image](https://github.com/user-attachments/assets/2dfd7b6c-cdab-4837-94c6-1a3dffa1e7e7)

Irá aparecer uma interface com informações das configuração e botões "build" e "update", clique em "build"
![image](https://github.com/user-attachments/assets/c25e484c-b175-4fc6-91b5-8335c21b6e23)

Vai aparecer uma mensagem de alerta, não se preocupe.

![image](https://github.com/user-attachments/assets/26c612f3-5c9b-4386-b61f-274f7f730e0a)

O arquivo "firmware.bin" irá aparecer na dirtório "<pasta_onde_o_repositório_esta_salvo>\.pio\build\LPC1769

## Atualizando firmware

salvar no cartão de memória que vai na impressora o arquivo "firmware.bin", desligar a impressora, colocar o cartão e religar a impressora. Ao religar a impressora a placa irá ler o arquivo "firmware.bin" e atualizar o firmware.


