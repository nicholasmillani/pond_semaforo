# Ponderada semáforo
## Objetivo:
Nesta atividade, o objetivo é compreender o funcionamento e a utilização das portas digitais e analógicas do Arduino. Para isso, será montado um circuito contendo LEDs e resistores.

Durante a prática, será desenvolvido um código que acende e apaga LEDs de acordo com o estado do botão, demonstrando na prática o conceito de leitura (input) e escrita (output) nas portas do microcontrolador. Além disso, aprender a diferenciar portas analógicas e digitais, compreender a importância dos resistores de proteção e aplicar conceitos de lógica de controle em um sistema simples.


## Materiais:
Foram usados:
- 1 Arduino uno
- 3 resistores de 1k hmn
- 3 leds(azul - pq nn tinha vermelho, verde e amarelo)
- 10 jumpers
- Estrutura do semáforo


## código
````
using namespace std;

class LED {
  public:
    int pin;
    bool ligado; 

    LED(int pin) {
      this->pin = pin;
      pinMode(pin, OUTPUT);
      ligado = false;
    }

    void ligar() {
      digitalWrite(this->pin, HIGH);
    }

    void desligar() {
      digitalWrite(this->pin, LOW);
    }
};
	
LED* vermelho;
LED* verde;
LED* amarelo;

void setup() {
  	pinMode(A0, INPUT);
  	
	vermelho = new LED(12);
  	verde = new LED(13);
  	amarelo = new LED(11);
  
}

// define a variavel estado, ela mostra qual cor deve estar ligada.
// 0 = vermelho; 1 = verde; 2 = amarelo;
int estado = 0;

void loop() {
  
  int leitura = analogRead(A0);
  
   if(estado == 0){
     vermelho->ligar();
     verde->desligar();
     amarelo->desligar();      delay(3000);
     estado = 1;
  	}
  	else if(estado == 1){
     vermelho->desligar();
     verde->ligar();
     amarelo->desligar();
     delay(3000);      
     estado = 2;
  	}	
  	else if(estado == 2){
     vermelho->desligar();
     verde->desligar();
     amarelo->ligar();
     delay(1500);
     estado = 0;
  	}
      
  }

  	
  ````

## Imagens:
<img src="Imagem do WhatsApp de 2025-10-31 à(s) 12.00.36_018ceb14.jpg" height=400 widht=400>
<img src="Imagem do WhatsApp de 2025-10-31 à(s) 12.00.37_fe24df26.jpg" height=400 widht=400>
<img src="Imagem do WhatsApp de 2025-10-31 à(s) 12.00.38_a801dc22.jpg" height=400 widht=400>
