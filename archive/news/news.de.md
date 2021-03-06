## 2018.03.17
### Ankündigung
Es wurde die neue Cloud-Adapter-Version vorbereitet.

Es ist wichtig, dass ALLE diese Version haben, wenn der Cloud-Server nächtes mal neu gestartet wird (in einer Woche).

Das ist gültig für iobroker.net und auch für iobroker.pro. Allerdings iobroker.pro wird nach ca. einer Woche nach iobroker.net upgedatet sein.

#### Was ist geändert
Cloud-Adapter unterstützt jetzt die Steuerungsbefehle vom Cloud-Server.

Es gibt 3 Arten von Cloud-Befehlen:

##### 1. "Redirect". 
Da iobroker.net mit sehr vielen veralteten Clients belastet ist, kann jetzt Cloud-Server die neue Clients auf die neue Adresse 10557 umleiten und die alte Clients einfach zu machen.

Die alten Clients werden alten Server 10555 immer noch belasten, aber es wird ein spezieller schneller Server sein, der nichts macht, ausser die Versionen prüfen. Damit kann Cloud-Server ungefähr 30 Connections pro Sekunde (!) sparen.

Auch zukünftige Umzuge und Load-Ballancing wird damit möglich sein.
 
##### 2. "Stop". 
Cloud-Server kann jetzt zu Clients, die nicht passende Version haben, "stop"-Befehl senden. Damit werden die Clients angehalten und werden den Server mit Anfragen nicht mehr belasten.

Client wird so lange disconnected, bis der nicht upgedated wird. 

Leider ist noch das Befehl mit älteren < 2.5.0 Clients nicht unterstützt und deswegen muss man Trick mit Serverumzug machen. 

Aber in der Zukunft wird dann es einfacher.

##### 3. "Wait". 
Beim Start bekommt der Cloud-Server SEHR viele gleizeitige Verbindungsanfragen. Da Datenbank nicht so viele Anfragen gleichzeitig verarbeiten kann werden die Clients gebeten 60-90 Sekunden zu warten und es wird 500 oder 1000 Clients gleichzeitig angebunden.

So kann der Server in Ruhe alle Anfragen verarbeiten, sonst hat man ein "Schaukel-Effekt".

#### "Schaukel-Effekt"
Es werden viele Clients angebunden und der Server wird langsammer. Die Clients verliehren die Verbindung und fangen sofort wieder eine Verbindung aufzubauen zusätzlich zu alten. Dann Verdoppelt sich die Anzahl von Verbindungen bis der Server gar nichts machen kann. So ein Zustand kann bis zu 5 Stunden dauern.

## 2018.01.19
Neuegkeiten für 19 Januar

## 2018.01.11
Neuegkeiten für 11 Januar