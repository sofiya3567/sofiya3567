// C++ code
//
unsigned long timeTmp, time;
int k=13;
bool out=1;
byte c=0;
int sing=1;
int myDelay=50; //frequrency

void setup()
{
  for (int i=9;i<=13;i++)
  pinMode(i, OUTPUT);

  digitalWrite(12, LOW);
  digitalWrite(10, LOW);
  Serial.begin(19200);
}

void loop()
{
   pinOut(k,out);
  time=millis();
  if (time-timeTmp>myDelay){
     timeTmp=time;
   
     c++;
    out=!out;
  }
  if (c==2) {
    k=k-2*sing;
    c=0;
  }
  if ((k==7) ||(k==15)){
   
    sing=-sing;
  }
  Serial.println( k);
   Serial.println( sing);
 
}

void pinOut (int pin,int val){
  digitalWrite(pin, val);
 
 
}
