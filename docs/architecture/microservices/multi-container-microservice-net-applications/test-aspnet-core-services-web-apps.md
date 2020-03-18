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
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="27f0e-103">Testowanie aplikacji internetowych i usług ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="27f0e-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="27f0e-104">Kontrolery są centralną częścią każdej ASP.NET podstawowej usługi API i ASP.NET aplikacji Sieci Web MVC.</span><span class="sxs-lookup"><span data-stu-id="27f0e-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="27f0e-105">W związku z tym należy mieć pewność, że zachowują się zgodnie z przeznaczeniem dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27f0e-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="27f0e-106">Zautomatyzowane testy mogą zapewnić ci to zaufanie i wykrywać błędy, zanim dotrą do produkcji.</span><span class="sxs-lookup"><span data-stu-id="27f0e-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="27f0e-107">Należy przetestować, jak kontroler zachowuje się na podstawie prawidłowych lub nieprawidłowych danych wejściowych i przetestować odpowiedzi kontrolera na podstawie wyniku operacji biznesowej, którą wykonuje.</span><span class="sxs-lookup"><span data-stu-id="27f0e-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="27f0e-108">Jednak powinny mieć te typy testów dla mikrousług:</span><span class="sxs-lookup"><span data-stu-id="27f0e-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="27f0e-109">Testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="27f0e-109">Unit tests.</span></span> <span data-ttu-id="27f0e-110">Zapewniają one, że poszczególne składniki aplikacji działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="27f0e-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="27f0e-111">Potwierdzenia przetestować składnik api.</span><span class="sxs-lookup"><span data-stu-id="27f0e-111">Assertions test the component API.</span></span>

- <span data-ttu-id="27f0e-112">Testy integracji.</span><span class="sxs-lookup"><span data-stu-id="27f0e-112">Integration tests.</span></span> <span data-ttu-id="27f0e-113">Zapewniają one, że interakcje składników działają zgodnie z oczekiwaniami w odniesieniu do zewnętrznych artefaktów, takich jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="27f0e-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="27f0e-114">Potwierdzenia można przetestować składnik api, interfejsu użytkownika lub skutki uboczne działań, takich jak we/wy bazy danych, rejestrowania, itp.</span><span class="sxs-lookup"><span data-stu-id="27f0e-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="27f0e-115">Testy funkcjonalne dla każdej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="27f0e-115">Functional tests for each microservice.</span></span> <span data-ttu-id="27f0e-116">Zapewniają one, że aplikacja działa zgodnie z oczekiwaniami z punktu widzenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="27f0e-116">These ensure that the application works as expected from the user’s perspective.</span></span>

- <span data-ttu-id="27f0e-117">Testy serwisowe.</span><span class="sxs-lookup"><span data-stu-id="27f0e-117">Service tests.</span></span> <span data-ttu-id="27f0e-118">Zapewniają one, że przypadki użycia usługi end-to-end, w tym testowanie wielu usług w tym samym czasie, są testowane.</span><span class="sxs-lookup"><span data-stu-id="27f0e-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="27f0e-119">Dla tego typu testów należy najpierw przygotować środowisko.</span><span class="sxs-lookup"><span data-stu-id="27f0e-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="27f0e-120">W takim przypadku oznacza to uruchomienie usług (na przykład przy użyciu docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="27f0e-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="27f0e-121">Implementowanie testów jednostkowych dla ASP.NET podstawowych interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="27f0e-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="27f0e-122">Testowanie jednostkowe polega na testowaniu części aplikacji w izolacji od jej infrastruktury i zależności.</span><span class="sxs-lookup"><span data-stu-id="27f0e-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="27f0e-123">Podczas testowania jednostek logiki kontrolera, tylko zawartość pojedynczej akcji lub metody jest testowany, a nie zachowanie jego zależności lub samej struktury.</span><span class="sxs-lookup"><span data-stu-id="27f0e-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="27f0e-124">Testy jednostkowe nie wykrywają problemów w interakcji między składnikami — jest to cel testowania integracji.</span><span class="sxs-lookup"><span data-stu-id="27f0e-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="27f0e-125">Podczas testowania jednostek akcji kontrolera upewnij się, że skupiasz się tylko na ich zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="27f0e-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="27f0e-126">Test jednostki kontrolera pozwala uniknąć takich elementów, jak filtry, routing lub powiązanie modelu (mapowanie danych żądania do ViewModel lub DTO).</span><span class="sxs-lookup"><span data-stu-id="27f0e-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="27f0e-127">Ponieważ koncentrują się one na testowaniu tylko jednej rzeczy, testy jednostkowe są zazwyczaj proste do napisania i szybkie do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="27f0e-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="27f0e-128">Dobrze napisany zestaw testów jednostkowych można uruchomić często bez większego narzutów.</span><span class="sxs-lookup"><span data-stu-id="27f0e-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="27f0e-129">Testy jednostkowe są implementowane na podstawie struktur testowych, takich jak xUnit.net, MSTest, Moq lub NUnit.</span><span class="sxs-lookup"><span data-stu-id="27f0e-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="27f0e-130">Dla eShopOnContainers przykładowej aplikacji używamy xUnit.</span><span class="sxs-lookup"><span data-stu-id="27f0e-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="27f0e-131">Podczas pisania testu jednostkowego dla kontrolera interfejsu API sieci Web, można utworzyć\#wystąpienia klasy kontrolera bezpośrednio przy użyciu nowego słowa kluczowego w C , tak, że test będzie działać tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="27f0e-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="27f0e-132">W poniższym przykładzie pokazano, jak to zrobić podczas korzystania [z xUnit](https://xunit.github.io/) jako framework testów.</span><span class="sxs-lookup"><span data-stu-id="27f0e-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="27f0e-133">Implementowanie testów integracji i funkcjonalności dla każdej mikrousługi</span><span class="sxs-lookup"><span data-stu-id="27f0e-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="27f0e-134">Jak wspomniano, testy integracyjne i testy funkcjonalne mają różne cele i cele.</span><span class="sxs-lookup"><span data-stu-id="27f0e-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="27f0e-135">Jednak sposób implementowania zarówno podczas testowania kontrolerów ASP.NET Core jest podobny, więc w tej sekcji koncentrujemy się na testach integracji.</span><span class="sxs-lookup"><span data-stu-id="27f0e-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="27f0e-136">Testowanie integracji zapewnia, że składniki aplikacji działają poprawnie po złożeniu.</span><span class="sxs-lookup"><span data-stu-id="27f0e-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="27f0e-137">ASP.NET Core obsługuje testowanie integracji przy użyciu platform testów jednostkowych i wbudowanego testowego hosta internetowego, który może służyć do obsługi żądań bez narzutów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="27f0e-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="27f0e-138">W przeciwieństwie do testów jednostkowych testy integracji często obejmują problemy z infrastrukturą aplikacji, takie jak baza danych, system plików, zasoby sieciowe lub żądania i odpowiedzi sieci web.</span><span class="sxs-lookup"><span data-stu-id="27f0e-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="27f0e-139">Testy jednostkowe używają podróbek lub makiety obiektów w miejsce tych problemów.</span><span class="sxs-lookup"><span data-stu-id="27f0e-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="27f0e-140">Ale celem testów integracji jest potwierdzenie, że system działa zgodnie z oczekiwaniami z tymi systemami, więc do testowania integracji nie należy używać podróbek lub makiety obiektów.</span><span class="sxs-lookup"><span data-stu-id="27f0e-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="27f0e-141">Zamiast tego należy dołączyć infrastruktury, takich jak dostęp do bazy danych lub wywołanie usługi z innych usług.</span><span class="sxs-lookup"><span data-stu-id="27f0e-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="27f0e-142">Ponieważ testy integracji wykonywania większych segmentów kodu niż testy jednostkowe, a ponieważ testy integracji opierają się na elementy infrastruktury, wydają się być rzędy wielkości wolniej niż testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="27f0e-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="27f0e-143">W związku z tym jest dobrym pomysłem, aby ograniczyć liczbę testów integracji, które piszesz i uruchamiasz.</span><span class="sxs-lookup"><span data-stu-id="27f0e-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="27f0e-144">ASP.NET Core zawiera wbudowany testowy host internetowy, który może służyć do obsługi żądań HTTP bez narzutów sieciowych, co oznacza, że można uruchomić te testy szybciej niż podczas korzystania z prawdziwego hosta sieci web.</span><span class="sxs-lookup"><span data-stu-id="27f0e-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster than when using a real web host.</span></span> <span data-ttu-id="27f0e-145">Test web host (TestServer) jest dostępny w składniku NuGet jako Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="27f0e-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="27f0e-146">Można go dodać do projektów testów integracji i służyć do obsługi ASP.NET podstawowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27f0e-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="27f0e-147">Jak widać w poniższym kodzie, podczas tworzenia testów integracji dla kontrolerów ASP.NET Core, można utworzyć wystąpienia kontrolerów za pośrednictwem hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="27f0e-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="27f0e-148">Jest to porównywalne do żądania HTTP, ale działa szybciej.</span><span class="sxs-lookup"><span data-stu-id="27f0e-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="27f0e-149">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="27f0e-149">Additional resources</span></span>

- <span data-ttu-id="27f0e-150">**Steve Smith. Testowanie kontrolerów** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="27f0e-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="27f0e-151">**Steve Smith. Testowanie integracji** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="27f0e-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="27f0e-152">**Testowanie jednostkowe w .NET Core przy użyciu testu dotnet** </span><span class="sxs-lookup"><span data-stu-id="27f0e-152">**Unit testing in .NET Core using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="27f0e-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="27f0e-153">**xUnit.net**.</span></span> <span data-ttu-id="27f0e-154">Oficjalna strona internetowa.</span><span class="sxs-lookup"><span data-stu-id="27f0e-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="27f0e-155">**Podstawy testu jednostkowego.**</span><span class="sxs-lookup"><span data-stu-id="27f0e-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="27f0e-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="27f0e-156">**Moq**.</span></span> <span data-ttu-id="27f0e-157">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="27f0e-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="27f0e-158">**Jednostka .**</span><span class="sxs-lookup"><span data-stu-id="27f0e-158">**NUnit**.</span></span> <span data-ttu-id="27f0e-159">Oficjalna strona internetowa.</span><span class="sxs-lookup"><span data-stu-id="27f0e-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="27f0e-160">Wdrażanie testów serwisowych w aplikacji wielokontenerowej</span><span class="sxs-lookup"><span data-stu-id="27f0e-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="27f0e-161">Jak wspomniano wcześniej podczas testowania aplikacji wielokontenerowych, wszystkie mikrousługi muszą być uruchomione w hosta platformy Docker lub klastra kontenera.</span><span class="sxs-lookup"><span data-stu-id="27f0e-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="27f0e-162">Testy usługi end-to-end, które obejmują wiele operacji obejmujących kilka mikrousług wymagają wdrożenia i uruchomienia całej aplikacji w hoście platformy Docker przez uruchomienie docker-compose up (lub porównywalny mechanizm, jeśli używasz koordynatora).</span><span class="sxs-lookup"><span data-stu-id="27f0e-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="27f0e-163">Po uruchomieniu całej aplikacji i wszystkich jej usług można wykonać integrację end-to-end i testy funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="27f0e-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="27f0e-164">Istnieje kilka podejść, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="27f0e-164">There are a few approaches you can use.</span></span> <span data-ttu-id="27f0e-165">W pliku docker-compose.yml, którego używasz do wdrażania aplikacji na poziomie rozwiązania, można rozwinąć punkt wejścia, aby użyć [testu dotnet](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="27f0e-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="27f0e-166">Można również użyć innego pliku redagowania, który uruchamiałby testy na obrazie, na który kierujesz reklamy.</span><span class="sxs-lookup"><span data-stu-id="27f0e-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="27f0e-167">Za pomocą innego pliku redagowania dla testów integracji, który zawiera mikrousług i baz danych w kontenerach, można upewnić się, że powiązane dane są zawsze resetowane do stanu pierwotnego przed uruchomieniem testów.</span><span class="sxs-lookup"><span data-stu-id="27f0e-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="27f0e-168">Po uruchomieniu aplikacji redagowania można skorzystać z punktów przerwania i wyjątków, jeśli używasz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27f0e-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="27f0e-169">Lub można uruchomić testy integracji automatycznie w potoku ciągłej integracji w usłudze Azure DevOps Services lub innego systemu ciągłej integracji/cd, który obsługuje kontenery platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="27f0e-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="27f0e-170">Testowanie w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="27f0e-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="27f0e-171">Testy aplikacji referencyjnej (eShopOnContainers) zostały niedawno zrestrukturyzowane, a teraz istnieją cztery kategorie:</span><span class="sxs-lookup"><span data-stu-id="27f0e-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="27f0e-172">**Testy jednostkowe,** po prostu stare regularne testy jednostkowe, zawarte w **{MicroserviceName}. Projekty testów jednostkowych**</span><span class="sxs-lookup"><span data-stu-id="27f0e-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="27f0e-173">**Mikrousługi funkcjonalne/integracyjne testy**, z przypadków testowych obejmujących infrastrukturę dla każdej mikrousługi, ale odizolowane od innych i są zawarte w **{MicroserviceName}. FunctionalTests** projektów.</span><span class="sxs-lookup"><span data-stu-id="27f0e-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="27f0e-174">**Testy funkcjonalności/integracji aplikacji**, które koncentrują się na integracji mikrousług, z przypadków testowych, które wywierają kilka mikrousług.</span><span class="sxs-lookup"><span data-stu-id="27f0e-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="27f0e-175">Testy te znajdują się w projekcie **Application.FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="27f0e-175">These tests are located in project **Application.FunctionalTests**.</span></span>

<span data-ttu-id="27f0e-176">Test jednostkowy i integracyjny na mikrousługę są zawarte w folderze testowym w każdej mikrousługi i aplikacji testów obciążenia są zawarte w folderze testowym w folderze rozwiązania, jak pokazano na rysunku 6-25.</span><span class="sxs-lookup"><span data-stu-id="27f0e-176">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Zrzut ekranu przedstawiający punkt vs wskazujący niektóre projekty testowe w rozwiązaniu.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="27f0e-178">**Rysunek 6-25**.</span><span class="sxs-lookup"><span data-stu-id="27f0e-178">**Figure 6-25**.</span></span> <span data-ttu-id="27f0e-179">Testowanie struktury folderów w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="27f0e-179">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="27f0e-180">Mikrousługi i aplikacji funkcjonalnych/integracji testy są uruchamiane z programu Visual Studio, przy użyciu regularnych testów runner, ale najpierw trzeba uruchomić wymagane usługi infrastruktury za pomocą zestawu plików docker-compose zawarte w folderze testowym rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="27f0e-180">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="27f0e-181">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="27f0e-181">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="27f0e-182">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="27f0e-182">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="27f0e-183">Tak więc, aby uruchomić testy funkcjonalne/integracyjne należy najpierw uruchomić to polecenie z folderu testowego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="27f0e-183">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="27f0e-184">Jak widać, te pliki docker-compose tylko uruchomić Redis, RabbitMQ, SQL Server i MongoDB mikrousług.</span><span class="sxs-lookup"><span data-stu-id="27f0e-184">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="27f0e-185">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="27f0e-185">Additional resources</span></span>

- <span data-ttu-id="27f0e-186">**Testuje plik README** na reppo eShopOnContainers w githubie </span><span class="sxs-lookup"><span data-stu-id="27f0e-186">**Tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="27f0e-187">**Załaduj testów pliku README** na reppo eShopOnContainers w githubie </span><span class="sxs-lookup"><span data-stu-id="27f0e-187">**Load tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="27f0e-188">[Poprzedni](subscribe-events.md)
> [następny](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="27f0e-188">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
