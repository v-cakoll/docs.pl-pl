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
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="9260e-103">Telemetria za pomocą usługi Application Insights</span><span class="sxs-lookup"><span data-stu-id="9260e-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="9260e-104">[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights) to bezserwerowa platforma diagnostyczna, która umożliwia deweloperom wykrywanie, klasyfikowanie i diagnozowanie problemów w aplikacjach sieci Web, aplikacjach mobilnych, aplikacjach klasycznych i mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="9260e-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="9260e-105">Usługi Application Insights można włączyć w aplikacjach funkcyjnych, przerzucając przełącznik w portalu.</span><span class="sxs-lookup"><span data-stu-id="9260e-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="9260e-106">Usługa Application Insights udostępnia wszystkie te możliwości bez konieczności konfigurowania serwera lub konfigurowania własnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9260e-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="9260e-107">Wszystkie funkcje usługi Application Insights są dostarczane jako usługa, która automatycznie integruje się z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="9260e-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logo Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="9260e-109">Dodawanie aplikacji Insights do istniejących aplikacji jest tak proste, jak dodanie klucza instrumentacji do ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9260e-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="9260e-110">Dzięki aplikacji Application Insights możesz:</span><span class="sxs-lookup"><span data-stu-id="9260e-110">With Application Insights you can:</span></span>

- <span data-ttu-id="9260e-111">Tworzenie niestandardowych wykresów i alertów na podstawie metryk, takich jak liczba wywołań funkcji, czas potrzebny do uruchomienia funkcji i wyjątki</span><span class="sxs-lookup"><span data-stu-id="9260e-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="9260e-112">Analizowanie błędów i wyjątków serwera</span><span class="sxs-lookup"><span data-stu-id="9260e-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="9260e-113">Przechodzenie do wydajności według operacji i mierzenie czasu potrzebnego do wywołania zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="9260e-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="9260e-114">Monitorowanie użycia procesora, pamięci i szybkości na wszystkich serwerach hostujący aplikacje funkcji</span><span class="sxs-lookup"><span data-stu-id="9260e-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="9260e-115">Wyświetlanie transmisji na żywo danych, w tym liczby żądań i opóźnień dla aplikacji funkcyjnych</span><span class="sxs-lookup"><span data-stu-id="9260e-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="9260e-116">Używanie [analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) do wyszukiwania, wykonywania zapytań i tworzenia niestandardowych wykresów nad danymi funkcji</span><span class="sxs-lookup"><span data-stu-id="9260e-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Eksplorator metryk](./media/metrics-explorer.png)

<span data-ttu-id="9260e-118">Oprócz wbudowanej telemetrii można również wygenerować niestandardową telemetrię.</span><span class="sxs-lookup"><span data-stu-id="9260e-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="9260e-119">Poniższy fragment kodu tworzy niestandardowego klienta telemetrii przy użyciu zestawu kluczy instrumentacji dla aplikacji funkcji:</span><span class="sxs-lookup"><span data-stu-id="9260e-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="9260e-120">Poniższy kod mierzy, jak długo trwa wstawianie nowego wiersza do wystąpienia [usługi Azure Table Storage:](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="9260e-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="9260e-121">Wynikowy wykres wydajności jest pokazany:</span><span class="sxs-lookup"><span data-stu-id="9260e-121">The resulting performance graph is shown:</span></span>

![Telemetria niestandardowa](./media/custom-telemetry.png)

<span data-ttu-id="9260e-123">Niestandardowa telemetria ujawnia średni czas wstawiania nowego wiersza wynosi 32,6 milisekund.</span><span class="sxs-lookup"><span data-stu-id="9260e-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="9260e-124">Usługa Application Insights zapewnia zaawansowany i wygodny sposób rejestrowania szczegółowych danych telemetrycznych dotyczących aplikacji bezserwerowych.</span><span class="sxs-lookup"><span data-stu-id="9260e-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="9260e-125">Masz pełną kontrolę nad poziomem śledzenia i rejestrowania, który jest podany.</span><span class="sxs-lookup"><span data-stu-id="9260e-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="9260e-126">Można śledzić statystyki niestandardowe, takie jak zdarzenia, zależności i widok strony.</span><span class="sxs-lookup"><span data-stu-id="9260e-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="9260e-127">Na koniec zaawansowana analiza umożliwia pisanie zapytań, które zadają ważne pytania i generują wykresy i zaawansowane szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="9260e-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="9260e-128">Aby uzyskać więcej informacji, zobacz [Monitorowanie funkcji platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="9260e-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9260e-129">[Poprzedni](azure-functions.md)
>[następny](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="9260e-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
