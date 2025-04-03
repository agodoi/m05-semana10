# Atendimento do Professor

## Terças e quintas. Professor de horário parcial. Nesses 2 dias, podem contar comigo!

# Semama 10 - Ponte H Transistorizado

## (1) Impacto em Projetos Futuros

### Serve para o controle de motores DC, especialmente no controle do sentido de rotação e controle de velocidade via PWM (largura de pulso).

### Imagine quais circuitos você poderia desenvolver usando a ponte H. Aqui vão alguns exemplos:

#### Braços robóticos com movimento reversível

#### Fechadura eletrônica com motor DC

#### Cortinas automatizadas com motores reversíveis

#### Motores de retrovisores elétricos

#### Controle de servoacionamento ou gimbal (estabilização)

#### Portões automáticos e cancelas

---
## (2) Ponte H por Dentro

Observe o circuito a seguir. A Ponte H literalmente tem a forma de um H e a função dela é ter 4 chaves liga/desliga feitas de transistor.

* CH AE = Chave A do lado esquerdo
* CH BE = Chave B do lado esquerdo
* CH AD = Chave A do lado direito
* CH BD = Chave B do lado direito

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/ponte-01.jpg" width="300">


Vamos juntar uns ajustes:

* As chaves da ESQUERDA serão um transistor NPN e PNP em série. O mesmo para as chaves da DIREITA;
* Os pinos de controle das chaves A e B da Esquerda serão unificados para um único pino ESQUERDO e vamos apelidar de **INA** e as chaves A e B da Direita para um único pino DIREITA e vamos apelidá-lo de **INB**;
* Acrescentar os resistores de base para cada transistor;
* Colocar uma bateria no circuito; Veja a imagem a seguir para entender como ficou.


<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/ponte-06.png" width="600">

### (2.1) Transistores como Chave Liga/Desliga

A ideia da ponte H é herdar o funcionamento do transistor nas suas regiões de corte, saturação.

Veja a imagem a seguir como fica o fluxo de corrente para cada valor de **INA** e **INB**.

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/transistor-h-bridge.gif" width="600">

| INA | INB | Fluxo | Situação | Cor do fluxo |
|-----|-----|-------|----------| -------------|
| 0   | 0   | ninguém conduz   | motor parado | nenhum |
| 0   | 1   | Q1 e Q4 conduzem | motor vira para direita| vermelho |
| 1   | 0   | Q2 e Q3 conduzem | motor vira para esquerda| azul |
| 1   | 1   | ninguém conduz   | motor parado | nenhum |

Note que se você excitar os dois lados do controle ao mesmo tempo, os dois lados vão se excitar e a d.d.p. no motor será ZERO, porque ambos lados terão a mesma tensão. E quando você corta o controle (nível ZERO em INA e INB) também nada acontece porque a d.d.p. continua ZERO nos terminais do motor.


2. Topologia da Ponte H
Estrutura com 4 transistores (Q1–Q4).

Caminhos de corrente para sentido horário e anti-horário do motor.

Explicação de funcionamento:

Q1 e Q4 ligados → motor gira num sentido.

Q2 e Q3 ligados → sentido oposto.

Q1 e Q2 ou Q3 e Q4 juntos → curto (situação a ser evitada).

3. Controle da Polarização
Como acionar cada transistor com sinais digitais.

Utilização de resistores de base/gate para controle.

Importância do dead-time (tempo morto) para evitar curto.

Exemplos de circuitos de polarização.

4. Proteção e Eficiência
Diodos de flyback para proteção contra corrente reversa (motor DC como carga indutiva).

Considerações sobre perdas por comutação e aquecimento.

Uso de drivers de gate/base.

5. Simulação ou Demonstração Prática
Montagem no Proteus, LTspice ou simulação online como Falstad/Wokwi.

Comando de um motor DC simples via Arduino ou ESP32 com ponte H.

Alternativa: H-bridge pronta (ex: L298N) e comparação com montagem discreta.

PRÁTICA - MONTAR O CIRCUITO NO TINKERCAD

📌 Dicas Extras para Aula
Mostre um exemplo de ponte H com transistores NPN e PNP, depois com MOSFETs N e P.

Traga um motorzinho DC pequeno para demonstração prática com Arduino e L298N.

Use animações ou simulações interativas para mostrar o fluxo de corrente.

