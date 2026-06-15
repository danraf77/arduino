// Definimos los pines con nombres descriptivos en lugar de números sueltos.
// Si cambias el cableado, solo modificas esta sección.
const int PIN_ROJO     = 13;
const int PIN_AMARILLO = 12;
const int PIN_VERDE    = 11;

// Tiempos de cada fase en milisegundos (1000 ms = 1 segundo).
const int TIEMPO_VERDE    = 5000;  // 5 s en verde
const int TIEMPO_AMARILLO = 2000;  // 2 s en amarillo
const int TIEMPO_ROJO     = 5000;  // 5 s en rojo

void setup() {
  // Configuramos los tres pines como salidas.
  pinMode(PIN_ROJO, OUTPUT);
  pinMode(PIN_AMARILLO, OUTPUT);
  pinMode(PIN_VERDE, OUTPUT);

  // Apagamos todos los LEDs al iniciar para partir de un estado conocido.
  digitalWrite(PIN_ROJO, LOW);
  digitalWrite(PIN_AMARILLO, LOW);
  digitalWrite(PIN_VERDE, LOW);
}

void loop() {
  // --- Fase VERDE: pase el tránsito ---
  digitalWrite(PIN_ROJO, LOW);      // aseguramos el rojo apagado
  digitalWrite(PIN_VERDE, HIGH);    // encendemos el verde
  delay(TIEMPO_VERDE);

  // --- Fase AMARILLA: precaución ---
  digitalWrite(PIN_VERDE, LOW);     // apagamos el verde
  digitalWrite(PIN_AMARILLO, HIGH); // encendemos el amarillo
  delay(TIEMPO_AMARILLO);

  // --- Fase ROJA: alto ---
  digitalWrite(PIN_AMARILLO, LOW);  // apagamos el amarillo
  digitalWrite(PIN_ROJO, HIGH);     // encendemos el rojo
  delay(TIEMPO_ROJO);
  // Al terminar loop() vuelve a empezar por la fase verde.
}
