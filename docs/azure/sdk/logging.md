---
title: Rejestrowanie za pomocą zestawu SDK platformy Azure dla platformy .NET
description: Dowiedz się, jak włączyć rejestrowanie za pomocą narzędzia Azure SDK dla bibliotek klienckich platformy .NET
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
# <a name="logging-with-the-azure-sdk-for-net"></a>Rejestrowanie za pomocą zestawu SDK platformy Azure dla platformy .NET

Zestaw [SDK platformy Azure](https://azure.microsoft.com/downloads/) dla bibliotek klienckich platformy .NET zawiera możliwość rejestrowania operacji biblioteki klienta. Dzięki temu można monitorować żądania we/wy i odpowiedzi, które biblioteki klientów robią do usług platformy Azure. Zazwyczaj dzienniki są używane do debugowania lub diagnozowania problemów z komunikacją. W tym artykule opisano trzy podejścia umożliwiające rejestrowanie za pomocą narzędzia Azure SDK dla platformy .NET:

- Logowanie do okna konsoli
- Rejestrowanie śledzenia diagnostyki platformy .NET
- Konfigurowanie rejestrowania niestandardowego

> [!IMPORTANT]
> Ten artykuł dotyczy bibliotek klienckich, które używają najnowszych wersji zestawu SDK platformy Azure dla platformy .NET. Aby sprawdzić, czy biblioteka jest obsługiwana, zapoznaj się z listą [najnowszych wersji zestawu SDK platformy Azure](https://azure.github.io/azure-sdk/releases/latest/index.html). Jeśli aplikacja używa starszej wersji bibliotek klienta usługi Azure SDK, zapoznaj się z określonymi instrukcjami w odpowiedniej dokumentacji usługi.

## <a name="log-information"></a>Rejestrowanie informacji

Zestaw SDK rejestruje następujące informacje, odkażanie kwerendy parametrycznej i wartości nagłówka w celu usunięcia danych osobowych.

Wpis dziennika żądania HTTP:

- Unikatowy identyfikator
- Metoda HTTP
- Identyfikator URI
- Nagłówki żądań wychodzących

Wpis dziennika odpowiedzi HTTP:

- Czas trwania operacji we/wy (czas, jaki upłynął)
- Identyfikator żądania
- Kod stanu HTTP
- Fraza przyczyny HTTP
- Nagłówki odpowiedzi
- Informacje o błędzie, jeśli ma to zastosowanie

W przypadku treści z prośbą i odpowiedzią:

- Strumień zawartości jako tekst lub bajty w zależności od nagłówka Typ zawartości.
     > [! UWAGA} Rejestrowanie zawartości jest domyślnie wyłączone. Aby ją włączyć, `true` `ClientOptions`ustaw `Diagnostics.IsLoggingContentEnabled` opcję w pliku .

Dzienniki zdarzeń są dane wyjściowe zwykle na jednym z tych trzech poziomów:

- Informacje dotyczące zdarzeń żądania i odpowiedzi
- Ostrzeżenie o błędach
- Szczegółowa szczegółowa treść wiadomości i rejestrowania zawartości

## <a name="enable-logging-with-built-in-methods"></a>Włączanie rejestrowania za pomocą wbudowanych metod

Zestaw Azure SDK dla bibliotek klienckich platformy .NET rejestrowa zdarzenia śledzenia zdarzeń dla systemu Windows (ETW) za pośrednictwem [ `EventSource` klasy,](/dotnet/api/system.diagnostics.tracing.eventsource)która jest typowa dla platformy .NET. Źródła zdarzeń umożliwiają korzystanie z rejestrowania strukturalnego w kodzie aplikacji przy minimalnym obciążeniu wydajności. Aby uzyskać dostęp do tych dzienników zdarzeń, należy zarejestrować detektory zdarzeń.

Zestaw SDK `Azure.Core.Diagnostics.AzureEventSourceListener` zawiera klasę (zdefiniowaną w pakiecie Azure.Core NuGet), która zawiera dwie metody statyczne, które upraszczają kompleksowe rejestrowanie aplikacji .NET: `CreateConsoleLogger` i `CreateTraceLogger`. Metody te przyjmują parametr opcjonalny, który określa poziom dziennika.

### <a name="log-to-the-console-window"></a>Logowanie do okna konsoli

Podstawową zasadą zestawu SDK platformy Azure dla bibliotek klienckich platformy .NET jest uproszczenie możliwości wyświetlania kompleksowych dzienników w czasie rzeczywistym. Metoda `CreateConsoleLogger` umożliwia wysyłanie dzienników do okna konsoli za pomocą jednego wiersza kodu:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Zaloguj się do śledzenia diagnostycznego

Jeśli zaimplementujesz detektory `CreateTraceLogger` śledzenia, można użyć tej metody, aby[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)zalogować się do standardowego mechanizmu śledzenia zdarzeń .NET ( ). Aby uzyskać więcej informacji na temat śledzenia zdarzeń w .NET, zobacz [Śledzenie odbiorników](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners). W tym przykładzie określa poziom dziennika pełne:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Konfigurowanie rejestrowania niestandardowego

Jak wspomniano powyżej, należy zarejestrować detektory zdarzeń, aby odbierać komunikaty dziennika z narzędzia Azure SDK dla platformy .NET. Jeśli nie chcesz zaimplementować kompleksowe rejestrowanie przy użyciu jednej z `AzureEventSourceListener` metod uproszczonych powyżej, można utworzyć wystąpienie klasy i przekazać mu funkcję wywołania zwrotnego, który piszesz. Ta metoda będzie odbierać komunikaty dziennika, które można przetwarzać jednak trzeba. Ponadto podczas konstruowania wystąpienia, można określić poziomy dziennika do uwzględnienia.

Poniższy przykład tworzy detektor zdarzeń, który rejestruje do konsoli z komunikatem niestandardowym i jest filtrowany do zdarzeń podstawowych platformy Azure na poziomie pełne.

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

- [Włączanie rejestrowania diagnostyki dla aplikacji w usłudze Azure App Service](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- Przejrzyj opcje [rejestrowania i inspekcji zabezpieczeń platformy Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)
- Dowiedz się, jak pracować z [dziennikami platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)
- Dowiedz się więcej o [rejestrowaniu i śledzeniu rdzenia .NET](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)
