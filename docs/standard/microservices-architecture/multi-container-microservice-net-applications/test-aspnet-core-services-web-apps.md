---
title: Testowanie aplikacji internetowych i usług platformy ASP.NET Core
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Testowanie aplikacji internetowych i usług platformy ASP.NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 2702a273ade0e58ba93d556cfd1ecc5531027f93
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705365"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="51593-103">Testowanie aplikacji internetowych i usług platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51593-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="51593-104">Kontrolery są centralnym elementem interfejsu API platformy ASP.NET Core usług i aplikacji sieci Web programu ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="51593-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="51593-105">W efekcie powinien mieć pewność, której działają zgodnie z przeznaczeniem dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51593-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="51593-106">Testy automatyczne udostępnić Ci ten zaufania i umożliwić wykrycie błędów, zanim dotrą produkcji.</span><span class="sxs-lookup"><span data-stu-id="51593-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="51593-107">Należy przetestować sposób działania oparte na prawidłowe lub nieprawidłowe dane wejściowe kontrolera i test controller odpowiedzi na podstawie wyniku operacji biznesowych, który wykonuje.</span><span class="sxs-lookup"><span data-stu-id="51593-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="51593-108">Jednak tego rodzaju testy powinny być zapisane na mikrousługi:</span><span class="sxs-lookup"><span data-stu-id="51593-108">However, you should have these types of tests for your microservices:</span></span>

-   <span data-ttu-id="51593-109">Testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="51593-109">Unit tests.</span></span> <span data-ttu-id="51593-110">Te upewnij się, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="51593-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="51593-111">Potwierdzenia testowanie składników interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="51593-111">Assertions test the component API.</span></span>

-   <span data-ttu-id="51593-112">Testy integracji.</span><span class="sxs-lookup"><span data-stu-id="51593-112">Integration tests.</span></span> <span data-ttu-id="51593-113">Te upewnij się, że interakcje składnika działać zgodnie z oczekiwaniami względem zewnętrznych artefaktów, takich jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="51593-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="51593-114">Potwierdzenia można przetestować, składnik interfejsu API, interfejs użytkownika lub efekty uboczne akcji, takich jak bazy danych we/wy, rejestrowanie, itp.</span><span class="sxs-lookup"><span data-stu-id="51593-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="51593-115">Testy funkcjonalne dla poszczególnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="51593-115">Functional tests for each microservice.</span></span> <span data-ttu-id="51593-116">Te upewnij się, że aplikacja działa zgodnie z oczekiwaniami z perspektywy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="51593-116">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="51593-117">Usługa badania.</span><span class="sxs-lookup"><span data-stu-id="51593-117">Service tests.</span></span> <span data-ttu-id="51593-118">Te upewnij się, że są przetestowane przypadki użycia usługi end-to-end, w tym testowanie wielu usług, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="51593-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="51593-119">Tego rodzaju kontrolach musisz najpierw przygotować środowisko.</span><span class="sxs-lookup"><span data-stu-id="51593-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="51593-120">W takim przypadku oznacza to uruchamianie usług (na przykład przy użyciu narzędzia docker-compose się).</span><span class="sxs-lookup"><span data-stu-id="51593-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="51593-121">Implementowanie testów jednostkowych dla interfejsów API sieci Web programu ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51593-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="51593-122">Testy jednostkowe polega części aplikacji w izolacji od jego infrastruktura i zależności.</span><span class="sxs-lookup"><span data-stu-id="51593-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="51593-123">Podczas testów jednostkowych można logiką kontrolera, tylko zawartość jednej akcji lub metoda jest testowany, nie zachowanie jego zależności lub samej strukturze.</span><span class="sxs-lookup"><span data-stu-id="51593-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="51593-124">Testy jednostkowe nie wykryto problemów, interakcja między składnikami — to znaczy celem testów integracji.</span><span class="sxs-lookup"><span data-stu-id="51593-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="51593-125">Jako jednostki możesz przetestować akcji kontrolera, upewnij się, że możesz skoncentrować się tylko na ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="51593-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="51593-126">Kontroler testu jednostkowego pozwala uniknąć elementów, takich jak filtrów routingu i wiązania modelu.</span><span class="sxs-lookup"><span data-stu-id="51593-126">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="51593-127">Ponieważ skupiają się na testowanie tylko jedną z rzeczy, testy jednostkowe są zwykle łatwe do zapisania i szybkie uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="51593-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="51593-128">Dobrze napisane zestaw testów jednostkowych mogą być uruchamiane często bez koszty ogólne.</span><span class="sxs-lookup"><span data-stu-id="51593-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="51593-129">Testy jednostkowe są implementowane w oparciu o struktury testów, takimi jak xUnit.net, MSTest, Moq lub NUnit.</span><span class="sxs-lookup"><span data-stu-id="51593-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="51593-130">W ramach aplikacji eShopOnContainers przykładowej aplikacji użyto xUnit.</span><span class="sxs-lookup"><span data-stu-id="51593-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="51593-131">Podczas pisania testów jednostkowych dla kontrolera interfejsu API sieci Web, tworzenia wystąpienia klasy kontrolera bezpośrednio przy użyciu słowa kluczowego new w języku C\#, dzięki czemu testy zostaną uruchomione tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="51593-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="51593-132">Poniższy przykład pokazuje, jak to zrobić, korzystając z [xUnit](https://xunit.github.io/) jako struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="51593-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="51593-133">Implementowanie integracji i testów funkcjonalnych dla poszczególnych mikrousług</span><span class="sxs-lookup"><span data-stu-id="51593-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="51593-134">Jak wspomniano, testy integracji i testów funkcjonalnych mają różnych celów i cele.</span><span class="sxs-lookup"><span data-stu-id="51593-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="51593-135">Jednak sposób implementacji zarówno podczas testowania kontrolerów platformy ASP.NET Core jest podobny, więc w tej sekcji możemy skoncentrować się na testy integracji.</span><span class="sxs-lookup"><span data-stu-id="51593-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="51593-136">Testowanie integracji gwarantuje, że składniki aplikacji działać prawidłowo, jeśli połączone.</span><span class="sxs-lookup"><span data-stu-id="51593-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="51593-137">Integracja obsługuje platformy ASP.NET Core testowania przy użyciu platform testów jednostkowych i testów wbudowanych hosta sieci web, który może służyć do obsługi żądań bez obciążenie sieci.</span><span class="sxs-lookup"><span data-stu-id="51593-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="51593-138">W przeciwieństwie do testów jednostkowych testów integracji często obejmują obaw infrastruktury aplikacji, takich jak bazy danych, system plików, zasobów sieciowych lub żądania sieci web i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="51593-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="51593-139">Testy jednostkowe używane sztuczne elementy testowe lub testowanie obiektów, zamiast tych problemów.</span><span class="sxs-lookup"><span data-stu-id="51593-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="51593-140">Ale testy integracji ma na celu upewnij się, że system działa zgodnie z oczekiwaniami w tych systemach, więc do testowania integracji nie używane sztuczne elementy testowe lub testowanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="51593-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="51593-141">Zamiast tego możesz uwzględnić infrastruktury, takich jak wywołania dostępu lub usługa bazy danych z innych usług.</span><span class="sxs-lookup"><span data-stu-id="51593-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="51593-142">Ponieważ testy integracji wykonywania większych segmenty kodu niż testy jednostkowe i testy integracji zależą elementy infrastruktury, mają zwykle rzędów wolniej niż testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="51593-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="51593-143">W związku z tym to dobry pomysł, aby ograniczyć liczbę testów integracji pisania i uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="51593-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="51593-144">Platforma ASP.NET Core zawiera wbudowany test hosta sieci web używanym do obsługi żądań HTTP bez obciążenie sieci, co oznacza, że mogą szybciej uruchamiania tych testów, korzystając z hosta sieci web rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="51593-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="51593-145">Test hosta sieci web jest dostępna w składniku NuGet jako Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="51593-145">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="51593-146">On mogą być dodawane do projektów testów integracji i używane do hosta platformy ASP.NET Core aplikacje.</span><span class="sxs-lookup"><span data-stu-id="51593-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="51593-147">Jak widać w poniższym kodzie, tworząc testy integracji dla platformy ASP.NET Core kontrolerów, tworzy się kontrolery, za pośrednictwem hosta testów.</span><span class="sxs-lookup"><span data-stu-id="51593-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="51593-148">To jest porównywalna do żądania HTTP, ale działa szybciej.</span><span class="sxs-lookup"><span data-stu-id="51593-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="51593-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="51593-149">Additional resources</span></span>

-   <span data-ttu-id="51593-150">**Steve Smith. Kontrolery testów** (platformy ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="51593-150">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="51593-151">**Steve Smith. Testowanie integracji** (platformy ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)</span><span class="sxs-lookup"><span data-stu-id="51593-151">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)</span></span>

-   <span data-ttu-id="51593-152">**Testowanie jednostek w .NET Core za pomocą polecenia dotnet test**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="51593-152">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span></span>

-   <span data-ttu-id="51593-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="51593-153">**xUnit.net**.</span></span> <span data-ttu-id="51593-154">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="51593-154">Official site.</span></span>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   <span data-ttu-id="51593-155">**O teście jednostkowym.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="51593-155">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="51593-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="51593-156">**Moq**.</span></span> <span data-ttu-id="51593-157">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="51593-157">GitHub repo.</span></span>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   <span data-ttu-id="51593-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="51593-158">**NUnit**.</span></span> <span data-ttu-id="51593-159">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="51593-159">Official site.</span></span>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="51593-160">Wdrażanie usługi testów na aplikację obsługującą wiele kontenerów</span><span class="sxs-lookup"><span data-stu-id="51593-160">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="51593-161">Jak wspomniano wcześniej, podczas testowania aplikacji obsługującej wiele kontenerów, wszystkie mikrousługi muszą działać w ramach klastra hostów lub kontenera Docker.</span><span class="sxs-lookup"><span data-stu-id="51593-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="51593-162">Testy usług end-to-end, obejmujących wiele operacji obejmujących wiele mikrousług wymagają jej wdrażanie i uruchamianie całej aplikacji na hoście platformy Docker za pomocą platformy docker-compose up (lub porównywalny mechanizmu, jeśli używasz programu orchestrator).</span><span class="sxs-lookup"><span data-stu-id="51593-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="51593-163">Gdy całej aplikacji i wszystkich jego usług jest uruchomiona, można wykonać end-to-end integracji i testów funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="51593-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="51593-164">Istnieje kilka metod, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="51593-164">There are a few approaches you can use.</span></span> <span data-ttu-id="51593-165">W pliku docker-compose.yml, który zostanie użyty do wdrożenia aplikacji (lub podobnych, takich jak docker-compose.ci.build.yml), na poziomie rozwiązania można rozwinąć punktu wejścia, aby użyć [polecenia dotnet test](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="51593-165">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="51593-166">Można również użyć innego pliku compose, która może uruchomić testy na ilustracji, które są przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="51593-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="51593-167">Przy użyciu innego pliku compose dla testów integracyjnych, które obejmuje z mikrousług i bazami danych w kontenerach, należy upewnić się, że powiązanych danych zawsze jest resetowany do stanu pierwotnego przed uruchomieniem testów.</span><span class="sxs-lookup"><span data-stu-id="51593-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="51593-168">Po skonfigurowaniu i uruchomieniu aplikacji compose możesz korzystać z zalet punktów przerwania i wyjątków w przypadku korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51593-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="51593-169">Lub uruchomić testy integracji automatycznie w potoku ciągłej integracji w usługach infrastruktury DevOps platformy Azure lub inny system ciągłej integracji/ciągłego wdrażania, który obsługuje kontenery platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="51593-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="51593-170">[Poprzednie](subscribe-events.md)
[dalej](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="51593-170">[Previous](subscribe-events.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
