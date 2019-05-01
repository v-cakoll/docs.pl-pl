---
title: Testowanie aplikacji internetowych i usług ASP.NET Core
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Eksplorowanie architektury do testowania aplikacji internetowych i usług platformy ASP.NET Core w kontenerach.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 106e38a3cf3a121c4d7f879b718c832d27e0910f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864299"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testowanie aplikacji internetowych i usług ASP.NET Core

Kontrolery są centralnym elementem interfejsu API platformy ASP.NET Core usług i aplikacji sieci Web programu ASP.NET MVC. W efekcie powinien mieć pewność, której działają zgodnie z przeznaczeniem dla aplikacji. Testy automatyczne udostępnić Ci ten zaufania i umożliwić wykrycie błędów, zanim dotrą produkcji.

Należy przetestować sposób działania oparte na prawidłowe lub nieprawidłowe dane wejściowe kontrolera i test controller odpowiedzi na podstawie wyniku operacji biznesowych, który wykonuje. Jednak tego rodzaju testy powinny być zapisane na mikrousługi:

- Testy jednostkowe. Te upewnij się, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami. Potwierdzenia testowanie składników interfejsu API.

- Testy integracji. Te upewnij się, że interakcje składnika działać zgodnie z oczekiwaniami względem zewnętrznych artefaktów, takich jak bazy danych. Potwierdzenia można przetestować, składnik interfejsu API, interfejs użytkownika lub efekty uboczne akcji, takich jak bazy danych we/wy, rejestrowanie, itp.

- Testy funkcjonalne dla poszczególnych mikrousług. Te upewnij się, że aplikacja działa zgodnie z oczekiwaniami z perspektywy użytkownika.

- Usługa badania. Te upewnij się, że są przetestowane przypadki użycia usługi end-to-end, w tym testowanie wielu usług, w tym samym czasie. Tego rodzaju kontrolach musisz najpierw przygotować środowisko. W takim przypadku oznacza to uruchamianie usług (na przykład przy użyciu narzędzia docker-compose się).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementowanie testów jednostkowych dla interfejsów API sieci Web programu ASP.NET Core

Testy jednostkowe polega części aplikacji w izolacji od jego infrastruktura i zależności. Podczas testów jednostkowych można logiką kontrolera, tylko zawartość jednej akcji lub metoda jest testowany, nie zachowanie jego zależności lub samej strukturze. Testy jednostkowe nie wykryto problemów, interakcja między składnikami — to znaczy celem testów integracji.

Jako jednostki możesz przetestować akcji kontrolera, upewnij się, że możesz skoncentrować się tylko na ich zachowanie. Kontroler testu jednostkowego pozwala uniknąć elementów, takich jak filtrów routingu i wiązania modelu (mapowanie dane żądania ViewModel lub obiekt DTO). Ponieważ skupiają się na testowanie tylko jedną z rzeczy, testy jednostkowe są zwykle łatwe do zapisania i szybkie uruchamianie. Dobrze napisane zestaw testów jednostkowych mogą być uruchamiane często bez koszty ogólne.

Testy jednostkowe są implementowane w oparciu o struktury testów, takimi jak xUnit.net, MSTest, Moq lub NUnit. W ramach aplikacji eShopOnContainers przykładowej aplikacji użyto xUnit.

Podczas pisania testów jednostkowych dla kontrolera interfejsu API sieci Web, tworzenia wystąpienia klasy kontrolera bezpośrednio przy użyciu słowa kluczowego new w języku C\#, dzięki czemu testy zostaną uruchomione tak szybko, jak to możliwe. Poniższy przykład pokazuje, jak to zrobić, korzystając z [xUnit](https://xunit.github.io/) jako struktury testowej.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementowanie integracji i testów funkcjonalnych dla poszczególnych mikrousług

Jak wspomniano, testy integracji i testów funkcjonalnych mają różnych celów i cele. Jednak sposób implementacji zarówno podczas testowania kontrolerów platformy ASP.NET Core jest podobny, więc w tej sekcji możemy skoncentrować się na testy integracji.

Testowanie integracji gwarantuje, że składniki aplikacji działać prawidłowo, jeśli połączone. Integracja obsługuje platformy ASP.NET Core testowania przy użyciu platform testów jednostkowych i testów wbudowanych hosta sieci web, który może służyć do obsługi żądań bez obciążenie sieci.

W przeciwieństwie do testów jednostkowych testów integracji często obejmują obaw infrastruktury aplikacji, takich jak bazy danych, system plików, zasobów sieciowych lub żądania sieci web i odpowiedzi. Testy jednostkowe używane sztuczne elementy testowe lub testowanie obiektów, zamiast tych problemów. Ale testy integracji ma na celu upewnij się, że system działa zgodnie z oczekiwaniami w tych systemach, więc do testowania integracji nie używane sztuczne elementy testowe lub testowanie obiektów. Zamiast tego możesz uwzględnić infrastruktury, takich jak wywołania dostępu lub usługa bazy danych z innych usług.

Ponieważ testy integracji wykonywania większych segmenty kodu niż testy jednostkowe i testy integracji zależą elementy infrastruktury, mają zwykle rzędów wolniej niż testy jednostkowe. W związku z tym to dobry pomysł, aby ograniczyć liczbę testów integracji pisania i uruchamiania.

Platforma ASP.NET Core zawiera wbudowany test hosta sieci web używanym do obsługi żądań HTTP bez obciążenie sieci, co oznacza, że mogą szybciej uruchamiania tych testów, korzystając z hosta sieci web rzeczywistych. Test hosta sieci web (element TestServer) jest dostępna w składniku NuGet jako Microsoft.AspNetCore.TestHost. On mogą być dodawane do projektów testów integracji i używane do hosta platformy ASP.NET Core aplikacje.

Jak widać w poniższym kodzie, tworząc testy integracji dla platformy ASP.NET Core kontrolerów, tworzy się kontrolery, za pośrednictwem hosta testów. To jest porównywalna do żądania HTTP, ale działa szybciej.

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

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Steve Smith. Kontrolery testów** (platformy ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith. Testowanie integracji** (platformy ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Testowanie jednostek w .NET Core za pomocą polecenia dotnet test** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**. Oficjalna witryna. \
    <https://xunit.github.io/>

- **O teście jednostkowym.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**. Repozytorium GitHub. \
    <https://github.com/moq/moq>

- **NUnit**. Oficjalna witryna. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Wdrażanie usługi testów na aplikację obsługującą wiele kontenerów

Jak wspomniano wcześniej, podczas testowania aplikacji obsługującej wiele kontenerów, wszystkie mikrousługi muszą działać w ramach klastra hostów lub kontenera Docker. Testy usług end-to-end, obejmujących wiele operacji obejmujących wiele mikrousług wymagają jej wdrażanie i uruchamianie całej aplikacji na hoście platformy Docker za pomocą platformy docker-compose up (lub porównywalny mechanizmu, jeśli używasz programu orchestrator). Gdy całej aplikacji i wszystkich jego usług jest uruchomiona, można wykonać end-to-end integracji i testów funkcjonalnych.

Istnieje kilka metod, których można użyć. W pliku docker-compose.yml, która umożliwia wdrażanie aplikacji na poziomie rozwiązania można rozwinąć punktu wejścia, aby użyć [polecenia dotnet test](../../../core/tools/dotnet-test.md). Można również użyć innego pliku compose, która może uruchomić testy na ilustracji, które są przeznaczone dla. Przy użyciu innego pliku compose dla testów integracyjnych, które obejmuje z mikrousług i bazami danych w kontenerach, należy upewnić się, że powiązanych danych zawsze jest resetowany do stanu pierwotnego przed uruchomieniem testów.

Po skonfigurowaniu i uruchomieniu aplikacji compose możesz korzystać z zalet punktów przerwania i wyjątków w przypadku korzystania z programu Visual Studio. Lub uruchomić testy integracji automatycznie w potoku ciągłej integracji w usługach infrastruktury DevOps platformy Azure lub inny system ciągłej integracji/ciągłego wdrażania, który obsługuje kontenery platformy Docker.

## <a name="testing-in-eshoponcontainers"></a>Testowanie w ramach aplikacji eShopOnContainers

Odwołanie do testów aplikacji (w ramach aplikacji eShopOnContainers) zostały ostatnio przekształcony, a teraz istnieją cztery kategorie:

1. **Jednostka** testów, wystarczy zwykłe stare regularnych testów jednostkowych zawarte w **{MicroserviceName}. UnitTests** projektów

2. **Testy funkcjonalne/integracji Mikrousług**z przypadkami testowymi dotyczące infrastruktury dla poszczególnych mikrousług, ale odizolowany od innych i są zawarte w **{MicroserviceName}. FunctionalTests** projektów.

3. **Testy funkcjonalne/integracja aplikacji**, koncentrujących się na mikrousługi integracji z przypadkami testowymi, które powodowały kilka mikrousług. Te testy znajdują się w projekcie **Application.FunctionalTests**.

4. **Testy obciążenia**, koncentrujących się na czasy odpowiedzi dla poszczególnych mikrousług. Te testy znajdują się w projekcie **LoadTest** i Visual Studio 2017 Enterprise Edition.

Testu jednostki i integrację na mikrousługę znajdują się w folderze testu w każdej mikrousługi i testy obciążenia są umieszczane w folderze testu w folderze rozwiązania aplikacji, jak pokazano w rysunek 6-25.

![Struktura testów w ramach aplikacji eShopOnContainers: Każda usługa ma folder "test", który zawiera jednostki i testów funkcjonalnych. W folderze rozwiązania "test" istnieją testów szeroki funkcjonalnych aplikacji i ładowanie testów.](./media/image42.png)

**Rysunek 6-25**. Testowanie strukturę folderów w ramach aplikacji eShopOnContainers

Mikrousługi i testów funkcjonalnych/integracja aplikacji są uruchamiane z programu Visual Studio, przy użyciu modułu uruchamiającego testy w regularnych, ale najpierw należy do uruchamiania usług wymaganej infrastruktury, za pomocą zestawu plików docker-compose zawartych w rozwiązaniu test folderu :

**docker-compose-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
  nosql.data:
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
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
```

Tak do uruchamiania testów funkcjonalnych/integracja należy najpierw uruchomić to polecenie z folderu testów rozwiązania:

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Jak widać, te narzędzia docker-compose plików Uruchom mikrousług pamięci podręcznej Redis, RabbitMQ, programu SQL Server i bazy danych MongoDB.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Plik README testy** w ramach aplikacji eShopOnContainers repozytorium w serwisie GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **Plik README testy obciążenia** w ramach aplikacji eShopOnContainers repozytorium w serwisie GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Poprzednie](subscribe-events.md)
> [dalej](background-tasks-with-ihostedservice.md)
