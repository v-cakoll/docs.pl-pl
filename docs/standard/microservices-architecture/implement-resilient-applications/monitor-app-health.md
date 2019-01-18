---
title: Monitorowanie kondycji
description: Zapoznaj się z jednym ze sposobów wdrażania, monitorowania kondycji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362486"
---
# <a name="health-monitoring"></a>Monitorowanie kondycji

Monitorowanie kondycji można zezwolić na niemal w czasie rzeczywistym informacje o stanie mikrousług i kontenerów. Monitorowanie kondycji mają kluczowe znaczenie dla wielu aspektów Obsługa mikrousług i jest szczególnie ważne podczas koordynatorów wykonywania uaktualnień aplikacji częściowej w fazach, zgodnie z opisem w dalszej części.

Aplikacje oparte na Mikrousługach często używają pulsów lub kontroli kondycji, aby umożliwić ich monitory wydajności, harmonogramów i koordynatorów śledzić wiele różnych usług. Jeśli usługi nie może wysłać jakiegoś rodzaju sygnału "Jestem aktywności", na żądanie lub zgodnie z harmonogramem, aplikacja może stoją w obliczu ryzyka podczas wdrażania aktualizacji lub może po prostu za późno wykrywanie błędów i nie można zatrzymać występują kaskadowe awarie, które mogą znaleźć się w głównych awarii.

W typowym modelu usług wysyłać raporty o ich stanie, a te informacje mają charakter do zapewnienia całościowego widoku stanu kondycji aplikacji. Jeśli używasz programu orchestrator można określić informacje o kondycji klastra usługi orchestrator w co klaster może działać w związku z tym. Użytkownik inwestujący w raportowania stanu wysokiej jakości, który jest dostosowany do Twojej aplikacji, można wykryć i znacznie łatwiejsze Rozwiązywanie problemów dla uruchomionej aplikacji.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Kontroli kondycji implementacji w usługach platformy ASP.NET Core

Podczas tworzenia aplikacji mikrousług lub sieci web platformy ASP.NET Core, można użyć eksperymentalne biblioteki out-of-band (nie oficjalne jako część ASP.NETCore i teraz przestarzałe) o nazwie *kontroli kondycji* przez zespół programu ASP.NET. Jest on dostępny w tym [repozytorium GitHub architektury dotnet](https://github.com/dotnet-architecture/HealthChecks). Jednak oficjalną wersję elementu *kontroli kondycji* [zostaną wydane w programie ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (powinna być oficjalnym wydaniu przed zakończeniem 2018 r.).

Ta biblioteka jest łatwa w użyciu i udostępnia funkcje, dzięki którym Sprawdź poprawność określonego zasobu zewnętrznego potrzebne dla aplikacji (np. bazy danych programu SQL Server lub zdalnemu interfejsowi API) działa poprawnie. Korzystając z tej biblioteki, można również określić, co oznacza że zasobu jest w dobrej kondycji, jak możemy wyjaśnić później.

Aby można było używać tej biblioteki, należy najpierw użyć biblioteki w mikrousługi. Po drugie potrzebujesz aplikacji frontonu, który odpytuje raportów kondycji. Fronton aplikacji może być niestandardowych aplikacji do raportowania lub może być orchestrator sam można odpowiednio reagować na stany kondycji.

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Korzystanie z biblioteki HealthChecks w mikrousługi zaplecza programu ASP.NET

Aby zobaczyć, jak biblioteka HealthChecks jest używana w ramach aplikacji eShopOnContainers przykładowej aplikacji. Aby rozpocząć, musisz zdefiniować, co stanowi stan kondycji dla poszczególnych mikrousług. W przykładowej aplikacji mikrousług są w dobrej kondycji, jeśli mikrousług interfejsu API jest dostępny za pośrednictwem protokołu HTTP i jeśli jego powiązanej bazy danych programu SQL Server jest również dostępna.

W przyszłości będzie mógł zainstalować bibliotekę HealthChecks jako pakiet NuGet. Jednak na chwilę obecną, musisz pobrać i skompilować kod jako część rozwiązania. Klonowanie kodu dostępne pod adresem <https://github.com/dotnet-architecture/HealthChecks> i skopiuj następujące foldery do rozwiązania:

- src/common
- src/Microsoft.AspNetCore.HealthChecks
- src/Microsoft.Extensions.HealthChecks
- src/Microsoft.Extensions.HealthChecks.SqlServer

Można także użyć dodatkowe czynności kontrolne, takie jak te dla platformy Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale ponieważ w tej wersji w ramach aplikacji eShopOnContainers nie ma żadnych zależności na platformie Azure, nie jest potrzebna. Nie potrzebujesz kontrole kondycji programu ASP.NET, ponieważ w ramach aplikacji eShopOnContainers zależy od platformy ASP.NET Core.

Rysunek 8-7 przedstawia biblioteki HealthChecks w programie Visual Studio, gotowe do użycia jako blok konstrukcyjny przez wszystkie mikrousługi.

![Widok Eksploratora rozwiązania folderze HealthChecks przedstawiający trzy projekty.](./media/image6.png)

**Rysunek 8-7**. Kod źródłowy biblioteki ASP.NET Core HealthChecks w rozwiązaniu Visual Studio

Jak wprowadzone wcześniej, najpierw należy w każdym projekcie mikrousług jest można dodać odwołania do bibliotek HealthChecks trzy. Później możesz dodać akcje sprawdzania kondycji, które mają być wykonywane w tym mikrousług. Te akcje są po prostu zależności dla innych baz danych lub mikrousługi (HttpUrlCheck) (obecnie SqlCheck\* baz danych programu SQL Server). Możesz dodać akcję w obrębie klasy uruchamiania poszczególnych mikrousług platformy ASP.NET lub aplikacji sieci web platformy ASP.NET.

Każdej usługi lub aplikacji sieci web, należy skonfigurować przez dodanie wszystkich jego zależności HTTP lub baza danych jako jedna metoda AddHealthCheck. Na przykład aplikacji sieci web MVC, w ramach aplikacji eShopOnContainers zależy od wielu usług, dlatego ma kilka metod AddCheck dodane do kontroli kondycji.

Na przykład w poniższym kodzie (uproszczonego) widać jak mikrousługi katalogu została dodana zależność dotycząca swojej bazy danych programu SQL Server.

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

Jednak aplikację sieci web MVC w ramach aplikacji eShopOnContainers ma wiele zależności na pozostałą część mikrousług. W związku z tym wywołuje jedną metodę AddUrlCheck dla poszczególnych mikrousług, jak pokazano w poniższym przykładzie (uproszczony):

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

W związku z tym mikrousługi nie będą umożliwiać "" dobrej kondycji, dopóki wszystkie jego kontrole są w dobrej kondycji również.

Jeśli mikrousług ma zależność w usłudze lub w programie SQL Server, należy po prostu dodać wyboru Healthy("Ok"). Poniższy kod jest w ramach aplikacji eShopOnContainers `basket.api` mikrousług. (Mikrousług koszyka korzysta z pamięci podręcznej redis cache, ale biblioteki nie ma jeszcze dostawcę sprawdzanie kondycji pamięci podręcznej Redis).

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Dla usługi lub aplikacji sieci web można uwidocznić punkt końcowy kontroli kondycji, musi włączyć `UseHealthChecks([*url_for_health_checks*])` — metoda rozszerzenia. Ta metoda przechodzi na `WebHostBuilder` poziomu w metodzie głównej `Program` klasy usługi ASP.NET Core usługi lub aplikacji sieci web, zaraz po <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> jak pokazano w poniższym kodzie uproszczone:

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

Proces działa w ten sposób: każda mikrousługa udostępnia HC punktu końcowego. Punkt końcowy jest tworzony przez bibliotekę HealthChecks oprogramowania pośredniczącego platformy ASP.NET Core. Po wywołaniu tego punktu końcowego, uruchamia wszystkie kontrole kondycji, które są skonfigurowane w metodzie AddHealthChecks w klasie uruchamiania.

Metoda UseHealthChecks oczekuje portu lub ścieżki. Tego portu lub ścieżki jest punkt końcowy, aby użyć, aby sprawdzić kondycję usługi. Na przykład mikrousług katalogu używa HC ścieżki.

### <a name="cache-health-check-responses"></a>Buforowanie odpowiedzi sprawdzania kondycji

Ponieważ nie chcesz spowodować odmowę usługi (DoS) w usługach lub po prostu nie chcesz mieć wpływ na wydajność usługi, sprawdzając zasobów można zbyt często, zwraca wartość w pamięci podręcznej i skonfigurować czas trwania pamięci podręcznej, przy każdym sprawdzaniu kondycji.

Domyślnie czas trwania pamięci podręcznej wewnętrznie jest ustawiony na 5 minut, ale możesz zmienić ten czas trwania pamięci podręcznej w każdym sprawdzenie kondycji, tak jak w poniższym kodzie:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Zapytanie mikrousługi do raportów dotyczących stanu kondycji

Po skonfigurowaniu kontrole kondycji, zgodnie z opisem w tym artykule i masz mikrousług uruchamiane na platformie Docker, możesz bezpośrednio sprawdzić z przeglądarki, jeśli jest w dobrej kondycji.

Należy opublikować port kontenera na hoście platformy Docker, dzięki czemu można korzystać z kontenera, za pośrednictwem zewnętrzny adres IP hosta platformy Docker lub za pomocą `localhost`, jak pokazano na rysunku 8-8.

![Widok w przeglądarce odpowiedź JSON zwracany przez kontrolę kondycji](./media/image7.png)

**Rysunek 8-8**. Sprawdzanie stanu kondycji jednej usługi w przeglądarce

W tym teście widać, mikrousługi catalog.api (uruchomiony na porcie 5101) jest w dobrej kondycji i zwracanie stanu HTTP 200 i informacje o stanie w formacie JSON. Oznacza to również, że wewnętrznie usługa również sprawdzane kondycję jego zależność bazy danych programu SQL Server i że sprawdzenie kondycji zgłoszono sama jako w dobrej kondycji.

## <a name="use-watchdogs"></a>Użyj watchdogs

Strażnika jest oddzielną usługą, którą można obejrzeć kondycji i obciążenia usług i kondycji raport na temat mikrousług, badając z `HealthChecks` biblioteki wprowadzone wcześniej. Może to pomóc uniknąć błędów, które nie są wykrywane na podstawie widoku jednej usługi. Watchdogs również są dobrym miejscem do śledzenia hostowanie kodu, które może wykonywać działania korygujące znane warunki bez interakcji z użytkownikiem.

Próbki w ramach aplikacji eShopOnContainers zawiera strona internetowa, która wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano w rysunek 8 do 9. Jest to najprostsza strażnika, który może mieć, ponieważ tylko pokazuje stan mikrousług i aplikacji sieci web w ramach aplikacji eShopOnContainers. Strażnika również potrzebuje zazwyczaj akcje w przypadku wykrycia złej kondycji stanów.

![Widok przeglądarki aplikacji WebStatus, wyświetlanie stanu kondycji pięć mikrousługi w ramach aplikacji eShopOnContainers](./media/image8.png)

**Rysunek 8 – 9**. Przykładowy raport ze sprawdzania kondycji w ramach aplikacji eShopOnContainers

W podsumowaniu oprogramowanie pośredniczące ASP.NET, ASP.NET Core HealthChecks biblioteki udostępnia punkt końcowy kontroli kondycji jednego dla poszczególnych mikrousług. Spowoduje to wykonania sprawdzenia kondycji wykona zdefiniowaną i zwracać o ogólnej kondycji, w zależności od tych sprawdzeń.

Biblioteka HealthChecks jest rozszerzalny poprzez nowe funkcje sprawdzania kondycji przyszłych zasobów zewnętrznych. Na przykład oczekujemy, że w przyszłości biblioteki będzie miał kontrole kondycji dla pamięci podręcznej redis Cache i innych baz danych. Biblioteka umożliwia raportowania przez wiele zależności aplikacji lub usługi kondycji, i może następnie podjąć działania w oparciu kontrole kondycji.

## <a name="health-checks-when-using-orchestrators"></a>Kontrole kondycji w przypadku korzystania z koordynatorami

Aby monitorować dostępność mikrousługi, koordynatorów, takich jak Kubernetes i usługi Service Fabric okresowo sprawdzać kondycję, wysyłając żądania do testowania mikrousług. Gdy koordynatora ustali, że kontenerze/usługi jest zła, przestanie kierowania żądań do tego wystąpienia. Również zazwyczaj tworzy nowe wystąpienie tego kontenera.

Na przykład większość koordynatorów można użyć kontroli kondycji Zarządzanie wdrożeniami bez jakichkolwiek przestojów. Tylko wtedy, gdy stan zmiany/z kontenera usługi w dobrej kondycji będzie koordynatora start routingu ruchu do/z kontenera usługi wystąpień.

Monitorowanie kondycji jest szczególnie ważne w przypadku, gdy koordynatora wykonuje uaktualnienie aplikacji. Niektórych koordynatorów (np. usługi Azure Service Fabric) aktualizacji usługi w fazach — na przykład może zaktualizować co piątej powierzchni klastra dla uaktualnienie każdej aplikacji. Zestaw węzłów, który jest uaktualniony, w tym samym czasie jest określany jako *domeny uaktualnień*. Po każdej z domen został uaktualniony i jest dostępna dla użytkowników, że domena uaktualnienia musi upłynąć kontrole kondycji wdrożenia przechodzi do następnej domeny uaktualnienia.

Innym aspektem kondycja usługi zgłasza metryki z usługi. Jest to zaawansowana funkcja model kondycji niektórych koordynatorów, takich jak usługi Service Fabric. Metryki są ważne w przypadku, gdy za pomocą programu orchestrator, ponieważ są one używane do równoważyć obciążenie zasobów. Metryki można także wskaźnik określający kondycji systemu. Na przykład Niewykluczone, że aplikacja, która ma wiele mikrousług i każde wystąpienie raporty Metryka żądania na sekundę (RPS). Jeśli jedna usługa używa więcej zasobów (pamięci, procesora, itp.), od innej usługi, koordynatora można poruszanie wystąpień usługi w klastrze w celu utrzymania nawet wykorzystanie zasobów.

Należy pamiętać, że usługi Azure Service Fabric udostępnia swoje własne [monitorowanie kondycji modelu](/azure/service-fabric/service-fabric-health-introduction), co jest bardziej zaawansowane niż kontrole kondycji proste.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Zaawansowane monitorowanie: wizualizacja, analizy i alerty

Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raporty dotyczące wydajności i alerty po wykryciu problemu. Można użyć różnych rozwiązań dla systemów monitorowania.

Można użyć prostej aplikacji niestandardowych, przedstawiający stan usług, takich jak niestandardowa strona wyświetlana podczas wyjaśniających [platformy ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks). Lub za pomocą bardziej zaawansowanych narzędzi, takich jak Azure Application Insights można zgłaszać alerty w oparciu o strumień zdarzeń.

Na koniec jeśli są przechowywane wszystkie strumienie zdarzeń, służy Microsoft Power BI ani innych rozwiązań, takich jak Kibana lub Splunk umożliwiają wizualizację danych.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **ASP.NET Core HealthChecks** (wersja eksperymentalna) \
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- **Wprowadzenie do monitorowania kondycji usługi Service Fabric**\
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- **Usługi Azure Application Insights**\
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- **Microsoft Operations Management Suite**\
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Poprzednie](implement-circuit-breaker-pattern.md)
>[dalej](../secure-net-microservices-web-applications/index.md)