# HELLO_WORD


 

//constants for this sketch


// pins to which the on-board LED is connected.

const int led1Pin = 11; //

const int led2Pin = 5;

const int led3Pin = 13; // Use the onboard Uno LED

const int led4Pin = 12; // Use the onboard Uno LED
 

int isObstaclePin = 3;  // Input pin for infrared  sensor

int isObstacle = HIGH;  // The default is HIGH meaning no obstacle 


// Pin 2 of the potentiometer  connected to to the  analog pin A0 on the board

const int potPin = A0;  

//This pin connect the analog A2 to the
photoresistor in series with a resistor, performing hence the voltage division

const int pot1Pin = A2;//

 

// variables for this sketch

int pot_value;

int frequency;

int IRTC500Value;

 

void setup()

{

//The LED (led1Pin) becomes an output as it can be
either turned on or off depending on

//the voltage read from the potentiometer

 

  pinMode(led1Pin,
OUTPUT);

 
pinMode(led2Pin, OUTPUT);

 
pinMode(led3Pin, OUTPUT);

  
pinMode(led4Pin, OUTPUT);

 
pinMode(isObstaclePin, INPUT);

 

  

  //Prints
data to the serial port

  //begin
sending messages to the serial port 

 
Serial.begin(9600);

}

 

void loop()

{

  //read
voltage from the potentiometer

  pot_value =
analogRead(pot1Pin);

 
//IRTC500Value = analogRead();

  //Set the
LED to brightness pot_value

 // output to
confirm that the serial port  is reading

 
//Serial.print("IRTC500Value is:");

  Serial.print("Photoresistor
value is:");

  // print
values read that can be accessed by pressing the Serial Monitor button

 
Serial.println(pot_value);

 
//Serial.println(IRTC500Value);

  delay(10);

 //From the
values read it is possible  to compute
the theshold  values below which, we can
turn the light on or off

 // In this
case the value of  790  have been found

  if(pot_value
< 790)

  {

    // Turn
the LED on when pot_value is below  790 .
i.e when it is darker

   
digitalWrite(led1Pin, HIGH);

   
digitalWrite(led2Pin, HIGH);

   
digitalWrite(led4Pin, HIGH);

   }

   

    else

    {

      // Turn
the LED off when pot_value is above 790 . i.e when  there is too much light 

     
digitalWrite(led1Pin, LOW);

     
digitalWrite(led2Pin, HIGH);

     
digitalWrite(led4Pin, LOW);

    }

 

 isObstacle =
digitalRead(isObstaclePin);

  if
(isObstacle == LOW)

  {

   
Serial.println("OBSTACLE!!, OBSTACLE!!");

   
digitalWrite(led3Pin, HIGH);

  }

  else

  {

    Serial.println("clear");

   
digitalWrite(led3Pin, LOW);

  }

  delay(200);

 

  }

 

