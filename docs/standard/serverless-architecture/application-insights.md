---
title: Application Insights — aplikacje niekorzystające z serwera
description: Application Insights to platforma diagnostyki bez użycia serwera, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacji sieci web, aplikacje mobilne, aplikacje klasyczne i mikrousług.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4884d483de07c1c2077f7280b6b77c6059572c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051233"
---
# <a name="telemetry-with-application-insights"></a>Dane telemetryczne za pomocą usługi Application Insights

[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights) to platforma bezserwerowa diagnostyki, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacji sieci web, aplikacje mobilne, aplikacje klasyczne i mikrousług. Można włączyć usługi Application Insights dla aplikacji funkcji po prostu, przestawiając przełącznik w portalu. Application Insights udostępnia wszystkie te możliwości bez konieczności konfigurowania serwera lub utworzyć własną bazę danych. Wszystkie funkcje usługi Application Insights są dostarczane jako usługa, która automatycznie integruje się z aplikacjami.

![Application Insights logo](./media/application-insights-logo.png)

Dodawanie usługi Application Insights do istniejących aplikacji jest bardzo proste — wystarczy dodanie klucza Instrumentacji do ustawień aplikacji. Za pomocą usługi Application Insights można wykonywać następujące czynności:

* Tworzenie wykresów niestandardowych i alerty na podstawie metryk, takich jak liczba wywołań funkcji, to czas do uruchomienia funkcji i wyjątków
* Analizowanie błędów i wyjątków serwera
* Dogłębne analizowanie wydajności przez operację i do pomiaru czasu potrzebnego do wywołania zależności innych firm
* Monitorowanie użycia procesora CPU, pamięci i kursów na wszystkich serwerach obsługujących Twoje aplikacje funkcji
* Wyświetl strumienia na żywo z metryk, takich jak liczby żądań i opóźnień dla aplikacji funkcji
* Użyj [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) do wyszukiwania, wykonywania kwerend i tworzenie wykresów niestandardowych danych — funkcja

![Eksplorator metryk](./media/metrics-explorer.png)

Oprócz wbudowanych telemetrii istnieje również możliwość generowania niestandardowych danych telemetrycznych. Poniższy fragment kodu tworzy niestandardową telemetrię klienta przy użyciu klucza instrumentacji dla aplikacji funkcji:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Poniższy kod mierzy, jak długo trwa wstawić nowy wiersz do [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) wystąpienie:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Wynikowy Wykres wydajności jest wyświetlany:

![Telemetria niestandardowa](./media/custom-telemetry.png)

Niestandardowych danych telemetrycznych wykazuje, że średni czas, aby wstawić nowy wiersz jest 32.6 milisekund.

Application Insights zapewnia zaawansowane i wygodny sposób logowania szczegółowe dane telemetryczne dotyczące Twojej aplikacji bez użycia serwera. Masz pełną kontrolę nad poziomem śledzenia i rejestrowania, które jest dostępne. Możliwe jest śledzenie niestandardowych statystyk, takich jak zdarzenia, zależności i widoku strony. Na koniec zaawansowane analizy umożliwiają pisanie zapytań, które są ważne pytania oraz generować wykresy i zaawansowane szczegółowe informacje.

Aby uzyskać więcej informacji, zobacz [monitora usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Poprzednie](azure-functions.md)
>[dalej](logic-apps.md)