---
title: "Testowanie platformy ASP.NET Core usług i aplikacji sieci web"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Testowanie platformy ASP.NET Core usług i aplikacji sieci web"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 80b7fa75344f8737baacfba6462a03b436fdf6a8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testowanie platformy ASP.NET Core usług i aplikacji sieci web

Kontrolery są środkowej części interfejsu API platformy ASP.NET Core usług i aplikacji sieci Web programu ASP.NET MVC. Tak powinien mieć pewność, które działają zgodnie z przeznaczeniem dla aplikacji. Testy automatyczne może udostępnić tym zaufania i może szybko wykrywać błędy przed dotarciem produkcji.

Należy przetestować, jak kontroler ma zachowywać się oparte na prawidłowe lub nieprawidłowe dane wejściowe i na podstawie wyniku prowadzonej działalności, którą wykonuje odpowiedzi kontrolera testu. Jednak powinny mieć następujące typy testów z mikrousług:

-   Testy jednostkowe. Te upewnij się, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami. Potwierdzenia testu API składnika.

-   Testy integracji. Te upewnij się, że składnik interakcje działać zgodnie z oczekiwaniami przed zewnętrznych artefaktów, takich jak bazy danych. Potwierdzenia można przetestować składnika interfejsu API, interfejsu użytkownika lub efektami ubocznymi akcji, takich jak bazy danych we/wy, rejestrowanie, itp.

-   Testy funkcjonalne dla każdego mikrousługi. Te upewnij się, że aplikacja działa zgodnie z oczekiwaniami z perspektywy użytkownika.

-   Testy usługi. Te upewnij się, sprawdzane są przypadki użycia usługi end-to-end, łącznie z testowaniem wielu usług w tym samym czasie. Dla tego typu testowania musisz najpierw przygotować środowisko. W takim przypadku oznacza to, uruchamiania usług (na przykład przy użyciu rozwiązania docker-compose się).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementującej testów jednostkowych dla interfejsów API platformy ASP.NET Core sieci Web

Testy jednostkowe obejmuje testowania części aplikacji w izolacji od jego infrastruktury i zależności. Podczas testu jednostkowego możesz logiką kontrolera, tylko zawartość jednej akcji lub jest testowana metoda, nie zachowanie z jego zależności lub struktury, sam. Testy jednostkowe Nie wykrywaj problemy w interakcji między składnikami — to znaczy celem testów integracji.

Jako jednostki można przetestować akcji kontrolera, upewnij się, że można skupić się tylko na ich zachowanie. Kontroler testu jednostkowego pozwala uniknąć np. filtry routingu i wiązania modelu. Ponieważ one skupić się na tylko jeden element testowania, testy jednostkowe są zwykle proste do zapisu i szybkie uruchamianie. Dobrze napisane zbiór testy jednostkowe mogą być uruchamiane często bez znacznie obciążenie.

Testy jednostkowe są implementowane oparte na platformach testu, takie jak xUnit.net, MSTest, Moq lub NUnit. EShopOnContainers przykładowej aplikacji użyto XUnit.

Podczas pisania testów jednostkowych dla kontrolera interfejsu API sieci Web, można utworzyć wystąpienia klasy kontrolera, bezpośrednio za pomocą nowych słów kluczowych w języku C\#, dzięki czemu tak szybko jak to możliwe uruchomienia testu. Poniższy przykład pokazuje, jak na przykład przy użyciu [XUnit](https://xunit.github.io/) jako struktury testowej.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Wdrażanie integracji i testy funkcjonalne dla każdego mikrousługi

Jak wspomniano, testów integracji i funkcjonalności mają różnych celów i cele. Jednak sposób implementowania zarówno podczas testowania kontrolery ASP.NET Core jest podobny, więc w tej sekcji możemy skoncentrować się na testów integracji.

Testowanie integracji gwarantuje, że składniki aplikacji działać prawidłowo, jeśli połączone. Integracja obsługuje platformy ASP.NET Core testowania przy użyciu platform testów jednostkowych i wbudowane testu hosta sieci web, który może służyć do obsługi żądań bez obciążenie sieci.

W przeciwieństwie do przeprowadzania testów jednostkowych integracji testy obejmują często dotyczy infrastruktury aplikacji, takich jak bazy danych, system plików, zasobów sieciowych lub żądania sieci web i odpowiedzi. Testy jednostkowe Użyj elementów sztucznych lub mock obiektów zamiast te problemy. Ale testy integracji ma na celu potwierdzenie, że system działa zgodnie z oczekiwaniami w przypadku tych systemów, do integracji testowania nie używać elementów sztucznych ani mock obiektów. Zamiast tego możesz uwzględnić infrastruktury, takie jak wywołania dostępu lub usługi bazy danych z innych usług.

Ponieważ testy integracji wykonywania większych segmenty kodu niż testy jednostkowe i testy integracji zależne elementy infrastruktury, mają zwykle rzędów wolniej niż testy jednostkowe. W związku z tym jest dobrym rozwiązaniem, aby ograniczyć liczbę testów integracji zapisu i uruchom.

Platformy ASP.NET Core obejmuje wbudowane testu sieci web hosta, który może służyć do obsługi żądań HTTP bez obciążenie sieci, co oznacza, że można uruchomić te testy szybciej używając hosta sieci web rzeczywistych. Host testów sieci web jest dostępna w składniku NuGet jako Microsoft.AspNetCore.TestHost. Można dodać do integracji projekty testowe, a używany do hostowania platformy ASP.NET Core aplikacji.

Jak widać w poniższym kodzie podczas tworzenia testów integracji dla platformy ASP.NET Core kontrolerów, można utworzyć wystąpienia kontrolerów przez hosta testów. To jest porównywalna do żądania HTTP, ale działa szybciej.

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

-   **Steve Smith. Testowanie kontrolerów** (platformy ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Testowanie integracji** (platformy ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)

-   **Testowanie w .NET Core za pomocą testu dotnet jednostki**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**. Oficjalna witryna.
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **Unit Test Basics.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. Repozytorium GitHub.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Oficjalna witryna.
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Wdrażanie usługi testów w kontenerze wielu aplikacji 

Jak wspomniano wcześniej, podczas testowania aplikacji kontenera usługi, wszystkie mikrousług musi być uruchomiona w klastrze hosta lub kontener Docker. Testy na trasie usługi, obejmujące wiele operacji dotyczących kilku mikrousług wymagają wdrażanie i uruchamianie całej aplikacji na hoście Docker uruchamiając docker-tworzą w górę (lub porównywalny mechanizmu, jeśli używasz programu orchestrator). Po uruchomieniu całej aplikacji i jej usług, można wykonywać na trasie integracji i testy funkcjonalne.

Istnieje kilka metod, których można użyć. W plik docker-compose.yml, który umożliwia wdrażanie aplikacji (lub podobny migawek, takich jak docker compose.ci.build.yml), na poziomie rozwiązania można rozwinąć punkt wejścia, aby użyć [testu dotnet](https://docs.microsoft.com/dotnet/core/tools/dotnet-test). Umożliwia także innego pliku Redaguj, który będzie uruchomić testy w obrazie docelowych. Przy użyciu innego pliku compose dla testów integracji, które obejmują baz danych do kontenerów i mikrousług, na których, można upewnić się, że powiązanych danych zawsze jest resetowany do stanu pierwotnego przed uruchomieniem testów.

Po skonfigurowaniu i uruchomieniu aplikacji tworzenia może potrwać z punktów przerwania i wyjątków zalet Jeśli używasz programu Visual Studio. Lub uruchom testy integracji automatycznie planowaną CI w Visual Studio Team Services lub inny system CI/CD, który obsługuje kontenery Docker.

>[!div class="step-by-step"]
[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)
