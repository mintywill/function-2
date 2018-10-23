/*function name: isForceSensitiveResistorOnA0Touched
input: none
output: boolean // what is it?
description: Assume A0 is the input pin and you'll have to read that pin inside the function. This function should read that pin with analogRead() and then return a value between 0-1023 and return whether the FSR is touched. Assume an A0 reading above 167 will mean the FSR is touched.
*/


const int analogPin = A0;
const int ledPin = 13; 
const int threshold = 167; //is it right?


void setup(){
	pinMode(13, OUTPUT);
	Serial.begin(9600);
}

void loop(){
	isForceSensitiveResistorOnA0Touched();
	int analogValue = analogRead(analogPin);
	Serial.printIn(analogValue);

	//conditional?
	if (analogValue > threshold) {
		isForceSensitiveResistorOnA0Touched == true;
	} else {
		isForceSensitiveResistorOnA0Touched == false;
	}



/*function name: isForceSensitiveResistorTouched
input: one integer that will be in the range 0-1023
output: boolean
description: Unlike the last function, here we'll assume the pin read is happening somewhere else and this function just takes that value. So, the input will vary between 0-1023 and return whether the FSR is touched. Assume an input above 167 will mean the FSR is touched.
But, now let's make this more useful. An FSR affords a continuous range of outputs and, so far, we've just been treating it like a discrete on/off button. Let's make use of this continuous range by writing a function that will return how hard the FSR is being pressed. 
0=not pressed 
1=light press (let's define this as an input value above 400)
2=medium press (let's define this as an input value above 800)
3=hard press (let's define this as an input value above 1000)
*/

const int analogPin = A0;
const int ledPin = 13; 


void setup(){
	pinMode(13, OUTPUT);
	Serial.begin(9600);
}

void loop(){
	isForceSensitiveResistorTouched();
	int analogValue = analogRead(analogPin);
	Serial.printIn(analogValue);


	if (analogValue = 0) {
	return "not pressed"
	} else if (800 > analogValue > 400) {
	return "light press"
	} else if (1000 > analogValue > 800) {
	return "medium press"
	} else if (analogValue > 1000) {
	return "hard press"
	} 
	



3)
function name: getFSRTouchState
input: integer that will be in the range 0-1023
output: an integer between 0 and 3 corresponding to how hard the FSR is pressed



4)
function name: printFSRTouchStateToSerial
input: int that will be in the range 0-3
output: none (the function won't return a value but it should print to Serial from inside the function)
description: The idea here is to create a function that can use the 0 to 3 output range of the previous function and then print something human readable to Serial. If the input is 0 you should print "no touch", else if it's 1 you should print "light touch", else if it's 2 you should print "medium touch", else if it's 3 you should print "hard touch" 

