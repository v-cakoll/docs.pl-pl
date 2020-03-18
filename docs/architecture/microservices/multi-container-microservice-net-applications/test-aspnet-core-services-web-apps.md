---
title: Testowanie aplikacji internetowych i usług ASP.NET Core
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Poznaj architekturę testowania ASP.NET podstawowych usług i aplikacji sieci Web w kontenerach.
ms.date: 01/30/2020
ms.openlocfilehash: ab3ae6276ea4e4c741731f050913d956046271ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501985"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testowanie aplikacji internetowych i usług ASP.NET Core

Kontrolery są centralną częścią każdej ASP.NET podstawowej usługi API i ASP.NET aplikacji Sieci Web MVC. W związku z tym należy mieć pewność, że zachowują się zgodnie z przeznaczeniem dla aplikacji. Zautomatyzowane testy mogą zapewnić ci to zaufanie i wykrywać błędy, zanim dotrą do produkcji.

Należy przetestować, jak kontroler zachowuje się na podstawie prawidłowych lub nieprawidłowych danych wejściowych i przetestować odpowiedzi kontrolera na podstawie wyniku operacji biznesowej, którą wykonuje. Jednak powinny mieć te typy testów dla mikrousług:

- Testy jednostkowe. Zapewniają one, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami. Potwierdzenia przetestować składnik api.

- Testy integracji. Zapewniają one, że interakcje składników działają zgodnie z oczekiwaniami w odniesieniu do zewnętrznych artefaktów, takich jak bazy danych. Potwierdzenia można przetestować składnik api, interfejsu użytkownika lub skutki uboczne działań, takich jak we/wy bazy danych, rejestrowania, itp.

- Testy funkcjonalne dla każdej mikrousługi. Zapewniają one, że aplikacja działa zgodnie z oczekiwaniami z punktu widzenia użytkownika.

- Testy serwisowe. Zapewniają one, że przypadki użycia usługi end-to-end, w tym testowanie wielu usług w tym samym czasie, są testowane. Dla tego typu testów należy najpierw przygotować środowisko. W takim przypadku oznacza to uruchomienie usług (na przykład przy użyciu docker-compose up).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementowanie testów jednostkowych dla ASP.NET podstawowych interfejsów API sieci Web

Testowanie jednostkowe polega na testowaniu części aplikacji w izolacji od jej infrastruktury i zależności. Podczas testowania jednostek logiki kontrolera, tylko zawartość pojedynczej akcji lub metody jest testowany, a nie zachowanie jego zależności lub samej struktury. Testy jednostkowe nie wykrywają problemów w interakcji między składnikami — jest to cel testowania integracji.

Podczas testowania jednostek akcji kontrolera upewnij się, że skupiasz się tylko na ich zachowaniu. Test jednostki kontrolera pozwala uniknąć takich elementów, jak filtry, routing lub powiązanie modelu (mapowanie danych żądania do ViewModel lub DTO). Ponieważ koncentrują się one na testowaniu tylko jednej rzeczy, testy jednostkowe są zazwyczaj proste do napisania i szybkie do uruchomienia. Dobrze napisany zestaw testów jednostkowych można uruchomić często bez większego narzutów.

Testy jednostkowe są implementowane na podstawie struktur testowych, takich jak xUnit.net, MSTest, Moq lub NUnit. Dla eShopOnContainers przykładowej aplikacji używamy xUnit.

Podczas pisania testu jednostkowego dla kontrolera interfejsu API sieci Web, można utworzyć\#wystąpienia klasy kontrolera bezpośrednio przy użyciu nowego słowa kluczowego w C , tak, że test będzie działać tak szybko, jak to możliwe. W poniższym przykładzie pokazano, jak to zrobić podczas korzystania [z xUnit](https://xunit.github.io/) jako framework testów.

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementowanie testów integracji i funkcjonalności dla każdej mikrousługi

Jak wspomniano, testy integracyjne i testy funkcjonalne mają różne cele i cele. Jednak sposób implementowania zarówno podczas testowania kontrolerów ASP.NET Core jest podobny, więc w tej sekcji koncentrujemy się na testach integracji.

Testowanie integracji zapewnia, że składniki aplikacji działają poprawnie po złożeniu. ASP.NET Core obsługuje testowanie integracji przy użyciu platform testów jednostkowych i wbudowanego testowego hosta internetowego, który może służyć do obsługi żądań bez narzutów sieciowych.

W przeciwieństwie do testów jednostkowych testy integracji często obejmują problemy z infrastrukturą aplikacji, takie jak baza danych, system plików, zasoby sieciowe lub żądania i odpowiedzi sieci web. Testy jednostkowe używają podróbek lub makiety obiektów w miejsce tych problemów. Ale celem testów integracji jest potwierdzenie, że system działa zgodnie z oczekiwaniami z tymi systemami, więc do testowania integracji nie należy używać podróbek lub makiety obiektów. Zamiast tego należy dołączyć infrastruktury, takich jak dostęp do bazy danych lub wywołanie usługi z innych usług.

Ponieważ testy integracji wykonywania większych segmentów kodu niż testy jednostkowe, a ponieważ testy integracji opierają się na elementy infrastruktury, wydają się być rzędy wielkości wolniej niż testy jednostkowe. W związku z tym jest dobrym pomysłem, aby ograniczyć liczbę testów integracji, które piszesz i uruchamiasz.

ASP.NET Core zawiera wbudowany testowy host internetowy, który może służyć do obsługi żądań HTTP bez narzutów sieciowych, co oznacza, że można uruchomić te testy szybciej niż podczas korzystania z prawdziwego hosta sieci web. Test web host (TestServer) jest dostępny w składniku NuGet jako Microsoft.AspNetCore.TestHost. Można go dodać do projektów testów integracji i służyć do obsługi ASP.NET podstawowych aplikacji.

Jak widać w poniższym kodzie, podczas tworzenia testów integracji dla kontrolerów ASP.NET Core, można utworzyć wystąpienia kontrolerów za pośrednictwem hosta testowego. Jest to porównywalne do żądania HTTP, ale działa szybciej.

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Steve Smith. Testowanie kontrolerów** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith. Testowanie integracji** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Testowanie jednostkowe w .NET Core przy użyciu testu dotnet** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**. Oficjalna strona internetowa. \
    <https://xunit.github.io/>

- **Podstawy testu jednostkowego.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**. Repozytorium GitHub. \
    <https://github.com/moq/moq>

- **Jednostka .** Oficjalna strona internetowa. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Wdrażanie testów serwisowych w aplikacji wielokontenerowej

Jak wspomniano wcześniej podczas testowania aplikacji wielokontenerowych, wszystkie mikrousługi muszą być uruchomione w hosta platformy Docker lub klastra kontenera. Testy usługi end-to-end, które obejmują wiele operacji obejmujących kilka mikrousług wymagają wdrożenia i uruchomienia całej aplikacji w hoście platformy Docker przez uruchomienie docker-compose up (lub porównywalny mechanizm, jeśli używasz koordynatora). Po uruchomieniu całej aplikacji i wszystkich jej usług można wykonać integrację end-to-end i testy funkcjonalne.

Istnieje kilka podejść, których można użyć. W pliku docker-compose.yml, którego używasz do wdrażania aplikacji na poziomie rozwiązania, można rozwinąć punkt wejścia, aby użyć [testu dotnet](../../../core/tools/dotnet-test.md). Można również użyć innego pliku redagowania, który uruchamiałby testy na obrazie, na który kierujesz reklamy. Za pomocą innego pliku redagowania dla testów integracji, który zawiera mikrousług i baz danych w kontenerach, można upewnić się, że powiązane dane są zawsze resetowane do stanu pierwotnego przed uruchomieniem testów.

Po uruchomieniu aplikacji redagowania można skorzystać z punktów przerwania i wyjątków, jeśli używasz programu Visual Studio. Lub można uruchomić testy integracji automatycznie w potoku ciągłej integracji w usłudze Azure DevOps Services lub innego systemu ciągłej integracji/cd, który obsługuje kontenery platformy Docker.

## <a name="testing-in-eshoponcontainers"></a>Testowanie w eShopOnContainers

Testy aplikacji referencyjnej (eShopOnContainers) zostały niedawno zrestrukturyzowane, a teraz istnieją cztery kategorie:

1. **Testy jednostkowe,** po prostu stare regularne testy jednostkowe, zawarte w **{MicroserviceName}. Projekty testów jednostkowych**

2. **Mikrousługi funkcjonalne/integracyjne testy**, z przypadków testowych obejmujących infrastrukturę dla każdej mikrousługi, ale odizolowane od innych i są zawarte w **{MicroserviceName}. FunctionalTests** projektów.

3. **Testy funkcjonalności/integracji aplikacji**, które koncentrują się na integracji mikrousług, z przypadków testowych, które wywierają kilka mikrousług. Testy te znajdują się w projekcie **Application.FunctionalTests**.

Test jednostkowy i integracyjny na mikrousługę są zawarte w folderze testowym w każdej mikrousługi i aplikacji testów obciążenia są zawarte w folderze testowym w folderze rozwiązania, jak pokazano na rysunku 6-25.

![Zrzut ekranu przedstawiający punkt vs wskazujący niektóre projekty testowe w rozwiązaniu.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**Rysunek 6-25**. Testowanie struktury folderów w eShopOnContainers

Mikrousługi i aplikacji funkcjonalnych/integracji testy są uruchamiane z programu Visual Studio, przy użyciu regularnych testów runner, ale najpierw trzeba uruchomić wymagane usługi infrastruktury za pomocą zestawu plików docker-compose zawarte w folderze testowym rozwiązania:

**docker-compose-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

**docker-compose-test.override.yml**

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

Tak więc, aby uruchomić testy funkcjonalne/integracyjne należy najpierw uruchomić to polecenie z folderu testowego rozwiązania:

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Jak widać, te pliki docker-compose tylko uruchomić Redis, RabbitMQ, SQL Server i MongoDB mikrousług.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Testuje plik README** na reppo eShopOnContainers w githubie \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **Załaduj testów pliku README** na reppo eShopOnContainers w githubie \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Poprzedni](subscribe-events.md)
> [następny](background-tasks-with-ihostedservice.md)
