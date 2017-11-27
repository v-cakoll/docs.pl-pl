---
title: Monitorowanie kondycji
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Monitorowanie kondycji"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a>Monitorowanie kondycji

Monitorowanie kondycji można zezwolić na niemal czasie rzeczywistym informacje o stanie kontenery i mikrousług. Monitorowanie kondycji znaczenie ma wiele aspektów pracy mikrousług i jest szczególnie ważne w przypadku orchestrators przeprowadzania uaktualnień aplikacja częściowa w faz, jak wyjaśniono dalej.

Aplikacje oparte na Mikrousług często używają pulsów lub testy kondycji, aby włączyć ich monitory wydajności, planiści i orchestrators na zarządzanie wieloma usługami. Jeśli usługi nie może wysłać jakiegoś "Jestem aktywności" sygnału na żądanie lub według harmonogramu, aplikacja może stają przed ryzyka podczas wdrażania aktualizacji lub może po prostu za późno wykrywanie błędów i nie można zatrzymać kaskadowych błędów, które może zakończyć w głównych awarii.

W typowej modelu usług wysyłać raporty o stanie ich, a tych informacji jest agregowana w celu zapewnienia przeglądu ogólny stan kondycji aplikacji. Jeśli używasz programu orchestrator, musisz podać informacje o kondycji do klastra programu orchestrator, aby klaster mógł działać w związku z tym. Jeśli poświęcić raportowania kondycji wysokiej jakości, dostosowany do aplikacji, można wykrywać i znacznie łatwiejsze Rozwiązywanie problemów w uruchomionej aplikacji.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Implementowanie kondycji sprawdza w usługach platformy ASP.NET Core

Podczas tworzenia aplikacji platformy ASP.NET Core mikrousługi lub sieci web, mogą używać biblioteki o nazwie HealthChecks od zespołu ASP.NET. (Począwszy od 2017 maja wczesnego wydawania jest dostępna w serwisie GitHub).

Ta biblioteka jest łatwy w użyciu i udostępnia funkcje, dzięki którym można zweryfikować określonego zasobu zewnętrznego wymagane dla aplikacji (na przykład baza danych SQL Server lub zdalnego interfejsu API) działa prawidłowo. Korzystając z tej biblioteki, można również określić, co oznacza to, czy zasób jest w dobrej kondycji, jak możemy wyjaśnić później.

Aby użyć tej biblioteki, musisz najpierw użyć biblioteki w Twojej mikrousług. Po drugie należy aplikacji frontonu, który odpytuje raportów kondycji. Można raportowania aplikacji niestandardowej aplikacji frontonu lub może być orchestrator sam mogły odpowiednio zareagować na stany kondycji.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Za pomocą biblioteki HealthChecks w sieci wewnętrznej mikrousług ASP.NET

Widać, jak biblioteka HealthChecks jest używana w eShopOnContainers przykładowej aplikacji. Aby rozpocząć, musisz zdefiniować, co stanowi stan kondycji dla każdego mikrousługi. W przykładowej aplikacji mikrousług są w dobrej kondycji, jeśli mikrousługi interfejsu API jest dostępny za pośrednictwem protokołu HTTP i jeśli jego powiązanych bazy danych programu SQL Server jest również dostępna.

W przyszłości można zainstalować biblioteki HealthChecks jako pakietu NuGet. Jednak opracowywania tego tekstu, musisz pobrać i Skompiluj kod jako część rozwiązania. Klonowanie kodu, które są dostępne pod adresem https://github.com/aspnet/HealthChecks i skopiuj następujące foldery do rozwiązania.

  - src/wspólne
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Można także użyć dodatkowe kontrole, takich jak te dla platformy Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale ponieważ ta wersja eShopOnContainers nie ma żadnych zależności na platformie Azure, nie jest potrzebna. Nie trzeba kontroli kondycji programu ASP.NET, ponieważ eShopOnContainers jest oparta na platformy ASP.NET Core.

Rysunek 10 – 6 przedstawia biblioteki HealthChecks w programie Visual Studio, gotowy do użycia jako bloku konstrukcyjnego przez dowolnego mikrousług.

![](./media/image6.png)

**Rysunek 10 – 6**. Kod źródłowy platformy ASP.NET Core HealthChecks biblioteki w rozwiązaniu Visual Studio

Jak wprowadzone wcześniej, najpierw musisz w każdym projekcie mikrousługi jest można dodać odwołania do bibliotek HealthChecks trzy. Następnie należy dodać akcje sprawdzania kondycji, które należy wykonać w tym mikrousługi. Te akcje są po prostu zależne od innych baz danych lub mikrousług (HttpUrlCheck) (obecnie SqlCheck\* baz danych programu SQL Server). Możesz dodać akcji w obrębie klasy uruchamiania każdego mikrousługi ASP.NET lub aplikacji sieci web ASP.NET.

Każdej usługi lub aplikacji sieci web należy skonfigurować przez dodanie wszystkich jego zależności HTTP lub bazy danych jako jedną metodę AddHealthCheck. Na przykład aplikacja sieci web MVC z eShopOnContainers zależy od wielu usług, w związku z tym ma kilka metod AddCheck dodane do kontroli kondycji.

Na przykład w poniższym kodzie widać jak mikrousługi katalogu Dodaje zależność w swojej bazie danych programu SQL Server.

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

Jednak aplikację sieci web MVC eShopOnContainers ma wiele zależności od reszty mikrousług. W związku z tym wywołuje jedną metodę AddUrlCheck dla każdego mikrousługi, jak pokazano w poniższym przykładzie:

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

W związku z tym mikrousługi nie będą umożliwiać stanu "zdrowy", dopóki wszystkie jego testy są w dobrej kondycji oraz.

Jeśli mikrousługi nie ma zależności usługi lub na serwerze SQL, należy po prostu Dodaj wyboru Healthy("Ok"). Poniższy kod jest mikrousługi basket.api eShopOnContainers. (Mikrousługi koszyka korzysta z pamięci podręcznej Redis, ale biblioteki nie ma jeszcze dostawcę Redis kondycji wyboru).

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Dla usługi lub aplikacji sieci web do udostępnienia punktu końcowego sprawdzania kondycji, musi włączyć UseHealthChecks (\[*adres url\_dla\_kondycji\_sprawdza*\]) rozszerzenia Metoda. Ta metoda przechodzi w WebHostBuilder w głównej metody klasy Program ASP.NET Core usługi lub sieci web aplikacji, tuż po UseKestrel, jak pokazano w poniższym kodzie.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

Proces przebiega następująco: każdego mikrousługi przedstawia HC punktu końcowego. Tego punktu końcowego jest tworzony przez bibliotekę HealthChecks platformy ASP.NET Core oprogramowania pośredniczącego. Po wywołaniu tego punktu końcowego uruchamia wszystkie testy kondycji skonfigurowanych w metodzie AddHealthChecks w klasie uruchamiania.

Metoda UseHealthChecks oczekuje na port lub ścieżki. Tego portu lub ścieżka jest punkt końcowy do użycia w celu sprawdzenia kondycji usługi. Na przykład mikrousługi katalogu używa HC ścieżki.

### <a name="caching-health-check-responses"></a>Buforowanie odpowiedzi na sprawdzenie kondycji

Ponieważ nie chcesz spowodować "odmowa usługi" (DoS) w usługach lub po prostu nie chcesz mieć wpływ na wydajność usługi poprzez sprawdzenie zasobów można zbyt często pamięci podręcznej zwraca i skonfigurować czas trwania pamięci podręcznej dla każdego sprawdzania kondycji.

Domyślnie czas buforowania wewnętrznie jest ustawiony na 5 minut, ale można zmienić ten czas trwania pamięci podręcznej w każdym sprawdzenie kondycji, zgodnie z poniższym kodem:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Wykonywanie zapytania z mikrousług raport stanu kondycji

Po skonfigurowaniu kontroli kondycji zgodnie z opisem w tym miejscu po mikrousługi działa w Docker można bezpośrednio sprawdzić z przeglądarki, jeśli jest w dobrej kondycji. (To wymagają są publikowania port kontenera poza hostów Docker, więc można uzyskać dostęp do kontenera, za pośrednictwem hosta lokalnego lub zewnętrzny adres IP hosta Docker). Rysunek 10-7 przedstawiono żądania w przeglądarce i odpowiadająca mu reakcja.

![](./media/image7.png)

**Rysunek 10-7**. Sprawdzanie stanu kondycji pojedynczą usługę przy użyciu przeglądarki

W tym teście widać mikrousługi catalog.api (uruchomiony na porcie 5101) jest w dobrej kondycji zwracanie stan HTTP 200 i informacje o stanie w formacie JSON. Oznacza to również, czy wewnętrznie usługi również sprawdzić kondycję jego zależność bazy danych programu SQL Server i że sprawdzenie kondycji został raportuje swój stan jako dobrej kondycji.

## <a name="using-watchdogs"></a>Przy użyciu watchdogs

Programu alarmowego jest oddzielny usługa można obejrzeć kondycji i obciążenie usługi i kondycji raport o mikrousług badając z biblioteką HealthChecks wprowadzone wcześniej. Może to pomóc zapobiec wystąpieniu błędów, które nie można wykryć na podstawie widoku jednej usługi. Watchdogs są również dobrym miejscem do kodu hosta, który może wykonywać akcje naprawcze wykonane dla znanych warunki bez interakcji z użytkownikiem.

Przykład eShopOnContainers zawiera strony sieci web, która wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano na rysunku nr 10-8. Jest to najprostsza programu alarmowego może wystąpić, ponieważ wszystkie robi są pokazuje stan aplikacji sieci web i mikrousług w eShopOnContainers. Zazwyczaj programu alarmowego również wykonuje akcje, po wykryciu stanów złej kondycji.

![](./media/image8.png)

**Rysunek 10-8**. Przykładowy raport ze sprawdzania kondycji w eShopOnContainers

Podsumowując oprogramowanie pośredniczące ASP.NET biblioteki ASP.NET Core HealthChecks zawiera punkt końcowy wyboru jednego kondycji dla każdego mikrousługi. Spowoduje to wykonania sprawdzenia kondycji zdefiniowane w nim i zwracany ogólny stan kondycji, w zależności od tych kontroli.

Biblioteka HealthChecks jest otwarty przez nowe funkcje sprawdzania kondycji przyszłych zasobów zewnętrznych. Na przykład oczekuje się, że w przyszłości biblioteki będzie miało kontroli kondycji dla pamięci podręcznej Redis i innych baz danych. Biblioteki umożliwia raportowania przez wiele zależności aplikacji lub usługi kondycji, a następnie można wykonać akcji w oparciu o te testy kondycji.

## <a name="health-checks-when-using-orchestrators"></a>Sprawdzanie kondycji, używając orchestrators

Monitorowanie dostępności sieci mikrousług, orchestrators jak Docker Swarm, Kubernetes i sieci szkieletowej usług okresowo sprawdzania kondycji, wysyłając żądania do testowania mikrousług. Gdy orchestrator Określa, że kontenerze/usługi jest zła, przestaje routingu żądań do tego wystąpienia. Również zazwyczaj tworzy nowe wystąpienie tego kontenera.

Na przykład większość orchestrators służy kontroli kondycji Zarządzanie wdrożeniami przestoju zero. Tylko wtedy, gdy stan zmienia kontener/usługi, do dobrej kondycji będzie orchestrator start routingu ruchu do wystąpień kontenera/usług.

Monitorowanie kondycji jest szczególnie ważne w przypadku, gdy orchestrator przeprowadza uaktualnienie aplikacji. Usługi w aktualizacji niektórych orchestrators (takich jak sieć szkieletowa usług Azure), fazy — na przykład może zaktualizować co piątej powierzchni klastra dla każdego uaktualnienia aplikacji. Zestaw określonych węzłów, który jest uaktualniony, w tym samym czasie jest określany jako *domeny uaktualnienia*. Po każdej z domen został uaktualniony i jest dostępny dla użytkowników, że domena uaktualnienia musi upłynąć kontroli kondycji wdrożenia przechodzi do następnej domeny uaktualnienia.

Innym aspektem usługi kondycji jest raportowania metryki z usługi. Jest to zaawansowane możliwości model kondycji niektóre orchestrators, takich jak sieć szkieletowa usług. Metryki są ważne, gdy za pomocą programu orchestrator, ponieważ są one używane do równoważyć obciążenie zasobów. Metryki można również wskaźnik kondycji systemu. Na przykład może być aplikacja, która ma wiele mikrousług i każde wystąpienie raporty Metryka żądania na sekundę (RPS). Jeśli jedna usługa używa więcej zasobów (pamięci, procesora, itp.) od innej usługi, orchestrator można poruszanie wystąpień usługi w klastrze, aby spróbować Obsługa nawet wykorzystania zasobów.

Należy pamiętać, że jeśli używasz usługi Azure Service Fabric zawiera własną [monitorowanie kondycji modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), który jest bardziej zaawansowane niż kontroli kondycji proste.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Zaawansowane monitorowanie: wizualizacji, analizy i alerty

Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raporty dotyczące wydajności usługi i alerty, gdy zostanie wykryty problem. Można użyć różnych rozwiązań dla ten aspekt monitorowania.

Można użyć prostego niestandardowych aplikacji przedstawiający stan usług, takich jak niestandardowe strony firma Microsoft wykazały, gdy firma Microsoft wyjaśniono [platformy ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Lub można zgłaszać alerty w oparciu o strumień zdarzeń za pomocą bardziej zaawansowanych narzędzi, takich jak Azure Application Insights and Operations Management Suite.

Ponadto jeśli były przechowywane wszystkich strumieni zdarzeń, służy Microsoft Power BI lub rozwiązanie innej firmy, takich jak Kibana lub Splunk do wizualizacji danych.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Program ASP.NET Core HealthChecks** (wczesnego wydawania) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Wprowadzenie do monitorowania kondycji sieci szkieletowej usług**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Usługa Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[Poprzednie] (wdrożenie obwodu-dzielącego wyrazy pattern.md) [dalej] (.. /Secure-NET-microservices-Web-Applications/index.MD)
