# .env 

Umgebungsvariablen sind Variablen, die "global" für die Umgebung sind, in der der Code ausgeführt wird

Da sie auf die Umgebung beschränkt sind, sind sie überall im Code verfügbar.

Sie müssen weder importiert werden, noch musst du einen Verweis auf sie erstellen


## Warum sollten wir Umgebungsvariablen verwenden?

Das ist nicht gut! 😮

##### app.js

```javascript
const data = fetch("https://somewebsite.com/getData?secret_api_key=1234567xxx");
```

> Frage:
> Warum ist das nicht gut?

---

> Antwort:

- Eine Menge Arbeit, diese Werte zu ändern, wenn wir sie an mehreren Stellen verwenden
- Außerdem wollen wir keine privaten Daten, Geheimcodes, API-Schlüssel oder Passwörter in unserem Git-Repository speichern.

## Wie kann process.env uns bei privaten Daten helfen?

Wir können unsere eigenen Schlüssel und Werte zu "process.env" hinzufügen, genau wie bei normalen Objekten

Wenn wir der Variable `process.env` Werte hinzufügen können, haben wir eine Möglichkeit, die Werte vor unserem Git-Repository "geheim" zu halten

server.js
```javascript
process.env.SECRET_API_KEY = "1234567xxx";
console.log(process.env.SECRET_API_KEY); // "1234567xxx"

const data = fetch(
  `https://somewebsite.com/getData?secret_api_key=${process.env.SECRET_API_KEY}`
);
```

Anmerkungen:

Immer noch nicht gut genug, warum?

---

- Wir brauchen eine bessere Lösung

- Wir werden den geheimen Schlüssel in einer separaten Datei speichern

- Die Datei "process.env" wird uns helfen (ist aber nicht die endgültige Lösung)