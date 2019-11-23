---
title: Zarządzanie wydajnością aplikacji — gRPC dla deweloperów WCF
description: Rejestrowanie, metryki i śledzenie dla ASP.NET Core aplikacji gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 2b6a30ab68cb6e2fdc81c59e7faef81064b948c1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968180"
---
# <a name="application-performance-management"></a>Zarządzanie wydajnością aplikacji

W nowoczesnych środowiskach produkcyjnych, takich jak Kubernetes, bardzo ważne jest, aby monitorować aplikacje w celu zapewnienia optymalnego działania. Problemy, takie jak rejestrowanie i metryki, nigdy nie były ważniejsze. ASP.NET Core, w tym gRPC, ma wbudowaną obsługę tworzenia komunikatów dziennika i danych metryk oraz zarządzania nimi, a także *śledzenia* danych. Ta sekcja zawiera szczegółowe informacje dotyczące tych obszarów.

## <a name="logging-vs-metrics"></a>Rejestrowanie metryk a

Przed przejrzeniem szczegółów implementacji należy zrozumieć różnicę między rejestrowaniem i metrykami.

Rejestrowanie jest powiązane z wiadomościami tekstowymi, które rejestrują szczegółowe informacje o elementach, które wystąpiły w systemie. Komunikaty dziennika mogą zawierać dane wyjątku, takie jak ślady stosu, lub dane strukturalne, które udostępniają kontekst o wiadomości. Dane wyjściowe rejestrowania są często zapisywane w magazynie tekstu do przeszukiwania.

Metryki odnoszą się do danych liczbowych, które są przeznaczone do agregowania i przedstawiane za pomocą wykresów i wykresów na pulpicie nawigacyjnym, który zapewnia widok ogólnej kondycji i wydajności aplikacji. Dane metryk mogą być również używane do wyzwalania automatycznych alertów w przypadku przekroczenia progu. Na poniższej liście przedstawiono przykłady danych metryk:

- Czas przetwarzania żądań.
- Liczba żądań na sekundę obsługiwanych przez wystąpienie usługi.
- Liczba żądań zakończonych niepowodzeniem w wystąpieniu.

## <a name="logging-in-aspnet-core-grpc"></a>Logowanie w ASP.NET Core gRPC

ASP.NET Core zapewnia wbudowaną obsługę rejestrowania w postaci pakietu NuGet [Microsoft. Extensions. Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) . Podstawowe części tej biblioteki są dołączone do zestawu SDK sieci Web, więc nie trzeba instalować go ręcznie. Domyślnie komunikaty dziennika są zapisywane w standardowym wyjściu (konsoli) i w dowolnym dołączonym debugerze. Aby pisać dzienniki do trwałych zewnętrznych magazynów danych, może zajść potrzeba zaimportowania [opcjonalnych pakietów ujścia rejestrowania](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers).

ASP.NET Core gRPC Framework zapisuje szczegółowe komunikaty rejestrowania diagnostycznego do tej struktury rejestrowania, dzięki czemu mogą być przetwarzane/przechowywane wraz z własnymi komunikatami aplikacji.

### <a name="produce-log-messages"></a>Generowanie komunikatów dziennika

Rozszerzenie rejestrowania jest automatycznie rejestrowane w systemie ASP.NET Core, aby można było określić rejestratory jako parametr konstruktora dla typów usługi gRPC.

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

Wiele komunikatów dziennika wokół żądań, wyjątków i tak dalej jest udostępnianych przez składniki ASP.NET Core i gRPC Framework. Dodawanie własnych wiadomości dziennika w celu zapewnienia szczegółowych informacji i kontekstu logiki aplikacji, a nie zagadnień niższego poziomu.

Aby uzyskać więcej informacji na temat pisania komunikatów dziennika i dostępnych ujść i elementów docelowych rejestrowania, zobacz artykuł [Rejestrowanie w programie .NET Core i ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) .

## <a name="metrics-in-aspnet-core-grpc"></a>Metryki w ASP.NET Core gRPC

Środowisko uruchomieniowe programu .NET Core udostępnia zestaw składników służących do emitowania i obserwowania metryk, które obejmują interfejsy API, takie jak <xref:System.Diagnostics.Tracing.EventSource> i klasy <xref:System.Diagnostics.Tracing.EventCounter>. Za pomocą tych interfejsów API można emitować podstawowe dane liczbowe, które mogą być używane przez procesy zewnętrzne, takie jak [globalne narzędzie liczników dotnet](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md)lub śledzenie zdarzeń systemu Windows. Aby uzyskać więcej informacji na temat używania `EventCounter` w własnym kodzie, zobacz samouczek [wprowadzenie do EventCounter](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md) .

W przypadku bardziej zaawansowanych metryk i zapisywania danych metryk w szerszym zakresie magazynów danych istnieje doskonały projekt typu "open source" o nazwie [metryki aplikacji](https://www.app-metrics.io). Ten pakiet bibliotek zawiera rozbudowany zestaw typów służący do Instrumentacji kodu. Oferuje również pakiety do zapisywania metryk do różnych rodzajów obiektów docelowych, które obejmują bazy danych szeregów czasowych, takich jak Prometheus i InfluxDB, [Azure Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)i wiele innych. Pakiet NuGet [App. Metrics. AspNetCore. MVC](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) dodatkowo dodaje kompleksowy zestaw podstawowych metryk, które są automatycznie generowane przez integrację z platformą ASP.NET Core, a witryna sieci Web udostępnia [Szablony](https://www.app-metrics.io/samples/grafana/) do wyświetlania tych metryk przy użyciu platformy wizualizacji [Grafana](https://grafana.com/) .

Aby uzyskać więcej informacji i dokumentacji dotyczącej metryk aplikacji, zobacz witrynę sieci Web [App-Metrics.IO](https://app-metrics.io) .

### <a name="produce-metrics"></a>Tworzenie metryk

Większość platform metryk obsługuje pięć podstawowych typów metryk, które opisano w poniższej tabeli:

| Typ metryki | Opis |
| ----------- | ----------- |
| Licznik     | Śledzi, jak często coś się dzieje, takich jak żądania, błędy i tak dalej. |
| Miernik       | Rejestruje pojedynczą wartość, która zmienia się w czasie, na przykład aktywne połączenia. |
| Histogram   | Mierzy rozkład wartości w ramach dowolnych limitów. Na przykład histogram może śledzić rozmiar zestawu danych, zliczać, ile zawiera < 10 rekordów, liczbę 11-100 i 101-1000 i > 1000 rekordów. |
| Wyższy       | Mierzy szybkość, z jaką zdarzenie występuje w różnych przedziałach czasowych. |
| Czasomierz       | Śledzi czas trwania zdarzeń i szybkość ich występowania, przechowywane jako histogram. |

Korzystając z *metryk aplikacji*, interfejs `IMetrics` może zostać uzyskany za pośrednictwem iniekcji zależności i używany do rejestrowania dowolnej z tych metryk dla usługi gRPC. Poniższy przykład pokazuje, jak zliczyć liczbę `Get` żądań wykonywanych w czasie:

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a>Przechowywanie i Wizualizacja danych metryk

Najlepszym sposobem przechowywania danych metryk znajduje się w *bazie danych szeregów czasowych*, wyspecjalizowany magazyn danych przeznaczony do rejestrowania liczbowych serii danych oznaczonych sygnaturami czasowymi. Najpopularniejsze bazy danych to [Prometheus](https://prometheus.io/) i [InfluxDB](https://www.influxdata.com/products/influxdb-overview/). Microsoft Azure udostępnia również dedykowany magazyn metryk za pomocą usługi [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) .

Obecne rozwiązanie do wizualizacji danych metryk to [Grafana](https://grafana.com), które współpracuje z szeroką gamę dostawców magazynu, w tym Azure monitor, InfluxDB i Prometheus. Na poniższej ilustracji przedstawiono przykładowy pulpit nawigacyjny Grafana, w którym są wyświetlane metryki z sieci łączącej usługi z uruchomioną próbą StockData:

![Pulpit nawigacyjny Grafana](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>Alerty oparte na metrykach

Liczbowy charakter danych metryk oznacza, że jest to idealne rozwiązanie w przypadku systemów ostrzegających o alertach, które są przeznaczone dla deweloperów lub inżynierów pomocy technicznej, gdy wartość wykracza poza pewną określoną tolerancję. Już wspomniane platformy zapewniają obsługę alertów za pośrednictwem różnych opcji, w tym wiadomości e-mail, wiadomości SMS lub wizualizacji w pulpicie nawigacyjnym.

## <a name="distributed-tracing"></a>Śledzenie rozproszone

*Śledzenie rozproszone* to stosunkowo niedawne programowanie w zakresie monitorowania, które powstało na podstawie zwiększenia użycia mikrousług i rozproszonych architektur. Pojedyncze żądanie z przeglądarki klienta, aplikacji lub urządzenia mogą być podzielone na wiele kroków i żądań podrzędnych oraz korzystać z wielu usług w sieci. Utrudnia to skorelowanie komunikatów dziennika i metryk z konkretnym żądaniem, które je wywołało. Śledzenie rozproszone stosuje identyfikatory do żądań, które umożliwiają skorelowanie dzienników i metryk z konkretną operacją. Jest to podobne do [kompleksowego śledzenia usługi WCF](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing), ale jest stosowane na wielu platformach.

Mimo że nadal jest obszar technologii Nascent, rozproszone śledzenie szybko się rozwinęło i przechodzą przez proces normalizacji. Natywna platforma obliczeniowa w chmurze stworzyła [model śledzenia Open](https://opentracing.io), próbując udostępnić niezależnym od dostawcy biblioteki do pracy z założeniami, takimi jak [Jaeger](https://www.jaegertracing.io/) i [elastyczny system APM](https://www.elastic.co/products/apm). W tym samym czasie, firma Google utworzyła [projekt OpenCensus](https://opencensus.io/) w celu rozwiązania tego samego zestawu problemów. Te dwa projekty są teraz scalane do nowego projektu, [OpenTelemetry](https://opentelemetry.io), który ma być przyszłym standardem branżowym.

### <a name="how-distributed-tracing-works"></a>Jak działa śledzenie rozproszone

Śledzenie rozproszone opiera się na koncepcji *zakresów*: nazwanych, czasochłonnych operacjach, które są częścią pojedynczego *śledzenia*, co może obejmować przetwarzanie na wielu węzłach systemu. Po zainicjowaniu nowej operacji jest tworzony ślad z unikatowym identyfikatorem. Dla każdej operacji podrzędnej zakres jest tworzony z własnym identyfikatorem i identyfikatorem śledzenia. Gdy żądanie przebiega w systemie, różne składniki mogą tworzyć zakresy *podrzędne* , które zawierają identyfikator ich *elementu nadrzędnego*. Zakres ma *kontekst*, który zawiera identyfikatory śledzenia i zakresu, a także przydatne dane w postaci par klucz/wartość (zwany *bagażem*).

### <a name="distributed-tracing-with-diagnosticsource"></a>Śledzenie rozproszone z DiagnosticSource

Platforma .NET Core ma wewnętrzny moduł, który jest dobrze mapowany do dystrybuowanych śladów i zakresów: [DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide). Jak również zapewnić prostą metodę tworzenia i korzystania z diagnostyki w ramach procesu, moduł `DiagnosticSource` ma koncepcję *działania*, która jest efektywnie implementacją rozproszonego śledzenia lub zakresu w śladzie. Elementy wewnętrzne modułu wykorzystują działania nadrzędne i podrzędne, w tym przydzielanie identyfikatorów. Więcej informacji o używaniu typu `Activity` można znaleźć w [podręczniku użytkownika działania w witrynie GitHub](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)

Ponieważ DiagnosticSource jest częścią podstawowego środowiska, jest obsługiwana przez kilka podstawowych składników, w tym <xref:System.Net.Http.HttpClient>, Entity Framework Core i ASP.NET Core, w tym z jawną obsługą w strukturze gRPC. Gdy ASP.NET Core odbiera żądanie, sprawdza parę nagłówków HTTP zgodnych ze standardem [kontekstu śledzenia W3C](https://www.w3.org/TR/trace-context) . Jeśli nagłówki zostaną znalezione, działanie jest uruchamiane przy użyciu wartości tożsamości i kontekstu z nagłówków. Jeśli nie zostaną znalezione żadne nagłówki, działanie jest uruchamiane z wygenerowanymi wartościami tożsamości, które pasują do formatu standardowego. Wszystkie diagnostyki generowane przez platformę lub przez kod aplikacji w okresie istnienia tego działania mogą być otagowane przy użyciu identyfikatorów śledzenia i zakresu. Pomoc techniczna `HttpClient` rozszerza to więcej, sprawdzając, czy są obecne działania na każdym żądaniu i automatycznie dodając nagłówki śledzenia do żądania wychodzącego.

Biblioteka gRPC klienta i serwera zawiera jawną obsługę DiagnosticSource i działania, a ASP.NET Core także tworzy działania i automatycznie stosuje informacje nagłówka.

> [!NOTE]
> Wszystko to występuje tylko wtedy, gdy *odbiornik* zużywa informacje diagnostyczne. Jeśli nie ma odbiornika, Diagnostyka nie jest zapisywana i żadne działania nie są tworzone.

### <a name="add-your-own-diagnosticsources-and-activities"></a>Dodawanie własnych DiagnosticSources i działań

Mimo że dobra ilość danych jest generowana automatycznie przez ASP.NET Core, w tym gRPC, a także Entity Framework Core i `HttpClient`, można dodać własną diagnostykę lub utworzyć jawne zakresy w kodzie aplikacji. Aby uzyskać szczegółowe informacje na temat implementowania własnej diagnostyki, zapoznaj się z podręcznikiem użytkownika [DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) i [podręcznikiem użytkownika](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage) dotyczącym działania.

### <a name="store-distributed-trace-data"></a>Przechowywanie danych śledzenia rozproszonego

W momencie pisania projektu OpenTelemetry jest nadal na wczesnych etapach i dostępne są tylko pakiety z jakością alfa dla aplikacji .NET. Projekt OpenTracing oferuje bardziej dojrzałe biblioteki, ale zostaną one zastąpione przez biblioteki OpenTelemetry w przyszłości.

Interfejs API OpenTracing został opisany poniżej. Jeśli wolisz używać nowszego interfejsu API OpenTelemetry w aplikacji, zapoznaj się z [repozytorium zestawu SDK platformy .NET OpenTelemetry w witrynie GitHub](https://github.com/open-telemetry/opentelemetry-dotnet).

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>Przechowywanie danych śledzenia rozproszonego przy użyciu pakietu OpenTracing

[Pakiet NuGet OpenTracing](https://www.nuget.org/packages/OpenTracing/) , który obsługuje wszystkie plecze zgodne z OpenTracing (które mogą być używane niezależnie od `DiagnosticSource`). Istnieje dodatkowy pakiet z projektu OpenTracing API [OpenTracing. contrib. Core](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/), który dodaje odbiornik `DiagnosticSource` i automatycznie zapisuje zdarzenia i działania na zapleczu. Włączenie tego pakietu jest proste, ponieważ instalowanie go z narzędzia NuGet i dodawanie go jako usługi w klasie `Startup`.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

Pakiet OpenTracing jest warstwą abstrakcji i w związku z tym wymaga implementacji specyficznej dla zaplecza. Implementacje interfejsu API OpenTracing są dostępne dla następujących zaplecza Open Source.

| Nazwa | Package | Witryna sieci Web |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| Elastyczny system APM | [Elastyczny. APM. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

Aby uzyskać więcej informacji na temat interfejsu API OpenTracing dla platformy .NET, zobacz [OpenTracing for C# ](https://github.com/opentracing/opentracing-csharp) i [OpenTracing C#contrib/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) w witrynie GitHub.

>[!div class="step-by-step"]
>[Poprzedni](load-balancing.md)
>[Następny](appendix.md)
