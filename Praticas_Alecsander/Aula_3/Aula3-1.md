
---

# Materiais de Aula - Práticas de Robótica Educacional

---

## Prática 3: Efeito de Iluminação Sequencial com LEDs

### 1. Roteiro de Aula (Professor)

* **Título da Aula:** Efeito de Iluminação Sequencial com LEDs
* **Duração Estimada:** 50-60 minutos
* **Objetivos de Aprendizagem:**

  * Compreender o conceito de arrays no Arduino.
  * Utilizar uma sequência de LEDs para criar um efeito de iluminação sequencial.
  * Controlar LEDs de forma programada usando o Arduino.
  * Compreender como alternar a direção do efeito (avanço e retrocesso).
* **Materiais:**

  * Computador com Arduino IDE instalado.
  * Kit Arduino: Arduino Uno, cabo USB, protoboard, 10 LEDs (5mm), 10 resistores de 220Ω, fios jumper.
* **Procedimento:**

  1. **Introdução:** Apresentar o conceito de arrays no Arduino e sua utilidade em projetos com múltiplos componentes.
  2. **Componentes e Circuito:** Mostrar os LEDs, resistores e explicar como organizar a sequência na protoboard.
  3. **Montagem:** Auxiliar os alunos na montagem dos 10 LEDs conectados aos pinos digitais 4 a 13.
  4. **Código e Explicação:** Apresentar o código do efeito sequencial (estilo KITT) e explicar o funcionamento das variáveis e estruturas.
  5. **Teste e Exploração:** Fazer upload do código, observar o padrão de acendimento e alterar variáveis como `ledDelay` e `direction`.
* **Avaliação:** Verificar se o circuito foi montado corretamente, se os LEDs estão funcionando em sequência e se os alunos compreendem o uso de arrays.
* **Desafios (Opcional/Tarefa):**

  * Modificar o código para acender dois LEDs simultaneamente.
  * Alterar a velocidade do efeito variando o `ledDelay`.

---

### 2. Esboço dos Slides (Prática 3)

* **Slide 1:** Título: Prática 3 - Efeito de Iluminação Sequencial com LEDs
* **Slide 2:** O que é um array? (Conceito e exemplo simples no Arduino)
* **Slide 3:** Componentes do Projeto (Lista com imagens dos LEDs, resistores, protoboard, Arduino)
* **Slide 4:** Montagem do Circuito (Esquema de ligação dos LEDs nos pinos 4 a 13)
* **Slide 5:** Estrutura do Código (Apresentar o array, variáveis, laços e função `millis()`)
* **Slide 6:** Efeito KITT (Explicação visual da lógica de ida e volta)
* **Slide 7:** Vamos Programar! (Passo a passo para digitar ou carregar o código)
* **Slide 8:** Explorando Mudanças (Alterar `ledDelay`, acender dois LEDs, inverter direção)
* **Slide 9:** Resultados Esperados (Demonstração do efeito e possíveis variações)
* **Slide 10:** Conclusão e Próximos Desafios

---

### 3. Apostila do Aluno (Prática 3)

**Prática 3 – Efeito de Iluminação Sequencial com LEDs**

**Introdução:**
Nesta prática, você aprenderá a controlar 10 LEDs de forma sequencial utilizando **arrays no Arduino**, criando um efeito visual semelhante ao do carro **KITT**, da série *A Super Máquina*.

**Componentes Necessários:**

* 1x Placa Arduino Uno
* 1x Cabo USB
* 1x Protoboard
* 10x LEDs (5mm)
* 10x Resistores de 220Ω
* Fios jumper

**Montando o Circuito:**
Monte o circuito conectando os LEDs aos pinos digitais 4 a 13, cada um com um resistor em série.

**(Inserir diagrama do circuito aqui)**

**Código Arduino:**

```cpp
// Projeto – Efeito de Iluminação Sequencial com LEDs

byte ledPin[] = {4, 5, 6, 7, 8, 9, 10, 11, 12, 13};  // Pinos dos LEDs
int ledDelay = 80;                                   // Tempo entre os LEDs
int direction = 1;                                   // Direção da sequência
int currentLED = 0;
unsigned long changeTime;

void setup() {
  for (int x = 0; x < 10; x++) {
    pinMode(ledPin[x], OUTPUT);
  }
  changeTime = millis();
}

void loop() {
  if ((millis() - changeTime) > ledDelay) {
    changeLED();
    changeTime = millis();
  }
}

void changeLED() {
  for (int x = 0; x < 10; x++) {
    digitalWrite(ledPin[x], LOW); // Apaga todos os LEDs
  }

  digitalWrite(ledPin[currentLED], HIGH); // Acende o LED atual

  currentLED += direction;

  if (currentLED == 9) {
    direction = -1;
  }
  if (currentLED == 0) {
    direction = 1;
  }
}
```

**Entendendo o Código:**

* `ledPin[]`: array com os pinos dos LEDs.
* `ledDelay`: define o tempo entre cada troca de LED.
* `direction`: controla o sentido (avança ou volta).
* `currentLED`: identifica qual LED está aceso.
* `millis()`: retorna o tempo desde o início da execução do programa.
* `changeLED()`: função que troca o LED aceso conforme a direção.

**Executando:**

* Conecte o Arduino ao computador via cabo USB.
* Abra a Arduino IDE, cole o código e faça o upload.
* Observe o efeito de ida e volta dos LEDs.
* Em caso de falha, revise as conexões e os pinos utilizados.

**Desafio:**

* Altere o valor de `ledDelay` para ajustar a velocidade.
* Modifique o código para acender **dois LEDs ao mesmo tempo**.

---

