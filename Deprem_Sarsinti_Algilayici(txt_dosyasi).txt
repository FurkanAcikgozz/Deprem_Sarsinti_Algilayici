#include <MPU6050.h>
#include <Wire.h>

MPU6050 mpu;



int angle_x, angle_y, angle_z, offset_x, offset_y, offset_z;

void setup() {

  Serial.begin(9600);
  Wire.begin();
  mpu.initialize();
}

void loop() {
  mpu.getAcceleration(&angle_x, &angle_y, &angle_z);
  mpu.getRotation(&offset_x, &offset_y, &offset_z);

  delay(500);
  Serial.print("ivme X = ");
  Serial.println(angle_x);

  Serial.print("ivme Y = ");
  Serial.println(angle_y);

  Serial.print("ivme Z = ");
  Serial.println(angle_z);
delay(500);
  Serial.print("Gyro X = ");
  Serial.println(offset_x);

  Serial.print("Gyro Y = ");
  Serial.println(offset_y);

  Serial.print("Gyro Z = ");
  Serial.println(offset_z);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
  digitalWrite(9, HIGH);
  

  if(angle_x>3000 || angle_x<100)
    {
        digitalWrite(9, LOW);
        digitalWrite(10, LOW);
        digitalWrite(11, HIGH);
        delay(1000); // Wait for 1000 millisecond(s)
        digitalWrite(10, LOW);
        delay(50); // Wait for 1000 millisecond(s
        tone(8,1000);
        delay(750);
        noTone(8);
        delay(250); 
        
    }
    else if(angle_x>1500 && angle_x<3000)
    {
        digitalWrite(9, LOW);
        digitalWrite(11, LOW);
        digitalWrite(10, HIGH);
        delay(750); // Wait for 1000 millisecond(s)
        digitalWrite(11, LOW);
        delay(50); // Wait for 1000 millisecond(s
        tone(8,1000);
        delay(250);
        noTone(8);
        delay(50);  
    }
}
 
  
  
