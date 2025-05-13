# Prática 2: Leitura de Sensor de Luz (LDR)
---
## 1. Roteiro de Aula 

*   **Título da Aula:** Interagindo com o Ambiente: Sensor de Luz e Som
*   **Duração Estimada:** 50-60 minutos
*   **Objetivos de Aprendizagem:**
    *   Identificar um LDR (fotorresistor) e um buzzer piezoelétrico.
    *   Montar um circuito com um sensor analógico (LDR) e um atuador sonoro (piezo).
    *   Compreender o conceito de entrada analógica e a função `analogRead()`.
    *   Entender o princípio básico de um divisor de tensão (aplicado ao LDR).
    *   Utilizar comandos para gerar som: `tone()` e `noTone()`.
    *   Usar o valor lido de um sensor para controlar o comportamento do programa (intervalo de `delay`).
    *   (Opcional) Utilizar o Monitor Serial para visualizar os valores do sensor.
*   **Materiais:**
    *   Computador com Arduino IDE instalado OU acesso ao Tinkercad.
    *   Kit Arduino: Placa Arduino Uno, cabo USB, protoboard, 1 LDR (Fotorresistor), 1 Resistor de 10kΩ (Marrom, Preto, Laranja), 1 Buzzer Piezoelétrico, fios jumper.
    *   (Opcional) Projetor.
*   **Procedimento:**
    1.  **Revisão e Introdução (5 min):**
        *   Relembrar rapidamente a Prática 1 (piscar LED, `digitalWrite`, `delay`).
        *   Introduzir o conceito de *sensores*: Dispositivos que permitem ao Arduino "sentir" o ambiente.
        *   Apresentar o LDR: Explicar que sua resistência muda com a luz (mais luz = menos resistência).
        *   Apresentar o Piezo Buzzer: Explicar que ele produz som quando recebe um sinal elétrico.
        *   Objetivo da aula: Ler a quantidade de luz e fazer um som variar com ela.
    2.  **Entrada Analógica e Divisor de Tensão (10 min):**
        *   Explicar a diferença entre pinos digitais (HIGH/LOW) e analógicos (leem uma faixa de voltagem).
        *   Introduzir `analogRead()`: Lê a voltagem em um pino analógico (A0-A5) e a converte para um número entre 0 (0V) e 1023 (5V).
        *   Explicar *simplesmente* o divisor de tensão com LDR e resistor fixo: "O Arduino lê a voltagem no ponto entre o LDR e o resistor. Como a resistência do LDR muda com a luz, a voltagem nesse ponto também muda, e é isso que o `analogRead()` mede."
    3.  **Montagem do Circuito (10 min):**
        *   Exibir o diagrama do circuito (Slide/Tinkercad).
        *   Demonstrar a montagem:
            *   Conectar 5V e GND aos barramentos da protoboard.
            *   Montar o divisor de tensão: 5V -> LDR -> Pino A0; Pino A0 -> Resistor 10kΩ -> GND.
            *   Conectar o Piezo: Pino 8 -> Terminal (+), Terminal (-) -> GND.
        *   Auxiliar os alunos.
    4.  **Introdução ao Código (15 min):**
        *   Abrir IDE/Tinkercad (modo Texto).
        *   Explicar o código linha por linha:
            *   Definição dos pinos (`piezoPin`, `ldrPin`).
            *   `ldrValue = analogRead(ldrPin);` (lê o sensor).
            *   `tone(piezoPin, 1000);` (inicia um tom de 1000Hz).
            *   `delay(25);` (toca o tom brevemente).
            *   `noTone(piezoPin);` (para o tom).
            *   `delay(ldrValue);` (pausa com duração baseada na leitura do LDR).
        *   *Opcional:* Introduzir `Serial.begin(9600)` no `setup()` e `Serial.println(ldrValue)` no `loop()` para ver os valores no Monitor Serial.
    5.  **Execução e Teste (5 min):**
        *   Fazer upload/simular.
        *   Demonstrar como cobrir/iluminar o LDR (ou usar o slider no Tinkercad) e ouvir a mudança na frequência dos bipes.
        *   *Opcional:* Abrir o Monitor Serial para ver os valores mudando.
    6.  **Discussão e Variações (5 min):**
        *   Perguntar: Por que o bip fica mais rápido com mais luz? (Porque `ldrValue` diminui, diminuindo o `delay`).
        *   Que outras coisas poderíamos controlar com o LDR? (Brilho de um LED, posição de um servo, etc.).
        *   Recapitular os comandos: `analogRead`, `tone`, `noTone`.
*   **Avaliação:**
    *   Observar a montagem correta do circuito.
    *   Verificar se o código funciona e se o som varia com a luz simulada/real.
    *   Perguntar sobre a função do `analogRead` e o que os valores representam.
*   **Desafios (Opcional/Tarefa):**
    *   Mudar a frequência do `tone()` baseada no `ldrValue` em vez do `delay`.
    *   Fazer um LED acender apenas quando estiver escuro (abaixo de um certo valor de `ldrValue`).

link: [Tinkercad - Simulação do Circuito](https://www.tinkercad.com/things/2J0xbfTzyl0-pratica-2-leitura-de-sensor-de-luz-ldr-?sharecode=lUS3KvnAskcK4zWpUPisW9eNPH1J-5J7aqNGDDODOm8)

---

## 2. Esboço dos Slides (Prática 4)

*   **Slide 1:** Título: Prática 4 - Sentindo o Ambiente: Sensor de Luz e Som
*   **Slide 2:** Revisão Rápida
    *   Lembram da Prática 1 (piscar LED)? Usamos `digitalWrite` e `delay`.
    *   Hoje: Vamos *ler* algo do ambiente (luz) e fazer o Arduino *reagir* com som!
*   **Slide 3:** Nossos Novos Amigos: Componentes
    *   **LDR (Fotorresistor):**
        *   Imagem do LDR.
        *   "Sensor de Luz": Sua resistência elétrica muda com a quantidade de luz que incide sobre ele.
        *   Mais luz = Menor resistência. Menos luz = Maior resistência.
    *   **Buzzer Piezoelétrico (Piezo):**
        *   Imagem do Piezo.
        *   "Faz Barulho!": Converte um sinal elétrico em som.
    *   **Resistor de 10kΩ:**
        *   Imagem do resistor.
        *   "Ajudante do LDR": Usaremos junto com o LDR para ler a luz.
*   **Slide 4:** Pinos Analógicos vs. Digitais
    *   **Pinos Digitais (como o pino 10 da Prática 1):**
        *   Entendem apenas dois estados: LIGADO (HIGH, 5V) ou DESLIGADO (LOW, 0V).
        *   Usamos `digitalWrite()` para controlar e `digitalRead()` para ler.
    *   **Pinos Analógicos (A0 a A5 no Arduino Uno):**
        *   Conseguem ler uma *faixa* de voltagens (entre 0V e 5V).
        *   O Arduino converte essa voltagem para um número entre 0 e 1023.
        *   Comando: `analogRead(pino_analogico);`
        *   Exemplo: Se o pino A0 está com 2.5V, `analogRead(A0)` retornaria algo perto de 512.
*   **Slide 5:** Como Lemos a Luz com o LDR? O Divisor de Tensão!
    *   Diagrama simples do divisor de tensão:
        *   `5V --- [ LDR ] --- (Ponto de Leitura A0) --- [ Resistor 10kΩ ] --- GND`
    *   Explicação:
        *   O Arduino mede a voltagem no "Ponto de Leitura A0".
        *   Quando há **muita luz**: Resistência do LDR é baixa. Mais voltagem "passa" pelo LDR e menos "sobra" no ponto A0. `analogRead(A0)` retorna um valor **baixo**.
        *   Quando há **pouca luz**: Resistência do LDR é alta. Menos voltagem "passa" pelo LDR e mais "sobra" no ponto A0. `analogRead(A0)` retorna um valor **alto**.
*   **Slide 6:** Montando o Circuito
    *   Diagrama claro do circuito completo (preferencialmente um screenshot do Tinkercad finalizado ou uma foto da montagem real).
    *   **Lembretes:**
        *   LDR não tem polaridade.
        *   Piezo: Fio vermelho ou terminal marcado com (+) vai para o pino do Arduino; fio preto ou terminal (-) vai para o GND.
*   **Slide 7:** O Código - Vamos Entender!
    ```c++
    // Projeto 14 – Sensor de luz

    int piezoPin = 8;    // Pino onde o buzzer está conectado
    int ldrPin = 0;      // Pino Analógico A0 para o LDR
    int ldrValue = 0;    // Variável para guardar a leitura do LDR

    void setup() {
      // Nada especial para configurar aqui!
    }

    void loop() {
      ldrValue = analogRead(ldrPin); // Lê o valor do LDR (0-1023)

      tone(piezoPin, 1000);       // Começa um tom de 1000Hz no pino 8
      delay(25);                 // Deixa o tom tocar por 25ms (bip curto)
      noTone(piezoPin);          // Para o tom

      delay(ldrValue);           // Espera um tempo baseado na luz
                                 // Muita luz -> ldrValue baixo -> espera curta (bipes rápidos)
                                 // Pouca luz -> ldrValue alto -> espera longa (bipes lentos)
    }
    ```
*   **Slide 8:** Comandos Chave
    *   `analogRead(pino_analogico)`: Lê o valor de um pino analógico (0-1023).
    *   `tone(pino, frequencia)`: Começa a gerar um som com uma `frequencia` específica no `pino` indicado.
    *   `noTone(pino)`: Para qualquer som que esteja tocando no `pino`.
    *   `delay(valor)`: Pausa o programa pelo `valor` em milissegundos.
*   **Slide 9:** Mãos à Obra!
    *   Monte o circuito com cuidado.
    *   Digite ou copie o código no Arduino IDE / Tinkercad.
    *   Faça o upload (IDE) ou clique em "Start Simulation" (Tinkercad).
    *   **Teste:** Cubra o LDR com a mão. O que acontece com os bipes?
    *   Ilumine o LDR (com a lanterna do celular). E agora?
    *   **No Tinkercad:** Clique no LDR durante a simulação e use o controle deslizante para mudar a luz.
*   **Slide 10:** Para que Serve o Monitor Serial? (Opcional, mas útil!)
    *   Se quisermos ver os números que o LDR está lendo:
    *   No `setup()`: Adicione `Serial.begin(9600);`
    *   No `loop()`: Adicione `Serial.println(ldrValue);` (antes do primeiro `delay`).
    *   Como abrir o Monitor Serial (ícone de lupa no IDE).
    *   "Agora você pode ver os valores mudando com a luz!"
*   **Slide 11:** Discussão
    *   Como a quantidade de luz afeta o valor lido em `ldrValue`?
    *   Como `ldrValue` afeta o intervalo entre os bipes?
    *   Onde mais poderíamos usar um sensor de luz? (Acender luzes automaticamente, alarmes, etc.)
*   **Slide 12:** Resumo e Próximos Passos
    *   Recapitulação dos comandos e conceitos: `analogRead`, `tone`, `noTone`, LDR, divisor de tensão.
    *   Parabéns por fazer o Arduino sentir e reagir ao ambiente!

---

## 3. Apostila do Aluno (Prática 4)

**(Cabeçalho: Prática 4 – Sentindo o Ambiente: Sensor de Luz e Som)**

**Introdução:**
Nesta prática, vamos fazer o Arduino interagir com o ambiente! Usaremos um sensor de luz (LDR) para medir a luminosidade e um buzzer piezo para criar um som. O interessante é que a velocidade dos bipes do buzzer vai mudar dependendo de quanta luz o sensor detecta. É como um pequeno "contador Geiger" para luz!

**Componentes Necessários:**
*   1x Placa Arduino Uno (ou similar)
*   1x Cabo USB
*   1x Protoboard (Matriz de Contato)
*   1x LDR (Fotorresistor)
*   1x Resistor de 10kΩ (Cores: Marrom, Preto, Laranja)
*   1x Buzzer Piezoelétrico (Piezo)
*   Pelo menos 5x Fios Jumper (macho-macho)

**Entendendo os Componentes:**
*   **LDR (Light Dependent Resistor - Resistor Dependente de Luz):** É um tipo especial de resistor que muda sua resistência elétrica dependendo da quantidade de luz que o atinge.
    *   Com **muita luz**, a resistência do LDR diminui.
    *   Com **pouca luz**, a resistência do LDR aumenta.
*   **Buzzer Piezoelétrico:** É um pequeno dispositivo que produz som quando uma corrente elétrica passa por ele de uma certa maneira.
*   **Resistor de 10kΩ:** Usaremos este resistor junto com o LDR para criar um "divisor de tensão". Isso nos permite ler a mudança de resistência do LDR como uma mudança de voltagem, que o Arduino pode entender.

**Montando o Circuito:**
Siga o diagrama abaixo com atenção. O LDR não tem uma "perna certa" para conectar (não tem polaridade). O Piezo geralmente tem um terminal marcado com `+` (positivo) ou um fio vermelho, que deve ser conectado ao pino do Arduino, e o outro terminal (negativo ou fio preto) ao GND.

**(Inserir aqui o diagrama claro do circuito, como o do Slide 6 da apresentação do professor)**

**Passos da Montagem:**
1.  Conecte o pino `5V` do Arduino a uma das linhas vermelhas (+) da protoboard (barramento de alimentação positivo).
2.  Conecte o pino `GND` do Arduino a uma das linhas azuis (-) da protoboard (barramento de alimentação negativo/terra).
3.  Encaixe o LDR na protoboard.
4.  Conecte um terminal do LDR ao barramento (+) (5V).
5.  Conecte o outro terminal do LDR ao pino analógico `A0` do Arduino.
6.  **Importante:** Na mesma linha da protoboard onde você conectou o pino A0 e o LDR, conecte uma perna do resistor de 10kΩ.
7.  Conecte a outra perna do resistor de 10kΩ ao barramento (-) (GND).
8.  Encaixe o Piezo na protoboard.
9.  Conecte o terminal positivo (+) do Piezo ao pino digital `8` do Arduino.
10. Conecte o terminal negativo (-) do Piezo ao barramento (-) (GND).

**Escrevendo o Código:**
1.  Conecte o Arduino ao computador com o cabo USB.
2.  Abra o Arduino IDE (ou crie um novo circuito no Tinkercad e vá para a aba Código > Texto).
3.  Digite (ou copie e cole) o seguinte código:

```c++
// Projeto 14 – Sensor de luz

// Define o pino digital onde o sonorizador piezo está conectado
int piezoPin = 8;
// Define o pino analógico onde o LDR (e o divisor de tensão) está conectado
int ldrPin = 0; // Pino Analógico A0
// Variável para armazenar o valor lido do LDR (0 a 1023)
int ldrValue = 0;

// A função setup() é executada uma vez no início.
void setup() {
  // Para este projeto, não precisamos de nenhuma configuração inicial aqui.
  // O comando tone() e analogRead() não exigem pinMode() para estes usos.
}

// A função loop() é executada repetidamente.
void loop() {
  // Lê o valor da voltagem no pino analógico 'ldrPin' (A0).
  // O valor será entre 0 (0V) e 1023 (5V).
  // Mais luz = menor resistência do LDR = menor voltagem em A0 = menor ldrValue.
  // Pouca luz = maior resistência do LDR = maior voltagem em A0 = maior ldrValue.
  ldrValue = analogRead(ldrPin);

  // Emite um tom de frequência fixa (1000 Hz) no 'piezoPin' (pino 8).
  tone(piezoPin, 1000);

  // Pequena pausa de 25 milissegundos para que o tom seja audível (bip curto).
  delay(25);

  // Interrompe o tom que está tocando no 'piezoPin'.
  noTone(piezoPin);

  // Pausa a execução pelo número de milissegundos lido do LDR ('ldrValue').
  // Se há muita luz, 'ldrValue' será baixo, e a pausa será curta (bipes rápidos).
  // Se há pouca luz, 'ldrValue' será alto, e a pausa será longa (bipes lentos).
  delay(ldrValue);

  // O loop recomeça, lendo o sensor e emitindo outro bip.
}
```

**Entendendo o Código:**
*   `int piezoPin = 8;`: Guarda o número do pino do buzzer.
*   `int ldrPin = 0;`: Guarda o número do pino analógico A0, onde o LDR está conectado.
*   `int ldrValue = 0;`: Uma "caixinha" para guardar o valor que o Arduino lê do LDR.
*   `void setup() { }`: A função `setup` está vazia porque os comandos que usamos (`analogRead` e `tone`) não precisam de configuração prévia com `pinMode` para este circuito específico.
*   `ldrValue = analogRead(ldrPin);`: O Arduino lê a voltagem no pino `ldrPin` (A0) e converte para um número entre 0 e 1023. Esse número é guardado em `ldrValue`.
*   `tone(piezoPin, 1000);`: Faz o buzzer no `piezoPin` (pino 8) começar a tocar um som com frequência de 1000 Hertz (Hz).
*   `delay(25);`: O programa espera por 25 milissegundos, então o som toca por esse tempinho.
*   `noTone(piezoPin);`: Para o som no `piezoPin`.
*   `delay(ldrValue);`: O programa espera por um tempo igual ao valor que foi lido do LDR. Se `ldrValue` for pequeno (muita luz), a espera é curta. Se `ldrValue` for grande (pouca luz), a espera é longa.

**Executando:**
*   **No IDE:** Clique no botão de Verificação (✓) e depois no botão de Upload (→).
*   **No Tinkercad:** Clique em "Start Simulation".
*   Você deverá ouvir bipes curtos.
*   **Teste:**
    1.  Cubra o LDR com sua mão. Os bipes devem ficar mais lentos (o intervalo entre eles aumenta).
    2.  Aponte uma luz (como a lanterna do seu celular) para o LDR. Os bipes devem ficar mais rápidos (o intervalo diminui).
    3.  **No Tinkercad:** Durante a simulação, clique no componente LDR. Um controle deslizante aparecerá. Mova-o para simular mais ou menos luz e observe o que acontece com o som.

**Desafio (Para Explorar Mais):**
1.  **Monitorando os Valores:** Adicione os seguintes comandos ao seu código para ver os valores que o LDR está lendo:
    *   No `setup()`: `Serial.begin(9600);`
    *   No `loop()`, logo após `ldrValue = analogRead(ldrPin);`: `Serial.println(ldrValue);`
    *   Faça o upload e abra o "Monitor Serial" (ícone de lupa no canto superior direito do IDE). Veja como os números mudam quando você cobre ou ilumina o LDR.
2.  **Mudando o Tom:** Em vez de mudar o *intervalo* entre os bipes, tente mudar a *frequência* (o tom) do som com base na leitura do LDR. Você pode precisar usar a função `map()` para converter o `ldrValue` (0-1023) para uma faixa de frequências que soem bem (por exemplo, de 200Hz a 2000Hz).
    *   Exemplo de como usar `map()`: `int frequenciaDoSom = map(ldrValue, 0, 1023, 200, 2000);`
    *   Depois, use `frequenciaDoSom` no comando `tone()`.

**(Espaço para Anotações do Aluno)**
```