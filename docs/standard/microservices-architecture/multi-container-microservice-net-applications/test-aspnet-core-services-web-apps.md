---
title: Testowanie aplikacji internetowych i usług platformy ASP.NET Core
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Testowanie aplikacji internetowych i usług platformy ASP.NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 2702a273ade0e58ba93d556cfd1ecc5531027f93
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45652654"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testowanie aplikacji internetowych i usług platformy ASP.NET Core

Kontrolery są centralnym elementem interfejsu API platformy ASP.NET Core usług i aplikacji sieci Web programu ASP.NET MVC. W efekcie powinien mieć pewność, której działają zgodnie z przeznaczeniem dla aplikacji. Testy automatyczne udostępnić Ci ten zaufania i umożliwić wykrycie błędów, zanim dotrą produkcji.

Należy przetestować sposób działania oparte na prawidłowe lub nieprawidłowe dane wejściowe kontrolera i test controller odpowiedzi na podstawie wyniku operacji biznesowych, który wykonuje. Jednak tego rodzaju testy powinny być zapisane na mikrousługi:

-   Testy jednostkowe. Te upewnij się, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami. Potwierdzenia testowanie składników interfejsu API.

-   Testy integracji. Te upewnij się, że interakcje składnika działać zgodnie z oczekiwaniami względem zewnętrznych artefaktów, takich jak bazy danych. Potwierdzenia można przetestować, składnik interfejsu API, interfejs użytkownika lub efekty uboczne akcji, takich jak bazy danych we/wy, rejestrowanie, itp.

-   Testy funkcjonalne dla poszczególnych mikrousług. Te upewnij się, że aplikacja działa zgodnie z oczekiwaniami z perspektywy użytkownika.

-   Usługa badania. Te upewnij się, że są przetestowane przypadki użycia usługi end-to-end, w tym testowanie wielu usług, w tym samym czasie. Tego rodzaju kontrolach musisz najpierw przygotować środowisko. W takim przypadku oznacza to uruchamianie usług (na przykład przy użyciu narzędzia docker-compose się).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementowanie testów jednostkowych dla interfejsów API sieci Web programu ASP.NET Core

Testy jednostkowe polega części aplikacji w izolacji od jego infrastruktura i zależności. Podczas testów jednostkowych można logiką kontrolera, tylko zawartość jednej akcji lub metoda jest testowany, nie zachowanie jego zależności lub samej strukturze. Testy jednostkowe nie wykryto problemów, interakcja między składnikami — to znaczy celem testów integracji.

Jako jednostki możesz przetestować akcji kontrolera, upewnij się, że możesz skoncentrować się tylko na ich zachowanie. Kontroler testu jednostkowego pozwala uniknąć elementów, takich jak filtrów routingu i wiązania modelu. Ponieważ skupiają się na testowanie tylko jedną z rzeczy, testy jednostkowe są zwykle łatwe do zapisania i szybkie uruchamianie. Dobrze napisane zestaw testów jednostkowych mogą być uruchamiane często bez koszty ogólne.

Testy jednostkowe są implementowane w oparciu o struktury testów, takimi jak xUnit.net, MSTest, Moq lub NUnit. W ramach aplikacji eShopOnContainers przykładowej aplikacji użyto xUnit.

Podczas pisania testów jednostkowych dla kontrolera interfejsu API sieci Web, tworzenia wystąpienia klasy kontrolera bezpośrednio przy użyciu słowa kluczowego new w języku C\#, dzięki czemu testy zostaną uruchomione tak szybko, jak to możliwe. Poniższy przykład pokazuje, jak to zrobić, korzystając z [xUnit](https://xunit.github.io/) jako struktury testowej.

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementowanie integracji i testów funkcjonalnych dla poszczególnych mikrousług

Jak wspomniano, testy integracji i testów funkcjonalnych mają różnych celów i cele. Jednak sposób implementacji zarówno podczas testowania kontrolerów platformy ASP.NET Core jest podobny, więc w tej sekcji możemy skoncentrować się na testy integracji.

Testowanie integracji gwarantuje, że składniki aplikacji działać prawidłowo, jeśli połączone. Integracja obsługuje platformy ASP.NET Core testowania przy użyciu platform testów jednostkowych i testów wbudowanych hosta sieci web, który może służyć do obsługi żądań bez obciążenie sieci.

W przeciwieństwie do testów jednostkowych testów integracji często obejmują obaw infrastruktury aplikacji, takich jak bazy danych, system plików, zasobów sieciowych lub żądania sieci web i odpowiedzi. Testy jednostkowe używane sztuczne elementy testowe lub testowanie obiektów, zamiast tych problemów. Ale testy integracji ma na celu upewnij się, że system działa zgodnie z oczekiwaniami w tych systemach, więc do testowania integracji nie używane sztuczne elementy testowe lub testowanie obiektów. Zamiast tego możesz uwzględnić infrastruktury, takich jak wywołania dostępu lub usługa bazy danych z innych usług.

Ponieważ testy integracji wykonywania większych segmenty kodu niż testy jednostkowe i testy integracji zależą elementy infrastruktury, mają zwykle rzędów wolniej niż testy jednostkowe. W związku z tym to dobry pomysł, aby ograniczyć liczbę testów integracji pisania i uruchamiania.

Platforma ASP.NET Core zawiera wbudowany test hosta sieci web używanym do obsługi żądań HTTP bez obciążenie sieci, co oznacza, że mogą szybciej uruchamiania tych testów, korzystając z hosta sieci web rzeczywistych. Test hosta sieci web jest dostępna w składniku NuGet jako Microsoft.AspNetCore.TestHost. On mogą być dodawane do projektów testów integracji i używane do hosta platformy ASP.NET Core aplikacje.

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

-   **Steve Smith. Kontrolery testów** (platformy ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Testowanie integracji** (platformy ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)

-   **Testowanie jednostek w .NET Core za pomocą polecenia dotnet test**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)

-   **xUnit.net**. Oficjalna witryna.
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **O teście jednostkowym.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. Repozytorium GitHub.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Oficjalna witryna.
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Wdrażanie usługi testów na aplikację obsługującą wiele kontenerów 

Jak wspomniano wcześniej, podczas testowania aplikacji obsługującej wiele kontenerów, wszystkie mikrousługi muszą działać w ramach klastra hostów lub kontenera Docker. Testy usług end-to-end, obejmujących wiele operacji obejmujących wiele mikrousług wymagają jej wdrażanie i uruchamianie całej aplikacji na hoście platformy Docker za pomocą platformy docker-compose up (lub porównywalny mechanizmu, jeśli używasz programu orchestrator). Gdy całej aplikacji i wszystkich jego usług jest uruchomiona, można wykonać end-to-end integracji i testów funkcjonalnych.

Istnieje kilka metod, których można użyć. W pliku docker-compose.yml, który zostanie użyty do wdrożenia aplikacji (lub podobnych, takich jak docker-compose.ci.build.yml), na poziomie rozwiązania można rozwinąć punktu wejścia, aby użyć [polecenia dotnet test](../../../core/tools/dotnet-test.md). Można również użyć innego pliku compose, która może uruchomić testy na ilustracji, które są przeznaczone dla. Przy użyciu innego pliku compose dla testów integracyjnych, które obejmuje z mikrousług i bazami danych w kontenerach, należy upewnić się, że powiązanych danych zawsze jest resetowany do stanu pierwotnego przed uruchomieniem testów.

Po skonfigurowaniu i uruchomieniu aplikacji compose możesz korzystać z zalet punktów przerwania i wyjątków w przypadku korzystania z programu Visual Studio. Lub uruchomić testy integracji automatycznie w potoku ciągłej integracji w usługach infrastruktury DevOps platformy Azure lub inny system ciągłej integracji/ciągłego wdrażania, który obsługuje kontenery platformy Docker.

>[!div class="step-by-step"]
[Poprzednie](subscribe-events.md)
[dalej](../microservice-ddd-cqrs-patterns/index.md)
