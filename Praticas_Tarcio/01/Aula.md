# Materiais de Aula - Práticas de Robótica Educacional

---

## Prática 1: Piscar LED (Ref: Livro - Proj. 1, Cap. 2)

### 1. Roteiro de Aula (Professor)

*   **Título da Aula:** Introdução ao Arduino: Fazendo um LED Piscar
*   **Duração Estimada:** 50-60 minutos
*   **Objetivos de Aprendizagem:**
    *   Identificar os componentes básicos: Arduino Uno, LED, resistor, protoboard, jumpers.
    *   Montar um circuito simples em uma protoboard seguindo um diagrama.
    *   Compreender a estrutura básica de um código Arduino (`setup()` e `loop()`).
    *   Utilizar comandos básicos: `pinMode()`, `digitalWrite()`, `delay()`.
    *   Fazer o upload de um código para o Arduino (ou simular no Tinkercad).
    *   Entender a função do resistor para proteger o LED.
*   **Materiais:**
    *   Computador com Arduino IDE instalado OU acesso ao Tinkercad.
    *   Kit Arduino: Placa Arduino Uno, cabo USB, protoboard, 1 LED (qualquer cor), 1 resistor (220Ω ou 330Ω), fios jumper.
    *   Projetor.
*   **Procedimento:**
    1.  **Introdução (5 min):** Apresentar Arduino, placa Uno, objetivo da aula.
    2.  **Componentes e Protoboard (10 min):** Apresentar LED (polaridade), Resistor (função), Protoboard (conexões), Jumpers.
    3.  **Montagem do Circuito (10 min):** Exibir diagrama, demonstrar montagem (física ou Tinkercad), auxiliar alunos.
    4.  **Introdução ao Código (15 min):** Abrir IDE/Tinkercad, explicar `setup()`/`loop()`, explicar código linha a linha (`int`, `pinMode`, `digitalWrite`, `delay`, comentários).
    5.  **Execução e Teste (5 min):** Mostrar verificação/upload/simulação, observar LED, resolver problemas.
    6.  **Discussão e Variações (5 min):** Alterar `delay()`, recapitular comandos.
*   **Avaliação:** Observação da montagem, funcionamento do código, perguntas sobre comandos.
*   **Desafios (Opcional/Tarefa):** Alterar padrão de piscada, adicionar segundo LED.

link: [Tinkercad - Simulação do Circuito](https://www.tinkercad.com/things/78oGplaYCtD-pratica-1-piscar-led-ref-livro-proj-1-cap-2)

### 2. Esboço dos Slides (Prática 1)

*   **Slide 1:** Título: Prática 1 - Olá, Arduino! Fazendo um LED Piscar
*   **Slide 2:** O que é o Arduino? (Imagem Uno, breve explicação, objetivo)
*   **Slide 3:** Componentes Essenciais (Imagens e descrições: LED, Resistor, Protoboard, Jumpers, USB)
*   **Slide 4:** Entendendo o LED (Imagem com polaridade, explicação, função do resistor)
*   **Slide 5:** Entendendo a Protoboard (Imagem com conexões internas destacadas)
*   **Slide 6:** Montando o Circuito (Diagrama claro, passos resumidos)
*   **Slide 7:** O Código Arduino - Estrutura Básica (`setup()` e `loop()`)
*   **Slide 8:** Código do LED Piscante - Parte 1 (`setup`) (Código e explicação: `int`, `pinMode`, `OUTPUT`)
*   **Slide 9:** Código do LED Piscante - Parte 2 (`loop`) (Código e explicação: `digitalWrite`, `HIGH`, `LOW`, `delay`)
*   **Slide 10:** Mãos à Obra! (Instruções, "Seu LED deve piscar!")
*   **Slide 11:** Experimentando (Sugestões para alterar `delay()`)
*   **Slide 12:** Resumo e Próximos Passos (Recapitulação)

### 3. Apostila do Aluno (Prática 1)

**(Cabeçalho: Prática 1 – Olá, Arduino! Fazendo um LED Piscar)**

**Introdução:**
Bem-vindo ao mundo do Arduino! Nesta primeira prática, vamos montar nosso primeiro circuito eletrônico e escrever um programa simples para fazer um LED (uma pequena luz) piscar.

**Componentes Necessários:**
*   1x Placa Arduino Uno
*   1x Cabo USB
*   1x Protoboard
*   1x LED (qualquer cor)
*   1x Resistor de 220Ω (Vermelho, Vermelho, Marrom) ou 330Ω (Laranja, Laranja, Marrom)
*   2x Fios Jumper

**Montando o Circuito:**
Siga o diagrama abaixo. Lembre-se da polaridade do LED (perna longa +, perna curta -).

**(Inserir aqui o diagrama do circuito)**

**Passos da Montagem:**
1.  Conecte `GND` do Arduino ao barramento (-) da protoboard.
2.  Conecte `Pino 10` do Arduino a uma linha central da protoboard.
3.  Encaixe o LED: Perna longa (+) na linha do Pino 10, perna curta (-) em outra linha.
4.  Encaixe o Resistor: Uma perna na linha da perna curta (-) do LED, outra perna no barramento (-).

**Escrevendo o Código:**
Abra o Arduino IDE ou o Tinkercad (Código > Texto) e digite:

```c++
// Projeto 1 - LED piscante

int ledPin = 10; // Variável para guardar o número do pino do LED

// A função setup() roda uma vez no início
void setup() {
  // Configura o pino do LED como uma SAÍDA
  pinMode(ledPin, OUTPUT);
}

// A função loop() roda repetidamente
void loop() {
  digitalWrite(ledPin, HIGH); // Liga o LED
  delay(1000);             // Espera 1000 milissegundos (1 segundo)
  digitalWrite(ledPin, LOW);  // Desliga o LED
  delay(1000);             // Espera 1000 milissegundos (1 segundo)
}
```
Entendendo o Código:
-------------------------------------
* int ledPin = 10;: Guarda o número do pino.
* pinMode(ledPin, OUTPUT);: Define o pino como saída. 
* digitalWrite(ledPin, HIGH);: Liga o LED.
* digitalWrite(ledPin, LOW);: Desliga o LED.
* delay(1000);: Pausa por 1000ms.
* setup(): Configuração inicial.
* loop(): Repete para sempre.

Executando:
-------------------------------------
* Faça o upload (IDE) ou clique em "Start Simulation" (Tinkercad). Seu LED deve piscar!

Desafio:
-------------------------------------
* Altere os números no delay() para mudar a velocidade da piscada.

-------------------------------------
(Espaço para Anotações)

