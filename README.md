//shout out to Aaron!!! <3

bool debugMode = false;

void setup() {
  Serial.begin(9600);
}

void loop() {
  bool fsrState = isForceSensitiveResistorOnA0Touched();
  Serial.println(fsrState);
  //  printFSRTouchStateToSerial(getFSRTouchState);
  printFSRTouchStateToSerial(getFSRTouchState(analogRead(A0)));
}

bool isForceSensitiveResistorOnA0Touched() {
  int fsrState = analogRead(A0);
  if (fsrState > 167) {
    return true;
  } else {
    return false;
  }
}

bool isForceSensitiveResistorTouched(int i) {
  if (i > 167) {
    return true;
  } else {
    return false;
  }
}

//make sure it actually covers the value in the correct range!
int getFSRTouchState(int i) {
  debug(i);
  if (i <= 400) {
    return 0;
  } else if (i < 800) {
    return 1;
  } else if (i < 1000) {
    return 2;
  } else {
    return 3;
  }
}


void printFSRTouchStateToSerial(int x) {
  if (x == 0) {
    Serial.println("not pressed");
  } else if (x == 1) {
    Serial.println("light press");
  } else if (x == 2) {
    Serial.println("medium press");
  } else if (x == 3) {
    Serial.println("hard press");
  }
}

//if it printed something else than what we asked, there was something wrong
void debug(int val) {
  if (debugMode) {
    Serial.println(val);
  }
}
