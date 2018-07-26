---
title: Tworzenie platformy ASP.NET Core MVC aplikacji
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Tworzenie aplikacji programu ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 2fd3eb1e123959130884b96ee9d2e59b83c41b0a
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404648"
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="a3472-103">Tworzenie platformy ASP.NET Core MVC aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3472-103">Develop ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="a3472-104">"Należy nie można pobrać jej prawej po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a3472-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="a3472-105">To wszechobecne uzyskać odpowiednie ostatniego".</span><span class="sxs-lookup"><span data-stu-id="a3472-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="a3472-106">_— Andrew Hunt i Davida Thomas_</span><span class="sxs-lookup"><span data-stu-id="a3472-106">_- Andrew Hunt and David Thomas_</span></span>

<span data-ttu-id="a3472-107">Platforma ASP.NET Core to dla wielu platform, typu open source umożliwiająca tworzenie aplikacji nowoczesne rozwiązania sieci web, które są zoptymalizowane pod kątem chmury.</span><span class="sxs-lookup"><span data-stu-id="a3472-107">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="a3472-108">Aplikacje platformy ASP.NET Core to uproszczone, modułowe, z wbudowaną obsługę wstrzykiwania zależności, umożliwiając większe możliwości testowania i łatwość konserwacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-108">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling greater testability and maintainability.</span></span> <span data-ttu-id="a3472-109">W połączeniu z MVC, który obsługuje tworzenie nowoczesnych internetowych interfejsów API oprócz aplikacji opartych na widok, platforma ASP.NET Core to Rozbudowana platforma umożliwiające tworzenie aplikacji sieci web enterprise.</span><span class="sxs-lookup"><span data-stu-id="a3472-109">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="a3472-110">Mapowania żądania do odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="a3472-110">Mapping requests to responses</span></span>

<span data-ttu-id="a3472-111">Centrum w aplikacji platformy ASP.NET Core żądania przychodzące są mapowane na wychodzące odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="a3472-111">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="a3472-112">Na niskim poziomie odbywa się za pomocą oprogramowania pośredniczącego i proste aplikacje platformy ASP.NET Core i mikrousług może składać się wyłącznie z niestandardowego oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="a3472-112">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="a3472-113">Korzystając z platformy ASP.NET Core MVC, można pracować na nieco wyższy poziom, myśl pod względem _trasy_, _kontrolerów_, i _akcje_.</span><span class="sxs-lookup"><span data-stu-id="a3472-113">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of _routes_, _controllers_, and _actions_.</span></span> <span data-ttu-id="a3472-114">Każdego żądania przychodzącego jest porównywana z tabeli routingu aplikacji, a jeśli znajduje się trasy zgodne, skojarzona metoda akcji (należące do kontrolera) jest wywoływana, aby obsłużyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3472-114">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="a3472-115">Jeśli żadna trasa dopasowania zostanie znaleziony, jest wywoływana procedura obsługi błędów (w tym przypadku zwracając wynik NotFound).</span><span class="sxs-lookup"><span data-stu-id="a3472-115">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="a3472-116">Konwencjonalne tras i/lub tras atrybutów, można użyć aplikacji ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="a3472-116">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="a3472-117">Konwencjonalne trasy są definiowane w kodzie, określając routing _konwencje_ przy użyciu składni podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a3472-117">Conventional routes are defined in code, specifying routing _conventions_ using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="a3472-118">W tym przykładzie dodano trasę o nazwie "domyślna" do tabeli routingu.</span><span class="sxs-lookup"><span data-stu-id="a3472-118">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="a3472-119">Definiuje szablon trasy z symbolami zastępczymi _kontrolera_, _akcji_, i _identyfikator_. Symbole zastępcze kontrolerów i akcji ma określony domyślny ("Home" i "Index", odpowiednio), a symbol zastępczy identyfikator jest opcjonalny (na mocy niniejszej "?" zastosowano).</span><span class="sxs-lookup"><span data-stu-id="a3472-119">It defines a route template with placeholders for _controller_, _action_, and _id_. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="a3472-120">Konwencji zdefiniowane w tym miejscu stany odpowiadające pierwszej części żądania do nazwy kontrolera, a druga sekcja do akcji, a następnie w razie potrzeby trzeciej części będzie reprezentować parametru identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a3472-120">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="a3472-121">Konwencjonalne trasy są zazwyczaj definiowane w jednym miejscu aplikacji, takich jak w metodzie Konfiguruj w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="a3472-121">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="a3472-122">Tras atrybutów są stosowane do kontrolerów i akcji bezpośrednio, a nie określono globalnie.</span><span class="sxs-lookup"><span data-stu-id="a3472-122">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="a3472-123">To ma tę zaletę, dzięki czemu mogą znacznie szybciej odnajdywać podczas poszukujesz w konkretnej metody, ale oznacza, że informacje routingu nie są przechowywane w jednym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-123">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="a3472-124">Za pomocą tras atrybutów można można łatwo określić wiele tras dla danej akcji, a także połączyć tras między kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-124">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="a3472-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a3472-125">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

<span data-ttu-id="a3472-126">Można określić trasy w [HttpGet] i podobne atrybuty, unikając konieczności dodawania oddziel atrybuty [trasy].</span><span class="sxs-lookup"><span data-stu-id="a3472-126">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route] attributes.</span></span> <span data-ttu-id="a3472-127">Tras atrybutów można także użyć tokenów, aby zmniejszyć liczbę powtórzeń nazwy kontrolera lub akcji, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="a3472-127">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

<span data-ttu-id="a3472-128">Gdy danego żądania został dopasowany do trasy, ale przed akcją, metoda jest wywoływana, ASP.NET Core MVC wykona [wiązanie modelu](/aspnet/core/mvc/models/model-binding) i [Walidacja modelu](/aspnet/core/mvc/models/validation) na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3472-128">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](/aspnet/core/mvc/models/model-binding) and [model validation](/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="a3472-129">Wiązanie modelu jest odpowiedzialny za konwersji danych przychodzących HTTP do typów .NET określane jako parametry metody akcji, które ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="a3472-129">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="a3472-130">Na przykład jeśli metoda akcji oczekuje parametru id int, wiązania modelu będzie podejmowana próba udostępnienia tego parametru z wartością podana jako część żądania.</span><span class="sxs-lookup"><span data-stu-id="a3472-130">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="a3472-131">Aby to zrobić, wiązanie modelu szuka wartości przesłanego formularza, wartości trasy, sama i wartości ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="a3472-131">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="a3472-132">Przy założeniu, że wartość zostanie znaleziony, zostanie przekonwertowany na liczbę całkowitą przed przekazaniem do metody akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-132">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="a3472-133">Po powiązaniu modelu, ale przed wywołaniem metody akcji występuje weryfikacji modelu.</span><span class="sxs-lookup"><span data-stu-id="a3472-133">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="a3472-134">Sprawdzanie poprawności modelu korzysta z opcjonalnych atrybutów na typ modelu, a może pomóc upewnić się, że obiekt podany model spełnia określone wymagania danych.</span><span class="sxs-lookup"><span data-stu-id="a3472-134">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="a3472-135">Niektóre wartości mogą być określone jako wymagane lub ograniczone do niektórych długości lub zakresu liczbowego, itp. Jeśli podano atrybutów sprawdzania poprawności, ale modelu nie jest zgodny z ich wymaganiami, właściwość ModelState.IsValid będzie mieć wartość false, a zestaw reguł sprawdzania poprawności, które uległy awarii, będzie można wysłać do klienta wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="a3472-135">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="a3472-136">Jeśli używasz weryfikacji modelu, należy się, że zawsze sprawdzić, czy model jest prawidłowy, przed wykonaniem dowolnego polecenia zmiany stanu, aby upewnić się, że aplikacja nie jest uszkodzony, przez nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="a3472-136">If you're using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="a3472-137">Możesz użyć [filtru](/aspnet/core/mvc/controllers/filters) Aby uniknąć konieczności dodawania kodu w tym w każdym działaniu.</span><span class="sxs-lookup"><span data-stu-id="a3472-137">You can use a [filter](/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="a3472-138">Platforma ASP.NET Core MVC filtry oferują sposób przechwycenia grup żądań, tak, aby wspólnych zasad i odciąż przekrojowe zagadnienia, które mogą być stosowane na podstawie docelowej.</span><span class="sxs-lookup"><span data-stu-id="a3472-138">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="a3472-139">Filtry można stosować do poszczególnych czynności w całej kontrolerów, lub globalnie dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-139">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="a3472-140">W przypadku internetowych interfejsów API obsługuje platformy ASP.NET Core MVC [ _negocjacji zawartości_](/aspnet/core/mvc/models/formatting), zezwolenie na żądania określić, jak powinny być sformatowane odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a3472-140">For web APIs, ASP.NET Core MVC supports [_content negotiation_](/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="a3472-141">Oparte na nagłówki podany w żądaniu, akcje zwracający dane sformatuje odpowiedzi XML, JSON lub innego obsługiwanego formatu.</span><span class="sxs-lookup"><span data-stu-id="a3472-141">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="a3472-142">Ta funkcja umożliwia tego samego interfejsu API, który będzie używany przez wielu klientów z różnymi danymi format wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="a3472-142">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="a3472-143">Odwołania — mapowania żądania do odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="a3472-143">References – Mapping Requests to Responses</span></span>
>
> - <span data-ttu-id="a3472-144">**Routing do akcji kontrolera**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="a3472-144">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="a3472-145">**Wiązanie modelu**
> <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding></span><span class="sxs-lookup"><span data-stu-id="a3472-145">**Model Binding**
<https://docs.microsoft.com/aspnet/core/mvc/models/model-binding></span></span>
> - <span data-ttu-id="a3472-146">**Walidacja modelu**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="a3472-146">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="a3472-147">**Filtry**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="a3472-147">**Filters**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="a3472-148">Praca z zależnościami</span><span class="sxs-lookup"><span data-stu-id="a3472-148">Working with dependencies</span></span>

<span data-ttu-id="a3472-149">Platforma ASP.NET Core ma wbudowaną obsługę i wewnętrznie sprawia, że użycie to technika, znana jako [wstrzykiwanie zależności](/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="a3472-149">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="a3472-150">Wstrzykiwanie zależności jest techniką, która umożliwia luźne powiązanie między różne części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-150">Dependency injection is a technique that enables loose coupling between different parts of an application.</span></span> <span data-ttu-id="a3472-151">Im sprzężenia jest pożądane, ponieważ ułatwia Izolowanie części aplikacji, co umożliwia testowanie lub wymiany.</span><span class="sxs-lookup"><span data-stu-id="a3472-151">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="a3472-152">Również powoduje mniej prawdopodobne, że zmiany w jednej części aplikacji będą miały wpływ nieoczekiwany gdzieś w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-152">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="a3472-153">Wstrzykiwanie zależności opiera się na zasadzie odwrócenie zależności i często ma kluczowe znaczenie dla osiągnięcia zasady otwarty/zamknięty.</span><span class="sxs-lookup"><span data-stu-id="a3472-153">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="a3472-154">Podczas obliczania, jak aplikacja współpracuje z jego zależności, należy [statyczne przylepna](https://deviq.com/static-cling/) kodu zapachu i pamiętać aphorism "[nowe jest pośredniczącego](https://ardalis.com/new-is-glue)."</span><span class="sxs-lookup"><span data-stu-id="a3472-154">When evaluating how your application works with its dependencies, beware of the [static cling](https://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](https://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="a3472-155">Statyczne przylepna występuje, gdy Twoich zajęciach wykonywać wywołania do metod statycznych lub dostępu do właściwości statycznej, które ma efekty uboczne ani zależności w infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="a3472-155">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="a3472-156">Na przykład w przypadku metody, która wywołuje statyczną metodę, która z kolei zapis w bazie danych, metoda jest ściśle powiązany z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="a3472-156">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="a3472-157">Wszystko, co powoduje przerwanie wywołania bazy danych spowoduje przerwanie metodę.</span><span class="sxs-lookup"><span data-stu-id="a3472-157">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="a3472-158">Testowanie takich metod jest bardzo trudne, ponieważ takie testy wymagają komercyjnych pozorowania bibliotek testowanie wywołania statycznych, lub należy badać tylko z bazą danych testów w miejscu.</span><span class="sxs-lookup"><span data-stu-id="a3472-158">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="a3472-159">Wywołania statycznych, które nie mają żadnych zależności w infrastrukturze, zwłaszcza tych, które są całkowicie bezstanowe są w dobrym stanie wywołać i nie ma wpływu na sprzężenie lub testowania (poza sprzężenia kodu na wywołanie statyczne, sam).</span><span class="sxs-lookup"><span data-stu-id="a3472-159">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="a3472-160">Wielu programistów zrozumieć ryzyko przylepna statycznych i stan globalny, ale będzie nadal ściśle Połącz swój kod do implementacji określonego poprzez bezpośrednie utworzenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a3472-160">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="a3472-161">"Nowe jest pośredniczącego" ma być przypomnieniem o tym sprzężenia, a nie ogólny potępianiu użycie słowa kluczowego new.</span><span class="sxs-lookup"><span data-stu-id="a3472-161">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="a3472-162">Podobnie jak za pomocą wywołania metody statycznej nowych wystąpień typów, które zwykle mają bez zewnętrznych zależności nie ściśle sprzęgnięcie kodu do szczegółów implementacji lub utrudniają testowania.</span><span class="sxs-lookup"><span data-stu-id="a3472-162">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="a3472-163">Ale każdorazowo, gdy jest tworzone wystąpienie klasy przyjrzeć tylko krótkie należy wziąć pod uwagę, czy warto się kodować sprzętowo tego konkretnego wystąpienia w tej konkretnej lokalizacji, czy byłoby lepsze projektu, aby zażądać tego wystąpienia jako zależność.</span><span class="sxs-lookup"><span data-stu-id="a3472-163">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="a3472-164">Zadeklaruj zależności</span><span class="sxs-lookup"><span data-stu-id="a3472-164">Declare your dependencies</span></span>

<span data-ttu-id="a3472-165">Platforma ASP.NET Core powstał z myślą o metod i klas zadeklarować ich zależności, żądając jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="a3472-165">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="a3472-166">Aplikacje ASP.NET są zazwyczaj ustawiane w klasie uruchamiania, który sam jest skonfigurowany do obsługi iniekcji zależności w kilku miejscach.</span><span class="sxs-lookup"><span data-stu-id="a3472-166">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="a3472-167">Jeśli klasa uruchamiania ma konstruktora, może zażądać jej zależności za pomocą konstruktora, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a3472-167">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

<span data-ttu-id="a3472-168">Klasa początkowa jest interesujące, że nie ma żadnych wymagań jawnego typu dla niego.</span><span class="sxs-lookup"><span data-stu-id="a3472-168">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="a3472-169">Nie dziedziczy z klasy bazowej specjalne uruchamiania nie zawiera implementacji dowolnego określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3472-169">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="a3472-170">Możesz nadać mu konstruktora, czy nie. Ponadto można określić dowolną liczbę parametrów w Konstruktorze dowolną.</span><span class="sxs-lookup"><span data-stu-id="a3472-170">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="a3472-171">Podczas uruchamiania hosta sieci web skonfigurowanych dla danej aplikacji będzie wywoływać klasę uruchamiania, którą Informujesz, aby użyć i użyje wstrzykiwanie zależności w celu wypełnienia żadnych zależności, o których klasa startowa. wymaga.</span><span class="sxs-lookup"><span data-stu-id="a3472-171">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="a3472-172">Oczywiście jeśli użytkownik zażąda parametry, które nie są skonfigurowane w kontenerze usługi używane przez program ASP.NET Core, otrzymasz wyjątek, ale tak długo, jak trzymaj zależności kontenera obsługującemu, możesz poprosić o coś, czego chcesz.</span><span class="sxs-lookup"><span data-stu-id="a3472-172">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="a3472-173">Wstrzykiwanie zależności jest wbudowana w aplikacji platformy ASP.NET Core bezpośrednio od samego początku, po utworzeniu wystąpienia uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a3472-173">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="a3472-174">Nie zatrzymał istnieje dla klasy uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="a3472-174">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="a3472-175">Możesz również poprosić o zależności w metodzie skonfiguruj:</span><span class="sxs-lookup"><span data-stu-id="a3472-175">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="a3472-176">Metoda ConfigureServices jest wyjątek do zachowania; należy ją wykonać tylko jeden parametr typu IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="a3472-176">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="a3472-177">Tak naprawdę nie musi obsługiwać wstrzykiwanie zależności, ponieważ z jednej strony jest odpowiedzialny za dodawanie obiektów do kontenera usług, a na drugim ma dostęp do wszystkich usług aktualnie skonfigurowane za pomocą parametru IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="a3472-177">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="a3472-178">W związku z tym można pracować z zdefiniowanych w kolekcji usługi ASP.NET Core w każdej części klasy uruchamiania, żądając wymagane usługi, jako parametr lub poprzez współdziałanie z IServiceCollection w ConfigureServices zależności.</span><span class="sxs-lookup"><span data-stu-id="a3472-178">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="a3472-179">Jeśli musisz upewnić się, niektóre usługi są dostępne do klasy uruchamiania, można je skonfigurować przy użyciu WebHostBuilder oraz sposób jej ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="a3472-179">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="a3472-180">Klasa początkowa to model umożliwiający powinien strukturą innych części aplikacji platformy ASP.NET Core z kontrolerów, aby oprogramowanie pośredniczące do filtrów do swoich własnych usług.</span><span class="sxs-lookup"><span data-stu-id="a3472-180">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="a3472-181">W obu przypadkach należy przestrzegać [jawne zależności zasady](https://deviq.com/explicit-dependencies-principle/)żądania z zależności, a nie bezpośrednio są one tworzone i wykorzystując wstrzykiwanie zależności w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-181">In each case, you should follow the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="a3472-182">Należy zachować ostrożność, z którym i w jaki sposób bezpośrednio wystąpienia implementacji, szczególnie usług i obiektów, które współdziałać z infrastrukturą lub mieć skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="a3472-182">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="a3472-183">Preferuje pracę z abstrakcje zdefiniowane w podstawowych aplikacji i przekazany jako argumenty do hardcoding odwołania do typów konkretnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-183">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="a3472-184">Tworzenie struktury aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3472-184">Structuring the application</span></span>

<span data-ttu-id="a3472-185">Aplikacje monolityczne zwykle mają jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="a3472-185">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="a3472-186">W przypadku aplikacji sieci web platformy ASP.NET Core punkt wejścia będą projektu sieci web platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3472-186">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="a3472-187">Jednakże, nie oznacza, że rozwiązanie powinna składać się z pojedynczego projektu.</span><span class="sxs-lookup"><span data-stu-id="a3472-187">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="a3472-188">Warto podzielić aplikację w różnych warstwach, aby wykonać separacji zagadnień.</span><span class="sxs-lookup"><span data-stu-id="a3472-188">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="a3472-189">Gdy podzielone na warstwy, warto wykracza poza folderów do osobnych projektów, które może pomóc w osiągnięciu lepszej hermetyzacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-189">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="a3472-190">Najlepszym rozwiązaniem, aby osiągnąć te cele za pomocą aplikacji platformy ASP.NET Core jest odmianą czystej architektury omówionych w rozdziale 5.</span><span class="sxs-lookup"><span data-stu-id="a3472-190">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="a3472-191">Następujące tego podejścia rozwiązania aplikacji będzie składać się z oddzielnych bibliotek interfejsu użytkownika, infrastruktury i ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="a3472-191">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="a3472-192">Oprócz tych projektów projekty testowe w oddzielnych uwzględniono również (testowanie opisanej w rozdziale 9).</span><span class="sxs-lookup"><span data-stu-id="a3472-192">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="a3472-193">Model obiektu i interfejsy aplikacji będzie umieszczona w projekcie ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="a3472-193">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="a3472-194">Ten projekt będzie miał tak małą zależności jak to możliwe, a inne projekty w rozwiązaniu zostaną do niego odwołują.</span><span class="sxs-lookup"><span data-stu-id="a3472-194">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="a3472-195">Jednostki biznesowe, które muszą zostać utrwalona, są zdefiniowane w projekcie ApplicationCore, zgodnie z usług, które nie są bezpośrednio zależne od infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a3472-195">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="a3472-196">Szczegóły implementacji, takich jak jak odbywa się trwałości lub jak mogą być wysyłane powiadomienia do użytkownika, są przechowywane w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a3472-196">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="a3472-197">Ten projekt będzie odwoływać się do pakietów specyficzne dla implementacji, takich jak Entity Framework Core, ale nie powinny uwidaczniać szczegółowe informacje o tych implementacji, poza projektem.</span><span class="sxs-lookup"><span data-stu-id="a3472-197">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="a3472-198">Usługi infrastruktury i repozytoriów powinny implementować interfejsy, które są zdefiniowane w projekcie ApplicationCore i ich implementacji trwałości jest odpowiedzialny za pobieranie i przechowywanie podmioty zdefiniowane w ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="a3472-198">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="a3472-199">Projekt interfejsu użytkownika programu ASP.NET Core jest odpowiedzialny za jakiekolwiek wątpliwości poziomu interfejsu użytkownika, ale nie może zawierać szczegóły logikę lub infrastruktury firmy.</span><span class="sxs-lookup"><span data-stu-id="a3472-199">The ASP.NET Core UI project is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="a3472-200">W rzeczywistości najlepiej go nie należy jeszcze mają zależności w projekcie infrastruktury, co poprawi, upewnij się, że przypadkowo wprowadzone nie zależności między dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="a3472-200">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="a3472-201">Można to osiągnąć za pomocą konteneru DI innych firm, takich jak StructureMap, dzięki czemu można zdefiniować reguły DI w klasach rejestru w każdym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a3472-201">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="a3472-202">Oddzielenie aplikacji, od szczegółów implementacji na innym sposobem jest mikrousługi wywołanie aplikacji, może być wdrażane w poszczególnych kontenerach platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a3472-202">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="a3472-203">Jeszcze większe rozdzielenie problemów i oddzielenie niż wykorzystaniu DI między dwa projekty, ale ma dodatkową złożoność.</span><span class="sxs-lookup"><span data-stu-id="a3472-203">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="a3472-204">Funkcja organizacji</span><span class="sxs-lookup"><span data-stu-id="a3472-204">Feature organization</span></span>

<span data-ttu-id="a3472-205">Domyślnie aplikacje platformy ASP.NET Core organizowanie ich strukturę folderów w celu uwzględnienia kontrolery i widoki i często modele widoków.</span><span class="sxs-lookup"><span data-stu-id="a3472-205">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="a3472-206">Kod po stronie klienta do obsługi tych struktur po stronie serwera są zwykle przechowywane osobno w folderze wwwroot.</span><span class="sxs-lookup"><span data-stu-id="a3472-206">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="a3472-207">Jednak duże aplikacje mogą wystąpić problemy z tej organizacji, ponieważ często nad dowolnym dana funkcja wymaga przechodzenie między te foldery.</span><span class="sxs-lookup"><span data-stu-id="a3472-207">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="a3472-208">Pobiera to bardziej trudne, wraz z rozwojem liczbę plików i podfolderów w folderze każdego skutkuje dużym stopniem przewijanie w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="a3472-208">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="a3472-209">Jedno rozwiązanie tego problemu jest zorganizowanie kod aplikacji przez _funkcji_ zamiast według typu pliku.</span><span class="sxs-lookup"><span data-stu-id="a3472-209">One solution to this problem is to organize application code by _feature_ instead of by file type.</span></span> <span data-ttu-id="a3472-210">Ten styl organizacji jest zwykle określane jako funkcja foldery lub wycinki funkcji (Zobacz również: [pionowe wycinki](https://deviq.com/vertical-slices/)).</span><span class="sxs-lookup"><span data-stu-id="a3472-210">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](https://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="a3472-211">Platforma ASP.NET Core MVC obsługuje obszary, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a3472-211">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="a3472-212">Obszary można utworzyć oddzielne zestawy kontrolery i widoki folderów (a także żadnych modeli skojarzone) w każdym folderze obszaru.</span><span class="sxs-lookup"><span data-stu-id="a3472-212">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="a3472-213">Rysunek 7-1 przedstawiono przykład struktury folderów, korzystać z obszarów.</span><span class="sxs-lookup"><span data-stu-id="a3472-213">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="a3472-214">Rysunek 7-1 próbka obszaru organizacji</span><span class="sxs-lookup"><span data-stu-id="a3472-214">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="a3472-215">Korzystając z obszarów, należy użyć atrybutów do dekorowania kontrolerach nazwą obszaru, do której należą:</span><span class="sxs-lookup"><span data-stu-id="a3472-215">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="a3472-216">Należy również dodać obsługę obszaru do trasy:</span><span class="sxs-lookup"><span data-stu-id="a3472-216">You also need to add area support to your routes:</span></span>

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="a3472-217">Oprócz wbudowanych funkcji dla obszarów umożliwia także własne strukturę folderów i konwencje zamiast atrybutów i tras niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a3472-217">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="a3472-218">Umożliwi to funkcja foldery, które nie zawierają oddzielnych folderów widoki, kontrolery, itp., utrzymywanie płaski hierarchii i ułatwiając widać wszystkie powiązane pliki w jednym miejscu dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-218">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="a3472-219">ASP.NET Core używa konwencji wbudowanych typów kontrolowanie swojego zachowania.</span><span class="sxs-lookup"><span data-stu-id="a3472-219">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="a3472-220">Można zmodyfikować lub zastąpienie tych konwencji.</span><span class="sxs-lookup"><span data-stu-id="a3472-220">You can modify or replace these conventions.</span></span> <span data-ttu-id="a3472-221">Na przykład można utworzyć z Konwencją, która zostanie automatycznie pobrana nazwa funkcji dla danego kontrolera, w oparciu o jego przestrzeń nazw (korelującą zwykle do folderu, w którym znajduje się kontroler):</span><span class="sxs-lookup"><span data-stu-id="a3472-221">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

<span data-ttu-id="a3472-222">Następnie możesz określić tę Konwencję jako opcja po dodaniu pomocy technicznej dla platformy MVC dla aplikacji w ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="a3472-222">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="a3472-223">Platforma ASP.NET Core MVC również używa konwencji zlokalizować widoki.</span><span class="sxs-lookup"><span data-stu-id="a3472-223">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="a3472-224">Można zastąpić go z Konwencją niestandardowe, aby widoki będą znajdować się w folderach funkcji (przy użyciu nazwy funkcji podana przez FeatureConvention powyżej).</span><span class="sxs-lookup"><span data-stu-id="a3472-224">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="a3472-225">Możesz dowiedzieć się więcej na temat tego podejścia i pobrać próbkę pracy z artykuł w witrynie MSDN [wycinki funkcji dla platformy ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span><span class="sxs-lookup"><span data-stu-id="a3472-225">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="a3472-226">Odciąż przekrojowe zagadnienia</span><span class="sxs-lookup"><span data-stu-id="a3472-226">Cross-cutting concerns</span></span>

<span data-ttu-id="a3472-227">Miarę wzrostu aplikacji, staje się coraz ważniejsze wyodrębnić odciąż przekrojowe zagadnienia, aby nie zawierała dublowania i zachowania spójności.</span><span class="sxs-lookup"><span data-stu-id="a3472-227">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="a3472-228">Kilka przykładów odciąż przekrojowe zagadnienia w aplikacjach ASP.NET Core to uwierzytelnianie, reguł sprawdzania poprawności modelu, buforowanie danych wyjściowych i obsługę błędów, chociaż istnieje wiele innych.</span><span class="sxs-lookup"><span data-stu-id="a3472-228">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="a3472-229">Platforma ASP.NET Core MVC [filtry](/aspnet/core/mvc/controllers/filters) pozwala na uruchamianie kodu przed lub po pewne czynności w potoku przetwarzania żądań.</span><span class="sxs-lookup"><span data-stu-id="a3472-229">ASP.NET Core MVC [filters](/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="a3472-230">Na przykład filtr, można uruchomić przed i po nim powiązanie modelu, przed i po wykonaniu akcji lub przed i po wyniku akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-230">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="a3472-231">Filtr autoryzacji można również użyć do kontrolowania dostępu do pozostałego potoku.</span><span class="sxs-lookup"><span data-stu-id="a3472-231">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="a3472-232">Jeśli skonfigurowano rysunki 7-2 pokazuje jak żądanie jest przesyłane wykonywania filtry przekazywania.</span><span class="sxs-lookup"><span data-stu-id="a3472-232">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![Żądanie jest przetwarzane przez filtry autoryzacji, filtrów zasobów, powiązanie modelu, filtry akcji, wykonywanie akcji i konwersji wynik akcji, filtry wyjątków, filtry wyników i wynik wykonywania.](./media/image7-2.png)

<span data-ttu-id="a3472-235">Wykonanie żądania na rysunku 7-2 przy użyciu filtrów i potok żądań.</span><span class="sxs-lookup"><span data-stu-id="a3472-235">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="a3472-236">Filtry zwykle są implementowane jako atrybuty, dzięki czemu można je stosować kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-236">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="a3472-237">Po dodaniu w taki sposób, filtry określone zastąpienia poziomie akcji lub bazują filtry określone na poziomie kontrolera znacznej zastąpić filtrów globalnych.</span><span class="sxs-lookup"><span data-stu-id="a3472-237">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="a3472-238">Na przykład \[trasy\] atrybut może służyć do zbudowania tras między kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-238">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="a3472-239">Podobnie autoryzacji można konfigurować na poziomie kontrolera i następnie zastępowane przez poszczególne akcje, tak jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a3472-239">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="a3472-240">Pierwszej metody logowania, używa filtra AllowAnonymous (atrybut), aby zastąpić filtr autoryzacji, należy ustawić na poziomie kontrolera.</span><span class="sxs-lookup"><span data-stu-id="a3472-240">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="a3472-241">Akcja ForgotPassword (i innych działań w klasie, która nie ma atrybutu AllowAnonymous) będzie wymagać uwierzytelnionego żądania.</span><span class="sxs-lookup"><span data-stu-id="a3472-241">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="a3472-242">Filtry można wyeliminować dublowanie w postaci wspólnego obsługi błędów zasady dla interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a3472-242">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="a3472-243">Na przykład typowych zasad interfejsu API jest zwracana NotFound odpowiedzi na żądania PRZYWOŁUJĄCE klucze, które nie istnieją, a element BadRequest odpowiedź, gdy sprawdzanie poprawności modelu nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="a3472-243">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="a3472-244">W poniższym przykładzie pokazano te dwie zasady w akcji:</span><span class="sxs-lookup"><span data-stu-id="a3472-244">The following example demonstrates these two policies in action:</span></span>

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="a3472-245">Nie zezwalaj na swoje metody akcji, aby zapełnić kod warunkowy następująco.</span><span class="sxs-lookup"><span data-stu-id="a3472-245">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="a3472-246">Zamiast tego należy ściągnąć zasady do filtrów, które mogą być stosowane w zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="a3472-246">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="a3472-247">W tym przykładzie można zastąpić sprawdzenie poprawności modelu, który powinno nastąpić każdym razem, gdy polecenie jest wysyłany do interfejsu API, według następującego atrybutu:</span><span class="sxs-lookup"><span data-stu-id="a3472-247">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

<span data-ttu-id="a3472-248">Podobnie filtr może służyć do sprawdzania, czy rekord istnieje i zwrócić kod 404, przed wykonaniem akcji, eliminując konieczność wykonywania tych sprawdzeń w akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-248">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="a3472-249">Po ściągane się typowych Konwencji i zorganizowane rozwiązania, aby oddzielić infrastruktury kodu i logiki biznesowej od interfejsu użytkownika, MVC metody akcji powinny być bardzo cienka:</span><span class="sxs-lookup"><span data-stu-id="a3472-249">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="a3472-250">Możesz dowiedzieć się więcej o implementacji filtry i pobrać przykładowy pracy z artykuł w witrynie MSDN [Real World ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).</span><span class="sxs-lookup"><span data-stu-id="a3472-250">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="a3472-251">Odwołania — struktury aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3472-251">References – Structuring applications</span></span>
>
> - <span data-ttu-id="a3472-252">**Obszary**</span><span class="sxs-lookup"><span data-stu-id="a3472-252">**Areas**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - <span data-ttu-id="a3472-253">**MSDN Magazine — wycinki funkcji dla platformy ASP.NET Core MVC**</span><span class="sxs-lookup"><span data-stu-id="a3472-253">**MSDN Magazine – Feature Slices for ASP.NET Core MVC**</span></span>  
 > <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - <span data-ttu-id="a3472-254">**Filtry**</span><span class="sxs-lookup"><span data-stu-id="a3472-254">**Filters**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - <span data-ttu-id="a3472-255">**MSDN — rzeczywistych platformy ASP.NET Core MVC filtry**</span><span class="sxs-lookup"><span data-stu-id="a3472-255">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a><span data-ttu-id="a3472-256">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="a3472-256">Security</span></span>

<span data-ttu-id="a3472-257">Zabezpieczanie aplikacji sieci web jest duże tematu, z wiele uwagi.</span><span class="sxs-lookup"><span data-stu-id="a3472-257">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="a3472-258">Na najbardziej podstawowym poziomie zabezpieczeń obejmuje zapewnienie, że wiesz, kto pochodzące z danego żądania i zapewnienie, że to żądanie tylko ma dostęp do zasobów, które powinno.</span><span class="sxs-lookup"><span data-stu-id="a3472-258">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="a3472-259">Uwierzytelnianie to proces porównanie poświadczenia dostarczone z żądaniem w zaufanym magazynie danych, aby zobaczyć, czy żądanie powinny być traktowane jako pochodzący od znanych jednostki.</span><span class="sxs-lookup"><span data-stu-id="a3472-259">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="a3472-260">Autoryzacja to proces ograniczanie dostępu do niektórych zasobów na podstawie tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3472-260">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="a3472-261">Trzeci kwestią zabezpieczeń chroni żądań podsłuchiwaniu przez osoby trzecie, dla których należy co najmniej [upewnij się, że protokół SSL jest używany przez aplikację](/aspnet/core/security/enforcing-ssl).</span><span class="sxs-lookup"><span data-stu-id="a3472-261">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="a3472-262">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="a3472-262">Authentication</span></span>

<span data-ttu-id="a3472-263">Tożsamość platformy ASP.NET Core jest systemu członkostwa, służących do obsługi funkcji logowania dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-263">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="a3472-264">Ma ona obsługi dla kont użytkowników lokalnych, a także informacje o obsłudze dostawców zewnętrznych danych logowania od dostawców, takich jak Account Microsoft, Twitter, Facebook i Google.</span><span class="sxs-lookup"><span data-stu-id="a3472-264">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="a3472-265">Oprócz tożsamości platformy ASP.NET Core, aplikacja może używać uwierzytelniania systemu windows lub z dostawcy tożsamości innych firm, takich jak [serwera tożsamości](https://github.com/IdentityServer/IdentityServer4).</span><span class="sxs-lookup"><span data-stu-id="a3472-265">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="a3472-266">Tożsamości platformy ASP.NET Core znajduje się w nowe szablony projektów, jeśli wybrano opcję indywidualnych kont użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a3472-266">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="a3472-267">Ten szablon obejmuje obsługę rejestracji, logowania, logowania zewnętrzne, zapomniane hasła i dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="a3472-267">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="a3472-268">Rysunek 7-3. Wybierz pojedyncze konta użytkowników mają tożsamości we wstępnie skonfigurowanym.</span><span class="sxs-lookup"><span data-stu-id="a3472-268">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="a3472-269">Obsługa tożsamości jest skonfigurowany w uruchamiania, zarówno w ConfigureServices i skonfiguruj:</span><span class="sxs-lookup"><span data-stu-id="a3472-269">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="a3472-270">Jest ważne, czy UseIdentity są wyświetlane przed UseMvc w metodzie Konfiguruj.</span><span class="sxs-lookup"><span data-stu-id="a3472-270">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="a3472-271">Podczas konfigurowania tożsamości w ConfigureServices, zauważysz AddDefaultTokenProviders po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a3472-271">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="a3472-272">To nie ma nic wspólnego z tokenów, które mogą służyć do zabezpieczenia komunikacji w sieci web, ale zamiast tego odwołuje się do dostawców tworzące monity, które mogą być wysyłane do użytkowników za pośrednictwem wiadomości SMS lub wiadomości e-mail, aby je, aby potwierdzić swoją tożsamość.</span><span class="sxs-lookup"><span data-stu-id="a3472-272">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="a3472-273">Możesz dowiedzieć się więcej [Konfigurowanie uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa) i [Włączanie dostawcy logowania zewnętrznego](/aspnet/core/security/authentication/social/) oficjalnych dokumentach platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3472-273">You can learn more about [configuring two-factor authentication](/aspnet/core/security/authentication/2fa) and [enabling external login providers](/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="a3472-274">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="a3472-274">Authorization</span></span>

<span data-ttu-id="a3472-275">Najprostsza forma autoryzacji polega na ograniczenie dostępu dla użytkowników anonimowych.</span><span class="sxs-lookup"><span data-stu-id="a3472-275">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="a3472-276">Można to osiągnąć, po prostu stosując \[Autoryzuj\] atrybutu do niektórych kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="a3472-276">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="a3472-277">Role są używane, ten atrybut może dodatkowo rozszerzona do ograniczania dostępu do użytkowników, którzy należą do określonych ról, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="a3472-277">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="a3472-278">W takim przypadku użytkownicy należący do ról HRManager lub Finance (lub obie) będzie mieć dostęp do SalaryController.</span><span class="sxs-lookup"><span data-stu-id="a3472-278">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="a3472-279">Aby wymagać, że użytkownik należy do wielu ról (nie tylko jeden z kilku), można zastosować atrybutu wiele razy, określając wymaganej roli każdorazowo.</span><span class="sxs-lookup"><span data-stu-id="a3472-279">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="a3472-280">Określanie określone zestawy ról, zgodnie z ciągów w wielu różnych kontrolerów i akcji może doprowadzić do powtarzania niepożądane.</span><span class="sxs-lookup"><span data-stu-id="a3472-280">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="a3472-281">Możesz skonfigurować zasady autoryzacji, które hermetyzują reguł autoryzacji, a następnie określ zasady, a nie poszczególnych ról podczas stosowania \[Autoryzuj\] atrybutu:</span><span class="sxs-lookup"><span data-stu-id="a3472-281">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="a3472-282">W ten sposób, korzystając z zasad, można oddzielić rodzaje działań jest ograniczony z określonych ról lub reguły, które go dotyczą.</span><span class="sxs-lookup"><span data-stu-id="a3472-282">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="a3472-283">Później, jeśli tworzysz nową rolę, która musi mieć dostęp do niektórych zasobów, można po prostu aktualizować zasady, a nie aktualizacji co listy ról na każdym \[Autoryzuj\] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a3472-283">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="a3472-284">oświadczenia</span><span class="sxs-lookup"><span data-stu-id="a3472-284">Claims</span></span>

<span data-ttu-id="a3472-285">Oświadczenia są pary nazwa / wartość, które reprezentują właściwości uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3472-285">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="a3472-286">Na przykład może przechowywać numer pracownika użytkowników jako oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="a3472-286">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="a3472-287">Następnie można oświadczeń jako część zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-287">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="a3472-288">Można utworzyć zasady o nazwie "EmployeeOnly" wymaga istnienia oświadczenie o nazwie "EmployeeNumber", jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a3472-288">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="a3472-289">Ta zasada może być użyta z \[Autoryzuj\] atrybutu, aby chronić kontroler i/lub akcji, jak opisano powyżej.</span><span class="sxs-lookup"><span data-stu-id="a3472-289">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="a3472-290">Zabezpieczanie interfejsów API sieci web</span><span class="sxs-lookup"><span data-stu-id="a3472-290">Securing web APIs</span></span>

<span data-ttu-id="a3472-291">Większość interfejsów API sieci web należy zaimplementować uwierzytelnianie oparte na token systemu.</span><span class="sxs-lookup"><span data-stu-id="a3472-291">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="a3472-292">Uwierzytelnianie przy użyciu tokenów jest przeznaczona do skalowalne i bezstanowych.</span><span class="sxs-lookup"><span data-stu-id="a3472-292">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="a3472-293">W systemie uwierzytelniania opartego na tokenach klienta muszą najpierw zostać uwierzytelnione za pomocą dostawcy uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a3472-293">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="a3472-294">Jeśli to się powiedzie, klient wystawił token, który jest po prostu kryptograficznie istotnych ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="a3472-294">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="a3472-295">Gdy klient musi wysłać żądanie do interfejsu API, dodaje ten token jako nagłówka w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="a3472-295">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="a3472-296">Serwer następnie weryfikuje token w nagłówku żądania znaleziono przed wykonaniem żądania.</span><span class="sxs-lookup"><span data-stu-id="a3472-296">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="a3472-297">Rysunek 7-4 przedstawiono ten proces.</span><span class="sxs-lookup"><span data-stu-id="a3472-297">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="a3472-299">**Rysunek 7-4.**</span><span class="sxs-lookup"><span data-stu-id="a3472-299">**Figure 7-4.**</span></span> <span data-ttu-id="a3472-300">Uwierzytelnianie oparte na tokenach dla interfejsów API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a3472-300">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="a3472-301">Odwołania — zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="a3472-301">References – Security</span></span>
>
> - <span data-ttu-id="a3472-302">**Omówienie zabezpieczeń usługi Docs**</span><span class="sxs-lookup"><span data-stu-id="a3472-302">**Security Docs Overview**</span></span>  
>   https://docs.microsoft.com/aspnet/core/security/
> - <span data-ttu-id="a3472-303">**Wymuszanie protokołu SSL w aplikacji ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="a3472-303">**Enforcing SSL in an ASP.NET Core App**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - <span data-ttu-id="a3472-304">**Wprowadzenie do tożsamości**</span><span class="sxs-lookup"><span data-stu-id="a3472-304">**Introduction to Identity**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - <span data-ttu-id="a3472-305">**Wprowadzenie do autoryzacji**</span><span class="sxs-lookup"><span data-stu-id="a3472-305">**Introduction to Authorization**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - <span data-ttu-id="a3472-306">**Uwierzytelnianie i autoryzacja dla usługi API Apps w usłudze Azure App Service**</span><span class="sxs-lookup"><span data-stu-id="a3472-306">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a><span data-ttu-id="a3472-307">Komunikacja z klientem</span><span class="sxs-lookup"><span data-stu-id="a3472-307">Client communication</span></span>

<span data-ttu-id="a3472-308">Oprócz obsługi stron i odpowiadanie na żądania dotyczące danych za pośrednictwem interfejsów API sieci web, aplikacje platformy ASP.NET Core mogą komunikować się bezpośrednio z połączonych klientów.</span><span class="sxs-lookup"><span data-stu-id="a3472-308">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="a3472-309">Ta komunikacja wychodząca można użyć wielu różnych technologii transportu jest najbardziej typowych funkcji WebSockets.</span><span class="sxs-lookup"><span data-stu-id="a3472-309">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="a3472-310">SignalR platformy ASP.NET Core to bibliotekę, która ułatwia dodawanie funkcji komunikacji serwera do klienta w czasie rzeczywistym do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-310">ASP.NET Core SignalR is a library that makes it simple to add real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="a3472-311">SignalR obsługuje szereg technologii transportu, w tym funkcji WebSockets i streszcza away wiele szczegółów implementacji od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="a3472-311">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="a3472-312">SignalR platformy ASP.NET Core jest dostępny za pomocą platformy ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="a3472-312">ASP.NET Core SignalR is available with ASP.NET Core 2.1.</span></span>

<span data-ttu-id="a3472-313">Komunikacja z klientem w czasie rzeczywistym, czy przy użyciu funkcji WebSockets bezpośrednio lub innych technik przydają się w różnych zastosowaniach.</span><span class="sxs-lookup"><span data-stu-id="a3472-313">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="a3472-314">Niektóre przykłady:</span><span class="sxs-lookup"><span data-stu-id="a3472-314">Some examples include:</span></span>

- <span data-ttu-id="a3472-315">Aplikacje na żywo pokoju rozmów</span><span class="sxs-lookup"><span data-stu-id="a3472-315">Live chat room applications</span></span>

- <span data-ttu-id="a3472-316">Monitorowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3472-316">Monitoring applications</span></span>

- <span data-ttu-id="a3472-317">Aktualizacje postępu zadania</span><span class="sxs-lookup"><span data-stu-id="a3472-317">Job progress updates</span></span>

- <span data-ttu-id="a3472-318">Powiadomienia</span><span class="sxs-lookup"><span data-stu-id="a3472-318">Notifications</span></span>

- <span data-ttu-id="a3472-319">Formularze interaktywne aplikacje</span><span class="sxs-lookup"><span data-stu-id="a3472-319">Interactive forms applications</span></span>

<span data-ttu-id="a3472-320">Podczas tworzenia komunikacji z klientem w swoich aplikacjach, istnieją zazwyczaj dwa składniki:</span><span class="sxs-lookup"><span data-stu-id="a3472-320">When building client communication into your applications, there are typically two components:</span></span>

- <span data-ttu-id="a3472-321">Menedżer połączeń po stronie serwera (Centrum SignalR, WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="a3472-321">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

- <span data-ttu-id="a3472-322">Biblioteka klienta</span><span class="sxs-lookup"><span data-stu-id="a3472-322">Client-side library</span></span>

<span data-ttu-id="a3472-323">Klienci nie są ograniczone do przeglądarek — aplikacje mobilne, aplikacje konsoli i inne aplikacje natywne mogą również komunikować się przy użyciu SignalR/Websocket.</span><span class="sxs-lookup"><span data-stu-id="a3472-323">Clients aren't limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="a3472-324">Następujący program prostą funkcją cała zawartość wysłana do aplikacji rozmów w konsoli jako część WebSocketManager przykładowej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="a3472-324">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

<span data-ttu-id="a3472-325">Należy rozważyć sposobów w których Twoje aplikacje komunikują się bezpośrednio z aplikacji klienckich i należy wziąć pod uwagę, czy komunikację w czasie rzeczywistym mogłyby poprawić użytkownika aplikacji środowiska.</span><span class="sxs-lookup"><span data-stu-id="a3472-325">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="a3472-326">Odwołania — komunikacja z klientem</span><span class="sxs-lookup"><span data-stu-id="a3472-326">References – Client Communication</span></span>
>
> - <span data-ttu-id="a3472-327">**SignalR platformy ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="a3472-327">**ASP.NET Core SignalR**</span></span>  
>   <https://github.com/aspnet/SignalR>
> - <span data-ttu-id="a3472-328">**Menedżer WebSocket**</span><span class="sxs-lookup"><span data-stu-id="a3472-328">**WebSocket Manager**</span></span>  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="a3472-329">Projektowanie oparte na domenie — powinien zastosowania?</span><span class="sxs-lookup"><span data-stu-id="a3472-329">Domain-driven design – Should you apply it?</span></span>

<span data-ttu-id="a3472-330">Projektowania opartego na domenach (DDD) jest podejście agile do tworzenia oprogramowania, która kładzie nacisk koncentrujących się na _domeny biznesowej_.</span><span class="sxs-lookup"><span data-stu-id="a3472-330">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the _business domain_.</span></span> <span data-ttu-id="a3472-331">Umieszcza mocno nacisk na komunikację i interakcję z expert(s) domeny biznesowej, który może odnosić się do deweloperów działania systemu rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="a3472-331">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="a3472-332">Na przykład jeśli tworzysz system, który obsługuje kursów akcji usługi eksperta domeny może być brokera podstawowe doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="a3472-332">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="a3472-333">DDD zaprojektowano w celu rozwiązania problemów w firmie dużymi, złożonymi i często nie jest odpowiednie w przypadku aplikacji mniejszy, prostszy, ponieważ inwestycji w zrozumienie i modelowanie domeny nie są one warte.</span><span class="sxs-lookup"><span data-stu-id="a3472-333">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="a3472-334">Podczas tworzenia oprogramowania, korzystając z podejścia DDD, Twój zespół (w tym Nietechniczne uczestnikom projektu i współautorzy) należy opracować _wszechobecne języka_ miejsca problem.</span><span class="sxs-lookup"><span data-stu-id="a3472-334">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a _ubiquitous language_ for the problem space.</span></span> <span data-ttu-id="a3472-335">Oznacza to należy używać terminologii tego samego pojęcia rzeczywistych są modelowane, odpowiednik oprogramowania i wszelkimi strukturami, które mogą istnieć do utrwalenia pojęcie (na przykład tabele bazy danych).</span><span class="sxs-lookup"><span data-stu-id="a3472-335">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="a3472-336">W efekcie pojęcia opisane w tym języku wszechobecne powinny być podstawą dla sieci _modelu domeny_.</span><span class="sxs-lookup"><span data-stu-id="a3472-336">Thus, the concepts described in the ubiquitous language should form the basis for your _domain model_.</span></span>

<span data-ttu-id="a3472-337">Model domeny składa się z obiektów, które współdziałają ze sobą do reprezentowania zachowanie systemu.</span><span class="sxs-lookup"><span data-stu-id="a3472-337">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="a3472-338">Te obiekty może można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="a3472-338">These objects may fall into the following categories:</span></span>

- <span data-ttu-id="a3472-339">[Jednostki](https://deviq.com/entity/), zawierające obiekty z wątkiem tożsamości.</span><span class="sxs-lookup"><span data-stu-id="a3472-339">[Entities](https://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="a3472-340">Jednostki są zazwyczaj przechowywane w trwałości za pomocą klucza za pomocą którego mogą później zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="a3472-340">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

- <span data-ttu-id="a3472-341">[Agregacje](https://deviq.com/aggregate-pattern/), które reprezentują grupy obiektów, które powinny zostać utrwalone jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="a3472-341">[Aggregates](https://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

- <span data-ttu-id="a3472-342">[Wartość obiekty](https://deviq.com/value-object/), które reprezentują pojęcia, które można porównać na podstawie sumy wartości ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3472-342">[Value objects](https://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="a3472-343">Na przykład DateRange składający się z datę początkową i końcową.</span><span class="sxs-lookup"><span data-stu-id="a3472-343">For example, DateRange consisting of a start and end date.</span></span>

- <span data-ttu-id="a3472-344">[Zdarzenia domeny](https://martinfowler.com/eaaDev/DomainEvent.html), które reprezentują czynności wykonywane w ramach systemu, które mają znaczenie w odniesieniu do innych części systemu.</span><span class="sxs-lookup"><span data-stu-id="a3472-344">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="a3472-345">Należy pamiętać, że model domeny DDD powinna hermetyzować złożonych zachowania w ramach modelu.</span><span class="sxs-lookup"><span data-stu-id="a3472-345">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="a3472-346">Jednostki, w szczególności, nie tylko należy kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3472-346">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="a3472-347">Jeśli model domeny nie ma zachowanie, jedynie reprezentuje stan systemu jest określany jako [anemic modelu](https://deviq.com/anemic-model/), czyli niepożądanych w DDD.</span><span class="sxs-lookup"><span data-stu-id="a3472-347">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](https://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="a3472-348">Oprócz tych typów modelu DDD zwykle stosuje różnych wzorców:</span><span class="sxs-lookup"><span data-stu-id="a3472-348">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

- <span data-ttu-id="a3472-349">[Repozytorium](https://deviq.com/repository-pattern/), dla abstrakcyjność szczegółów stanu trwałego.</span><span class="sxs-lookup"><span data-stu-id="a3472-349">[Repository](https://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

- <span data-ttu-id="a3472-350">[Fabryka](https://en.wikipedia.org/wiki/Factory_method_pattern), do enkapsulacji tworzenia obiektu złożonego.</span><span class="sxs-lookup"><span data-stu-id="a3472-350">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

- <span data-ttu-id="a3472-351">Zdarzenia domeny dla oddzielenie zachowanie zależnych wraz z zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="a3472-351">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

- <span data-ttu-id="a3472-352">[Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)dla hermetyzowany zachowanie złożone i/lub szczegółów implementacji infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a3472-352">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

- <span data-ttu-id="a3472-353">[Polecenie](https://en.wikipedia.org/wiki/Command_pattern)dla oddzielenie wydawanie polecenia i wykonywania w niej samo polecenie.</span><span class="sxs-lookup"><span data-stu-id="a3472-353">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

- <span data-ttu-id="a3472-354">[Specyfikacja](https://deviq.com/specification-pattern/), do enkapsulacji szczegółów zapytania.</span><span class="sxs-lookup"><span data-stu-id="a3472-354">[Specification](https://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="a3472-355">DDD zaleca również używanie czystej architektury omówionych wcześniej, pozwalając na tym luźne powiązanie, hermetyzacji i kod, który można łatwo zweryfikować za pomocą testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="a3472-355">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="a3472-356">Kiedy należy zastosować DDD</span><span class="sxs-lookup"><span data-stu-id="a3472-356">When should you apply DDD</span></span>

<span data-ttu-id="a3472-357">DDD dobrze nadaje się do dużej aplikacji przy użyciu złożoności firma (nie tylko weryfikacji technicznej).</span><span class="sxs-lookup"><span data-stu-id="a3472-357">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="a3472-358">Aplikacja powinna wymagają znajomości ekspertów z konkretnych dziedzin.</span><span class="sxs-lookup"><span data-stu-id="a3472-358">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="a3472-359">Powinna istnieć znaczące zachowanie w modelu domeny, reprezentujący reguł biznesowych i interakcje ponad po prostu przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych.</span><span class="sxs-lookup"><span data-stu-id="a3472-359">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="a3472-360">Kiedy nie należy zastosować DDD</span><span class="sxs-lookup"><span data-stu-id="a3472-360">When shouldn't you apply DDD</span></span>

<span data-ttu-id="a3472-361">DDD wymaga inwestycji w modelowania, architektury i komunikacji, który nie może być uzasadnione dla mniejszych aplikacji lub aplikacji, które zasadniczo są po prostu CRUD (Tworzenie/odczyt/aktualizowanie/usuwanie).</span><span class="sxs-lookup"><span data-stu-id="a3472-361">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="a3472-362">Jeśli użytkownik chce podejście do aplikacji następujące DDD, ale okazać, że domeny ma anemic modelu, z zachowaniem programu nie może być konieczne zmusza danej metody.</span><span class="sxs-lookup"><span data-stu-id="a3472-362">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="a3472-363">Aplikacja nie może być konieczne DDD albo możesz potrzebować pomocy refaktoryzacji hermetyzowania logiki biznesowej w modelu domeny, a nie w swojej bazie danych lub interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-363">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="a3472-364">Podejście hybrydowe byłoby tylko DDD obszarów transakcyjnej lub bardziej złożonych aplikacji, ale nie CRUD prostsze lub tylko do odczytu części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3472-364">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="a3472-365">Na przykład musi mieć ograniczenia agregacji, jeśli zadajesz zapytanie do danych do wyświetlania raportu lub wizualizacji danych dla pulpitu nawigacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a3472-365">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="a3472-366">Jest idealnie dopuszczalne mają oddzielny, prostsze modelu odczytu dla tych wymagań.</span><span class="sxs-lookup"><span data-stu-id="a3472-366">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="a3472-367">Odwołania — projektowania opartego na domenie</span><span class="sxs-lookup"><span data-stu-id="a3472-367">References – Domain-Driven Design</span></span>
>
> - <span data-ttu-id="a3472-368">**DDD w prostych słowach (StackOverflow odpowiedzi)**</span><span class="sxs-lookup"><span data-stu-id="a3472-368">**DDD in Plain English (StackOverflow Answer)**</span></span>  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a><span data-ttu-id="a3472-369">wdrażania</span><span class="sxs-lookup"><span data-stu-id="a3472-369">Deployment</span></span>

<span data-ttu-id="a3472-370">Zaangażowanych kilka czynności w procesie wdrażania aplikacji platformy ASP.NET Core, niezależnie od tego, w którym będzie hostowana.</span><span class="sxs-lookup"><span data-stu-id="a3472-370">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="a3472-371">Pierwszym krokiem jest opublikowanie aplikacji, co można zrobić za pomocą polecenia dotnet publikowanie interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a3472-371">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="a3472-372">Spowoduje to skompilować aplikację i umieścić wszystkie pliki potrzebne do uruchomienia aplikacji w wyznaczonym folderze.</span><span class="sxs-lookup"><span data-stu-id="a3472-372">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="a3472-373">Podczas wdrażania w programie Visual Studio, w tym kroku jest realizowane automatycznie dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="a3472-373">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="a3472-374">Folder publikowania zawiera pliki .exe i .dll dla aplikacji i jego zależności.</span><span class="sxs-lookup"><span data-stu-id="a3472-374">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="a3472-375">Samodzielna aplikacja będzie również udostępniać wersję środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="a3472-375">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="a3472-376">Aplikacje platformy ASP.NET Core będzie również udostępniać pliki konfiguracyjne, elementy zawartości statycznej klienta i widoków MVC.</span><span class="sxs-lookup"><span data-stu-id="a3472-376">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="a3472-377">Aplikacje platformy ASP.NET Core to aplikacji konsoli, które musi zostać uruchomiona, gdy serwer uruchamia się i ponownego uruchomienia, jeśli wystąpiła awaria aplikacji (lub serwera).</span><span class="sxs-lookup"><span data-stu-id="a3472-377">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="a3472-378">Menedżera procesów można zautomatyzować ten proces.</span><span class="sxs-lookup"><span data-stu-id="a3472-378">A process manager can be used to automate this process.</span></span> <span data-ttu-id="a3472-379">Najbardziej typowe menedżerów procesu dla platformy ASP.NET Core są serwera Nginx i Apache w systemie Linux oraz usług IIS lub usługa Windows na Windows.</span><span class="sxs-lookup"><span data-stu-id="a3472-379">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="a3472-380">Oprócz menedżera procesów aplikacje platformy ASP.NET Core hostowanych na serwerze sieci web Kestrel należy użyć zwrotnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a3472-380">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="a3472-381">Zwrotnego serwera proxy odbiera żądania HTTP z Internetu i przekazuje je do Kestrel po niektórych wstępnego obsługi.</span><span class="sxs-lookup"><span data-stu-id="a3472-381">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="a3472-382">Serwery zwrotny serwer proxy zapewnia warstwę zabezpieczeń dla aplikacji i są wymagane w przypadku wdrożeń usługi edge (ujawniony na ruch z Internetu).</span><span class="sxs-lookup"><span data-stu-id="a3472-382">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="a3472-383">Kestrel jest względnie nowe i jeszcze nie oferuje zabezpieczenia przed atakami niektórych.</span><span class="sxs-lookup"><span data-stu-id="a3472-383">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="a3472-384">Kestrel nie obsługuje również hostowania wielu aplikacji, w tym samym porcie, więc technik, takich jak nagłówki hosta nie można używać z nią hostowania wielu aplikacji na ten sam port i adres IP.</span><span class="sxs-lookup"><span data-stu-id="a3472-384">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Usługi kestrel do Internetu](./media/image7-5.png)

<span data-ttu-id="a3472-386">Rysunek 7-5 ASP.NET hostowane w Kestrel za serwerem proxy odwrotnej</span><span class="sxs-lookup"><span data-stu-id="a3472-386">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="a3472-387">Inny scenariusz, w którym zwrotny serwer proxy mogą być pomocne jest zapewnienie wielu aplikacji przy użyciu protokołu SSL i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3472-387">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="a3472-388">W takim przypadku tylko zwrotny serwer proxy będzie konieczne skonfigurowano protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="a3472-388">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="a3472-389">Komunikacja między zwrotnego serwera proxy i Kestrel może odbywać się za pośrednictwem protokołu HTTP, jak pokazano w rysunek 7-6.</span><span class="sxs-lookup"><span data-stu-id="a3472-389">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="a3472-390">Rysunek 7 – 6 ASP.NET hostowanych za zabezpieczone przez protokół HTTPS zwrotnego serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a3472-390">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="a3472-391">Jest coraz bardziej popularne podejście do hostowania aplikacji platformy ASP.NET Core w kontenerze platformy Docker, które następnie mogą być hostowane lokalnie lub wdrożona na platformie Azure do hostowania opartej na chmurze.</span><span class="sxs-lookup"><span data-stu-id="a3472-391">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="a3472-392">Kontener platformy Docker może zawierać kod aplikacji uruchomionych na Kestrel i będzie można wdrożyć za serwerem proxy odwrotnej, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="a3472-392">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="a3472-393">Jeśli hostujesz aplikację na platformie Azure umożliwia Microsoft Azure Application Gateway jako dedykowane urządzenie wirtualne zapewniają kilka usług.</span><span class="sxs-lookup"><span data-stu-id="a3472-393">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="a3472-394">Oprócz działający jako zwrotny serwer proxy dla poszczególnych aplikacji, usługa Application Gateway może oferują również następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a3472-394">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

- <span data-ttu-id="a3472-395">Równoważenie obciążenia HTTP</span><span class="sxs-lookup"><span data-stu-id="a3472-395">HTTP load balancing</span></span>

- <span data-ttu-id="a3472-396">Odciążanie protokołu SSL (SSL tylko z Internetu)</span><span class="sxs-lookup"><span data-stu-id="a3472-396">SSL offload (SSL only to Internet)</span></span>

- <span data-ttu-id="a3472-397">Kompleksowej usługi SSL</span><span class="sxs-lookup"><span data-stu-id="a3472-397">End to End SSL</span></span>

- <span data-ttu-id="a3472-398">Routing obejmujący wiele lokacji (skonsolidować maksymalnie 20 witryn na pojedynczą usługą Application Gateway)</span><span class="sxs-lookup"><span data-stu-id="a3472-398">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

- <span data-ttu-id="a3472-399">Zapora aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="a3472-399">Web application firewall</span></span>

- <span data-ttu-id="a3472-400">Obsługa protokołu Websocket</span><span class="sxs-lookup"><span data-stu-id="a3472-400">Websocket support</span></span>

- <span data-ttu-id="a3472-401">Zaawansowana Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a3472-401">Advanced diagnostics</span></span>

<span data-ttu-id="a3472-402">_Dowiedz się więcej o opcjach wdrażania platformy Azure w programie [rozdział 10](development-process-for-azure.md)._</span><span class="sxs-lookup"><span data-stu-id="a3472-402">_Learn more about Azure deployment options in [Chapter 10](development-process-for-azure.md)._</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="a3472-403">Odwołania — wdrożenia</span><span class="sxs-lookup"><span data-stu-id="a3472-403">References – Deployment</span></span>
>
> - <span data-ttu-id="a3472-404">**Omówienie wdrożenia i hosting**</span><span class="sxs-lookup"><span data-stu-id="a3472-404">**Hosting and Deployment Overview**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - <span data-ttu-id="a3472-405">**Kiedy należy używać Kestrel przy użyciu zwrotnego serwera proxy**</span><span class="sxs-lookup"><span data-stu-id="a3472-405">**When to use Kestrel with a reverse proxy**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - <span data-ttu-id="a3472-406">**Hostowanie aplikacji platformy ASP.NET Core na platformie Docker**</span><span class="sxs-lookup"><span data-stu-id="a3472-406">**Host ASP.NET Core apps in Docker**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - <span data-ttu-id="a3472-407">**Wprowadzenie do usługi Azure Application Gateway**</span><span class="sxs-lookup"><span data-stu-id="a3472-407">**Introducing Azure Application Gateway**</span></span>  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
<span data-ttu-id="a3472-408">[Poprzednie](common-client-side-web-technologies.md)
[dalej](work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a3472-408">[Previous](common-client-side-web-technologies.md)
[Next](work-with-data-in-asp-net-core-apps.md)</span></span>
