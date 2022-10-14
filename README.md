# verkefni-5
Verkefni 5 

Hópur:
| ----------- |
| Breki Hlynsson    |
|Svölnir Ás Hrafnkelsson|
|Hávarr Hrafn Jónsson|
|Isabelle Stella Markúsdóttir|

youtube mindband af Verkefninu að virka: [https://youtu.be/oL7oJQdIw5c](https://youtu.be/oL7oJQdIw5c)

Verkefni 5 gengur út á það að nýta allt sem við lærðum í gegnum áfangan til að gera eina stóra hrekkjavöku hauskúpu.
Til að byrja með þurfti maður að velja einn af nokkrum mögulegum týpum af þessu og svo mátti maður byrja.
Við byrjuðum með því að hugsa hvernig hlut maður ætlaði að gera og hvernig maður myndi gera hann.
Það tók okkur smá tíma mest vegnis að hugsa hvernig við ættluðum að gera hann það tók okkur engan tíma að ákveða hvað við ætluðum að gera.
Eftir að við fengum alt í verkefnið fórum við af stað tveir með hausinn og tveir með líkaman.
Það tók slatta af tíma til að ná miklu með hausinn en líkaminn byrjaði mjög vel.
Hópurinn skipti verkfninu þannig að Hávarr og Svölnir gerðu hausinn en  Breki með Isabelle gerðu líkamanum. Þessir hópar voru fínir.
Hópurinn með líkamann fór strax að gera hreyfinguna fyrir hendina á meðan hópurinn með hauskúpuna fór að reyna að finna út hvernig þeir myndu hreyfa kjálkann.

Efnið sem við notuðum  í fígúruna var plaströr, viðarplötur, koparvírar, gervihauskúpu og hendi. dc mótor og servo mótor í gatagrind sem tengdust við gata renninga með mismunandi skrúfum og festingu voru notaðir til að búa til hreyfingarnar


[það sem við hópurin enduðum á því að velja var þetta](https://www.youtube.com/watch?v=Ill7k_zleuQ)

## Mismunandi mindir af verkefninu

![20221014_131630](https://user-images.githubusercontent.com/88351016/195892488-cf5715de-e210-4cc5-bbbf-549be87fa1be.jpg)

![20221014_124155](https://user-images.githubusercontent.com/88351016/195892816-9d7380dd-5dbd-4881-b6a3-646e2aeaf096.jpg)

![20221014_124159](https://user-images.githubusercontent.com/88351016/195892822-28adefa6-a05b-4f85-9773-3323304b6229.jpg)

![20221014_130723](https://user-images.githubusercontent.com/88351016/195892528-75eb02a9-d69e-4298-9cc5-f4f218cf3be1.jpg)

![20221014_130707](https://user-images.githubusercontent.com/88351016/195892997-3b894441-6bb9-4e14-8432-2219bb897ef4.jpg)


![20221014_124202](https://user-images.githubusercontent.com/88351016/195892661-31dde7d5-5600-4ed3-bc8c-c28f4396b893.jpg)









kóði fyrir búkin:

```
#include <Servo.h>

  // Motor A connections
int enA = 9;
int in1 = 8;
int in2 = 7;

int pos = 0;

void setup() {

  // Set all the motor control pins to outputs
  pinMode(enA, OUTPUT);
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  
  // Turn off motors - Initial state
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
}

void loop() {
  speedfast();
  delay(5000);
  Thehand();
  delay(1000);
  speedslow();
  delay(1000);
  reset ();
  delay (20);
}


// This function lets you control speed of the motors


void reset(){
  pos = (0);
}

void speedfast(){
    // Turn on motors
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  
  // Accelerate
  {
    analogWrite(enA ,200);
    delay(20);
  }
}

void speedslow(){
    // Decelerate
  {
    analogWrite(enA, 0);
    delay(20);
  }
  
  // Now turn off motors
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
}

void servo(){

}

void Thehand(){
Servo myservo;

  myservo.attach(3);  // attaches the servo on pin 9 to the servo object

  myservo.write(0);  
  delay(20);
  
  {
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  }
  delay(20);

  
  for (pos = 0; pos <= 180; pos += 4) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(30);   // waits 15 ms for the servo to reach the position
  }
  
  for (pos = 180; pos >= 0; pos -= 4) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(35);                       // waits 15 ms for the servo to reach the position
  }
}
```


kóði fyrir hausin:

```
#include "SoftwareSerial.h"
#include "DFRobotDFPlayerMini.h"
#include <Servo.h>

SoftwareSerial mySoftwareSerial(10, 11);
DFRobotDFPlayerMini myDFPlayer;

int servoPin = 9;

Servo servo;

int angle = 0;

void setup() {
    servo.attach(servoPin);

      mySoftwareSerial.begin(9600);
        if (!myDFPlayer.begin(mySoftwareSerial)) {
    while(true);
  }
  myDFPlayer.reset();
  myDFPlayer.volume(0);
  myDFPlayer.play(1);
}

void loop() {

    for(angle = 0; angle < 180; angle++) {
        servo.write(angle);

        delay(1);
    }

    for(angle = 180; angle > 0; angle--) {
        servo.write(angle);

        delay(2000);

    }
}
```
