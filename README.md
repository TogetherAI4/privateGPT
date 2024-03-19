# 🔒 PrivateGPT 📑

[![Tests](https://github.com/imartinez/privateGPT/actions/workflows/tests.yml/badge.svg)](https://github.com/imartinez/privateGPT/actions/workflows/tests.yml?query=branch%3Amain)
[![Website](https://img.shields.io/website?up_message=check%20it&down_message=down&url=https%3A%2F%2Fdocs.privategpt.dev%2F&label=Dokumentation)](https://docs.privategpt.dev/)

[![Discord](https://img.shields.io/discord/1164200432894234644?logo=discord&label=PrivateGPT)](https://discord.gg/bK6mRVpErU)
[![X (ehemals Twitter) Folgen](https://img.shields.io/twitter/follow/ZylonPrivateGPT)](https://twitter.com/ZylonPrivateGPT)


> Installations- & Nutzungsanleitungen: https://docs.privategpt.dev/
> 
> Tritt der Community bei: [Twitter](https://twitter.com/PrivateGPT_AI) & [Discord](https://discord.gg/bK6mRVpErU)

![Gradio UI](/fern/docs/assets/ui.png?raw=true)

PrivateGPT ist ein produktionsbereites KI-Projekt, das es Ihnen ermöglicht, Fragen zu Ihren Dokumenten mithilfe von Large Language Models (LLMs) zu stellen, auch in Szenarien ohne Internetverbindung. 100 % privat, keine Daten verlassen Ihre Ausführungsumgebung zu irgendeinem Zeitpunkt.

Das Projekt bietet eine API an, die alle primitives bereitstellt, die zum Erstellen privater, kontextbewusster KI-Anwendungen erforderlich sind. Es folgt und erweitert den [OpenAI API-Standard](https://openai.com/blog/openai-api) und unterstützt sowohl normale als auch Streaming-Antworten.

Die API ist in zwei logische Blöcke unterteilt:

**Hochrangige API**, die alle Komplexität einer RAG (Retrieval Augmented Generation) Pipeline-Implementierung abstrahiert:
- Aufnahme von Dokumenten: Internes Management von Dokumentenparsen, Aufteilen, Metadatenextraktion, Einbettungsgenerierung und Speicherung.
- Chat & Vervollständigungen unter Verwendung von Kontext aus aufgenommenen Dokumenten: Abstrahierung der Abfrage des Kontexts, der Anregungsentwicklung und der Antwortgenerierung.

**Niedrigrangige API**, die es fortgeschrittenen Benutzern ermöglicht, ihre eigenen komplexen Pipelines zu implementieren:
- Einbettungsgenerierung: basierend auf einem Textstück.
- Kontextbezogene Chunk-Abfrage: Gibt eine Abfrage zurück und gibt die relevantesten Textstücke aus den aufgenommenen Dokumenten zurück.

Zusätzlich dazu wird ein funktionierender [Gradio UI](https://www.gradio.app/) Client bereitgestellt, um die API zu testen, zusammen mit einer Reihe nützlicher Tools wie Skript zum Massenmodell-Download, Skript zur Aufnahme, Überwachung des Dokumentenordners usw.

> 👂 **Brauchen Sie Hilfe bei der Anwendung von PrivateGPT für Ihren spezifischen Anwendungsfall?**
> [Lassen Sie es uns wissen](https://forms.gle/4cSDmH13RZBHV9at7)
> und wir werden versuchen zu helfen! Wir verbessern PrivateGPT durch Ihr Feedback.

## 🎞️ Überblick
HAFTUNGSAUSSCHLUSS: Dieses README wird nicht so häufig aktualisiert wie die [Dokumentation](https://docs.privategpt.dev/).
Bitte schauen Sie dort für die neuesten Updates nach!

### Motivation hinter PrivateGPT
Generative KI ist ein Game Changer für unsere Gesellschaft, aber die Akzeptanz in Unternehmen aller Größen und datensensiblen Bereichen wie Gesundheitswesen oder Recht ist durch eine klare Sorge begrenzt: **Privatsphäre**.
Die Unfähigkeit, sicherzustellen, dass Ihre Daten vollständig unter Ihrer Kontrolle stehen, wenn Sie KI-Tools von Drittanbietern verwenden, ist ein Risiko, das sich diese Branchen nicht leisten können.

### Urversion
Die erste Version von PrivateGPT wurde im Mai 2023 als neuartiger Ansatz zur Bewältigung der Datenschutzbedenken durch die Verwendung von LLMs auf eine vollständig offline Art und Weise eingeführt.

Diese Version, die schnell zu einem Standardprojekt für datenschutzsensible Setups wurde und als Keim für tausende lokal fokussierte generative KI-Projekte diente, war die Grundlage dessen, was PrivateGPT heute wird; daher eine einfachere und lehrreichere Implementierung, um die grundlegenden Konzepte zu verstehen, die erforderlich sind, um ein vollständig lokales - und daher privates - ChatGPT-ähnliches Tool zu erstellen.

Wenn Sie weiterhin damit experimentieren möchten, haben wir es im [Urversion-Zweig](https://github.com/imartinez/privateGPT/tree/primordial) des Projekts gespeichert.

> Es wird dringend empfohlen, eine saubere Kopie anzufertigen und diese neue Version von
PrivateGPT zu installieren, wenn Sie von der vorherigen, urzeitlichen Version kommen.

### Gegenwart und Zukunft von PrivateGPT
PrivateGPT entwickelt sich jetzt zu einem Gateway für generative KI-Modelle und primitives, einschließlich
Vervollständigungen, Dokumentenaufnahme, RAG-Pipelines und anderen niedrigschwelligen Bausteinen.
Wir möchten es jedem Entwickler erleichtern, KI-Anwendungen und -Erfahrungen zu erstellen, sowie eine geeignete umfangreiche Architektur für die Community bereitzustellen, um weiter beizutragen.

Bleiben Sie auf unsere [Veröffentlichungen](https://github.com/imartinez/privateGPT/releases) gespannt, um alle neuen Funktionen und Änderungen zu sehen.

## 📄 Dokumentation
Die vollständige Dokumentation zur Installation, Abhängigkeiten, Konfiguration, Ausführung des Servers, Bereitstellungsoptionen,
Aufnahme lokaler Dokumente, API-Details und UI-Funktionen finden Sie hier: https://docs.privategpt.dev/

## 🧩 Architektur
Konzeptionell ist PrivateGPT eine API, die eine RAG-Pipeline umhüllt und ihre
Primitives freilegt.
* Die API wurde unter Verwendung von [FastAPI](https://fastapi.tiangolo.com/) erstellt und folgt
 

 dem [API-Schema von OpenAI](https://platform.openai.com/docs/api-reference).
* Die RAG-Pipeline basiert auf [LlamaIndex](https://www.llamaindex.ai/).

Das Design von PrivateGPT ermöglicht es, sowohl die API als auch die
RAG-Implementierung einfach zu erweitern und anzupassen. Einige wichtige architektonische Entscheidungen sind:
* Dependency Injection, Entkopplung der verschiedenen Komponenten und Schichten.
* Verwendung von LlamaIndex-Abstraktionen wie `LLM`, `BaseEmbedding` oder `VectorStore`,
  was es sofort ermöglicht, die tatsächlichen Implementierungen dieser Abstraktionen zu ändern.
* Einfachheit, Hinzufügen so weniger Schichten und neuer Abstraktionen wie möglich.
* Einsatzbereit, Bereitstellung einer vollständigen Implementierung der API und RAG
  Pipeline.

Hauptbausteine:
* APIs sind in `private_gpt:server:<api>` definiert. Jedes Paket enthält einen
  `<api>_router.py` (FastAPI-Schicht) und einen `<api>_service.py` (die
  Dienstimplementierung). Jeder *Service* verwendet LlamaIndex-Basisabstraktionen anstelle von spezifischen Implementierungen,
  Entkopplung der tatsächlichen Implementierung von ihrer Verwendung.
* Komponenten sind in
  `private_gpt:components:<component>` platziert. Jede *Komponente* ist dafür verantwortlich,
  tatsächliche Implementierungen für die Basenabstraktionen bereitzustellen, die in den Services verwendet werden - zum Beispiel
  `LLMComponent` ist dafür verantwortlich, eine tatsächliche Implementierung eines `LLM` bereitzustellen
  (zum Beispiel `LlamaCPP` oder `OpenAI`).

## 💡 Mitarbeit
Beiträge sind willkommen! Um die Codequalität zu gewährleisten, haben wir mehrere Format- und
Typenprüfungen aktiviert. Führen Sie einfach `make check` aus, bevor Sie Änderungen commiten, um sicherzustellen, dass Ihr Code in Ordnung ist.
Vergessen Sie nicht, Ihren Code zu testen! Sie finden einen Testsordner mit Hilfsprogrammen, und Sie können
Tests mit dem Befehl `make test` ausführen.

Sie wissen nicht, was Sie beitragen sollen? Hier ist das öffentliche
[Projektboard](https://github.com/users/imartinez/projects/3) mit verschiedenen Ideen.

Gehen Sie zum Discord-Kanal
#contributors und bitten Sie um Schreibberechtigungen für dieses GitHub-Projekt.

## 💬 Community
Treten Sie der Diskussion rund um PrivateGPT bei auf:
- [Twitter (aka X)](https://twitter.com/PrivateGPT_AI)
- [Discord](https://discord.gg/bK6mRVpErU)

## 📖 Zitierung
Wenn Sie PrivateGPT in einem Paper verwenden, schauen Sie sich die [Zitationsdatei](CITATION.cff) für die korrekte Zitierung an.  
Sie können auch die Schaltfläche "Dieses Repository zitieren" in diesem Repository verwenden, um die Zitierung in verschiedenen Formaten zu erhalten.

Hier sind ein paar Beispiele:

#### BibTeX
```bibtex
@software{Martinez_Toro_PrivateGPT_2023,
author = {Martínez Toro, Iván and Gallego Vico, Daniel and Orgaz, Pablo},
license = {Apache-2.0},
month = may,
title = {{PrivateGPT}},
url = {https://github.com/imartinez/privateGPT},
year = {2023}
}
```

#### APA
```
Martínez Toro, I., Gallego Vico, D., & Orgaz, P. (2023). PrivateGPT [Computer software]. https://github.com/imartinez/privateGPT
```

## 🤗 Partner & Unterstützer
PrivateGPT wird aktiv unterstützt von den Teams hinter:
* [Qdrant](https://qdrant.tech/), Bereitstellung der Standard-Vektordatenbank
* [Fern](https://buildwithfern.com/), Bereitstellung von Dokumentation und SDKs
* [LlamaIndex](https://www.llamaindex.ai/), Bereitstellung des Basissystems und der Abstraktionen für RAG

Dieses Projekt wurde stark von anderen erstaunlichen Projekten beeinflusst und unterstützt wie
[LangChain](https://github.com/hwchase17/langchain),
[GPT4All](https://github.com/nomic-ai/gpt4all),
[LlamaCpp](https://github.com/ggerganov/llama.cpp),
[Chroma](https://www.trychroma.com/)
und [SentenceTransformers](https://www.sbert.net/).
