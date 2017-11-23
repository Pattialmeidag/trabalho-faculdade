# trabalho-faculdade
O objetivo do projeto é, facilitar o acesso na passagem de uma porta, fazendo dela um portão inteligente usando sensor ultrassônico, servo motor e um led. Pode ser aplicado em rotinas diárias onde é necessário algum tipo de automação e/ou inteligência em ambientes como casas, lojas etc.
#include <Ultrasonic.h>
#include <Servo.h>
#define echoPin 13
#define trigPin 12

Servo servo_objeto;
Ultrasonicultrasonic(12,13);

intposicao_inicial_servo = 0;
intledPin =  10;

void setup()
{
Serial.begin(9600);
pinMode(echoPin, INPUT);
pinMode(trigPin, OUTPUT);
pinMode(ledPin, OUTPUT);
servo_objeto.attach(9);

}
void loop()
{
digitalWrite(ledPin, LOW);
servo_objeto.write(posicao_inicial_servo);
int valor = func_distancia_ultrasonico();
if(valor <=15)
    {
func_controladora();
delay(5000);
    }

delay(500);
}

voidfunc_controladora()
{
func_liga_led();
func_chama_servo();
}
voidfunc_liga_led()
{
digitalWrite(ledPin, HIGH);
}
voidfunc_chama_servo()
{
intposicao_final_servo = 90;
servo_objeto.write(posicao_final_servo);
}
intfunc_distancia_ultrasonico()
{
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

digitalWrite(trigPin, HIGH);
delayMicroseconds(10);

digitalWrite(trigPin, LOW);
int distancia = (ultrasonic.Ranging(CM));
Serial.print("Distancia em CM: ");
Serial.println(distancia);
return distancia;
}
	
