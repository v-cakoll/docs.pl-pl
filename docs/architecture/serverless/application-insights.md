---
title: Application Insights — aplikacje bezserwerowe
description: Application Insights to platforma diagnostyki bezserwerowej, która pozwala deweloperom wykrywać, klasyfikacja i diagnozować problemy w aplikacjach sieci Web, aplikacjach mobilnych, aplikacjach klasycznych i mikrousługach.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522748"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="085a9-103">Dane telemetryczne z Application Insights</span><span class="sxs-lookup"><span data-stu-id="085a9-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="085a9-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) to platforma diagnostyki bezserwerowej, która pozwala deweloperom wykrywać, klasyfikacja i diagnozować problemy w aplikacjach sieci Web, aplikacjach mobilnych, aplikacjach klasycznych i mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="085a9-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="085a9-105">Application Insights dla aplikacji funkcji można włączyć, przełączając przełącznik w portalu.</span><span class="sxs-lookup"><span data-stu-id="085a9-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="085a9-106">Application Insights zapewnia wszystkie te możliwości bez konieczności konfigurowania serwera ani konfigurowania własnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="085a9-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="085a9-107">Wszystkie możliwości Application Insights "są udostępniane jako usługa, która jest automatycznie integrowana z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="085a9-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logo Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="085a9-109">Dodawanie Application Insights do istniejących aplikacji jest tak proste jak dodanie klucza instrumentacji do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="085a9-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="085a9-110">Za pomocą Application Insights można:</span><span class="sxs-lookup"><span data-stu-id="085a9-110">With Application Insights you can:</span></span>

- <span data-ttu-id="085a9-111">Tworzenie niestandardowych wykresów i alertów na podstawie metryk, takich jak liczba wywołań funkcji, czas potrzebny do uruchomienia funkcji i wyjątków</span><span class="sxs-lookup"><span data-stu-id="085a9-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="085a9-112">Analizowanie błędów i wyjątków serwera</span><span class="sxs-lookup"><span data-stu-id="085a9-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="085a9-113">Przechodzenie do szczegółów wydajności według operacji i mierzenie czasu potrzebnego do wywołania zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="085a9-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="085a9-114">Monitoruj użycie procesora CPU, pamięci i szybkości na wszystkich serwerach, które obsługują aplikacje funkcji</span><span class="sxs-lookup"><span data-stu-id="085a9-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="085a9-115">Wyświetl strumień na żywo metryk, w tym liczbę żądań i czas oczekiwania dla aplikacji funkcji</span><span class="sxs-lookup"><span data-stu-id="085a9-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="085a9-116">Korzystanie z [analizy](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) do wyszukiwania, wykonywania zapytań i tworzenia niestandardowych wykresów za pośrednictwem danych funkcji</span><span class="sxs-lookup"><span data-stu-id="085a9-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Eksplorator metryk](./media/metrics-explorer.png)

<span data-ttu-id="085a9-118">Oprócz wbudowanej telemetrii możliwe jest również generowanie niestandardowych danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="085a9-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="085a9-119">Poniższy fragment kodu tworzy niestandardowego klienta telemetrii przy użyciu zestawu kluczy Instrumentacji dla aplikacji funkcji:</span><span class="sxs-lookup"><span data-stu-id="085a9-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="085a9-120">Poniższy kod mierzy, jak długo trwa wstawianie nowego wiersza do wystąpienia [usługi Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) :</span><span class="sxs-lookup"><span data-stu-id="085a9-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="085a9-121">Zostanie wyświetlony wynikowy Wykres wydajności:</span><span class="sxs-lookup"><span data-stu-id="085a9-121">The resulting performance graph is shown:</span></span>

![Niestandardowa Telemetria](./media/custom-telemetry.png)

<span data-ttu-id="085a9-123">Niestandardowa Telemetria pokazuje średni czas wstawiania nowego wiersza wynosi 32,6 milisekund.</span><span class="sxs-lookup"><span data-stu-id="085a9-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="085a9-124">Application Insights zapewnia zaawansowany i wygodny sposób rejestrowania szczegółowej telemetrii dotyczącej aplikacji bezserwerowych.</span><span class="sxs-lookup"><span data-stu-id="085a9-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="085a9-125">Masz pełną kontrolę nad poziomem śledzenia i udostępnianym rejestrowaniem.</span><span class="sxs-lookup"><span data-stu-id="085a9-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="085a9-126">Można śledzić niestandardowe statystyki, takie jak zdarzenia, zależności i widok strony.</span><span class="sxs-lookup"><span data-stu-id="085a9-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="085a9-127">Dzięki zaawansowanej analizie można napisać zapytania, które zadają ważne pytania i generować wykresy i szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="085a9-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="085a9-128">Aby uzyskać więcej informacji, zobacz [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="085a9-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="085a9-129">[Poprzedni](azure-functions.md)
>[Następny](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="085a9-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
