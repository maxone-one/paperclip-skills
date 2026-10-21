# paperclip-skills

Die globalen Regeln gelten zusätzlich und gehen vor: `~/.claude/CLAUDE.md` und `~/.claude/rules/`. Hier
steht nur, was an diesem Repo anders ist.

## Was dieses Repo ist

**Eine kleine Sammlung von Skills für Paperclip**, den Multi-Agent-Orchestrator (ein Werkzeug, das mehrere
KI-Agenten Aufgaben verteilen lässt). Heute gibt es genau einen Skill, `create-issue`: Er bringt einem
Paperclip-Agenten bei, bei einer Aufgabe selbst ein Issue (einen Aufgabeneintrag) anzulegen und es über die
Paperclip-API dem passenden Teammitglied zuzuweisen. Der einzige Commit ist vom 31.05.2026, das Repo ruht.
Es läuft nirgends, Paperclip importiert die Skills von GitHub (`maxone-one/paperclip-skills`).

## Der Startablauf

1. [README.md](README.md): die einzige Akte, sie beschreibt die Skills und den Import.

Fehlt eine dieser Akten, wird sie beim nächsten Anfassen angelegt (Vorlage für die Übergabe:
`~/Projekte/m1-standards/templates/HANDOFF.md`), und den Sinn jeder Datei pflegt die Datei selbst in ihrem Kopf.
Max' Zettel `~/.claude/NOTIZEN.md` wird bei jedem Start gelesen. Es gibt hier keine Übergabe, keine `BUGS.md`
und keine `IRRTUEMER.md`.

## Eigenheiten und Grenzen

**Das Repo ist öffentlich auf GitHub** (geprüft am 03.10.2026 mit `gh repo view`). Alles, was hier liegt,
auch diese Datei, kann jeder lesen: Kein Zugang, keine Server-Angabe, keine Kundendaten, kein Geheimnis. Ein
Push veröffentlicht Text unter Max' Namen und läuft deshalb vorher durch `slop-check` und braucht seine
Freigabe. Es gibt keinen Workflow in `.github/`, ein Push löst also keinen Deploy aus.

**Der Skill darf keine festen Kennungen tragen.** `skills/create-issue/SKILL.md` löst Teammitglieder
bewusst zur Laufzeit über die API auf (Platzhalter wie `{companyId}` und `{agentToken}`). Dort wird nie eine echte
Firmen-Nummer, Agenten-Nummer oder ein Token eingetragen.

**Offen:** Die `README.md` nennt die Lizenz MIT, eine Lizenzdatei liegt nicht im Repo `[?]`.

**Geschwister:** Die Konfiguration von Paperclip selbst liegt im Repo `paperclip` (mit eigener `CLAUDE.md`),
ein Klon des Programms im Repo `paperclip-de`. Dieses Repo hier enthält nur die Skills.

## Wo was liegt

| Pfad | Inhalt |
|---|---|
| `README.md` | Beschreibung der Skills, Installation per API-Import, Lizenzhinweis |
| `skills/create-issue/SKILL.md` | der Skill: Issue anlegen, Agenten finden, Priorität wählen |
| `.vscode/settings.json` | Editor-Einstellungen |

## Arbeiten in diesem Repo

Es gibt kein Manifest und kein Makefile, also keine Befehle zum Bauen, Testen oder Starten. Ein neuer Skill
bekommt einen Ordner unter `skills/` mit einer `SKILL.md`, und die `README.md` führt ihn unter
"Available skills" auf.

## Rollen: Maker und Enabler (Max, 13.10.2026)

Max wörtlich: „Du bist Maker und Executor, ich bin Enabler.“ **Claude führt jeden Handgriff selbst aus** (aufladen, einrichten, anmelden, klicken, einspielen), Max ermöglicht ihn mit Freigabe, Zugang und Budget. Zurück an Max geht nur, was kein Werkzeug von Claude erreicht, mit dem Beleg des Versuchs. Freigabepflichten bleiben, die Ausführung gehört Claude. Ergänzt Punkt 2 und 3 der globalen CLAUDE.md.
