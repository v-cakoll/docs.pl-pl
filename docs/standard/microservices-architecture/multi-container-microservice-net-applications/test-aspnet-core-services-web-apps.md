---
title: Testowanie platformy ASP.NET Core usług i aplikacji sieci web
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Testowanie platformy ASP.NET Core usług i aplikacji sieci web
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
ms.openlocfilehash: 596f588aae8c0814e5b40d29c4bf5723f944c5ac
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="67fad-104">Testowanie platformy ASP.NET Core usług i aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="67fad-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="67fad-105">Kontrolery są środkowej części interfejsu API platformy ASP.NET Core usług i aplikacji sieci Web programu ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="67fad-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="67fad-106">Tak powinien mieć pewność, które działają zgodnie z przeznaczeniem dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67fad-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="67fad-107">Testy automatyczne może udostępnić tym zaufania i może szybko wykrywać błędy przed dotarciem produkcji.</span><span class="sxs-lookup"><span data-stu-id="67fad-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="67fad-108">Należy przetestować, jak kontroler ma zachowywać się oparte na prawidłowe lub nieprawidłowe dane wejściowe i na podstawie wyniku prowadzonej działalności, którą wykonuje odpowiedzi kontrolera testu.</span><span class="sxs-lookup"><span data-stu-id="67fad-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="67fad-109">Jednak powinny mieć następujące typy testów z mikrousług:</span><span class="sxs-lookup"><span data-stu-id="67fad-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="67fad-110">Testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="67fad-110">Unit tests.</span></span> <span data-ttu-id="67fad-111">Te upewnij się, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="67fad-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="67fad-112">Potwierdzenia testu API składnika.</span><span class="sxs-lookup"><span data-stu-id="67fad-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="67fad-113">Testy integracji.</span><span class="sxs-lookup"><span data-stu-id="67fad-113">Integration tests.</span></span> <span data-ttu-id="67fad-114">Te upewnij się, że składnik interakcje działać zgodnie z oczekiwaniami przed zewnętrznych artefaktów, takich jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="67fad-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="67fad-115">Potwierdzenia można przetestować składnika interfejsu API, interfejsu użytkownika lub efektami ubocznymi akcji, takich jak bazy danych we/wy, rejestrowanie, itp.</span><span class="sxs-lookup"><span data-stu-id="67fad-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="67fad-116">Testy funkcjonalne dla każdego mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="67fad-116">Functional tests for each microservice.</span></span> <span data-ttu-id="67fad-117">Te upewnij się, że aplikacja działa zgodnie z oczekiwaniami z perspektywy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67fad-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="67fad-118">Testy usługi.</span><span class="sxs-lookup"><span data-stu-id="67fad-118">Service tests.</span></span> <span data-ttu-id="67fad-119">Te upewnij się, sprawdzane są przypadki użycia usługi end-to-end, łącznie z testowaniem wielu usług w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="67fad-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="67fad-120">Dla tego typu testowania musisz najpierw przygotować środowisko.</span><span class="sxs-lookup"><span data-stu-id="67fad-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="67fad-121">W takim przypadku oznacza to, uruchamiania usług (na przykład przy użyciu rozwiązania docker-compose się).</span><span class="sxs-lookup"><span data-stu-id="67fad-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="67fad-122">Implementującej testów jednostkowych dla interfejsów API platformy ASP.NET Core sieci Web</span><span class="sxs-lookup"><span data-stu-id="67fad-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="67fad-123">Testy jednostkowe obejmuje testowania części aplikacji w izolacji od jego infrastruktury i zależności.</span><span class="sxs-lookup"><span data-stu-id="67fad-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="67fad-124">Podczas testu jednostkowego możesz logiką kontrolera, tylko zawartość jednej akcji lub jest testowana metoda, nie zachowanie z jego zależności lub struktury, sam.</span><span class="sxs-lookup"><span data-stu-id="67fad-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="67fad-125">Testy jednostkowe Nie wykrywaj problemy w interakcji między składnikami — to znaczy celem testów integracji.</span><span class="sxs-lookup"><span data-stu-id="67fad-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="67fad-126">Jako jednostki można przetestować akcji kontrolera, upewnij się, że można skupić się tylko na ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="67fad-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="67fad-127">Kontroler testu jednostkowego pozwala uniknąć np. filtry routingu i wiązania modelu.</span><span class="sxs-lookup"><span data-stu-id="67fad-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="67fad-128">Ponieważ one skupić się na tylko jeden element testowania, testy jednostkowe są zwykle proste do zapisu i szybkie uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="67fad-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="67fad-129">Dobrze napisane zbiór testy jednostkowe mogą być uruchamiane często bez znacznie obciążenie.</span><span class="sxs-lookup"><span data-stu-id="67fad-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="67fad-130">Testy jednostkowe są implementowane oparte na platformach testu, takie jak xUnit.net, MSTest, Moq lub NUnit.</span><span class="sxs-lookup"><span data-stu-id="67fad-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="67fad-131">EShopOnContainers przykładowej aplikacji użyto XUnit.</span><span class="sxs-lookup"><span data-stu-id="67fad-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="67fad-132">Podczas pisania testów jednostkowych dla kontrolera interfejsu API sieci Web, można utworzyć wystąpienia klasy kontrolera, bezpośrednio za pomocą nowych słów kluczowych w języku C\#, dzięki czemu tak szybko jak to możliwe uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="67fad-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="67fad-133">Poniższy przykład pokazuje, jak na przykład przy użyciu [XUnit](https://xunit.github.io/) jako struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="67fad-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="67fad-134">Wdrażanie integracji i testy funkcjonalne dla każdego mikrousługi</span><span class="sxs-lookup"><span data-stu-id="67fad-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="67fad-135">Jak wspomniano, testów integracji i funkcjonalności mają różnych celów i cele.</span><span class="sxs-lookup"><span data-stu-id="67fad-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="67fad-136">Jednak sposób implementowania zarówno podczas testowania kontrolery ASP.NET Core jest podobny, więc w tej sekcji możemy skoncentrować się na testów integracji.</span><span class="sxs-lookup"><span data-stu-id="67fad-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="67fad-137">Testowanie integracji gwarantuje, że składniki aplikacji działać prawidłowo, jeśli połączone.</span><span class="sxs-lookup"><span data-stu-id="67fad-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="67fad-138">Integracja obsługuje platformy ASP.NET Core testowania przy użyciu platform testów jednostkowych i wbudowane testu hosta sieci web, który może służyć do obsługi żądań bez obciążenie sieci.</span><span class="sxs-lookup"><span data-stu-id="67fad-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="67fad-139">W przeciwieństwie do przeprowadzania testów jednostkowych integracji testy obejmują często dotyczy infrastruktury aplikacji, takich jak bazy danych, system plików, zasobów sieciowych lub żądania sieci web i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="67fad-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="67fad-140">Testy jednostkowe Użyj elementów sztucznych lub mock obiektów zamiast te problemy.</span><span class="sxs-lookup"><span data-stu-id="67fad-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="67fad-141">Ale testy integracji ma na celu potwierdzenie, że system działa zgodnie z oczekiwaniami w przypadku tych systemów, do integracji testowania nie używać elementów sztucznych ani mock obiektów.</span><span class="sxs-lookup"><span data-stu-id="67fad-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="67fad-142">Zamiast tego możesz uwzględnić infrastruktury, takie jak wywołania dostępu lub usługi bazy danych z innych usług.</span><span class="sxs-lookup"><span data-stu-id="67fad-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="67fad-143">Ponieważ testy integracji wykonywania większych segmenty kodu niż testy jednostkowe i testy integracji zależne elementy infrastruktury, mają zwykle rzędów wolniej niż testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="67fad-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="67fad-144">W związku z tym jest dobrym rozwiązaniem, aby ograniczyć liczbę testów integracji zapisu i uruchom.</span><span class="sxs-lookup"><span data-stu-id="67fad-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="67fad-145">Platformy ASP.NET Core obejmuje wbudowane testu sieci web hosta, który może służyć do obsługi żądań HTTP bez obciążenie sieci, co oznacza, że można uruchomić te testy szybciej używając hosta sieci web rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="67fad-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="67fad-146">Host testów sieci web jest dostępna w składniku NuGet jako Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="67fad-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="67fad-147">Można dodać do integracji projekty testowe, a używany do hostowania platformy ASP.NET Core aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67fad-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="67fad-148">Jak widać w poniższym kodzie podczas tworzenia testów integracji dla platformy ASP.NET Core kontrolerów, można utworzyć wystąpienia kontrolerów przez hosta testów.</span><span class="sxs-lookup"><span data-stu-id="67fad-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="67fad-149">To jest porównywalna do żądania HTTP, ale działa szybciej.</span><span class="sxs-lookup"><span data-stu-id="67fad-149">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="67fad-150">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="67fad-150">Additional resources</span></span>

-   <span data-ttu-id="67fad-151">**Steve Smith. Testowanie kontrolerów** (platformy ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="67fad-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="67fad-152">**Steve Smith. Testowanie integracji** (platformy ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="67fad-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="67fad-153">**Jednostka testowania w .NET Core za pomocą testu dotnet**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="67fad-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span></span>

-   <span data-ttu-id="67fad-154">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="67fad-154">**xUnit.net**.</span></span> <span data-ttu-id="67fad-155">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="67fad-155">Official site.</span></span>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   <span data-ttu-id="67fad-156">**Teście jednostkowym.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="67fad-156">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="67fad-157">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="67fad-157">**Moq**.</span></span> <span data-ttu-id="67fad-158">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="67fad-158">GitHub repo.</span></span>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   <span data-ttu-id="67fad-159">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="67fad-159">**NUnit**.</span></span> <span data-ttu-id="67fad-160">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="67fad-160">Official site.</span></span>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="67fad-161">Wdrażanie usługi testów w kontenerze wielu aplikacji</span><span class="sxs-lookup"><span data-stu-id="67fad-161">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="67fad-162">Jak wspomniano wcześniej, podczas testowania aplikacji kontenera usługi, wszystkie mikrousług musi być uruchomiona w klastrze hosta lub kontener Docker.</span><span class="sxs-lookup"><span data-stu-id="67fad-162">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="67fad-163">Testy na trasie usługi, obejmujące wiele operacji dotyczących kilku mikrousług wymagają wdrażanie i uruchamianie całej aplikacji na hoście Docker uruchamiając docker-tworzą w górę (lub porównywalny mechanizmu, jeśli używasz programu orchestrator).</span><span class="sxs-lookup"><span data-stu-id="67fad-163">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="67fad-164">Po uruchomieniu całej aplikacji i jej usług, można wykonywać na trasie integracji i testy funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="67fad-164">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="67fad-165">Istnieje kilka metod, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="67fad-165">There are a few approaches you can use.</span></span> <span data-ttu-id="67fad-166">W plik docker-compose.yml, który umożliwia wdrażanie aplikacji (lub podobny migawek, takich jak docker compose.ci.build.yml), na poziomie rozwiązania można rozwinąć punkt wejścia, aby użyć [testu dotnet](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="67fad-166">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="67fad-167">Umożliwia także innego pliku Redaguj, który będzie uruchomić testy w obrazie docelowych.</span><span class="sxs-lookup"><span data-stu-id="67fad-167">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="67fad-168">Przy użyciu innego pliku compose dla testów integracji, które obejmują baz danych do kontenerów i mikrousług, na których, można upewnić się, że powiązanych danych zawsze jest resetowany do stanu pierwotnego przed uruchomieniem testów.</span><span class="sxs-lookup"><span data-stu-id="67fad-168">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="67fad-169">Po skonfigurowaniu i uruchomieniu aplikacji tworzenia może potrwać z punktów przerwania i wyjątków zalet Jeśli używasz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67fad-169">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="67fad-170">Lub uruchom testy integracji automatycznie planowaną CI w Visual Studio Team Services lub inny system CI/CD, który obsługuje kontenery Docker.</span><span class="sxs-lookup"><span data-stu-id="67fad-170">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="67fad-171">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="67fad-171">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
