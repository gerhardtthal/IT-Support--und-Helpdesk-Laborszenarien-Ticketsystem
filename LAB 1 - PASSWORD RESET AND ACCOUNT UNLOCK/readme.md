# Lab 1: Kennwortrücksetzung und Kontenentsperrung

## Ziel
Zurücksetzen eines vergessenen Kennworts für ein Domänenkonto, Entsperren eines gesperrten Active-Directory-Kontos und Erzwingen einer Kennwortänderung bei der nächsten Anmeldung.

## Geschäftsszenario
**Ticket #0042 | Priorität: HOCH**

Ben Tenison (`ben10@mylab.local`) kann sich vor einem wichtigen Meeting nicht anmelden. Mehrere falsche Kennworteingaben haben zu einer Kontosperrung geführt.

## Verwendete Tools

| Komponente | Details |
|---|---|
| Domänencontroller | Windows Server 2022 |
| Client | Windows 11 |
| Domäne | `mylab.local` |
| ADUC | Active Directory-Benutzer und -Computer |
| GPMC | Gruppenrichtlinienverwaltung |
| CMD | `gpupdate /force` |

## Durchgeführte Schritte

### Phase 1 – Testbenutzer erstellen
- Active Directory-Benutzer und -Computer öffnen.
- Benutzer `ben10` erstellen.
- Anfangskennwort festlegen.
- Erstellung bestätigen.

### Phase 2 – Kontosperrungsrichtlinie konfigurieren
- Gruppenrichtlinienverwaltung öffnen.
- Kontosperrungsrichtlinie konfigurieren.
- Schwellenwert: 3 Fehlversuche.
- Sperrdauer: 15 Minuten.
- `gpupdate /force` ausführen.

### Phase 3 – Kontosperrung reproduzieren
- Dreimal mit falschem Kennwort anmelden.
- Kontosperrung bestätigen.

### Phase 4 – Problem beheben
- Benutzer in ADUC suchen.
- Kontosperrung prüfen.
- Kennwort zurücksetzen.
- Konto entsperren.
- Kennwortänderung bei nächster Anmeldung erzwingen.

### Phase 5 – Lösung validieren
- Anmeldung mit temporärem Kennwort.
- Neues Kennwort festlegen.
- Erfolgreiche Anmeldung bestätigen.
