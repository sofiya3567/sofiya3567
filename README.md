#define UP_BT 12
#define DOWN_BT 11

const int maks=7;
const int min=3;
bool up_button, down_button;
bool up_tmp,down_tmp, st=1;
int k=min;


void setup()
{
  for (int i=min;i<=maks;i++)
 pinMode(i,OUTPUT);
 
  pinMode(UP_BT,INPUT);
  pinMode(DOWN_BT,INPUT);
  Serial.begin(19200);
}

  void loop()
{
 up_button=digitalRead(UP_BT);
 down_button=digitalRead(DOWN_BT);
 if ((up_button==1) && (up_tmp==0))
 {
     digitalWrite(k,st);
       up_tmp=1;
       k++;
       
 }
  Serial.println(k);
   
    if ((up_button==0) && (up_tmp==1))
 {
      up_tmp=0;
         
 }
   
     if ((down_button==1) && (down_tmp==0))
 {
     digitalWrite(k,!st);
       down_tmp=1;
       k--;
       
 }
  Serial.println(k);
   
    if ((down_button==0) && (down_tmp==1))
 {
      down_tmp=0;
         
 }
   
   
 if (k>maks)
 {    k=min;
      st=!st;
 }
     if (k<0)
 {    k=maks;
      st=!st;
 }
}
