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
* CH AD = Chave C do lado direito
* CH BD = Chave D do lado direito

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/ponte-01.jpg" width="300">


### (2.1) Transistores como Chave Liga/Desliga

A ideia da ponte H é herdar o funcionamento do transistor nas suas regiões de corte, saturação e região ativa.

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/transistor-h-bridge.gif" width="300">


Corrente de coletor/emissor vs tensão de base.

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

