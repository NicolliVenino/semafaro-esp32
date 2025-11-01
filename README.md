# Atividade Ponderada Semáforo

Código:

```
// Adiciona biblioteca para protocolo I2C 
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Inicializa o display 
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Define os pinos dos LEDs e do botão
#define pin_red 16
#define pin_yellow 17
#define pin_green 18
#define pin_botao 15

// Define o tempo passado
unsigned long _previousMillis = 0;

void setup() {
  // Configura os pinos como saída
  pinMode(pin_red, OUTPUT);
  pinMode(pin_yellow, OUTPUT);
  pinMode(pin_green, OUTPUT);

  // Inicia o display
  lcd.init();
  lcd.backlight();

  // Começa com o LED vermelho aceso
  digitalWrite(pin_red, HIGH);
  digitalWrite(pin_yellow, LOW);
  digitalWrite(pin_green, LOW);
  lcd.clear();
  lcd.setCursor(5, 0);
  lcd.print("PARE!");
}

void loop() {
  unsigned long currentMillis = millis();
  if (digitalRead(pin_botao) == LOW){
      digitalWrite(pin_red, HIGH);
      digitalWrite(pin_yellow, HIGH);
      digitalWrite(pin_green, HIGH);
      lcd.clear();
  } else{
      // acender o verde
      if (currentMillis - _previousMillis == 6000 && digitalRead(pin_red) == HIGH) {
        digitalWrite(pin_red, LOW);
        digitalWrite(pin_yellow, LOW);
        digitalWrite(pin_green, HIGH);
        lcd.clear();
        lcd.setCursor(2, 0);
        lcd.print("Sinal aberto!");

        _previousMillis = currentMillis;
      }

      // acender o amarelo
      if ((currentMillis - _previousMillis == 4000) && digitalRead(pin_green) == HIGH) {
        digitalWrite(pin_red, LOW);
        digitalWrite(pin_yellow, HIGH);
        digitalWrite(pin_green, LOW);
        lcd.clear();
        lcd.setCursor(3, 0);
        lcd.print("Cuidado...");

        _previousMillis = currentMillis;
      }

      // acender o vermelho
      if ((currentMillis - _previousMillis == 2000) && digitalRead(pin_yellow) == HIGH) {
        digitalWrite(pin_red, HIGH);
        digitalWrite(pin_yellow, LOW);
        digitalWrite(pin_green, LOW);
        lcd.clear();
        lcd.setCursor(5, 0);
        lcd.print("PARE!");

        _previousMillis = currentMillis;
      }
    }
}

```

Imagens:

<div align = "center">
  <img src = "../assets/img1.jpg">
 </div>

<div align = "center">
  <img src = "../assets/img2.jpg">
 </div>

Obs: haja vista que o Arduino IDE está apresentando problemas na máquina de todos os usuários nesta semana, não foi possível, até o dia 31/10/2025, anexar o vídeo do funcionamento do semáforo. No entanto, o professor conseguiu analisá-lo em sala funcionando. Caso o professor precise de mais explicações sobre o circuito ou sobre o código, estou capacitada para respondê-lo.

### Tabela de Avaliação entre Pares

#### Avaliador: Lívia Cavalcante

|Critério|	Contempla (Pontos)|	Contempla Parcialmente (Pontos)	|Não Contempla (Pontos)	|Observações do Avaliador|
|-|-|-|-|-|
|Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores	|Até 3	|Até 1,5	| 3 | A convenção de cores está corretas e os componentes estão organizados. |	
|Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo	|Até 3	|Até 1,5	| 3 | O tempo que cada led fica acesso está correto |	
|Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) |	Até 3|	Até 1,5 |	3 | O código está muito bem estruturado e comentado. A lógica utilizada foi muito estratégica. |	
|Ir além: Implementou um componente de extra, fez com millis() ao invés do delay() e/ou usou ponteiros no código |	Até 1 |	Até 0,5 |	1,0 | Utiliza millis() e adiciona mais dois componentes. |	
| | | | |Pontuação Total: 10,0 |

#### Avaliador: Maria Arielly

|Critério|	Contempla (Pontos)|	Contempla Parcialmente (Pontos)	|Não Contempla (Pontos)	|Observações do Avaliador|
|-|-|-|-|-|
|Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores	|Até 3	|Até 1,5	| 2,5 | Uso adequado de resistores, mas os fios estão um pouco bagunçados. |	
|Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo	|Até 3	|Até 1,5	| 3 | Tempo conforme a demanda da atividade. |	
|Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) |	Até 3|	Até 1,5 |	3 | Código consiso e limpo, comentado e bem estruturado. |	
|Ir além: Implementou um componente de extra, fez com millis() ao invés do delay() e/ou usou ponteiros no código |	Até 1 |	Até 0,5 |	1,0 | Utiliza millis() ao invés de delay() e adiciona um display e um botão. |	
| | | | |Pontuação Total: 9.5 |
