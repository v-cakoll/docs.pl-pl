---
title: Testowanie aplikacji internetowych i usług ASP.NET Core
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Poznaj architekturę do testowania ASP.NET podstawowych usług i aplikacji sieci web w kontenerach.
ms.date: 01/30/2020
ms.openlocfilehash: f66d6184d913405c9372904f8072dda1dbfbe6ac
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988235"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testowanie aplikacji internetowych i usług ASP.NET Core

Kontrolery są centralną częścią każdej usługi interfejsu API ASP.NET Core i ASP.NET aplikacji MVC Web. W związku z tym należy mieć pewność, że zachowują się zgodnie z przeznaczeniem dla aplikacji. Zautomatyzowane testy mogą zapewnić ci to zaufanie i mogą wykrywać błędy, zanim dotrą do produkcji.

Należy przetestować zachowanie kontrolera na podstawie prawidłowych lub nieprawidłowych danych wejściowych i odpowiedzi kontrolera testów na podstawie wyniku operacji biznesowej, którą wykonuje. Jednak powinny mieć te typy testów dla mikrousług:

- Testy jednostkowe. Zapewniają one, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami. Potwierdzenia testować składnika interfejsu API.

- Testy integracji. Zapewniają one, że interakcje składników działają zgodnie z oczekiwaniami względem zewnętrznych artefaktów, takich jak bazy danych. Potwierdzenia można przetestować składnik interfejsu API, interfejsu użytkownika lub skutki uboczne akcji, takich jak we/wy bazy danych, rejestrowanie, itp.

- Testy funkcjonalne dla każdej mikrousługi. Zapewniają one, że aplikacja działa zgodnie z oczekiwaniami z punktu widzenia użytkownika.

- Testy serwisowe. Zapewniają one, że przypadki użycia usługi end-to-end, w tym testowania wielu usług w tym samym czasie, są testowane. Dla tego typu testów należy najpierw przygotować środowisko. W takim przypadku oznacza to uruchomienie usług (na przykład za pomocą docker-compose up).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementowanie testów jednostkowych dla ASP.NET podstawowych interfejsów API sieci Web

Testowanie jednostkowe polega na testowaniu części aplikacji w oderwaniu od jej infrastruktury i zależności. Podczas jednostkowej logiki kontrolera testów testowa testowana jest testowana tylko zawartość pojedynczej akcji lub metody, a nie zachowanie jej zależności lub samej struktury. Testy jednostkowe nie wykrywają problemów w interakcji między składnikami — to jest celem testowania integracji.

Podczas testowania jednostkowego akcji kontrolera upewnij się, że koncentrujesz się tylko na ich zachowaniu. Test jednostki kontrolera pozwala uniknąć takich obrażeń, jak filtry, routing lub powiązanie modelu (mapowanie danych żądania do ViewModel lub DTO). Ponieważ koncentrują się one na testowaniu tylko jednej rzeczy, testy jednostkowe są zazwyczaj proste do zapisu i szybkie uruchamianie. Dobrze napisany zestaw testów jednostkowych można często uruchamiać bez większego obciążenia.

Testy jednostkowe są implementowane na podstawie struktur testowych, takich jak xUnit.net, MSTest, Moq lub NUnit. Dla aplikacji przykładowej eShopOnContainers używamy xUnit.

Podczas pisania testu jednostkowego dla kontrolera interfejsu API sieci Web, można utworzyć\#wystąpienia klasy kontrolera bezpośrednio przy użyciu nowego słowa kluczowego w języku C , tak aby test będzie działać tak szybko, jak to możliwe. W poniższym przykładzie pokazano, jak to zrobić podczas korzystania z [xUnit](https://xunit.github.io/) jako struktury testowej.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Wdrażanie testów integracyjnych i funkcjonalnych dla każdej mikrousług

Jak wspomniano, testy integracji i testy funkcjonalne mają różne cele i cele. Jednak sposób implementowania zarówno podczas testowania ASP.NET kontrolerów Core jest podobny, więc w tej sekcji koncentrujemy się na testach integracji.

Testowanie integracji zapewnia, że składniki aplikacji działają poprawnie po złożeniu. ASP.NET Core obsługuje testowanie integracji przy użyciu jednostek testowych struktur i wbudowany testowy host sieci web, który może służyć do obsługi żądań bez narzutu sieciowego.

W przeciwieństwie do testowania jednostkowego testy integracji często dotyczą problemów z infrastrukturą aplikacji, takich jak baza danych, system plików, zasoby sieciowe lub żądania i odpowiedzi sieci web. Testy jednostkowe używają podróbek lub makiety obiektów zamiast tych problemów. Ale celem testów integracji jest potwierdzenie, że system działa zgodnie z oczekiwaniami z tymi systemami, więc do testowania integracji nie używasz podróbek lub makiety obiektów. Zamiast tego należy dołączyć infrastruktury, takich jak dostęp do bazy danych lub wywołania usługi z innych usług.

Ponieważ testy integracji wykonują większe segmenty kodu niż testy jednostkowe, a ponieważ testy integracji opierają się na elementach infrastruktury, wydają się być rzędami wielkości wolniejszymi niż testy jednostkowe. W związku z tym jest dobrym pomysłem, aby ograniczyć liczbę testów integracji piszesz i uruchamiasz.

ASP.NET Core zawiera wbudowany testowy host internetowy, który może być używany do obsługi żądań HTTP bez narzutu sieciowego, co oznacza, że można uruchomić te testy szybciej niż przy użyciu prawdziwego hosta sieci web. Testowy host internetowy (TestServer) jest dostępny w składniku NuGet jako Microsoft.AspNetCore.TestHost. Można go dodać do projektów testów integracji i używane do hostowania aplikacji ASP.NET Core.

Jak widać w poniższym kodzie, podczas tworzenia testów integracji dla ASP.NET kontrolerów core, można utworzyć wystąpienia kontrolerów za pośrednictwem hosta testowego. Jest to porównywalne z żądaniem HTTP, ale działa szybciej.

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

- **Steve Smith. Sterowniki testowe** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith. Testowanie integracji** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Testowanie jednostkowe w .NET Core przy użyciu testu dotnet** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**. Oficjalna strona. \
    <https://xunit.github.io/>

- **Podstawy testu jednostkowego.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**. Repozytorium GitHub. \
    <https://github.com/moq/moq>

- **NUnit**. Oficjalna strona. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Wdrażanie testów serwisowych w aplikacji wielokontenerowej

Jak wspomniano wcześniej podczas testowania aplikacji wielu kontenerów, wszystkie mikrousługi muszą być uruchomione w ramach hosta platformy Docker lub klastra kontenerów. Testy usługi end-to-end, które obejmują wiele operacji obejmujących kilka mikrousług wymagają wdrożenia i uruchomienia całej aplikacji w hoście platformy Docker przez uruchomienie docker-compose up (lub porównywalny mechanizm, jeśli używasz orchestrator). Po uruchomieniu całej aplikacji i wszystkich jej usług można wykonać kompleksową integrację i testy funkcjonalne.

Istnieje kilka podejść, których można użyć. W pliku docker-compose.yml używanym do wdrażania aplikacji na poziomie rozwiązania można rozwinąć punkt wejścia, aby użyć [testu dotnet](../../../core/tools/dotnet-test.md). Można również użyć innego pliku redagowania, który uruchamiałby testy w obrazie, na który kierowane są. Za pomocą innego pliku compose dla testów integracji, który zawiera mikrousług i baz danych na kontenerach, można upewnić się, że powiązane dane są zawsze resetowane do pierwotnego stanu przed uruchomieniem testów.

Po uruchomieniu aplikacji redpose można skorzystać z punktów przerwania i wyjątków, jeśli używasz programu Visual Studio. Lub można uruchomić testy integracji automatycznie w potoku ciągłej integracji w usłudze Azure DevOps services lub innego systemu ciągłej integracji/ciągłego wdrażania, który obsługuje kontenery platformy Docker.

## <a name="testing-in-eshoponcontainers"></a>Testowanie w eShopOnContainers

Testy aplikacji referencyjnej (eShopOnContainers) zostały niedawno zrestrukturyzowane, a teraz istnieją cztery kategorie:

1. **Testy jednostkowe,** po prostu stare regularne testy jednostkowe, zawarte w **{MicroserviceName}. Projekty UnitTests**

2. **Testy funkcjonalne/integracji mikrousług,** z przypadkami testowymi obejmującymi infrastrukturę dla każdej mikrousługi, ale odizolowane od innych i są zawarte w **{MicroserviceName}. Projekty Testy funkcjonalne.**

3. **Testy funkcjonalności/integracji aplikacji**, które koncentrują się na integracji mikrousług, z przypadków testowych, które wywierają kilka mikrousług. Testy te znajdują się w projekcie **Application.FunctionalTests**.

Jednostka i integracji test na mikrousługi są zawarte w folderze testowym w każdej mikrousługi i Application a Load testy znajdują się w folderze testowym w folderze rozwiązania, jak pokazano na rysunku 6-25.

![Zrzut ekranu programu VS wskazując niektóre projekty testowe w rozwiązaniu.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**Rysunek 6-25**. Struktura folderów testowych w eShopOnContainers

Testy funkcjonalne/integracyjne mikrousług i aplikacji są uruchamiane z programu Visual Studio przy użyciu zwykłego narzędzia testów, ale najpierw należy uruchomić wymagane usługi infrastruktury za pomocą zestawu plików docker-compose zawartych w folderze testu rozwiązania:

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

Tak, aby uruchomić testy funkcjonalne/integracyjne należy najpierw uruchomić to polecenie, z folderu testu rozwiązania:

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Jak widać, te pliki docker-compose uruchamiają tylko mikrousług Redis, RabbitMQ, SQL Server i MongoDB.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Testy pliku README** w repozytorium eShopOnContainers na GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **Testy obciążenia pliku README** w repozytorium eShopOnContainers na GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Poprzedni](subscribe-events.md)
> [następny](background-tasks-with-ihostedservice.md)
