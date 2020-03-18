---
title: Usługa Application Insights — aplikacje bezserwerowe
description: Usługa Application Insights to bezserwerowa platforma diagnostyczna, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacjach sieci Web, aplikacjach mobilnych, aplikacjach klasycznych i mikrousługach.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522748"
---
# <a name="telemetry-with-application-insights"></a>Telemetria za pomocą usługi Application Insights

[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights) to bezserwerowa platforma diagnostyczna, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacjach sieci Web, aplikacjach mobilnych, aplikacjach klasycznych i mikrousługach. Usługi Application Insights można włączyć w aplikacjach funkcyjnych, przerzucając przełącznik w portalu. Usługa Application Insights udostępnia wszystkie te możliwości bez konieczności konfigurowania serwera lub konfigurowania własnej bazy danych. Wszystkie funkcje usługi Application Insights są dostarczane jako usługa, która automatycznie integruje się z aplikacjami.

![Logo Application Insights](./media/application-insights-logo.png)

Dodawanie aplikacji Insights do istniejących aplikacji jest tak proste, jak dodanie klucza instrumentacji do ustawień aplikacji. Dzięki aplikacji Application Insights możesz:

- Tworzenie niestandardowych wykresów i alertów na podstawie metryk, takich jak liczba wywołań funkcji, czas potrzebny do uruchomienia funkcji i wyjątki
- Analizowanie błędów i wyjątków serwera
- Przechodzenie do wydajności według operacji i mierzenie czasu potrzebnego do wywołania zależności innych firm
- Monitorowanie użycia procesora, pamięci i szybkości na wszystkich serwerach hostujący aplikacje funkcji
- Wyświetlanie transmisji na żywo danych, w tym liczby żądań i opóźnień dla aplikacji funkcyjnych
- Używanie [analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) do wyszukiwania, wykonywania zapytań i tworzenia niestandardowych wykresów nad danymi funkcji

![Eksplorator metryk](./media/metrics-explorer.png)

Oprócz wbudowanej telemetrii można również wygenerować niestandardową telemetrię. Poniższy fragment kodu tworzy niestandardowego klienta telemetrii przy użyciu zestawu kluczy instrumentacji dla aplikacji funkcji:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Poniższy kod mierzy, jak długo trwa wstawianie nowego wiersza do wystąpienia [usługi Azure Table Storage:](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Wynikowy wykres wydajności jest pokazany:

![Telemetria niestandardowa](./media/custom-telemetry.png)

Niestandardowa telemetria ujawnia średni czas wstawiania nowego wiersza wynosi 32,6 milisekund.

Usługa Application Insights zapewnia zaawansowany i wygodny sposób rejestrowania szczegółowych danych telemetrycznych dotyczących aplikacji bezserwerowych. Masz pełną kontrolę nad poziomem śledzenia i rejestrowania, który jest podany. Można śledzić statystyki niestandardowe, takie jak zdarzenia, zależności i widok strony. Na koniec zaawansowana analiza umożliwia pisanie zapytań, które zadają ważne pytania i generują wykresy i zaawansowane szczegółowe informacje.

Aby uzyskać więcej informacji, zobacz [Monitorowanie funkcji platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Poprzedni](azure-functions.md)
>[następny](logic-apps.md)
