# how-to-make-a-voltmeter
We are designing a voltmeter
Designing and manufacturing measuring instruments is a difficult task. But the features of microcontroller cards make our job easier. The 6 analog inputs on the Arduino microcontroller board are very useful. We will use one of these analog inputs as a voltage input.
The voltage to be measured may be high. In this application, we have determined a voltage range between 0 and 50-55 volts. Since we can apply more than 5 volts to the analog inputs, we need to divide the voltage to be measured at the input by a large resistor. We did this division with the help of resistors R1 and R2.

Youtube Channel:




When the voltage on R1 exceeds 5-5.1 volts, we used a zener diode so that it would not damage the microcontroller board. This zener diode is a 5.1 volt zener diode. The 1N4733 zener diode is short-circuited when the voltage exceeds 5.1 volts. And so the microcontroller protects the board.

float volt_in = analogRead(A0);// Vin INPUT
   float  deg=(volt_in/1023)*53; // for max. 55 volt
The codes above are the codes used to get the value of the analog voltage on R1.

Arduino Codes:

//--------- -{a,b,c,d,e,f,g,dot}
  int s0[] = {1,1,1,1,1,1,0,0};
  int s1[] = {0,1,1,0,0,0,0,0};
  int s2[] = {1,1,0,1,1,0,1,0};
  int s3[] = {1,1,1,1,0,0,1,0};
  int s4[] = {0,1,0,0,1,1,1,0};
  int s5[] = {1,0,1,1,0,1,1,0};
  int s6[] = {1,0,1,1,1,1,1,0};
  int s7[] = {1,1,1,0,0,0,0,0};
  int s8[] = {1,1,1,1,1,1,1,0};
  int s9[] = {1,1,1,1,0,1,1,0};
  int s10[]= {1,1,1,1,1,1,0,0};
  
void setup()
{Serial.begin (9600);
  pinMode(13, OUTPUT);  // a 
  pinMode(12, OUTPUT);  // b 
  pinMode(11, OUTPUT);  // c 
  pinMode(10, OUTPUT);  // d 
  pinMode(9, OUTPUT);    // e 
  pinMode(8, OUTPUT);  // f
  pinMode(7, OUTPUT);  // g 
  pinMode(6, OUTPUT);  //DOT LED  <-----------
  pinMode(5, OUTPUT);    // D1 
  pinMode(4, OUTPUT);    // D2
  pinMode(3, OUTPUT);    // D3 
  pinMode(2, OUTPUT);    //D4
}

void loop()
{
   float volt_in = analogRead(A0);// Vin INPUT
   float  deg=(volt_in/1023)*53; // for max. 55 volt
   String svalue=String(deg);
   int st_len=svalue.length();
   if(st_len==4){
    digitalWrite(6,HIGH);
    digitalWrite(5,LOW);
      if(svalue[0]=='0'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s0[i-1]); digitalWrite(6,HIGH);}delay(5);digitalWrite(4,LOW);  }
      if(svalue[0]=='1'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s1[i-1]); digitalWrite(6,HIGH);}delay(5);digitalWrite(4,LOW);  }
      if(svalue[0]=='2'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s2[i-1]);digitalWrite(6,HIGH); }delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='3'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s3[i-1]); digitalWrite(6,HIGH);} delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='4'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s4[i-1]); digitalWrite(6,HIGH);} delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='5'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s5[i-1]);digitalWrite(6,HIGH); } delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='6'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s6[i-1]); digitalWrite(6,HIGH);} delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='7'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s7[i-1]);digitalWrite(6,HIGH); }delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='8'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s8[i-1]); digitalWrite(6,HIGH);}delay(5);digitalWrite(4,LOW); }
      if(svalue[0]=='9'){digitalWrite(4,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s9[i-1]);digitalWrite(6,HIGH); } delay(5);digitalWrite(4,LOW);}
      
      if(svalue[2]=='0'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s0[i-1]); } delay(5);digitalWrite(3,LOW);}
      if(svalue[2]=='1'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s1[i-1]); } delay(5);digitalWrite(3,LOW);}
      if(svalue[2]=='2'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s2[i-1]); }delay(5);digitalWrite(3,LOW); }
      if(svalue[2]=='3'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s3[i-1]); }delay(5);digitalWrite(3,LOW); }
      if(svalue[2]=='4'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s4[i-1]); }delay(5);digitalWrite(3,LOW); }
      if(svalue[2]=='5'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s5[i-1]); }delay(5);digitalWrite(3,LOW); }
      if(svalue[2]=='6'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s6[i-1]); }delay(5);digitalWrite(3,LOW); }
      if(svalue[2]=='7'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s7[i-1]); } delay(5);digitalWrite(3,LOW);}
      if(svalue[2]=='8'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s8[i-1]); }delay(5);digitalWrite(3,LOW); }
      if(svalue[2]=='9'){digitalWrite(3,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s9[i-1]); } delay(5);digitalWrite(3,LOW);}

      if(svalue[3]=='0'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s0[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='1'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s1[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='2'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s2[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='3'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s3[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='4'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s4[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='5'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s5[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='6'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s6[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='7'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s7[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='8'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s8[i-1]); }delay(5);digitalWrite(2,HIGH); }
      if(svalue[3]=='9'){digitalWrite(2,HIGH);for(int i=1;i<9;i++) { digitalWrite(14-i,s9[i-1]); }delay(5);digitalWrite(2,HIGH); }
    }
   
 Serial.println(svalue[0]);
  Serial.println(svalue[1]);
   Serial.println(svalue[2]);
    Serial.println(svalue[3]);
 Serial.print(deg);
 Serial.println(" Volt");
delay(3);} 
 


 Related link : https://milivolt.news/post/how-to-make-a-voltmeter
 Related video:  https://youtu.be/K-Nf1PCBIgs?si=ZhQ06Of01WCafmU8
