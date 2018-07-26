---
title: Application Insights — aplikacje niekorzystające z serwera
description: Application Insights to platforma diagnostyki bez użycia serwera, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacji sieci web, aplikacje mobilne, aplikacje klasyczne i mikrousług.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 57b1f70825251c48f720dcd78d094f5e8fb1edb8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404956"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="db11e-103">Dane telemetryczne za pomocą usługi Application Insights</span><span class="sxs-lookup"><span data-stu-id="db11e-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="db11e-104">[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights) to platforma bezserwerowa diagnostyki, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacji sieci web, aplikacje mobilne, aplikacje klasyczne i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="db11e-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="db11e-105">Można włączyć usługi Application Insights dla aplikacji funkcji po prostu, przestawiając przełącznik w portalu.</span><span class="sxs-lookup"><span data-stu-id="db11e-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="db11e-106">Application Insights udostępnia wszystkie te możliwości bez konieczności konfigurowania serwera lub utworzyć własną bazę danych.</span><span class="sxs-lookup"><span data-stu-id="db11e-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="db11e-107">Wszystkie funkcje usługi Application Insights są dostarczane jako usługa, która automatycznie integruje się z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="db11e-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights logo](./media/application-insights-logo.png)

<span data-ttu-id="db11e-109">Dodawanie usługi Application Insights do istniejących aplikacji jest bardzo proste — wystarczy dodanie klucza Instrumentacji do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db11e-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="db11e-110">Za pomocą usługi Application Insights można wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="db11e-110">With Application Insights you can:</span></span>

* <span data-ttu-id="db11e-111">Tworzenie wykresów niestandardowych i alerty na podstawie metryk, takich jak liczba wywołań funkcji, to czas do uruchomienia funkcji i wyjątków</span><span class="sxs-lookup"><span data-stu-id="db11e-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
* <span data-ttu-id="db11e-112">Analizowanie błędów i wyjątków serwera</span><span class="sxs-lookup"><span data-stu-id="db11e-112">Analyze failures and server exceptions</span></span>
* <span data-ttu-id="db11e-113">Dogłębne analizowanie wydajności przez operację i do pomiaru czasu potrzebnego do wywołania zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="db11e-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
* <span data-ttu-id="db11e-114">Monitorowanie użycia procesora CPU, pamięci i kursów na wszystkich serwerach obsługujących Twoje aplikacje funkcji</span><span class="sxs-lookup"><span data-stu-id="db11e-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
* <span data-ttu-id="db11e-115">Wyświetl strumienia na żywo z metryk, takich jak liczby żądań i opóźnień dla aplikacji funkcji</span><span class="sxs-lookup"><span data-stu-id="db11e-115">View a live stream of metrics including request count and latency for your function apps</span></span>
* <span data-ttu-id="db11e-116">Użyj [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) do wyszukiwania, wykonywania kwerend i tworzenie wykresów niestandardowych danych — funkcja</span><span class="sxs-lookup"><span data-stu-id="db11e-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Eksplorator metryk](./media/metrics-explorer.png)

<span data-ttu-id="db11e-118">Oprócz wbudowanych telemetrii istnieje również możliwość generowania niestandardowych danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="db11e-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="db11e-119">Poniższy fragment kodu tworzy niestandardową telemetrię klienta przy użyciu klucza instrumentacji dla aplikacji funkcji:</span><span class="sxs-lookup"><span data-stu-id="db11e-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="db11e-120">Poniższy kod mierzy, jak długo trwa wstawić nowy wiersz do [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="db11e-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="db11e-121">Wynikowy Wykres wydajności jest wyświetlany:</span><span class="sxs-lookup"><span data-stu-id="db11e-121">The resulting performance graph is shown:</span></span>

![Telemetria niestandardowa](./media/custom-telemetry.png)

<span data-ttu-id="db11e-123">Niestandardowych danych telemetrycznych wykazuje, że średni czas, aby wstawić nowy wiersz jest 32.6 milisekund.</span><span class="sxs-lookup"><span data-stu-id="db11e-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="db11e-124">Application Insights zapewnia zaawansowane i wygodny sposób logowania szczegółowe dane telemetryczne dotyczące Twojej aplikacji bez użycia serwera.</span><span class="sxs-lookup"><span data-stu-id="db11e-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="db11e-125">Masz pełną kontrolę nad poziomem śledzenia i rejestrowania, które jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="db11e-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="db11e-126">Możliwe jest śledzenie niestandardowych statystyk, takich jak zdarzenia, zależności i widoku strony.</span><span class="sxs-lookup"><span data-stu-id="db11e-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="db11e-127">Na koniec zaawansowane analizy umożliwiają pisanie zapytań, które są ważne pytania oraz generować wykresy i zaawansowane szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="db11e-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="db11e-128">Aby uzyskać więcej informacji, zobacz [monitora usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="db11e-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="db11e-129">[Poprzednie](azure-functions.md)
[dalej](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="db11e-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>