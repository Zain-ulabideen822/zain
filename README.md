
#include <UTFT.h>
#include <URTouch.h>

// Declare which fonts we will be using
extern uint8_t SmallFont[];
extern uint8_t BigFont[];
int x,y,c=0;
int ledPin0= 8;
int ledPin1= 9;
int ledPin2 = 10;
int ledPin3 = 11;
int ledPin4= 13;
UTFT myGLCD(ILI9341_16,38,39,40,41);
URTouch  myTouch( 6, 5, 4, 3, 2);

void RCT(int a,int b,int c,int d)
{
  myGLCD.setColor(0, 0, 0);
    myGLCD.fillRoundRect (a, b, c, d);
    delay(50);
  myGLCD.setColor(0, 255, 255);
  myGLCD.fillRoundRect (a, b, c, d);
}
void setup()
{
  
  myGLCD.InitLCD();

  myGLCD.clrScr();
    myTouch.InitTouch();
  myTouch.setPrecision(PREC_HI);
  myGLCD.InitLCD(LANDSCAPE);
   myGLCD.setColor(0, 255, 255);
  myGLCD.setBackColor(0, 0, 0);
  pinMode(ledPin0,OUTPUT);
  pinMode(ledPin1,OUTPUT);
  pinMode(ledPin2,OUTPUT);
  pinMode(ledPin3,OUTPUT);
  pinMode(ledPin4,OUTPUT);
  myGLCD.setFont(BigFont);
  myGLCD.print("A P C O M S", CENTER, 80);
  delay(1000);
  myGLCD.clrScr();
   myGLCD.setColor(0, 255, 0);
  myGLCD.print("A PROJECT BY  ", LEFT, 48);
  myGLCD.print("APCOMINS ", RIGHT, 64);
   // delay(3000);
  myGLCD.clrScr();
  myGLCD.print("SUPERVISED BY;", LEFT, 32);
 myGLCD.setColor(0, 255, 255);
  myGLCD.print("ENGR.AYYAZ ALI ", RIGHT, 64);
   //delay(3000);
  myGLCD.clrScr();
  myGLCD.setColor(0, 255, 0);
  myGLCD.print("GROUP MEMBERS ", LEFT, 16);
  myGLCD.setFont(SmallFont);
  myGLCD.setColor(0, 255, 255);
  myGLCD.print("JUNAID", CENTER, 64);
  myGLCD.print("HASEEB  ", CENTER, 80);
  myGLCD.print("TALHA", CENTER, 96);
  myGLCD.print("ZAIN-UL-ABIDEEN", CENTER,112 );
  //delay(5000);
  myGLCD.clrScr();
  myGLCD.setColor(0, 255, 0);
  myGLCD.print("SELECT SEQUENCE FROM BUTTONS", 20,64);
  myGLCD.setFont(BigFont);
    myGLCD.print("LED CUBE",CENTER,100);
    myGLCD.setColor(255, 255, 0);
    myGLCD.print("USING ARDINO & TFT",CENTER,116);
    myGLCD.setColor(0, 255, 0);
     myGLCD.setFont(SmallFont);
      myGLCD.clrScr();
  myGLCD.setColor(0, 255, 255);
  myGLCD.setFont(BigFont);
    myGLCD.fillRoundRect (20, 20, 300, 60);
    myGLCD.fillRoundRect (20, 80,300 , 120);
    myGLCD.fillRoundRect (20, 140,300 , 180);
    myGLCD.print("UP",80 , 33);
     myGLCD.setColor(255, 255, 0);
    myGLCD.print("DOWN",80 , 90);
    myGLCD.setColor(255, 0, 0);
    myGLCD.print("BLINK",80 , 150);
    myGLCD.setColor(0, 255, 255);
}

void loop()
{   

  while (true)
{   
    if (myTouch.dataAvailable())
    { 
      myTouch.read();
      x=myTouch.getX();
      y=myTouch.getY();
           myGLCD.setFont(BigFont);
      if ((x>=20) && (x<=300))
         {
             if ((y>=20) && (y<=60)) 
            {  RCT(20, 20, 300, 60);
             myGLCD.setColor(0, 255, 0);
               myGLCD.print("UP",80 , 30);
               myGLCD.setColor(0, 255, 255);
               c=3;
            }
            
             else if((y>=80)&& (y<=120))
            {
              RCT (20, 80,300 , 120);
               myGLCD.setFont(BigFont);
                myGLCD.setColor(255, 255, 0);
              myGLCD.print("DOWN",80, 90);
              myGLCD.setColor(0, 255, 255);
              c=2;
          
            }
            else if((y>=140)&& (y<=180))
            {RCT (20, 140,300 , 180);
              myGLCD.setFont(BigFont);
              myGLCD.setColor(255, 0, 0);
              myGLCD.print("BLINK",80 , 150);
               myGLCD.setColor(0, 255, 255);
               c=1;
  
             
           
            }
             
         } 
     
 
      }
