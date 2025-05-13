# Materiais de Aula - Práticas de Robótica Educacional

---

## Prática 2: Exibir Texto no Display LCD 16x2

### 1. Roteiro de Aula 

*   **Título da Aula:** Introdução ao Display LCD 16x2 com Arduino
*   **Duração Estimada:** 60-75 minutos
*   **Objetivos de Aprendizagem:**
    *   Identificar os componentes: Arduino Uno, Display LCD 16x2, Potenciômetro, Resistor, Protoboard, Jumpers.
    *   Compreender a função dos principais pinos do LCD (VCC, GND, VO, RS, E, D4-D7, A, K).
    *   Montar o circuito do LCD na protoboard seguindo um diagrama.
    *   Entender a necessidade e o uso do potenciômetro para ajustar o contraste.
    *   Entender a função do resistor para o backlight do LCD.
    *   Incluir e utilizar a biblioteca `LiquidCrystal.h`.
    *   Compreender a estrutura básica do código para LCD: inicialização, posicionamento e escrita.
    *   Utilizar comandos essenciais: `LiquidCrystal()`, `lcd.begin()`, `lcd.setCursor()`, `lcd.print()`, `lcd.clear()`.
    *   Fazer o upload do código para o Arduino (ou simular no Tinkercad) e visualizar o texto.
    *   Realizar o ajuste de contraste no display físico ou simulado.
*   **Materiais:**
    *   Computador com Arduino IDE instalado OU acesso ao Tinkercad.
    *   Kit Arduino: Placa Arduino Uno, cabo USB, protoboard.
    *   **Display LCD 16x2** (com pinos soldados, se físico).
    *   **Potenciômetro de 10kΩ**.
    *   1 Resistor (220Ω ou 330Ω) para o backlight.
    *   Fios jumper (Macho-Macho, aprox. 15-16 fios).
    *   (Opcional) Projetor.
*   **Procedimento:**
    1.  **Introdução (5 min):** Apresentar o display LCD, suas aplicações (mostrar texto/dados), objetivo da aula.
    2.  **Componentes e Pinos (15 min):** Explicar o LCD 16x2, função dos pinos essenciais (alimentação, contraste, controle, dados, backlight). Apresentar o potenciômetro (ajuste de contraste) e o resistor (proteção do backlight). Revisar protoboard.
    3.  **Montagem do Circuito (15-20 min):** Exibir diagrama de conexão claro. Demonstrar a montagem passo a passo (física ou Tinkercad), enfatizando a atenção aos pinos corretos. Auxiliar os alunos (esta etapa exige mais cuidado).
    4.  **Introdução ao Código (15 min):**
        *   Abrir IDE/Tinkercad.
        *   Explicar a necessidade da biblioteca: `#include <LiquidCrystal.h>`.
        *   Explicar a inicialização do objeto LCD: `LiquidCrystal lcd(rs, en, d4, d5, d6, d7);`, relacionando com os pinos do Arduino usados.
        *   No `setup()`: `lcd.begin(16, 2);` para definir o tamanho.
        *   Comandos básicos: `lcd.print("Texto");`, `lcd.setCursor(col, lin);`, `lcd.clear();`.
        *   Mostrar o código de exemplo completo.
    5.  **Execução e Teste (10 min):** Mostrar verificação/upload/simulação. **Demonstrar o ajuste do contraste usando o potenciômetro** até o texto ficar nítido. Observar o backlight. Solucionar problemas comuns (conexões erradas, contraste mal ajustado).
    6.  **Discussão e Variações (5 min):** Como limpar a tela (`lcd.clear()`), como escrever em locais diferentes (`setCursor`), como exibir números ou variáveis.
*   **Avaliação:** Observação da montagem correta, funcionamento do código, capacidade de ajustar o contraste, perguntas sobre os comandos e a função dos componentes.
*   **Desafios (Opcional/Tarefa):**
    *   Fazer o texto rolar na tela.
    *   Criar um contador que atualiza no LCD.
    *   Exibir dados de um sensor (se disponível/próxima aula).
*   **Link (Exemplo - Crie o seu):** [Tinkercad - Simulação LCD (Modelo)](https://www.tinkercad.com/things/axQyQwNe3Oo-pratica-3-exibindo-texto-no-display-lcd-?sharecode=x3RH2m_dnhd13T1wHZqqmJo9ugdjAWkzOF6MY5zwe5Y) 

---

### 2. Esboço dos Slides (Prática 2)

*   **Slide 1:** Título: Prática 2 - Exibindo Mensagens no Display LCD
*   **Slide 2:** O que é um Display LCD? (Imagem LCD 16x2, aplicações, objetivo)
*   **Slide 3:** Componentes da Prática (Imagens: LCD, Potenciômetro, Resistor, Arduino, Protoboard, Jumpers)
*   **Slide 4:** Entendendo o Display LCD 16x2 (Imagem com pinout, explicar pinos principais: VSS, VDD, VO, RS, R/W, E, D4-D7, A, K)
*   **Slide 5:** Ajustando o Contraste (Imagem Potenciômetro, conexão com VO, 5V, GND, função)
*   **Slide 6:** O Backlight (Luz de Fundo) (Pinos A e K, função do resistor)
*   **Slide 7:** Entendendo a Protoboard (Revisão rápida, imagem com conexões)
*   **Slide 8:** Montando o Circuito (Diagrama claro, passos resumidos, *atenção aos detalhes*)
*   **Slide 9:** O Código Arduino - Biblioteca LCD (Explicar `#include <LiquidCrystal.h>`)
*   **Slide 10:** Código LCD - Inicialização (Explicar `LiquidCrystal lcd(...)` e `lcd.begin(...)` no `setup()`)
*   **Slide 11:** Código LCD - Escrevendo na Tela (Explicar `lcd.setCursor(...)` e `lcd.print(...)`)
*   **Slide 12:** Código Completo (Mostrar o código de exemplo)
*   **Slide 13:** Mãos à Obra! (Instruções, "Seu LCD deve mostrar texto!", **"Ajuste o contraste!"**)
*   **Slide 14:** Experimentando (Sugestões: mudar texto, posição, usar `clear()`, contador)
*   **Slide 15:** Resumo e Próximos Passos (Recapitulação, possíveis projetos futuros)

---

### 3. Apostila do Aluno (Prática 2)

**(Cabeçalho: Prática 2 – Exibindo Mensagens no Display LCD)**

**Introdução:**
Nesta prática, vamos aprender a usar um Display de Cristal Líquido (LCD) 16x2 com o Arduino. Com ele, podemos mostrar textos, números e informações dos nossos projetos!

**Componentes Necessários:**
*   1x Placa Arduino Uno
*   1x Cabo USB
*   1x Protoboard
*   1x Display LCD 16x2
*   1x Potenciômetro 10kΩ
*   1x Resistor de 220Ω (Vermelho, Vermelho, Marrom) ou 330Ω (Laranja, Laranja, Marrom)
*   ~16x Fios Jumper (Macho-Macho)

**Montando o Circuito:**
A montagem do LCD exige atenção! Siga o diagrama e as conexões abaixo com cuidado.

**(Inserir aqui o diagrama claro do circuito LCD)**

**Conexões Principais:**
*(Confira os nomes dos pinos no seu LCD, podem variar um pouco)*
1.  **LCD VSS (Pino 1)** -> **GND** do Arduino
2.  **LCD VDD (Pino 2)** -> **5V** do Arduino
3.  **LCD VO / V0 (Pino 3)** -> **Pino Central** do Potenciômetro
4.  **Potenciômetro (Terminal 1)** -> **GND** do Arduino
5.  **Potenciômetro (Terminal 2)** -> **5V** do Arduino
6.  **LCD RS (Pino 4)** -> **Pino Digital 12** do Arduino
7.  **LCD R/W (Pino 5)** -> **GND** do Arduino
8.  **LCD E (Pino 6)** -> **Pino Digital 11** do Arduino
9.  **LCD D4 (Pino 11)** -> **Pino Digital 5** do Arduino
10. **LCD D5 (Pino 12)** -> **Pino Digital 4** do Arduino
11. **LCD D6 (Pino 13)** -> **Pino Digital 3** do Arduino
12. **LCD D7 (Pino 14)** -> **Pino Digital 2** do Arduino
13. **LCD A / LED+ (Pino 15)** -> Uma perna do **Resistor**
14. **Outra perna do Resistor** -> **5V** do Arduino
15. **LCD K / LED- (Pino 16)** -> **GND** do Arduino

**Escrevendo o Código:**
Abra o Arduino IDE ou o Tinkercad (Código > Texto) e digite:

```c++
// Prática 2 - Exibindo Texto no LCD

// Inclui a biblioteca para controlar o LCD
#include <LiquidCrystal.h>

// Define quais pinos do Arduino estão conectados ao LCD
// LiquidCrystal lcd(RS, E, D4, D5, D6, D7);
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

// A função setup() roda uma vez no início
void setup() {
  // Inicializa o LCD com 16 colunas e 2 linhas
  lcd.begin(16, 2);

  // Limpa qualquer texto anterior (boa prática)
  lcd.clear();

  // Posiciona o cursor na Coluna 0, Linha 0 (canto superior esquerdo)
  lcd.setCursor(0, 0);
  // Escreve na primeira linha
  lcd.print("Ola, Arduino!");

  // Posiciona o cursor na Coluna 0, Linha 1 (segunda linha)
  lcd.setCursor(0, 1);
  // Escreve na segunda linha
  lcd.print("LCD 16x2 OK!");
}

// A função loop() roda repetidamente (pode ficar vazia por enquanto)
void loop() {
  // O texto já foi escrito no setup() e permanecerá na tela.
  // Poderíamos adicionar código aqui para atualizar o texto depois.
}
```

**Entendendo o Código:**
*   `#include <LiquidCrystal.h>`: Traz as funções para usar o LCD.
*   `LiquidCrystal lcd(12, 11, 5, 4, 3, 2);`: Cria o "objeto" LCD, dizendo quais pinos do Arduino estão conectados (RS, E, D4-D7).
*   `lcd.begin(16, 2);`: Informa que nosso LCD tem 16 colunas e 2 linhas.
*   `lcd.clear();`: Limpa tudo que estiver escrito no LCD.
*   `lcd.setCursor(coluna, linha);`: Move o cursor para onde o próximo texto será escrito (começa em 0,0).
*   `lcd.print("Seu texto");`: Escreve o texto no LCD na posição atual do cursor.

**Executando:**
*   Faça o upload (IDE) ou clique em "Start Simulation" (Tinkercad).
*   **IMPORTANTE:** Se você não vir texto ou vir apenas blocos pretos, **gire o botão do potenciômetro lentamente** para ajustar o contraste até o texto ficar nítido! Verifique também se a luz de fundo (backlight) acendeu.

**Desafio:**
*   Mude as mensagens escritas no LCD.
*   Faça o Arduino escrever uma mensagem na primeira linha e um número (contador) que aumenta na segunda linha dentro do `loop()`. (Dica: use `lcd.print(variavel);` e `delay();`).

---
**(Espaço para Anotações)**

---