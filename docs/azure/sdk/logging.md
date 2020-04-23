---
title: Rejestrowanie przy użyciu zestawu Azure SDK dla platformy .NET
description: Dowiedz się, jak włączyć rejestrowanie przy użyciu bibliotek klienckich platformy Azure SDK dla platformy .NET
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071991"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="be1a2-103">Rejestrowanie przy użyciu zestawu Azure SDK dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="be1a2-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="be1a2-104">Biblioteki klienckie [zestawu Azure SDK](https://azure.microsoft.com/downloads/) dla platformy .NET obejmują możliwość rejestrowania operacji biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="be1a2-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="be1a2-105">Pozwala to monitorować żądania we/wy i odpowiedzi, które biblioteki klienckie wprowadzają do usług platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="be1a2-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="be1a2-106">Zazwyczaj dzienniki są używane do debugowania lub diagnozowania problemów z komunikacją.</span><span class="sxs-lookup"><span data-stu-id="be1a2-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="be1a2-107">W tym artykule opisano trzy podejścia do włączania rejestrowania za pomocą zestawu Azure SDK dla platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="be1a2-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="be1a2-108">Logowanie do okna konsoli</span><span class="sxs-lookup"><span data-stu-id="be1a2-108">Log to the console window</span></span>
- <span data-ttu-id="be1a2-109">Rejestruj w śladach diagnostyki .NET</span><span class="sxs-lookup"><span data-stu-id="be1a2-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="be1a2-110">Konfigurowanie rejestrowania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="be1a2-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be1a2-111">Ten artykuł dotyczy bibliotek klienckich, które korzystają z najnowszych wersji zestawu Azure SDK dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="be1a2-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="be1a2-112">Aby sprawdzić, czy biblioteka jest obsługiwana, zapoznaj się z listą [najnowszych wersji zestawu Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="be1a2-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="be1a2-113">Jeśli aplikacja używa starszej wersji bibliotek klienckich zestawu Azure SDK, zapoznaj się z określonymi instrukcjami w odpowiedniej dokumentacji usługi.</span><span class="sxs-lookup"><span data-stu-id="be1a2-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="be1a2-114">Informacje dziennika</span><span class="sxs-lookup"><span data-stu-id="be1a2-114">Log information</span></span>

<span data-ttu-id="be1a2-115">Zestaw SDK rejestruje następujące informacje, oczyszczanie zapytania parametrycznego i wartości nagłówka, aby usunąć dane osobowe.</span><span class="sxs-lookup"><span data-stu-id="be1a2-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="be1a2-116">Wpis dziennika żądania HTTP:</span><span class="sxs-lookup"><span data-stu-id="be1a2-116">HTTP request log entry:</span></span>

- <span data-ttu-id="be1a2-117">Unikatowy identyfikator</span><span class="sxs-lookup"><span data-stu-id="be1a2-117">Unique ID</span></span>
- <span data-ttu-id="be1a2-118">Metoda HTTP</span><span class="sxs-lookup"><span data-stu-id="be1a2-118">HTTP method</span></span>
- <span data-ttu-id="be1a2-119">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="be1a2-119">URI</span></span>
- <span data-ttu-id="be1a2-120">Wychodzące nagłówki żądań</span><span class="sxs-lookup"><span data-stu-id="be1a2-120">Outgoing request headers</span></span>

<span data-ttu-id="be1a2-121">Wpis dziennika odpowiedzi HTTP:</span><span class="sxs-lookup"><span data-stu-id="be1a2-121">HTTP response log entry:</span></span>

- <span data-ttu-id="be1a2-122">Czas trwania operacji we/wy (czas, który upłynął)</span><span class="sxs-lookup"><span data-stu-id="be1a2-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="be1a2-123">Identyfikator żądania</span><span class="sxs-lookup"><span data-stu-id="be1a2-123">Request ID</span></span>
- <span data-ttu-id="be1a2-124">Kod stanu HTTP</span><span class="sxs-lookup"><span data-stu-id="be1a2-124">HTTP status code</span></span>
- <span data-ttu-id="be1a2-125">Fraza przyczyny HTTP</span><span class="sxs-lookup"><span data-stu-id="be1a2-125">HTTP reason phrase</span></span>
- <span data-ttu-id="be1a2-126">Nagłówki odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="be1a2-126">Response headers</span></span>
- <span data-ttu-id="be1a2-127">Informacje o błędzie, jeśli ma zastosowanie</span><span class="sxs-lookup"><span data-stu-id="be1a2-127">Error information, when applicable</span></span>

<span data-ttu-id="be1a2-128">W przypadku zawartości żądania i odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="be1a2-128">For request and response content:</span></span>

- <span data-ttu-id="be1a2-129">Strumień zawartości jako tekst lub bajty w zależności od nagłówka Content-Type.</span><span class="sxs-lookup"><span data-stu-id="be1a2-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="be1a2-130">[! Uwaga} rejestrowanie zawartości jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="be1a2-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="be1a2-131">Aby ją włączyć, ustaw `Diagnostics.IsLoggingContentEnabled` wartość `true` w `ClientOptions`.</span><span class="sxs-lookup"><span data-stu-id="be1a2-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="be1a2-132">Dzienniki zdarzeń są zwykle na jednym z trzech poziomów:</span><span class="sxs-lookup"><span data-stu-id="be1a2-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="be1a2-133">Informacje o zdarzeniach żądania i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="be1a2-133">Informational for request and response events</span></span>
- <span data-ttu-id="be1a2-134">Ostrzeżenie o błędach</span><span class="sxs-lookup"><span data-stu-id="be1a2-134">Warning for errors</span></span>
- <span data-ttu-id="be1a2-135">Pełne informacje szczegółowe dotyczące komunikatów i rejestrowania zawartości</span><span class="sxs-lookup"><span data-stu-id="be1a2-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="be1a2-136">Włączanie rejestrowania za pomocą wbudowanych metod</span><span class="sxs-lookup"><span data-stu-id="be1a2-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="be1a2-137">Biblioteki klienckie zestawu Azure SDK dla platformy .NET rejestrują zdarzenia do śledzenia zdarzeń systemu Windows (ETW) za pośrednictwem [ `EventSource` klasy](/dotnet/api/system.diagnostics.tracing.eventsource), która jest typowa dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="be1a2-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="be1a2-138">Źródła zdarzeń umożliwiają używanie rejestrowania strukturalnego w kodzie aplikacji z minimalnym obciążeniem wydajności.</span><span class="sxs-lookup"><span data-stu-id="be1a2-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="be1a2-139">Aby uzyskać dostęp do tych dzienników zdarzeń, należy zarejestrować detektory zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="be1a2-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="be1a2-140">Zestaw SDK zawiera `Azure.Core.Diagnostics.AzureEventSourceListener` klasę (zdefiniowaną w pakiecie NuGet Azure. Core), która zawiera dwie metody statyczne, które upraszczają kompleksowe rejestrowanie dla aplikacji .NET: `CreateConsoleLogger` i `CreateTraceLogger`.</span><span class="sxs-lookup"><span data-stu-id="be1a2-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="be1a2-141">Te metody przyjmują opcjonalny parametr, który określa poziom rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="be1a2-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="be1a2-142">Logowanie do okna konsoli</span><span class="sxs-lookup"><span data-stu-id="be1a2-142">Log to the console window</span></span>

<span data-ttu-id="be1a2-143">Podstawowym cechą bibliotek klienckich platformy Azure SDK dla platformy .NET jest uproszczenie możliwości wyświetlania obszernych dzienników w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="be1a2-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="be1a2-144">`CreateConsoleLogger` Metoda umożliwia wysyłanie dzienników do okna konsoli z pojedynczym wierszem kodu:</span><span class="sxs-lookup"><span data-stu-id="be1a2-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="be1a2-145">Rejestruj do śladów diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="be1a2-145">Log to diagnostic traces</span></span>

<span data-ttu-id="be1a2-146">W przypadku implementacji detektorów śledzenia można użyć `CreateTraceLogger` metody, aby zalogować się do standardowego mechanizmu śledzenia zdarzeń .NET ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span><span class="sxs-lookup"><span data-stu-id="be1a2-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="be1a2-147">Aby uzyskać więcej informacji na temat śledzenia zdarzeń w programie .NET, zobacz [detektory śledzenia](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span><span class="sxs-lookup"><span data-stu-id="be1a2-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="be1a2-148">Ten przykład określa poziom dziennika pełny:</span><span class="sxs-lookup"><span data-stu-id="be1a2-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="be1a2-149">Konfigurowanie rejestrowania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="be1a2-149">Configure custom logging</span></span>

<span data-ttu-id="be1a2-150">Jak wspomniano powyżej, należy zarejestrować detektory zdarzeń do odbierania komunikatów dziennika z zestawu Azure SDK dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="be1a2-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="be1a2-151">Jeśli nie chcesz zaimplementować kompleksowego rejestrowania przy użyciu jednej z tych metod uproszczonych, możesz skonstruować wystąpienie `AzureEventSourceListener` klasy i przekazać ją do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="be1a2-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="be1a2-152">Ta metoda będzie odbierać komunikaty dziennika, które można przetworzyć, ale jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="be1a2-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="be1a2-153">Ponadto podczas konstruowania wystąpienia można określić poziomy dziennika do uwzględnienia.</span><span class="sxs-lookup"><span data-stu-id="be1a2-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="be1a2-154">Poniższy przykład tworzy odbiornik zdarzeń, który loguje się do konsoli z niestandardowym komunikatem, i jest filtrowany do zdarzeń Azure Core na poziomie pełne.</span><span class="sxs-lookup"><span data-stu-id="be1a2-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a><span data-ttu-id="be1a2-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="be1a2-155">Next steps</span></span>

- [<span data-ttu-id="be1a2-156">Włączanie rejestrowania diagnostycznego dla aplikacji w Azure App Service</span><span class="sxs-lookup"><span data-stu-id="be1a2-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="be1a2-157">Przejrzyj opcje [rejestrowania i inspekcji zabezpieczeń platformy Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="be1a2-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="be1a2-158">Dowiedz się, jak korzystać z [dzienników platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="be1a2-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="be1a2-159">Przeczytaj więcej na temat [rejestrowania i śledzenia w programie .NET Core](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="be1a2-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
