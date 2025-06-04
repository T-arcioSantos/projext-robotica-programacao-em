
---

# Materiais de Aula - Práticas de Robótica Educacional

---

## Prática 1: LED com Brilho Pulsante

### 1. Roteiro de Aula (Professor)

* **Título da Aula:** Controle de Brilho com PWM: Lâmpada Pulsante
* **Duração Estimada:** 50-60 minutos
* **Objetivos de Aprendizagem:**

  * Relembrar os conceitos básicos de LED e resistor.
  * Introduzir o conceito de modulação por largura de pulso (PWM).
  * Montar um circuito simples com interruptor deslizante.
  * Aplicar a função `analogWrite()` para controlar o brilho de um LED.
  * Compreender o uso de funções matemáticas no controle de dispositivos.
* **Materiais:**

  * Computador com Arduino IDE ou Tinkercad.
  * Kit Arduino: Arduino Uno, cabo USB, protoboard, LED verde de 5mm, resistor (220Ω ou 330Ω), interruptor deslizante, fios jumper.
  * Projetor.
* **Procedimento:**

  1. **Revisão:** Relembrar prática anterior (LED piscante), apresentar o desafio: controlar o brilho.
  2. **PWM e analogWrite:** Explicar brevemente o conceito de PWM e como o Arduino simula diferentes níveis de tensão.
  3. **Componentes e Circuito:** Apresentar LED verde, resistor, interruptor deslizante. Mostrar esquema de ligação.
  4. **Montagem:** Auxiliar alunos na montagem do circuito com o interruptor.
  5. **Código e Explicação:** Explicar o código da lâmpada pulsante: uso de seno para suavidade, analogWrite(), uso de variáveis.
  6. **Teste e Exploração:** Executar o código, observar o efeito de “respiração” da luz.
* **Avaliação:** Verificar montagem correta, funcionamento do código e entendimento de `analogWrite()`.
* **Desafios (Opcional/Tarefa):** Testar diferentes delays(aumentar/diminuir) e funções matemáticas.

---

### 2. Esboço dos Slides (Prática 2)

* **Slide 1:** Título: Prática 2 - Lâmpada Pulsante com PWM
* **Slide 2:** Revisando o LED Piscar (Resumo da prática anterior)
* **Slide 3:** O que é PWM? (Explicação visual de pulsos digitais)
* **Slide 4:** Novos Componentes (LED verde, interruptor deslizante)
* **Slide 5:** Esquema de Montagem (Diagrama com interruptor, resistor, LED, GND e pino 11)
* **Slide 6:** O que é o analogWrite()? (Explicação da função)
* **Slide 7:** O Código Pulsante - Visão Geral
* **Slide 8:** Usando Funções Matemáticas (seno, variação suave)
* **Slide 9:** Explicando estruturas de repetição
* **Slide 10:** Resultados Esperados (Efeito de respiração do LED)
* **Slide 11:** Hora de Testar!
* **Slide 12:** Desafios e Explorações
* **Slide 13:** Conclusão e Próximos Passos

---

### 3. Apostila do Aluno (Prática 2)

**(Cabeçalho: Prática 2 – Lâmpada Pulsante com PWM)**

**Introdução:**
Nesta prática, vamos aprender a controlar o brilho de um LED usando a técnica de PWM (Pulse Width Modulation) e a usar um interruptor deslizante com o Arduino. Vamos montar um circuito com um LED verde e um interruptor, e usaremos matemática para criar um efeito suave de pulsação.

**Componentes Necessários:**

* 1x Placa Arduino Uno
* 1x Cabo USB
* 1x Protoboard
* 1x LED verde difuso de 5 mm
* 1x Resistor de 220Ω ou 330Ω
* 1x Interruptor deslizante
* Fios jumper

**Montando o Circuito:**
Conecte o LED ao pino 11 do Arduino com um resistor em série. Use o interruptor deslizante para controlar a alimentação ou ativação do circuito.

**(Inserir diagrama do circuito aqui)**

**Código Arduino:**

```cpp
// Projeto X – Lâmpada pulsante

int ledPin = 11;
float sinVal;
int ledVal;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  for (int x = 0; x < 180; x++) {
    sinVal = sin(x * (3.1416 / 180)); // Converte para radianos e obtém o seno
    ledVal = int(sinVal * 255);       // Converte para escala PWM (0 a 255)
    analogWrite(ledPin, ledVal);      // Define brilho do LED
    delay(25);                        // Espera um pouco antes de continuar
  }
}
```

**Entendendo o Código:**

* `analogWrite(pino, valor)`: Controla o brilho via PWM (0 = apagado, 255 = brilho máximo).
* `sin()`: Função matemática para suavizar a variação de brilho.
* `for`: Repete a variação gradualmente de 0 a 180 graus.

**Executando:**

* Faça o upload do código (IDE) ou clique em “Start Simulation” (Tinkercad). O LED deverá pulsar suavemente!

**Desafio:**

* Altere a função matemática ou o tempo de delay para experimentar outros efeitos de brilho.

---