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

## (2) Situações do Transisto: Cortado / Saturado / Ativo


<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/transistor-cortado.png" width="500">


<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/transistor-saturado.png" width="500">


<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/transistor-ativo.png" width="500">

## (3) Ponte H por Dentro

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

### (3.1) Topologia da Ponte H

A ideia da ponte H é atuar como uma chave liga/desliga e herdar o funcionamento do transistor nas suas regiões de saturação (liga) e corte (desliga).

Veja a imagem a seguir como fica o fluxo de corrente para cada valor dos pinos de controle **INA** e **INB**.

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/transistor-h-bridge.gif" width="600">

| INA | INB | Fluxo / Cor | Situação |
|-----|-----|-------|----------|
| 0   | 0   | ninguém conduz   | motor parado |
| 0   | 1   | Q1 e Q4 conduzem / vermelho | motor vira para direita|
| 1   | 0   | Q2 e Q3 conduzem / azul | motor vira para esquerda|
| 1   | 1   | ninguém conduz   | motor parado |

Note que se você excitar os dois lados do controle ao mesmo tempo, os dois lados vão se excitar e a d.d.p. no motor será ZERO, porque ambos lados terão a mesma tensão. E quando você corta o controle (nível ZERO em INA e INB) também nada acontece porque a d.d.p. continua ZERO nos terminais do motor.

## (4) Chips e Drivers para Ponte H

### (4.1) Ponte L298

A ponte H mais famosa do mundo do Arduino é a da foto abaixo.

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/L298_shield.png" width="300">

Esse shield possui os seguintes pinos de controle:

<a href="https://imgv2-1-f.scribdassets.com/img/document/231652629/original/a52085b9ea/1?v=1">
  <img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/cheetos.png" alt="Datacheetos" width="100"/>
</a>

### (4.2) Ponte BTS7960

Essa ponte suporta 43A e controla apenas 1 motor

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/ponte-07.png" width="300">


### (4.3) Ponte H feito na Raça:

Esse projeto de Ponte H é feito de transistor BJT da família TIP, que são transistores mais poderesos que o BC548 e BC558.

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/ponte-04.png" width="600">

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/ponte-03.png" width="600">


Para você descobrir quão poderoso é uma ponte H, consulte o [DATASHEET](https://www.st.com/content/ccc/resource/technical/document/datasheet/82/c2/f6/15/8b/d4/49/6a/CD00142950.pdf/files/CD00142950.pdf/jcr:content/translations/en.CD00142950.pdf) do transistor envolvido.


### (4.4) Como evolução, temos Ponte H em Chip


<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/L298.png" width="300">

[DATASHEET](https://rocelec.widen.net/view/pdf/tjbkod1kk5/l293.pdf?t.download=true&u=5oefqw)


## (5) Simulando no Tinkecad

Abrir o Tinkercad, montar o circuito abaixo e associar o código-fonte disponível. Dê o play e veja o controle de rotação sendo feito.

<img src="https://github.com/agodoi/m05-semana10/blob/main/imgs/arduino-ponte-h.png" width="800">

Esse código abaixo serve para simular um motor girando para direita e para esquerda em intervalos de tempo fixo.

```
struct Roda {
  bool active, dir;
  uint8_t pin1;
  uint8_t pin2;
  Roda(const uint8_t& _pin1, const uint8_t& _pin2) : pin1(_pin1), pin2(_pin2) {}
  void init() {
    pinMode(pin1, OUTPUT);
    pinMode(pin2, OUTPUT);
  }
  void stop() {
    active = false;
    digitalWrite(pin1, LOW);
    digitalWrite(pin2, LOW);
  }

  void forward() {
    active = true;
    dir = true;
    digitalWrite(pin1, HIGH);
    digitalWrite(pin2, LOW);
  }

  void inverse() {
    active = true;
    dir = false;
    digitalWrite(pin1, LOW);
    digitalWrite(pin2, HIGH);
  }
};

Roda rodaDireita(3, 4), rodaEsquerda(5, 4);

void setup() {
  Serial.begin(9600);
  rodaDireita.init();
  rodaEsquerda.init();
  /// POWER SUPPLY (VCC) - analog
  pinMode(5, OUTPUT);

}
float clock = 0.f;
void loop() {
  analogWrite(5, 500);
  float t = millis() - clock;
  if(t >= 0 && t < 1000) {
  	rodaDireita.forward();
  }
  else if(t >= 1000 && t < 2000) {
  	rodaDireita.inverse();
  }
  else if(t >= 2000 && t < 3000) {
  	rodaDireita.stop();
  }
  else if(t >= 3000) {
  	clock = millis();
  }
}
```

## (6) Propor um desafio valendo um bis

Valendo 1 Bis
falar do duty cicle para controlar a velocidade do motor


