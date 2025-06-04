
---

# Materiais de Aula - Práticas de Robótica Educacional

---

## Prática 2-1: Semáforo com LEDs (Sistema de 4 Estados do Reino Unido)

### 1. Roteiro de Aula (Professor)

* **Título da Aula:** Construindo um Semáforo com Arduino
* **Duração Estimada:** 50-60 minutos
* **Objetivos de Aprendizagem:**

  * Compreender os conceitos básicos de sinalização com LEDs múltiplos.
  * Simular um sistema real de semáforo em miniatura.
  * Introduzir o conceito de estados e sequenciamento com `delay()` e `digitalWrite()`.
  * Utilizar boas práticas de identificação e controle de pinos.
* **Materiais:**

  * Kit Arduino Uno com cabo USB
  * Protoboard
  * 1 LED vermelho difuso
  * 1 LED amarelo difuso
  * 1 LED verde difuso
  * 3 resistores de 150Ω (ou próximos)
  * Fios jumper
* **Procedimento:**

  1. **Introdução:** Explicar o objetivo do projeto: simular o funcionamento de um semáforo.
  2. **Revisão de LEDs e `digitalWrite()`:** Mostrar como acender/apagar LEDs via código.
  3. **Montagem do Circuito:** Guiar os alunos na ligação dos três LEDs aos pinos digitais 9, 10 e 11, cada um com resistor ligado ao GND.
  4. **Explicação do Código:** Apresentar o código e discutir a lógica do ciclo semafórico (vermelho → vermelho+amarelo → verde → amarelo → vermelho).
  5. **Teste e Exploração:** Carregar o código, observar o ciclo de LEDs. Discutir variações culturais de sinalização.
* **Avaliação:** Checar se os LEDs acendem nas sequências corretas e se os alunos compreendem o uso de `delay()` e `digitalWrite()`.
* **Desafios (Opcional/Tarefa):**

  * Implementar o sistema sem `delay()` (usando `millis()`).
  * Alterar os tempos para simular diferentes situações (ex: hora do rush).
  * Mudar o sistema do semáforo para o brasileiro.

---

### 2. Esboço dos Slides (Prática 3)

* **Slide 1:** Título - Prática 2: Construindo um Semáforo com Arduino
* **Slide 2:** Para que servem os semáforos?
* **Slide 3:** Sinalização no Reino Unido x Brasil (ilustração dos 4 estados)
* **Slide 4:** Componentes necessários 
* **Slide 5:** Esquema de montagem (protoboard, Arduino e LEDs nos pinos 9, 10 e 11)
* **Slide 6:** Código comentado - Parte 1 (Explicando o setup)
* **Slide 7:** Código comentado - Parte 2 (Explicando o loop)
* **Slide 8:** O que acontece a cada etapa?
* **Slide 9:** Vamos testar e observar!
* **Slide 10:** Desafios extras (sem `delay`, pedestre, outros países)
* **Slide 11:** Conclusão da prática e próximos passos

---

### 3. Apostila do Aluno (Prática 3)

**(Cabeçalho: Prática 3 – Semáforo com LEDs e Arduino)**

**Introdução:**
Nesta prática, vamos simular um semáforo real usando três LEDs e o Arduino. A sequência segue o padrão do Reino Unido, onde há uma transição com luz vermelha e amarela acesas antes de mudar para o verde.

**Componentes Necessários:**

* 1x Arduino Uno
* 1x Protoboard
* 1x LED vermelho difuso
* 1x LED amarelo difuso
* 1x LED verde difuso
* 3x Resistores de 150Ω
* Fios jumper

**Montando o Circuito:**

1. Conecte o LED vermelho ao pino 11, o amarelo ao pino 10 e o verde ao pino 9.
2. Cada LED deve ter um resistor de 150Ω ligado ao seu terminal negativo (cátodo), indo para o GND.
3. Use um barramento de terra comum na protoboard.

**(Inserir diagrama do circuito aqui)**

**Código Arduino:**

```cpp
// Projeto Semáforo

int ledDelay = 3500; // Tempo de espera entre as alterações

int redPin = 11;
int yellowPin = 10;
int greenPin = 9;

void setup() {
  pinMode(redPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
}

void loop() {
  digitalWrite(redPin, HIGH);  // Acende a luz vermelha
  delay(ledDelay);             // Espera 3.5 segundos

  digitalWrite(yellowPin, HIGH); // Vermelha + Amarela (transição)
  digitalWrite(redPin, LOW);     // Apaga vermelha
  delay(1500);                   // Espera 1.5 segundos

  digitalWrite(greenPin, HIGH);  // Verde acesa
  digitalWrite(yellowPin, LOW);  // Apaga amarela
  delay(ledDelay);               // Espera 3.5 segundos

  digitalWrite(yellowPin, HIGH); // Amarela acesa
  digitalWrite(greenPin, LOW);   // Apaga verde
  delay(1500);                   // Espera 1.5 segundos

  digitalWrite(yellowPin, LOW);  // Apaga amarela
  // O loop recomeça: vermelho → vermelho+amarelo → verde → amarelo
}
```

**O que aprendemos:**

* Como simular um semáforo real com LEDs.
* Como programar uma sequência com `digitalWrite()` e `delay()`.
* Como nomear pinos e usar variáveis para deixar o código mais organizado.

**Desafio:**

* Modifique o código para adaptar a sinalização ao padrão brasileiro (verde → amarelo → vermelho, sem vermelho+amarelo).

---
