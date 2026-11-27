
Data kommer in och visualiseras i grafein via aws och Lambda:

ESP32 ➔AWS IoT Topic ➔ IoT Rule ➔ Lambda / AppSync ➔ DynamoDB (Telemetry) ➔ React-grafen

ToDo : att kunna sätta SetTemp via knappen

Webbläsaren ➔ AppSync/Lambda ➔ AWS IoT Core 

det är ett säkerare och skalbart sätt att hantera det på än att kommuinicera direkt till IoT Core:
(OBS just nu fungerar inte direktkommunikationen då url:t är en placeholder endpoint: "https://amazonaws.com") 
behöver i så fall ändras. men, som sagt bör ändå inte användas utan Lambda bör användas istället.

istället för direkt från React (Nuvarande kod)	
Hur det går till:	Webbläsaren ➔ AWS IoT Core	Webbläsaren ➔ AppSync/Lambda ➔ AWS IoT Core

tillfällig lösning(nackdelar): Endpoint-hanterin och du måste hårdkoda din 
personliga xxx-ats.iot... URL i frontend-koden.	
(fördelar med Lambda:)  kan hämta endpointen automatiskt via SDK eller miljövariabel.
Säkerhet (IAM)	Användarens webbläsare får direkt behörighet att ändra IoT Shadows.	Bara Lambda-funktionen har IoT-behörighet; användaren får bara anropa funktionen.


