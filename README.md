# Atividade Ponderada Semáforo

Código:

```
// define os pinos
#define pin_red 16
#define pin_yellow 17
#define pin_green 18
// define o tempo passado e inicializa como 0
unsigned long _previousMillis = 0;

void setup() {
  // configura os pinos como saída
  pinMode(pin_red, OUTPUT);
  pinMode(pin_yellow, OUTPUT);
  pinMode(pin_green, OUTPUT);
  // inicia acedendo o led vermelho
  digitalWrite(pin_red, HIGH);
}

void loop() {
  unsigned long currentMillis = millis();
  // acender o verde
  if (currentMillis - _previousMillis == 6000 && digitalRead(pin_red) == HIGH){
      digitalWrite(pin_green, HIGH);
      digitalWrite(pin_yellow, LOW);
      digitalWrite(pin_red, LOW);
      _previousMillis = currentMillis;
  }

  // acender amarelo 
  if (currentMillis - _previousMillis == 4000 && digitalRead(pin_green) == HIGH){
      digitalWrite(pin_red, LOW);
      digitalWrite(pin_yellow, HIGH);
      digitalWrite(pin_green, LOW);
      _previousMillis = currentMillis;
  }

  // acende vermelho
  if ((currentMillis - _previousMillis == 2000 && digitalRead(pin_yellow) == HIGH)){
      digitalWrite(pin_green, LOW);
      digitalWrite(pin_yellow, LOW);
      digitalWrite(pin_red, HIGH);
      _previousMillis = currentMillis;
  }
}
```

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
