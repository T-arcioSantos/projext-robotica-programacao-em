## Prática 4: Controlando um Servo Motor com Potenciômetro

### 1. Roteiro de Aula

*   **Título da Aula:** Controle de Posição: Servo Motor e Potenciômetro com Arduino
*   **Duração Estimada:** 60 minutos
*   **Objetivos de Aprendizagem:**
    *   Identificar os componentes: Arduino Uno, Servo Motor, Potenciômetro, Protoboard, Jumpers.
    *   Compreender o funcionamento de um servo motor (controle de ângulo via sinal PWM).
    *   Entender a função de um potenciômetro como um divisor de tensão para entrada analógica.
    *   Montar o circuito conectando o servo e o potenciômetro ao Arduino.
    *   Incluir e utilizar a biblioteca `Servo.h`.
    *   Compreender a estrutura do código: criar um objeto Servo, anexá-lo a um pino.
    *   Utilizar comandos essenciais: `Servo()`, `myservo.attach()`, `analogRead()`, `map()`, `myservo.write()`.
    *   Entender como mapear a leitura analógica do potenciômetro (0-1023) para o ângulo do servo (0-180).
    *   Fazer o upload do código para o Arduino (ou simular no Tinkercad) e testar o controle em tempo real.
*   **Materiais:**
    *   Computador com Arduino IDE instalado OU acesso ao Tinkercad.
    *   Kit Arduino: Placa Arduino Uno, cabo USB, protoboard.
    *   **Servo Motor** (ex: SG90).
    *   **Potenciômetro de 10kΩ**.
    *   Fios jumper (Macho-Macho, aprox. 6-7 fios).
    *   (Opcional) Projetor.
*   **Procedimento:**
    1.  **Introdução (5 min):** Apresentar o servo motor, suas aplicações (robótica, aeromodelismo, automação) e o objetivo da aula: controlar sua posição com um botão giratório.
    2.  **Componentes e Conceitos (15 min):** Explicar o servo motor e seus 3 fios (VCC, GND, Sinal). Explicar o que é um sinal PWM. Apresentar o potenciômetro como um sensor de posição angular que fornece uma voltagem variável, lida como um valor analógico pelo Arduino.
    3.  **Montagem do Circuito (15 min):** Exibir o diagrama de conexão. Demonstrar a montagem passo a passo (física ou Tinkercad), que é mais simples e rápida que a do LCD.
    4.  **Introdução ao Código (15 min):**
        *   Abrir IDE/Tinkercad.
        *   Explicar a biblioteca: `#include <Servo.h>`.
        *   Explicar a criação do objeto: `Servo myservo;`.
        *   No `setup()`: `myservo.attach(9);` para associar o objeto ao pino físico.
        *   No `loop()`: Explicar a sequência lógica:
            1.  Ler o potenciômetro: `analogRead()`.
            2.  Converter a escala: `map()`.
            3.  Comandar o servo: `myservo.write()`.
        *   Mostrar o código de exemplo completo.
    5.  **Execução e Teste (10 min):** Mostrar verificação/upload/simulação. Girar o potenciômetro e observar o movimento correspondente do servo. Solucionar problemas comuns (fios invertidos no servo ou potenciômetro).
    6.  **Discussão e Variações (5 min):** O que acontece se mudarmos os valores no `map()`? Como poderíamos limitar o movimento do servo?
*   **Avaliação:** Observação da montagem, funcionamento do código, e a capacidade do aluno de explicar como o valor lido do potenciômetro se traduz no ângulo do servo.
*   **Desafios (Opcional/Tarefa):**
    *   Alterar o código para que o servo se mova apenas entre 45 e 135 graus.
    *   Usar o Monitor Serial para exibir o valor lido do potenciômetro e o ângulo enviado ao servo.
    *   Adicionar um botão que, quando pressionado, move o servo para a posição de 90 graus, ignorando o potenciômetro.
*   **Link (Exemplo - Crie o seu):** [Tinkercad - Simulação Servo e Potenciômetro (Modelo)](https://www.tinkercad.com/things/bBCOy8DqQXf-pratica-04-manipulando-um-servomotor?sharecode=Y_ZkkqvMRO0MnveGnvmDMTemQ6QBpoEHjatmbkddnLY)

---

### 2. Esboço dos Slides (Prática 4)

*   **Slide 1:** Título: Prática 4 - Controlando um Servo Motor com Potenciômetro
*   **Slide 2:** O que é um Servo Motor? (Imagem de um servo, aplicações como braços robóticos, objetivo da aula)
*   **Slide 3:** Componentes da Prática (Imagens: Servo Motor, Potenciômetro, Arduino, Protoboard, Jumpers)
*   **Slide 4:** Entendendo o Servo Motor (Imagem com os 3 fios coloridos, explicar VCC, GND e Sinal/PWM)
*   **Slide 5:** Entendendo o Potenciômetro (Imagem com os 3 pinos, explicar VCC, GND e o pino central como saída analógica)
*   **Slide 6:** Montando o Circuito (Diagrama claro e simples, tabela de conexões)
*   **Slide 7:** O Código Arduino - Biblioteca Servo (Explicar `#include <Servo.h>`)
*   **Slide 8:** Código - Configuração Inicial (Explicar `Servo myservo;` e `myservo.attach(9);` no `setup()`)
*   **Slide 9:** Código - A Lógica de Controle no `loop()` (Explicar o fluxo: `analogRead` -> `map` -> `write`)
*   **Slide 10:** A Função `map()` (Slide dedicado para explicar como ela converte uma faixa de números em outra)
*   **Slide 11:** Código Completo (Mostrar o código de exemplo)
*   **Slide 12:** Mãos à Obra! (Instruções, "Gire o potenciômetro e controle o servo!")
*   **Slide 13:** Experimentando (Sugestões: limitar o ângulo, usar o Monitor Serial)
*   **Slide 14:** Resumo e Próximos Passos (Recapitulação, ideias de projetos futuros)

---

### 3. Apostila do Aluno (Prática 4)

**(Cabeçalho: Prática 4 – Controlando um Servo Motor com Potenciômetro)**

**Introdução:**
Nesta prática, vamos aprender a controlar a posição exata de um servo motor. Usaremos um potenciômetro (um botão giratório) como um controle manual para dizer ao servo para qual ângulo ele deve se mover. É um dos blocos de construção fundamentais para a robótica!

**Componentes Necessários:**
*   1x Placa Arduino Uno
*   1x Cabo USB
*   1x Protoboard
*   1x Servo Motor (ex: SG90)
*   1x Potenciômetro 10kΩ
*   ~7x Fios Jumper (Macho-Macho)

**Montando o Circuito:**
Siga a tabela de conexões abaixo. Preste atenção especial às cores dos fios do servo motor.

**(Inserir aqui o diagrama do circuito)**

**Tabela de Conexões:**

**Conexões do Servo Motor**
| Servo | Arduino |
| :--- | :--- |
| Vermelho (VCC) | 5V |
| Marrom ou Preto (GND) | GND |
| Amarelo ou Branco (Sinal) | Pino Digital 9 |

**Conexões do Potenciômetro**
| Pino do Potenciômetro | Arduino |
| :--- | :--- |
| Terminador 1 (VCC) | 5V |
| Limpador (centro) | A0 |
| Terminador 2 (GND) | GND |

**Escrevendo o Código:**
Abra o Arduino IDE ou o Tinkercad (Código > Texto) e digite o código abaixo:

```c++
// Prática 4 - Controlando um Servo Motor com Potenciômetro

// Inclui a biblioteca para controlar o servo
#include <Servo.h>

// Cria um objeto 'servo' para que possamos usar os comandos da biblioteca
Servo myservo;

// Define em qual pino analógico o potenciômetro está conectado
int potPin = A0;

// Variável para armazenar o valor lido do potenciômetro
int potValue = 0;

// A função setup() roda uma vez no início
void setup() {
  // Anexa o nosso objeto 'servo' ao pino 9 do Arduino.
  // A partir de agora, o pino 9 enviará sinais para o servo.
  myservo.attach(9);
}

// A função loop() roda repetidamente
void loop() {
  // 1. Lê o valor do pino analógico A0. O valor varia de 0 a 1023.
  potValue = analogRead(potPin);
  
  // 2. Converte (mapeia) o valor lido (0-1023) para um ângulo (0-180).
  // A função map() faz essa "tradução" para nós.
  int angle = map(potValue, 0, 1023, 0, 180);
  
  // 3. Envia o ângulo calculado para o servo motor.
  myservo.write(angle);
  
  // 4. Pequeno atraso para dar tempo ao servo de se mover e estabilizar.
  delay(15);
}
```

**Entendendo o Código:**
*   `#include <Servo.h>`: Traz as funções prontas para controlar o servo motor.
*   `Servo myservo;`: Cria uma "variável especial" (objeto) do tipo Servo, que chamamos de `myservo`.
*   `myservo.attach(9);`: "Conecta" nosso objeto `myservo` ao pino físico 9 do Arduino.
*   `analogRead(potPin);`: Lê a voltagem no pino A0 e a converte em um número entre 0 (para 0V) e 1023 (para 5V).
*   `map(valor, de_min, de_max, para_min, para_max);`: Uma função muito útil! Ela pega um `valor` que está em uma faixa (de 0 a 1023) e o converte para o número correspondente em outra faixa (de 0 a 180).
*   `myservo.write(angle);`: Envia o comando final para o servo, dizendo a ele para se mover para o ângulo (`angle`) especificado.

**Executando:**
*   Faça o upload (IDE) ou clique em "Start Simulation" (Tinkercad).
*   Gire o botão do potenciômetro. Você deverá ver o braço do servo motor se movendo de acordo, imitando a posição do seu botão!

**Desafio:**
*   O servo motor consegue se mover 180 graus, mas e se você quisesse que ele se movesse apenas em um arco menor, por exemplo, entre 30 e 150 graus? Tente modificar os dois últimos números na função `map()` para limitar o movimento.
    *   *Dica: `map(potValue, 0, 1023, 30, 150);`*

**(Espaço para Anotações)**