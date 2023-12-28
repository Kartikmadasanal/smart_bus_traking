const int buttonPin1 = 2;
const int buttonPin2 = 3;
const int buttonPin3 = 4;
const int buttonPin4 = 5;
const int buttonPin5 = 6;
const int buttonPin6 = 7;
const int buttonPin7 = 8;
const int buttonPin8 = 9;

void setup() {
  Serial.begin(9600); // Start serial communication

  // Initialize GSM module
  Serial.println("Initializing GSM module...");
  delay(1000);

  // Insert code here to send necessary AT commands for GSM initialization
  Serial.println("AT"); // Check if the module is responding
  delay(500);
  Serial.println("AT+CMGF=1"); // Set SMS mode to text
  delay(500);

  Serial.println("GSM module initialized");

  // Setup buttons
  pinMode(buttonPin1, INPUT_PULLUP);
  pinMode(buttonPin2, INPUT_PULLUP);
  pinMode(buttonPin3, INPUT_PULLUP);
  pinMode(buttonPin4, INPUT_PULLUP);
  pinMode(buttonPin5, INPUT_PULLUP);
  pinMode(buttonPin6, INPUT_PULLUP);
  pinMode(buttonPin7, INPUT_PULLUP);
  pinMode(buttonPin8, INPUT_PULLUP);
}

void loop() {
  if (digitalRead(buttonPin1) == LOW) {
    sendSMS("8867975992", "BUS LEFT COLLEGE");
    delay(10000); // Delay before sending another SMS
  }

  if (digitalRead(buttonPin2) == LOW) {
    sendSMS("7022057435", "BUS LOCATION:CANNAMMA CIRCLE");
    delay(10000);
  }

  if (digitalRead(buttonPin3) == LOW) {
    sendSMS("8123029734", "BUS LOCATION:RAMDEV CIRCLE");
    delay(10000);
  }

  if (digitalRead(buttonPin4) == LOW) {
    sendSMS("8884395825", "BUS LOCATION:MORE STOP");
    delay(10000);
  }

  if (digitalRead(buttonPin5) == LOW) {
    sendSMS("8431835816", "BUS LOCATION:MAHANTESH NAGAR");
    delay(10000);
  }

  if (digitalRead(buttonPin6) == LOW) {
    sendSMS("9611608042", "BUS LOCATION:CBT");
    delay(10000);
  }

  if (digitalRead(buttonPin7) == LOW) {
    sendSMS("9900973878", "RTO CIRCLE");
    delay(10000);
  }
  if (digitalRead(buttonPin8) == LOW) {
    sendSMS("8867975992", "BUS REACHD COLLEGE");
    delay(10000);
  }
}

void sendSMS(const char* phoneNumber, const char* message) {
  Serial.print("Sending SMS to ");
  Serial.println(phoneNumber);

  // Insert code here to send necessary AT commands for sending SMS
  Serial.print("AT+CMGS=\"");
  Serial.print(phoneNumber);
  Serial.println("\"");
  delay(500);

  Serial.print(message);
  delay(500);

  Serial.print((char)26); // Send Ctrl+Z to indicate the end of the message
  delay(1000);
}
