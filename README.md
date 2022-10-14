# verkefni-5
Verkefni 5 
Svölnir,Hávar,Breki og isabelle

verkegni 5 er sett út á það að nota alt sem við lærðum í gegnum áfangan til að gera eina stóra hrekkjavöku hauskúpu.
til að byrja með þurfti maður að velja einn af nokkrum mögulegum típumm af þessu og svo mátti maður byrja.
við byrjuðum með því að hugsa hvernig hlut maður ætlaði að gera og hvernig maður myndi gera hann.
það tók okkur smá tíma mest vegniss að hugsa hvernig við ættluðum að gera hann það tók okkur engan tíma að ákveða hvað við ætluðum að gera.
eftir að við fengum alt í verkefnið fórum við af stað tveir með hausinn og tveir með líkaman.
það tók slatta af tíma til að ná miklu með hausinn en líkaminn byrjaði mjög vel.
vekefnin skiptu hópnum svona Hávar og Svölnir með hausinn og Breki með isabelle í líkamanum þessir hópar voru fínir.
hópurinn með líkamann fór strax að gera hreifinguna fyrir hendina á meðan hópurinn með hauskúpuna fór að reina að finna út hvernig þeir myndu hreifa kjálkann.


[það sem við hópurin enduðum á því að velja var þetta(https://www.youtube.com/watch?v=Ill7k_zleuQ)]

kóði
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
