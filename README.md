# Telegram AI Assistant (n8n + Gemini)

Ein persönlicher Assistent, der per Telegram (Text oder Sprachnachricht) bedient wird. Google Gemini erkennt, was ich will, und n8n führt es automatisch aus:

| Anfrage | Aktion |
|---|---|
| Termin ("Friseur morgen um 10") | Eintrag in Google Calendar |
| Notiz | Eintrag in Google Tasks |
| Wecker ("Wecker morgen um 8") | Pushover-Alarm mit Notfall-Priorität und lautem Dauerton |
| Erinnerung | Sofort als Aufgabe in Google Tasks, zur Uhrzeit leiser Pushover-Hinweis |
| Sprachmemo | Wird mit Gemini transkribiert und wie Text verarbeitet |
| Allgemeine Frage | Wird wie bei einem Chatbot beantwortet |

Nach jeder Aktion bestätigt der Bot in Telegram (z. B. "Alles klar, Wecker ist um 8 gestellt").

## Ablauf

Telegram Trigger → Absender-Prüfung (nur ich) → Text oder Sprache? → (Sprache: Datei laden und transkribieren) → Gemini klassifiziert die Nachricht als JSON → Switch nach Typ → Google Calendar / Google Tasks / Wait + Pushover / Chat-Antwort → Telegram-Bestätigung.

## Einrichtung

1. In n8n **Import from File** und `workflow.json` auswählen.
2. Eigene Zugangsdaten anlegen: Telegram Bot, Google Gemini, Google Calendar, Google Tasks, Pushover.
3. Platzhalter ersetzen: `YOUR_TELEGRAM_USER_ID` (nur dieser Nutzer darf den Bot nutzen), `YOUR_PUSHOVER_USER_KEY`, `YOUR_CALENDAR_ID`.
4. Workflow veröffentlichen.

Zugangsdaten und persönliche IDs sind bewusst nicht im Export enthalten.
