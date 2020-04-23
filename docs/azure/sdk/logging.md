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
# <a name="logging-with-the-azure-sdk-for-net"></a>Rejestrowanie przy użyciu zestawu Azure SDK dla platformy .NET

Biblioteki klienckie [zestawu Azure SDK](https://azure.microsoft.com/downloads/) dla platformy .NET obejmują możliwość rejestrowania operacji biblioteki klienta. Pozwala to monitorować żądania we/wy i odpowiedzi, które biblioteki klienckie wprowadzają do usług platformy Azure. Zazwyczaj dzienniki są używane do debugowania lub diagnozowania problemów z komunikacją. W tym artykule opisano trzy podejścia do włączania rejestrowania za pomocą zestawu Azure SDK dla platformy .NET:

- Logowanie do okna konsoli
- Rejestruj w śladach diagnostyki .NET
- Konfigurowanie rejestrowania niestandardowego

> [!IMPORTANT]
> Ten artykuł dotyczy bibliotek klienckich, które korzystają z najnowszych wersji zestawu Azure SDK dla platformy .NET. Aby sprawdzić, czy biblioteka jest obsługiwana, zapoznaj się z listą [najnowszych wersji zestawu Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html). Jeśli aplikacja używa starszej wersji bibliotek klienckich zestawu Azure SDK, zapoznaj się z określonymi instrukcjami w odpowiedniej dokumentacji usługi.

## <a name="log-information"></a>Informacje dziennika

Zestaw SDK rejestruje następujące informacje, oczyszczanie zapytania parametrycznego i wartości nagłówka, aby usunąć dane osobowe.

Wpis dziennika żądania HTTP:

- Unikatowy identyfikator
- Metoda HTTP
- Identyfikator URI
- Wychodzące nagłówki żądań

Wpis dziennika odpowiedzi HTTP:

- Czas trwania operacji we/wy (czas, który upłynął)
- Identyfikator żądania
- Kod stanu HTTP
- Fraza przyczyny HTTP
- Nagłówki odpowiedzi
- Informacje o błędzie, jeśli ma zastosowanie

W przypadku zawartości żądania i odpowiedzi:

- Strumień zawartości jako tekst lub bajty w zależności od nagłówka Content-Type.
     > [! Uwaga} rejestrowanie zawartości jest domyślnie wyłączone. Aby ją włączyć, ustaw `Diagnostics.IsLoggingContentEnabled` wartość `true` w `ClientOptions`.

Dzienniki zdarzeń są zwykle na jednym z trzech poziomów:

- Informacje o zdarzeniach żądania i odpowiedzi
- Ostrzeżenie o błędach
- Pełne informacje szczegółowe dotyczące komunikatów i rejestrowania zawartości

## <a name="enable-logging-with-built-in-methods"></a>Włączanie rejestrowania za pomocą wbudowanych metod

Biblioteki klienckie zestawu Azure SDK dla platformy .NET rejestrują zdarzenia do śledzenia zdarzeń systemu Windows (ETW) za pośrednictwem [ `EventSource` klasy](/dotnet/api/system.diagnostics.tracing.eventsource), która jest typowa dla platformy .NET. Źródła zdarzeń umożliwiają używanie rejestrowania strukturalnego w kodzie aplikacji z minimalnym obciążeniem wydajności. Aby uzyskać dostęp do tych dzienników zdarzeń, należy zarejestrować detektory zdarzeń.

Zestaw SDK zawiera `Azure.Core.Diagnostics.AzureEventSourceListener` klasę (zdefiniowaną w pakiecie NuGet Azure. Core), która zawiera dwie metody statyczne, które upraszczają kompleksowe rejestrowanie dla aplikacji .NET: `CreateConsoleLogger` i `CreateTraceLogger`. Te metody przyjmują opcjonalny parametr, który określa poziom rejestrowania.

### <a name="log-to-the-console-window"></a>Logowanie do okna konsoli

Podstawowym cechą bibliotek klienckich platformy Azure SDK dla platformy .NET jest uproszczenie możliwości wyświetlania obszernych dzienników w czasie rzeczywistym. `CreateConsoleLogger` Metoda umożliwia wysyłanie dzienników do okna konsoli z pojedynczym wierszem kodu:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Rejestruj do śladów diagnostycznych

W przypadku implementacji detektorów śledzenia można użyć `CreateTraceLogger` metody, aby zalogować się do standardowego mechanizmu śledzenia zdarzeń .NET ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)). Aby uzyskać więcej informacji na temat śledzenia zdarzeń w programie .NET, zobacz [detektory śledzenia](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners). Ten przykład określa poziom dziennika pełny:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Konfigurowanie rejestrowania niestandardowego

Jak wspomniano powyżej, należy zarejestrować detektory zdarzeń do odbierania komunikatów dziennika z zestawu Azure SDK dla platformy .NET. Jeśli nie chcesz zaimplementować kompleksowego rejestrowania przy użyciu jednej z tych metod uproszczonych, możesz skonstruować wystąpienie `AzureEventSourceListener` klasy i przekazać ją do funkcji wywołania zwrotnego. Ta metoda będzie odbierać komunikaty dziennika, które można przetworzyć, ale jest to konieczne. Ponadto podczas konstruowania wystąpienia można określić poziomy dziennika do uwzględnienia.

Poniższy przykład tworzy odbiornik zdarzeń, który loguje się do konsoli z niestandardowym komunikatem, i jest filtrowany do zdarzeń Azure Core na poziomie pełne.

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

## <a name="next-steps"></a>Następne kroki

- [Włączanie rejestrowania diagnostycznego dla aplikacji w Azure App Service](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- Przejrzyj opcje [rejestrowania i inspekcji zabezpieczeń platformy Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)
- Dowiedz się, jak korzystać z [dzienników platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)
- Przeczytaj więcej na temat [rejestrowania i śledzenia w programie .NET Core](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)
