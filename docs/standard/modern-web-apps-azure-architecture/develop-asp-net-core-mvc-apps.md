---
title: Tworzenie aplikacji MVC ASP.NET Core
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Tworzenie aplikacji programu ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10bf66dd37f0d99c038db7f95999d84986152fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="38781-103">Tworzenie aplikacji MVC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="38781-103">Develop ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="38781-104">"Nie jest ważna uzyskać prawo po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="38781-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="38781-105">Jest zasadnicze znaczenie uzyskać prawo ostatniego."</span><span class="sxs-lookup"><span data-stu-id="38781-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="38781-106">_-Andrew Hunt i blogu Thomasa Dominik_</span><span class="sxs-lookup"><span data-stu-id="38781-106">_- Andrew Hunt and David Thomas_</span></span>

## <a name="summary"></a><span data-ttu-id="38781-107">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="38781-107">Summary</span></span>

<span data-ttu-id="38781-108">Platformy ASP.NET Core to platforma i platform, open source do tworzenia nowoczesnych zoptymalizowanych pod kątem chmury aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="38781-108">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="38781-109">Aplikacje platformy ASP.NET Core to lekkie i moduły z wbudowaną obsługą iniekcji zależności, włączanie w większej kontroli i łatwości konserwacji.</span><span class="sxs-lookup"><span data-stu-id="38781-109">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling in greater testability and maintainability.</span></span> <span data-ttu-id="38781-110">Połączone z MVC, który obsługuje tworzenie nowoczesnych interfejsów API sieci web oprócz aplikacji opartych na widoku, platformy ASP.NET Core to platforma Zaawansowane umożliwiające tworzenie aplikacji sieci web organizacji.</span><span class="sxs-lookup"><span data-stu-id="38781-110">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="38781-111">Mapowania żądania do odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="38781-111">Mapping Requests to Responses</span></span>

<span data-ttu-id="38781-112">Centrum w aplikacji platformy ASP.NET Core żądania przychodzące są mapowane na wychodzące odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="38781-112">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="38781-113">Na niskim poziomie jest to zrobić za pomocą oprogramowania pośredniczącego i proste aplikacje platformy ASP.NET Core i mikrousług może składać się wyłącznie z niestandardowych oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="38781-113">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="38781-114">Podczas korzystania z platformy ASP.NET Core MVC, można pracować nieco wyższego poziomu, myśląc pod względem *tras*, *kontrolerów*, i *akcje*.</span><span class="sxs-lookup"><span data-stu-id="38781-114">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of *routes*, *controllers*, and *actions*.</span></span> <span data-ttu-id="38781-115">Każde żądanie przychodzące jest porównywana z tabeli routingu aplikacji, a jeśli znaleziono pasującej trasy do żądania obsługi ma zostać wywołana metoda skojarzone z akcją (należących do kontrolera).</span><span class="sxs-lookup"><span data-stu-id="38781-115">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="38781-116">Jeśli nie pasującej trasy zostanie znaleziony, program obsługi błędów (w tym przypadku zwracanie wyniku NotFound) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="38781-116">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="38781-117">Trasy z konwencjonalnej i tras atrybutów, można użyć aplikacji MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="38781-117">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="38781-118">Trasy z konwencjonalnej są zdefiniowane w kodzie, określając routingu *konwencje* przy użyciu składni, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="38781-118">Conventional routes are defined in code, specifying routing *conventions* using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="38781-119">W tym przykładzie dodano trasę o nazwie "domyślne" do tabeli routingu.</span><span class="sxs-lookup"><span data-stu-id="38781-119">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="38781-120">Definiuje szablon trasy z symbole zastępcze *kontrolera*, *akcji*, i *identyfikator*. Symbole zastępcze kontroler i akcja ma określony domyślny ("Home" i "Index", odpowiednio), i identyfikator symbol zastępczy jest opcjonalne (na mocy niniejszej "?" zastosowane do niego).</span><span class="sxs-lookup"><span data-stu-id="38781-120">It defines a route template with placeholders for *controller*, *action*, and *id*. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="38781-121">Konwencji zdefiniowane w tym miejscu stanów odpowiadających pierwsza część żądanie do nazwy kontrolera, a druga część do akcji, a następnie w razie potrzeby trzeciej części reprezentuje parametr id.</span><span class="sxs-lookup"><span data-stu-id="38781-121">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="38781-122">Trasy z konwencjonalnej są zazwyczaj definiowane w jednym miejscu aplikacji, takich jak w metodzie Konfiguruj w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="38781-122">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="38781-123">Tras atrybutów są stosowane bezpośrednio do kontrolerów i akcji, a nie określono globalnie.</span><span class="sxs-lookup"><span data-stu-id="38781-123">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="38781-124">To ustawienie zaleta ich mogą znacznie szybciej odnajdywać rozważasz usługę konkretnej metody, ale oznacza, że informacje routingu nie są przechowywane w jednym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-124">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="38781-125">Atrybut trasy możesz można łatwo określić wiele tras dla danego działania, a także łączenia tras między kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-125">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="38781-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="38781-126">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

<span data-ttu-id="38781-127">Można określić trasy [HttpGet] i oddziel podobne atrybutów, dzięki czemu nie trzeba dodać [trasy\] atrybutów.</span><span class="sxs-lookup"><span data-stu-id="38781-127">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route\] attributes.</span></span> <span data-ttu-id="38781-128">Tras atrybutów można także użyć tokenów, aby zmniejszyć trzeba powtórzyć nazwy kontrolera lub akcji, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="38781-128">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

<span data-ttu-id="38781-129">Po danego żądania ma dopasowane do trasy, ale przed akcją metoda jest wywoływana, ASP.NET Core MVC będzie wykonywać [modelu powiązania](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) i [modelu weryfikacji](https://docs.microsoft.com/aspnet/core/mvc/models/validation) na żądanie.</span><span class="sxs-lookup"><span data-stu-id="38781-129">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) and [model validation](https://docs.microsoft.com/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="38781-130">Wiązanie modelu jest odpowiedzialny za konwersji przychodzących danych protokołu HTTP do typów .NET określony jako parametry metody akcji do wywołania.</span><span class="sxs-lookup"><span data-stu-id="38781-130">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="38781-131">Na przykład jeśli metoda akcji oczekuje parametru identyfikatora int, ten parametr z wartości w ramach żądania będzie podejmować wiązania modelu.</span><span class="sxs-lookup"><span data-stu-id="38781-131">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="38781-132">Aby to zrobić, tworzenia powiązania modelu szuka wartości przesłanego formularza, wartości trasy, sama i wartości ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="38781-132">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="38781-133">Zakładając, że wartość identyfikatora zostanie znaleziony, zostanie przekonwertowany na liczbę całkowitą przed przekazaniem do metody akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-133">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="38781-134">Po powiązaniu modelu, ale przed wywołaniem metody akcji występuje weryfikacji modelu.</span><span class="sxs-lookup"><span data-stu-id="38781-134">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="38781-135">Weryfikacja modelu używa opcjonalnych atrybutów w typie modelu i pozwala zagwarantować, że obiekt modelu podana spełnia wymogi niektórych danych.</span><span class="sxs-lookup"><span data-stu-id="38781-135">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="38781-136">Niektóre wartości mogą być określone jako wymagane lub ograniczone do niektórych długości lub zakresu numerycznego, itp. Jeśli zostaną określone atrybuty weryfikacji, ale modelu nie jest zgodna z ich wymaganiami, właściwość ModelState.IsValid będzie mieć wartość false, a zestaw reguł sprawdzania poprawności, które uległy awarii będzie dostępna do wysłania do klienta zgłoszenia żądania.</span><span class="sxs-lookup"><span data-stu-id="38781-136">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="38781-137">Jeśli korzystasz z weryfikacją modelu, należy zawsze Sprawdź, czy model jest prawidłowy, przed wykonaniem wszelkie zmiany stanu polecenia, aby upewnić się, że aplikacja nie jest uszkodzony przez nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="38781-137">If you are using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="38781-138">Można użyć [filtru](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) Aby uniknąć konieczności dodawania kodu to każda akcja.</span><span class="sxs-lookup"><span data-stu-id="38781-138">You can use a [filter](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="38781-139">Filtry MVC ASP.NET Core umożliwiają o przechwytywaniu grup żądania, tak, aby wspólne zasady i kompleksowymi problemy, które mogą być stosowane na podstawie docelowego.</span><span class="sxs-lookup"><span data-stu-id="38781-139">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="38781-140">Filtry można zastosować do poszczególnych działań, całe kontrolerów lub globalnie dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-140">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="38781-141">Dla interfejsów API sieci web platformy ASP.NET MVC Core obsługuje [ *negocjowanie zawartości*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), dzięki czemu żądania określić, jak powinien być sformatowany odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="38781-141">For web APIs, ASP.NET Core MVC supports [*content negotiation*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="38781-142">W oparciu o nagłówki udostępnione w żądaniu, akcje zwracający dane sformatuje odpowiedzi w XML, JSON lub innego obsługiwanego formatu.</span><span class="sxs-lookup"><span data-stu-id="38781-142">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="38781-143">Ta funkcja umożliwia tego samego interfejsu API do użycia przez wielu klientów z wymagań formatu danych.</span><span class="sxs-lookup"><span data-stu-id="38781-143">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="38781-144">Odwołania — mapowania żądania do odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="38781-144">References – Mapping Requests to Responses</span></span>
> - <span data-ttu-id="38781-145">**Routing do akcji kontrolera**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="38781-145">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="38781-146">**Model powiązania** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span><span class="sxs-lookup"><span data-stu-id="38781-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span></span>
> - <span data-ttu-id="38781-147">**Sprawdzanie poprawności modelu**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="38781-147">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="38781-148">**Filtry** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span><span class="sxs-lookup"><span data-stu-id="38781-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="38781-149">Praca z zależnościami</span><span class="sxs-lookup"><span data-stu-id="38781-149">Working with Dependencies</span></span>

<span data-ttu-id="38781-150">Platformy ASP.NET Core ma wbudowaną obsługę i wewnętrznie sprawia, że użycie techniką [iniekcji zależności](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="38781-150">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="38781-151">Iniekcji zależności to technika, który umożliwia luźne powiązanie między poszczególnymi częściami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-151">Dependency injection is a technique that enabled loose coupling between different parts of an application.</span></span> <span data-ttu-id="38781-152">Im sprzężenia jest pożądane, ponieważ ułatwi do izolowania poszczególnych części aplikacji, co do testowania lub wymiany.</span><span class="sxs-lookup"><span data-stu-id="38781-152">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="38781-153">Również powoduje mniej prawdopodobne, że zmiany w jednej części aplikacji będą miały wpływ nieoczekiwany gdzieś w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-153">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="38781-154">Iniekcji zależności opiera się na zasadzie odwracanie zależności i często ma kluczowe znaczenie dla osiągnięcia zasady otwarty/zamknięty.</span><span class="sxs-lookup"><span data-stu-id="38781-154">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="38781-155">Podczas obliczania działanie aplikacji z zależnościami, należy wziąć pod [statycznych przylepna](http://deviq.com/static-cling/) kodu zapachu i zapamiętać aphorism "[nowe jest sklejki](http://ardalis.com/new-is-glue)."</span><span class="sxs-lookup"><span data-stu-id="38781-155">When evaluating how your application works with its dependencies, beware of the [static cling](http://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](http://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="38781-156">Statyczne przylepna występuje podczas wykonywania wywołań do metod statycznych klas lub dostępu do właściwości statycznych, które ma efekty uboczne ani zależności w infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="38781-156">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="38781-157">Na przykład jeśli masz metodę, która wywołuje metody statycznej, który z kolei zapisuje do bazy danych, metodę jest ściśle powiązane z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="38781-157">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="38781-158">Wszystko, co dzieli tego wywołania bazy danych spowoduje przerwanie metodę.</span><span class="sxs-lookup"><span data-stu-id="38781-158">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="38781-159">Testowanie tych metod jest bardzo trudne, ponieważ testy te wymagają komercyjnych mocking bibliotek mock statyczne wywołania, lub należy badać tylko z bazy danych testu w miejscu.</span><span class="sxs-lookup"><span data-stu-id="38781-159">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="38781-160">Statyczne wywołania, które nie ma żadnych zależności od infrastruktury, zwłaszcza tych, które są całkowicie bezstanowych jest poprawna wywołań i nie mają wpływu na sprzężenia lub pola (poza sprzężenia kodu statyczne wywołania, sam).</span><span class="sxs-lookup"><span data-stu-id="38781-160">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="38781-161">Wielu deweloperów zrozumieć ryzyka przylepna statyczne i stan globalny, ale będzie nadal ściśle połączenie ich kod do implementacji określonego przez bezpośrednie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="38781-161">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="38781-162">"Nowe jest sklejki" ma być przypomnieniem tego sprzężenia, a nie ogólne potępianiu stosowania słowo kluczowe new.</span><span class="sxs-lookup"><span data-stu-id="38781-162">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="38781-163">Tak jak w przypadku wywołania metody statycznej nowych wystąpień typów, które zwykle mają bez zewnętrznych zależności nie ściśle sprzęgania kodu szczegóły implementacji lub utrudnić testowania.</span><span class="sxs-lookup"><span data-stu-id="38781-163">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="38781-164">Jednak zawsze, gdy klasa zostanie uruchomiony, po prostu krótki chwilę potrwać należy wziąć pod uwagę, czy warto być zakodowane tego konkretnego wystąpienia w określonej lokalizacji, jeśli jest lepsze projekt, aby zażądać tego wystąpienia jako zależność.</span><span class="sxs-lookup"><span data-stu-id="38781-164">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="38781-165">Deklarowanie zależności</span><span class="sxs-lookup"><span data-stu-id="38781-165">Declare Your Dependencies</span></span>

<span data-ttu-id="38781-166">Platformy ASP.NET Core opiera się o metod i ich zależności, żądając jako argumenty zadeklarować klasy.</span><span class="sxs-lookup"><span data-stu-id="38781-166">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="38781-167">Aplikacje ASP.NET są zwykle tworzone w klasie uruchomienia, które jest skonfigurowany do obsługi iniekcji zależności w kilku miejscach.</span><span class="sxs-lookup"><span data-stu-id="38781-167">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="38781-168">Jeśli klasa uruchamiania konstruktora, mogą żądać zależności za pomocą konstruktora, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="38781-168">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

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

<span data-ttu-id="38781-169">Klasa początkowa jest interesujące, że nie ma żadnych wymagań jawnego typu dla niego.</span><span class="sxs-lookup"><span data-stu-id="38781-169">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="38781-170">Nie dziedziczy po klasie podstawowej specjalne uruchamiania, ani implementuje żadnych konkretnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="38781-170">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="38781-171">Można określić konstruktora, lub nie, a następnie można określić dowolną liczbę parametrów w Konstruktorze można dowolnie.</span><span class="sxs-lookup"><span data-stu-id="38781-171">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="38781-172">Po uruchomieniu hosta sieci web skonfigurowana dla aplikacji wywoła Klasa początkowa zostały informację, aby użyć i użyje do wypełnienia wszelkie zależności, wymaga Klasa początkowa iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="38781-172">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="38781-173">Oczywiście jeśli żądania parametrów, które nie są skonfigurowane w kontenerze usługi używane przez program ASP.NET Core otrzymasz wyjątek, ale tak długo, jak trzymać zależności kontenera zna, możesz poprosić o dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="38781-173">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="38781-174">Iniekcji zależności jest wbudowana w aplikacji platformy ASP.NET Core prawo od początku, po utworzeniu wystąpienia uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="38781-174">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="38781-175">Nie zatrzymał istnieje dla klasy uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="38781-175">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="38781-176">Możesz również poprosić o zależności w metodzie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="38781-176">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="38781-177">Metoda ConfigureServices jest wyjątkiem to zachowanie; tylko jeden parametr typu IServiceCollection musi wykonać.</span><span class="sxs-lookup"><span data-stu-id="38781-177">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="38781-178">Naprawdę nie musi obsługiwać iniekcji zależności, ponieważ z jednej strony jest odpowiedzialny za dodawanie obiektów w kontenerze usługi, a w drugim ma dostęp do wszystkich aktualnie skonfigurowanych usług za pomocą parametru IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="38781-178">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="38781-179">W związku z tym można pracować z zależnościami zdefiniowana w kolekcji usług platformy ASP.NET Core w każdej części Klasa początkowa, żądając wymagane usługi, jako parametr lub z IServiceCollection w ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="38781-179">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="38781-180">Jeśli należy się upewnić, niektóre usługi są dostępne do własnej klasy uruchamiania, można je skonfigurować przy użyciu WebHostBuilder oraz sposób jej ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="38781-180">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="38781-181">Klasa początkowa jest model powinien strukturą innych części aplikacji platformy ASP.NET Core, kontrolerów z oprogramowaniem pośredniczącym filtrów do własnych usług.</span><span class="sxs-lookup"><span data-stu-id="38781-181">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="38781-182">W każdym przypadku należy wykonać [jawne zależności zasady](http://deviq.com/explicit-dependencies-principle/)żąda zależności, a nie bezpośrednio ich tworzenia i wykorzystaniu iniekcji zależności w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-182">In each case, you should follow the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="38781-183">Należy zwrócić szczególną uwagę na jak i gdzie bezpośrednio wystąpienia implementacji, szczególnie usług i obiekty, które działają z infrastrukturą lub mieć skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="38781-183">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="38781-184">Preferowane jest praca z obiektów abstrakcyjnych zdefiniowanych w aplikacji podstawowych i przekazane jako argumenty do hardcoding odwołania do typów konkretnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="38781-184">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="38781-185">Struktura aplikacji</span><span class="sxs-lookup"><span data-stu-id="38781-185">Structuring the Application</span></span>

<span data-ttu-id="38781-186">Aplikacje wbudowanymi zwykle mają jeden punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="38781-186">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="38781-187">W przypadku aplikacji sieci web platformy ASP.NET Core punkt wejścia będą projektu sieci web platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="38781-187">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="38781-188">Jednakże, który nie oznacza rozwiązania powinien składać się z jednego projektu.</span><span class="sxs-lookup"><span data-stu-id="38781-188">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="38781-189">Warto podzielić aplikację do różnych warstw, aby wykonać separacji.</span><span class="sxs-lookup"><span data-stu-id="38781-189">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="38781-190">Po podzielić się do warstwy, warto wykracza poza folderów do osobnych projektów, które mogą pomóc osiągnąć lepszą hermetyzacji.</span><span class="sxs-lookup"><span data-stu-id="38781-190">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="38781-191">Najlepsze sposób na osiągnięcie tych celów z aplikacji platformy ASP.NET Core jest odmianą czystej architektury omówionych w rozdziale 5.</span><span class="sxs-lookup"><span data-stu-id="38781-191">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="38781-192">Po tej metody rozwiązanie aplikacji będzie składać się z oddzielnych biblioteki interfejsu użytkownika, infrastruktury i ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="38781-192">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="38781-193">Oprócz tych projektów projekty testowe oddzielne uwzględniono również (testowanie opisanej w rozdziale 9).</span><span class="sxs-lookup"><span data-stu-id="38781-193">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="38781-194">Model obiektów i interfejsów aplikacji powinna zostać umieszczona w projekcie ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="38781-194">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="38781-195">Ten projekt zostanie jako kilka zależności jak to możliwe, i innych projektów w rozwiązaniu będzie odwoływać się on.</span><span class="sxs-lookup"><span data-stu-id="38781-195">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="38781-196">Jednostki biznesowe, które muszą zostać utrwalony są definiowane w projekcie ApplicationCore są usług, które nie zależą bezpośrednio infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="38781-196">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="38781-197">Szczegóły implementacji, takie jak realizację trwałości lub jak powiadomienia zostaną wysłane do użytkownika, są przechowywane w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="38781-197">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="38781-198">Ten projekt będzie odwoływać się do konkretnej implementacji pakiety, takie jak Entity Framework Core, ale nie powinny ujawniać szczegółowe informacje o tych implementacji poza projektem.</span><span class="sxs-lookup"><span data-stu-id="38781-198">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="38781-199">Usługi infrastruktury oraz repozytoria powinien implementować interfejsów, które są zdefiniowane w projekcie ApplicationCore i ich implementacji trwałości są odpowiedzialne za odczytywanie i zapisywanie jednostek zdefiniowanych w ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="38781-199">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="38781-200">Projektu platformy ASP.NET Core jest odpowiedzialny za wszelkie problemy dotyczące do poziomu interfejsu użytkownika, ale nie może zawierać szczegóły infrastruktury i logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="38781-200">The ASP.NET Core project itself is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="38781-201">W rzeczywistości w idealnym przypadku nie powinny nawet ona zależności w projekcie infrastruktury, co pomoże upewnij się, że przypadkowo wprowadzono nie zależności między dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="38781-201">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="38781-202">Można to osiągnąć przy użyciu kontenera Podpisane innych firm, takich jak StructureMap, dzięki czemu można zdefiniować reguły Podpisane w klasach rejestru w każdym projekcie.</span><span class="sxs-lookup"><span data-stu-id="38781-202">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="38781-203">Innym sposobem oddzielenia aplikacji od szczegóły implementacji jest mikrousług wywołania aplikacji, możliwe, że wdrożone w poszczególnych kontenerach Docker.</span><span class="sxs-lookup"><span data-stu-id="38781-203">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="38781-204">Rozdzielenie lepsze problemy i oddzielenie niż wykorzystaniu Podpisane między dwa projekty, ale ma stopnia złożoności.</span><span class="sxs-lookup"><span data-stu-id="38781-204">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="38781-205">Funkcja organizacji</span><span class="sxs-lookup"><span data-stu-id="38781-205">Feature Organization</span></span>

<span data-ttu-id="38781-206">Domyślnie aplikacje platformy ASP.NET Core organizowanie struktury ich folderów kontrolery i widoki i często ViewModels.</span><span class="sxs-lookup"><span data-stu-id="38781-206">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="38781-207">Kod po stronie klienta do obsługi tych struktur po stronie serwera jest zwykle przechowywane oddzielnie w folderze wwwroot.</span><span class="sxs-lookup"><span data-stu-id="38781-207">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="38781-208">Jednak dużych aplikacji mogą wystąpić problemy z daną organizacją, ponieważ pracy z dowolnej funkcji danego często wymaga przechodzenie między folderami te.</span><span class="sxs-lookup"><span data-stu-id="38781-208">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="38781-209">Pobiera to bardziej trudne, wraz z rozwojem liczbę plików i podfolderów znajdujących się w każdym folderze, co zapewnia w dużym stopniem przewijanie w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="38781-209">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="38781-210">Jedno rozwiązanie tego problemu jest zorganizowanie kodu aplikacji przez *funkcji* zamiast według typu pliku.</span><span class="sxs-lookup"><span data-stu-id="38781-210">One solution to this problem is to organize application code by *feature* instead of by file type.</span></span> <span data-ttu-id="38781-211">Ten styl organizacji jest zazwyczaj zwane foldery funkcji lub funkcja wycinków (Zobacz też: [pionowy wycinków](http://deviq.com/vertical-slices/)).</span><span class="sxs-lookup"><span data-stu-id="38781-211">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](http://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="38781-212">ASP.NET Core MVC obsługuje obszary, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="38781-212">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="38781-213">Obszary można utworzyć oddzielne zestawy kontrolery i widoki folderów (a także żadnych modeli skojarzone) w każdym folderze obszaru.</span><span class="sxs-lookup"><span data-stu-id="38781-213">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="38781-214">Przykład struktury folderów, za pomocą obszarów przedstawiono na rysunku 7-1.</span><span class="sxs-lookup"><span data-stu-id="38781-214">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="38781-215">Rysunek 7-1 próbka obszaru organizacji</span><span class="sxs-lookup"><span data-stu-id="38781-215">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="38781-216">Korzystając z obszarów, należy użyć do dekoracji kontrolerów z nazwę obszaru, do którego należą te atrybuty:</span><span class="sxs-lookup"><span data-stu-id="38781-216">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="38781-217">Należy również dodać obsługę obszaru do trasy:</span><span class="sxs-lookup"><span data-stu-id="38781-217">You also need to add area support to your routes:</span></span>

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

<span data-ttu-id="38781-218">Oprócz wbudowanych wsparcia dla obszarów umożliwia także własne struktury folderów i konwencje zamiast atrybutów i trasy niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="38781-218">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="38781-219">Umożliwi to foldery funkcji, które nie obejmują osobne foldery widoki, kontrolery, itp., pamiętając płaska hierarchii i ułatwiając zobaczyć wszystkie powiązane pliki w jednym miejscu dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="38781-219">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="38781-220">Platformy ASP.NET Core używa konwencji wbudowanych typów kontrolowanie swojego zachowania.</span><span class="sxs-lookup"><span data-stu-id="38781-220">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="38781-221">Można zmodyfikować lub Zastąp te Konwencji.</span><span class="sxs-lookup"><span data-stu-id="38781-221">You can modify or replace these conventions.</span></span> <span data-ttu-id="38781-222">Na przykład można utworzyć Konwencji, który będzie automatycznie pobrać nazwy funkcji dla danego kontrolera oparte na przestrzeń nazw (która zazwyczaj są powiązane z folderu, w którym znajduje się kontroler):</span><span class="sxs-lookup"><span data-stu-id="38781-222">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

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

<span data-ttu-id="38781-223">Następnie możesz określić tę Konwencję jako opcja po dodaniu obsługi MVC dla aplikacji w ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="38781-223">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="38781-224">Platformy ASP.NET Core MVC również używa konwencji zlokalizować widoki.</span><span class="sxs-lookup"><span data-stu-id="38781-224">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="38781-225">Można zastąpić go z Konwencją niestandardowe, aby widoki będą znajdować się w folderach funkcji (przy użyciu nazwy funkcji podanego przez FeatureConvention powyżej).</span><span class="sxs-lookup"><span data-stu-id="38781-225">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="38781-226">Można dowiedzieć się więcej na temat tej metody i pobrać przykładowy pracy z artykuł w witrynie MSDN [wycinków funkcji dla platformy ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span><span class="sxs-lookup"><span data-stu-id="38781-226">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="38781-227">Cross-Cutting Concerns</span><span class="sxs-lookup"><span data-stu-id="38781-227">Cross-Cutting Concerns</span></span>

<span data-ttu-id="38781-228">Wzrostem aplikacji staje się coraz bardziej ważne składników wychodzących kompleksowymi problemy, aby wyeliminować dublowania i zachowanie spójności.</span><span class="sxs-lookup"><span data-stu-id="38781-228">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="38781-229">Przykłady kompleksowymi problemy w aplikacji platformy ASP.NET Core to uwierzytelnianie, reguł sprawdzania poprawności modelu, buforowanie danych wyjściowych i obsługi błędu, jeśli istnieje wiele innych.</span><span class="sxs-lookup"><span data-stu-id="38781-229">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="38781-230">Platformy ASP.NET Core MVC [filtry](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) zezwalają na uruchamianie kodu przed lub po pewne czynności w potoku przetwarzania żądań.</span><span class="sxs-lookup"><span data-stu-id="38781-230">ASP.NET Core MVC [filters](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="38781-231">Na przykład filtr można uruchomić przed i po wiązania modelu, przed i po akcji lub przed i po wyniku akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-231">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="38781-232">Umożliwia także filtr autoryzacji do kontrolowania dostępu do pozostałego potoku.</span><span class="sxs-lookup"><span data-stu-id="38781-232">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="38781-233">Pokazuje rysunki 7-2 jak żądanie wykonania przepływów filtry, skonfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="38781-233">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![Żądanie jest przetwarzane za pośrednictwem filtry autoryzacji, filtrów zasobów powiązania modelu, filtry akcji, wykonywanie akcji i konwersji wynik akcji, filtry wyjątków, filtry wyników i wykonania wyniku.](./media/image7-2.png)

<span data-ttu-id="38781-236">Rysunek 7-2 wykonywania żądania za pomocą filtrów i żądania potoku.</span><span class="sxs-lookup"><span data-stu-id="38781-236">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="38781-237">Filtry zwykle są zaimplementowane jako atrybuty, aby można było zastosować je kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-237">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="38781-238">Po dodaniu w taki sposób, filtry określone na zastąpienie poziomie akcji lub kompilacji na filtrów z określonego na poziomie kontrolera, które same zastąpić filtry globalne.</span><span class="sxs-lookup"><span data-stu-id="38781-238">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="38781-239">Na przykład \[trasy\] atrybut może służyć do zbudowania tras między kontrolerów i akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-239">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="38781-240">Podobnie autoryzacji można konfigurować na poziomie kontrolera i następnie zastąpione przez poszczególne działania, jak w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="38781-240">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="38781-241">Pierwsza metoda logowania, używa filtra AllowAnonymous (atrybut) do przesłonięcia filtr autoryzacji, należy ustawić na poziomie kontrolera.</span><span class="sxs-lookup"><span data-stu-id="38781-241">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="38781-242">Akcja ForgotPassword (i innych działań w klasie, która nie ma atrybutu AllowAnonymous) wymaga uwierzytelnionego żądania.</span><span class="sxs-lookup"><span data-stu-id="38781-242">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="38781-243">Filtry można wyeliminować dublowanie w postaci typowych obsługę błędów zasady dla interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="38781-243">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="38781-244">Na przykład typowa zasad interfejsu API jest do zwrócenia NotFound odpowiedzi na żądania PRZYWOŁUJĄCE klucze, które nie istnieją, a element BadRequest odpowiedzi w przypadku niepowodzenia weryfikacji modelu.</span><span class="sxs-lookup"><span data-stu-id="38781-244">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="38781-245">W poniższym przykładzie pokazano tych dwóch zasad, w akcji:</span><span class="sxs-lookup"><span data-stu-id="38781-245">The following example demonstrates these two policies in action:</span></span>

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

<span data-ttu-id="38781-246">Nie zezwalaj z metody akcji zapełnić warunkowego kodu następująco.</span><span class="sxs-lookup"><span data-stu-id="38781-246">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="38781-247">Zamiast tego należy pobierać zasady do filtrów, które mogą być stosowane w zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="38781-247">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="38781-248">W tym przykładzie sprawdzenie poprawności modelu, który powinna wystąpić zawsze, gdy polecenie są wysyłane do interfejsu API, może być zastąpiony następującego atrybutu:</span><span class="sxs-lookup"><span data-stu-id="38781-248">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

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

<span data-ttu-id="38781-249">Podobnie filtr może służyć do sprawdzenia, czy rekord istnieje i zwróć 404, przed wykonaniem akcji, eliminując konieczność wykonania tych testów w akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-249">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="38781-250">Po pobierane limit typowych konwersji i zorganizowane rozwiązanie, aby oddzielić infrastruktury kodu i logiki biznesowej w Interfejsie użytkownika, MVC metody akcji powinny być bardzo elastycznej:</span><span class="sxs-lookup"><span data-stu-id="38781-250">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="38781-251">Więcej o implementacji filtry i pobrać przykładowy pracy z artykuł w witrynie MSDN [rzeczywistych World platformy ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).</span><span class="sxs-lookup"><span data-stu-id="38781-251">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="38781-252">Odwołania — struktury aplikacji</span><span class="sxs-lookup"><span data-stu-id="38781-252">References – Structuring Applications</span></span>
> - <span data-ttu-id="38781-253">**Obszary**</span><span class="sxs-lookup"><span data-stu-id="38781-253">**Areas**</span></span>  
> <span data-ttu-id="38781-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span><span class="sxs-lookup"><span data-stu-id="38781-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span></span>
> - <span data-ttu-id="38781-255">**MSDN — funkcja wycinki dla platformy ASP.NET Core MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx></span><span class="sxs-lookup"><span data-stu-id="38781-255">**MSDN – Feature Slices for ASP.NET Core MVC**
<https://msdn.microsoft.com/magazine/mt763233.aspx></span></span>
> - <span data-ttu-id="38781-256">**Filtry**</span><span class="sxs-lookup"><span data-stu-id="38781-256">**Filters**</span></span>  
> <span data-ttu-id="38781-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="38781-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>
> - <span data-ttu-id="38781-258">**MSDN — rzeczywistych platformy ASP.NET Core MVC filtry**</span><span class="sxs-lookup"><span data-stu-id="38781-258">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
> <span data-ttu-id="38781-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span><span class="sxs-lookup"><span data-stu-id="38781-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span></span>

## <a name="security"></a><span data-ttu-id="38781-260">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="38781-260">Security</span></span>

<span data-ttu-id="38781-261">Zabezpieczanie aplikacji sieci web jest duża tematu, z wiele kwestii.</span><span class="sxs-lookup"><span data-stu-id="38781-261">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="38781-262">Na najbardziej podstawowym poziomie zabezpieczeń obejmuje zapewnienie, że wiesz, kto pochodzące z danego żądania i zapewnienie, że żądanie ma dostęp tylko do zasobów, które powinno.</span><span class="sxs-lookup"><span data-stu-id="38781-262">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="38781-263">Uwierzytelnianie to proces porównanie poświadczenia dostarczone z żądaniem w zaufanym magazynie danych, aby zobaczyć, czy żądanie powinny być traktowane jako pochodzący od znanych jednostek.</span><span class="sxs-lookup"><span data-stu-id="38781-263">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="38781-264">Autoryzacja jest przez proces ograniczania dostępu do niektórych zasobów na podstawie tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="38781-264">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="38781-265">Trzeci problem dotyczący zabezpieczeń chroni żądań podsłuchiwaniu przez osoby trzecie, dla których należy co najmniej [upewnij się, że protokół SSL jest używany przez aplikację](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span><span class="sxs-lookup"><span data-stu-id="38781-265">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="38781-266">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="38781-266">Authentication</span></span>

<span data-ttu-id="38781-267">Tożsamość platformy ASP.NET Core to system członkostwa, używanych do obsługi funkcji logowania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-267">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="38781-268">Ma ona Obsługa kont użytkowników lokalnych, a także Obsługa dostawcy logowania zewnętrznego od dostawców, takich jak Microsoft Account, Twitter, Facebook i Google.</span><span class="sxs-lookup"><span data-stu-id="38781-268">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="38781-269">Oprócz ASP.NET Core Identity, aplikacja może używać uwierzytelniania systemu windows lub dostawca tożsamości innych firm, takich jak [tożsamości serwera](https://github.com/IdentityServer/IdentityServer4).</span><span class="sxs-lookup"><span data-stu-id="38781-269">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="38781-270">Tożsamość platformy ASP.NET Core znajduje się w nowych szablonów projektu, jeśli wybrano opcję indywidualnych kont użytkowników.</span><span class="sxs-lookup"><span data-stu-id="38781-270">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="38781-271">Ten szablon obejmuje obsługę rejestracji i logowania, logowań zewnętrznych, zapomniane hasła oraz dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="38781-271">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="38781-272">Rysunek 7-3 Wybierz indywidualne konta użytkowników do ma tożsamość wstępnie.</span><span class="sxs-lookup"><span data-stu-id="38781-272">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="38781-273">Obsługa tożsamości jest konfigurowana w uruchamiania, zarówno w ConfigureServices i konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="38781-273">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

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

<span data-ttu-id="38781-274">Jest ważne, czy UseIdentity są wyświetlane przed UseMvc w metodzie Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="38781-274">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="38781-275">W przypadku konfigurowania tożsamości w ConfigureServices, można zauważyć wywołania AddDefaultTokenProviders.</span><span class="sxs-lookup"><span data-stu-id="38781-275">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="38781-276">To nie ma nic wspólnego z tokenów, które mogą służyć do zabezpieczenia komunikacji w sieci web, ale zamiast tego odwołuje się do dostawcy, które utworzyć monity, które mogą być wysyłane do użytkowników za pośrednictwem programu SMS lub wiadomości e-mail w kolejności ich, aby potwierdzić swoją tożsamość.</span><span class="sxs-lookup"><span data-stu-id="38781-276">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="38781-277">Możesz dowiedzieć się więcej [konfigurowania uwierzytelniania dwuskładnikowego](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) i [włączania dostawcy logowania zewnętrznego](https://docs.microsoft.com/aspnet/core/security/authentication/social/) z oficjalna dokumentacja platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="38781-277">You can learn more about [configuring two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) and [enabling external login providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="38781-278">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="38781-278">Authorization</span></span>

<span data-ttu-id="38781-279">Najprostsza forma autoryzacji obejmuje ograniczania dostępu do użytkowników anonimowych.</span><span class="sxs-lookup"><span data-stu-id="38781-279">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="38781-280">Można to osiągnąć poprzez zastosowanie po prostu \[autoryzacji\] atrybutu niektórych kontrolerach ani akcji.</span><span class="sxs-lookup"><span data-stu-id="38781-280">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="38781-281">Role są używane, ten atrybut może dodatkowo rozszerzona ograniczyć dostęp do użytkowników, którzy należą do określonych ról, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="38781-281">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="38781-282">W takim przypadku użytkowników należących do ról HRManager lub not (lub obie) będzie mieć dostęp do SalaryController.</span><span class="sxs-lookup"><span data-stu-id="38781-282">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="38781-283">Aby wymagać, że użytkownik należy do wielu ról (nie tylko jeden z kilku), można zastosować atrybutu wielokrotnie, określenie wymaganej roli zawsze.</span><span class="sxs-lookup"><span data-stu-id="38781-283">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="38781-284">Określanie niektóre zestawy role jako ciągi w wielu różnych kontrolerów i akcji może prowadzić do niepożądanych powtarzania.</span><span class="sxs-lookup"><span data-stu-id="38781-284">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="38781-285">Można skonfigurować zasady autoryzacji, które hermetyzują reguł autoryzacji, a następnie określ zasady zamiast poszczególnych ról, podczas stosowania \[autoryzacji\] atrybutu:</span><span class="sxs-lookup"><span data-stu-id="38781-285">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="38781-286">W ten sposób za pomocą zasad, można oddzielić rodzaje działań jest ograniczony z określonych ról lub reguły, które mają zastosowanie do niej.</span><span class="sxs-lookup"><span data-stu-id="38781-286">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="38781-287">Później, jeśli tworzysz nową rolę, która musi mieć dostęp do niektórych zasobów można tylko aktualizować zasady, a nie aktualizacji co lista ról na każdym \[autoryzacji\] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="38781-287">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="38781-288">Oświadczenia</span><span class="sxs-lookup"><span data-stu-id="38781-288">Claims</span></span>

<span data-ttu-id="38781-289">Oświadczenia są par wartości nazw, które reprezentują właściwości uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="38781-289">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="38781-290">Na przykład może przechowywać numer pracownika użytkowników jako oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="38781-290">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="38781-291">Następnie można oświadczeń jako część zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="38781-291">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="38781-292">Można utworzyć zasadę o nazwie "EmployeeOnly" wymaga istnienia oświadczenie o nazwie "NumerPracownika", jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="38781-292">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

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

<span data-ttu-id="38781-293">Ta zasada może być użyta z \[autoryzacji\] atrybut, aby chronić kontrolera i/lub akcji, jak opisano powyżej.</span><span class="sxs-lookup"><span data-stu-id="38781-293">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="38781-294">Zabezpieczanie interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="38781-294">Securing Web APIs</span></span>

<span data-ttu-id="38781-295">Większość interfejsów API sieci web należy zaimplementować uwierzytelnianie oparte na token systemu.</span><span class="sxs-lookup"><span data-stu-id="38781-295">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="38781-296">Token uwierzytelniania jest bezstanowe i skalowalne zaprojektowane.</span><span class="sxs-lookup"><span data-stu-id="38781-296">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="38781-297">W systemie uwierzytelniania opartego na tokenie klient muszą najpierw uwierzytelnić się z dostawcą uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="38781-297">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="38781-298">Jeśli to się powiedzie, klient wystawił token, to po prostu kryptograficznie znaczący ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="38781-298">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="38781-299">Gdy klient następnie musi wysłać żądania do interfejsu API, dodaje ten token jako nagłówka w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="38781-299">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="38781-300">Następnie serwer weryfikuje token w nagłówku żądania znaleziono przed wykonaniem żądania.</span><span class="sxs-lookup"><span data-stu-id="38781-300">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="38781-301">Rysunek 7-4 przedstawiono ten proces.</span><span class="sxs-lookup"><span data-stu-id="38781-301">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="38781-303">**Rysunek 7-4.**</span><span class="sxs-lookup"><span data-stu-id="38781-303">**Figure 7-4.**</span></span> <span data-ttu-id="38781-304">Token uwierzytelniania dla interfejsów API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="38781-304">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="38781-305">Odwołania — zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="38781-305">References – Security</span></span>
> - <span data-ttu-id="38781-306">**Omówienie dokumentów dotyczących zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="38781-306">**Security Docs Overview**</span></span>  
> <span data-ttu-id="38781-307">https://docs.microsoft.com/aspnet/core/security/</span><span class="sxs-lookup"><span data-stu-id="38781-307">https://docs.microsoft.com/aspnet/core/security/</span></span>
> - <span data-ttu-id="38781-308">**Wymuszanie protokołu SSL w aplikacji platformy ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="38781-308">**Enforcing SSL in an ASP.NET Core App**</span></span>  
> <span data-ttu-id="38781-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span><span class="sxs-lookup"><span data-stu-id="38781-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span></span>
> - <span data-ttu-id="38781-310">**Wprowadzenie do tożsamości**</span><span class="sxs-lookup"><span data-stu-id="38781-310">**Introduction to Identity**</span></span>  
> <span data-ttu-id="38781-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span><span class="sxs-lookup"><span data-stu-id="38781-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span></span>
> - <span data-ttu-id="38781-312">**Wprowadzenie do autoryzacji**</span><span class="sxs-lookup"><span data-stu-id="38781-312">**Introduction to Authorization**</span></span>  
> <span data-ttu-id="38781-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span><span class="sxs-lookup"><span data-stu-id="38781-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span></span>
> - <span data-ttu-id="38781-314">**Uwierzytelnianie i autoryzacja aplikacji interfejsu API w usłudze aplikacji Azure**</span><span class="sxs-lookup"><span data-stu-id="38781-314">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
> <span data-ttu-id="38781-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span><span class="sxs-lookup"><span data-stu-id="38781-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span></span>

## <a name="client-communication"></a><span data-ttu-id="38781-316">Komunikacja klienta</span><span class="sxs-lookup"><span data-stu-id="38781-316">Client Communication</span></span>

<span data-ttu-id="38781-317">Oprócz obsługująca stron i odpowiada na żądania danych za pośrednictwem interfejsów API sieci web, aplikacje platformy ASP.NET Core może komunikować się bezpośrednio z połączonych klientów.</span><span class="sxs-lookup"><span data-stu-id="38781-317">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="38781-318">Tej komunikacji wychodzącej można użyć różnych technologii transportu jest najbardziej typowych Websocket.</span><span class="sxs-lookup"><span data-stu-id="38781-318">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="38781-319">SignalR platformy ASP.NET Core to biblioteki, która upraszcza rodzaj funkcji komunikacji serwera do klienta w czasie rzeczywistym dla poszczególnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-319">ASP.NET Core SignalR is a library that makes it simple to kind of real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="38781-320">SignalR obsługuje wiele technologii transportu, w tym Websocket i abstracts wielu zadań szczegóły implementacji od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="38781-320">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="38781-321">SignalR platformy ASP.NET Core jest obecnie opracowywane i będą dostępne w następnej wersji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="38781-321">ASP.NET Core SignalR is currently under development, and will be available in the next release of ASP.NET Core.</span></span> <span data-ttu-id="38781-322">Jednak inne [otworzyć źródła Websocket biblioteki](https://github.com/radu-matei/websocket-manager) są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="38781-322">However, other [open source WebSockets libraries](https://github.com/radu-matei/websocket-manager) are currently available.</span></span>

<span data-ttu-id="38781-323">Komunikacja z klientem w czasie rzeczywistym, czy przy użyciu protokołu WebSockets bezpośrednio lub innych technik są przydatne w różnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="38781-323">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="38781-324">Oto kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="38781-324">Some examples include:</span></span>

-   <span data-ttu-id="38781-325">Aplikacje na żywo pokoju rozmów</span><span class="sxs-lookup"><span data-stu-id="38781-325">Live chat room applications</span></span>

-   <span data-ttu-id="38781-326">Monitorowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="38781-326">Monitoring applications</span></span>

-   <span data-ttu-id="38781-327">Aktualizacje postępu zadania</span><span class="sxs-lookup"><span data-stu-id="38781-327">Job progress updates</span></span>

-   <span data-ttu-id="38781-328">Powiadomienia</span><span class="sxs-lookup"><span data-stu-id="38781-328">Notifications</span></span>

-   <span data-ttu-id="38781-329">Interaktywne formularze aplikacji</span><span class="sxs-lookup"><span data-stu-id="38781-329">Interactive forms applications</span></span>

<span data-ttu-id="38781-330">Podczas kompilowania komunikacji z klientem w aplikacji, są zazwyczaj dwa składniki:</span><span class="sxs-lookup"><span data-stu-id="38781-330">When building client communication into your applications, there are typically two components:</span></span>

-   <span data-ttu-id="38781-331">Menedżer połączeń po stronie serwera (koncentratora SignalR, WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="38781-331">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

-   <span data-ttu-id="38781-332">Biblioteka klienta</span><span class="sxs-lookup"><span data-stu-id="38781-332">Client-side library</span></span>

<span data-ttu-id="38781-333">Klienci nie są ograniczone do przeglądarek — aplikacje mobilne, aplikacje konsoli i inne aplikacje natywne mogą również komunikować się za pomocą SignalR/Websocket.</span><span class="sxs-lookup"><span data-stu-id="38781-333">Clients are not limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="38781-334">Następujący program proste echa całą zawartość wysyłane do aplikacji rozmów w konsoli jako część WebSocketManager przykładową aplikację:</span><span class="sxs-lookup"><span data-stu-id="38781-334">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

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
```

<span data-ttu-id="38781-335">Należy rozważyć wystąpić sposoby, w których aplikacji komunikują się bezpośrednio z aplikacji klienckich i należy wziąć pod uwagę, czy w czasie rzeczywistym komunikacji poprawiające użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-335">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="38781-336">Odwołania — komunikacji z klientem</span><span class="sxs-lookup"><span data-stu-id="38781-336">References – Client Communication</span></span>
> - <span data-ttu-id="38781-337">**SignalR platformy ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="38781-337">**ASP.NET Core SignalR**</span></span>  
> <span data-ttu-id="38781-338"><https://github.com/aspnet/SignalR></span><span class="sxs-lookup"><span data-stu-id="38781-338"><https://github.com/aspnet/SignalR></span></span>
> - <span data-ttu-id="38781-339">**WebSocket Manager**</span><span class="sxs-lookup"><span data-stu-id="38781-339">**WebSocket Manager**</span></span>  
> <span data-ttu-id="38781-340">https://github.com/radu-matei/websocket-manager</span><span class="sxs-lookup"><span data-stu-id="38781-340">https://github.com/radu-matei/websocket-manager</span></span>

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="38781-341">Domeny oparte na projektowanie — powinien zastosowaniu?</span><span class="sxs-lookup"><span data-stu-id="38781-341">Domain-Driven Design – Should You Apply It?</span></span>

<span data-ttu-id="38781-342">Projektowanie oparte na domenie (DDD) jest elastyczne podejście do tworzenia oprogramowania, które jest kładzie nacisk koncentrujących się na *domeny business*.</span><span class="sxs-lookup"><span data-stu-id="38781-342">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the *business domain*.</span></span> <span data-ttu-id="38781-343">Umieszcza duże nacisk położono na komunikację i interakcji z expert(s) domeny biznesowe, które można powiązać z deweloperów, jak działa system rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="38781-343">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="38781-344">Na przykład jeśli tworzysz systemu, który obsługuje standardowych transakcji ekspert Twojej domeny może być doświadczonym brokera standardowych.</span><span class="sxs-lookup"><span data-stu-id="38781-344">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="38781-345">DDD zaprojektowano w celu rozwiązania problemów biznesowych dużych, złożonych i często nie jest odpowiedni dla aplikacji mniejszych, prostszy, inwestycji w opis i modelowanie domeny nie jest warto go.</span><span class="sxs-lookup"><span data-stu-id="38781-345">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="38781-346">Podczas tworzenia oprogramowania następujące podejście DDD, zespołu (w tym nietechnicznych uczestnikom projektu i współautorzy) należy opracować *powszechny języka* miejsce problem.</span><span class="sxs-lookup"><span data-stu-id="38781-346">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a *ubiquitous language* for the problem space.</span></span> <span data-ttu-id="38781-347">Oznacza to należy używać tej samej terminologii koncepcji rzeczywistych modelowanego, odpowiednik oprogramowania i wszelkich struktur, które może istnieć, aby utrwalić koncepcji (na przykład tabel bazy danych).</span><span class="sxs-lookup"><span data-stu-id="38781-347">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="38781-348">W związku z tym pojęcia opisane w języku powszechny powinny być podstawą dla Twojego *modelu domeny*.</span><span class="sxs-lookup"><span data-stu-id="38781-348">Thus, the concepts described in the ubiquitous language should form the basis for your *domain model*.</span></span>

<span data-ttu-id="38781-349">Model domeny obejmuje obiekty, które współdziałają ze sobą do reprezentowania zachowanie systemu.</span><span class="sxs-lookup"><span data-stu-id="38781-349">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="38781-350">Te obiekty mogą można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="38781-350">These objects may fall into the following categories:</span></span>

-   <span data-ttu-id="38781-351">[Jednostki](http://deviq.com/entity/), które reprezentują obiektów z wątkiem tożsamości.</span><span class="sxs-lookup"><span data-stu-id="38781-351">[Entities](http://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="38781-352">Jednostki są zwykle przechowywany w trwałości za pomocą klucza za pomocą którego mogą później zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="38781-352">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

-   <span data-ttu-id="38781-353">[Agreguje](http://deviq.com/aggregate-pattern/), które reprezentują grupy obiektów, które powinny zostać utrwalony jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="38781-353">[Aggregates](http://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

-   <span data-ttu-id="38781-354">[Wartość obiektów](http://deviq.com/value-object/), które reprezentują pojęcia, które można porównać na podstawie sumy wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="38781-354">[Value objects](http://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="38781-355">Na przykład DateRange składające się z datę początkową i końcową.</span><span class="sxs-lookup"><span data-stu-id="38781-355">For example, DateRange consisting of a start and end date.</span></span>

-   <span data-ttu-id="38781-356">[Zdarzenia domeny](https://martinfowler.com/eaaDev/DomainEvent.html), które reprezentują czynności wykonywane w ramach systemu, które mogą być przydatne do innych części systemu.</span><span class="sxs-lookup"><span data-stu-id="38781-356">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="38781-357">Należy pamiętać, że model domeny DDD zalecaną zachowanie złożonego w modelu.</span><span class="sxs-lookup"><span data-stu-id="38781-357">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="38781-358">Jednostki, w szczególności, nie tylko należy kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="38781-358">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="38781-359">Gdy model domeny nie ma zachowania, a jedynie reprezentuje stan systemu, jest określany jako [anemic modelu](http://deviq.com/anemic-model/), która jest niepożądanych w DDD.</span><span class="sxs-lookup"><span data-stu-id="38781-359">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](http://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="38781-360">Oprócz tych typów wzór DDD zwykle wdraża różnych wzorców:</span><span class="sxs-lookup"><span data-stu-id="38781-360">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

-   <span data-ttu-id="38781-361">[Repozytorium](http://deviq.com/repository-pattern/), dla abstrakcyjność szczegółów trwałości.</span><span class="sxs-lookup"><span data-stu-id="38781-361">[Repository](http://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

-   <span data-ttu-id="38781-362">[Fabryka](https://en.wikipedia.org/wiki/Factory_method_pattern), dla hermetyzując Tworzenie obiektów złożonych.</span><span class="sxs-lookup"><span data-stu-id="38781-362">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

-   <span data-ttu-id="38781-363">Zdarzenia domeny dla oddzielenie zachowanie zależne od wyzwalania zachowanie.</span><span class="sxs-lookup"><span data-stu-id="38781-363">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

-   <span data-ttu-id="38781-364">[Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)dla hermetyzowany zachowanie złożone i/lub szczegóły implementacji infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="38781-364">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

-   <span data-ttu-id="38781-365">[Polecenie](https://en.wikipedia.org/wiki/Command_pattern)dla oddzielenie wydawania polecenia i wykonywania samo polecenie.</span><span class="sxs-lookup"><span data-stu-id="38781-365">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

-   <span data-ttu-id="38781-366">[Specyfikacja](http://deviq.com/specification-pattern/), dla zawierający szczegóły zapytania.</span><span class="sxs-lookup"><span data-stu-id="38781-366">[Specification](http://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="38781-367">DDD również zalecane jest stosowanie czystej architektury omówionych wcześniej, co pozwala na luźne powiązanie, hermetyzacji i kod, który łatwo można sprawdzić za pomocą testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="38781-367">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="38781-368">Kiedy należy zastosować DDD</span><span class="sxs-lookup"><span data-stu-id="38781-368">When Should You Apply DDD</span></span>

<span data-ttu-id="38781-369">DDD jest dobrze nadaje się do dużych aplikacji z złożoności firma (nie tylko technicznych).</span><span class="sxs-lookup"><span data-stu-id="38781-369">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="38781-370">Aplikacja powinna wymagać wiedzy ekspertów domeny.</span><span class="sxs-lookup"><span data-stu-id="38781-370">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="38781-371">Model domeny, reprezentujący reguł biznesowych i interakcje poza po prostu przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych powinna mieć znaczący zachowanie.</span><span class="sxs-lookup"><span data-stu-id="38781-371">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="38781-372">Kiedy nie należy zastosować DDD</span><span class="sxs-lookup"><span data-stu-id="38781-372">When Shouldn't You Apply DDD</span></span>

<span data-ttu-id="38781-373">DDD obejmuje inwestycje w modelowania, architektura i komunikacji, który nie może być uzasadnione dla mniejszych aplikacji lub aplikacji, które są po prostu CRUD (Tworzenie/odczytu/aktualizowania/usuwania).</span><span class="sxs-lookup"><span data-stu-id="38781-373">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="38781-374">Jeśli użytkownik chce podejścia aplikacji po DDD, ale okazać, że domena ma anemic modelu i nie może być konieczne przemyślenia swoje podejście.</span><span class="sxs-lookup"><span data-stu-id="38781-374">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="38781-375">Aplikacja nie może być konieczne DDD albo może być potrzebna pomoc refaktoryzacji hermetyzowania logiki biznesowej w modelu domeny, a nie z bazy danych lub interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-375">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="38781-376">Rozwiązanie hybrydowe byłoby do użycia tylko DDD obszarów transakcyjnej lub bardziej złożonych aplikacji, ale nie prostsze CRUD lub tylko do odczytu części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38781-376">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="38781-377">Na przykład nie musi mieć ograniczenia agregacji, jeśli jest kwerendy danych, aby wyświetlić raport lub do wizualizacji danych dla pulpitu nawigacyjnego.</span><span class="sxs-lookup"><span data-stu-id="38781-377">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="38781-378">Jest całkowicie dopuszczalne mają oddzielne, prostszy model odczytu dla tych wymagań.</span><span class="sxs-lookup"><span data-stu-id="38781-378">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="38781-379">Odwołania — projektowanie oparte na domenie</span><span class="sxs-lookup"><span data-stu-id="38781-379">References – Domain-Driven Design</span></span>
> - <span data-ttu-id="38781-380">**DDD w zwykły język angielski (StackOverflow odpowiedzi)**</span><span class="sxs-lookup"><span data-stu-id="38781-380">**DDD in Plain English (StackOverflow Answer)**</span></span>  
> <span data-ttu-id="38781-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span><span class="sxs-lookup"><span data-stu-id="38781-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span></span>

## <a name="deployment"></a><span data-ttu-id="38781-382">wdrażania</span><span class="sxs-lookup"><span data-stu-id="38781-382">Deployment</span></span>

<span data-ttu-id="38781-383">Obejmuje kilka czynności w procesie wdrożenia aplikacji platformy ASP.NET Core, niezależnie od tego, w którym będzie hostowana.</span><span class="sxs-lookup"><span data-stu-id="38781-383">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="38781-384">Pierwszym krokiem jest, aby opublikować aplikację, można to zrobić przy użyciu dotnet publikowania polecenia interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="38781-384">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="38781-385">Spowoduje to skompilować aplikację i umieść wszystkie pliki potrzebne do uruchomienia aplikacji do wskazanego folderu.</span><span class="sxs-lookup"><span data-stu-id="38781-385">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="38781-386">Podczas wdrażania w programie Visual Studio, wykonanie tego kroku można automatycznie.</span><span class="sxs-lookup"><span data-stu-id="38781-386">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="38781-387">Folder publikowania zawiera pliki .exe i dll dla aplikacji i jej zależności.</span><span class="sxs-lookup"><span data-stu-id="38781-387">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="38781-388">Aplikację autonomiczną zawiera również wersję środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="38781-388">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="38781-389">Aplikacje platformy ASP.NET Core będą także obejmować widoków MVC, zasoby statyczne klienta i pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="38781-389">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="38781-390">Aplikacje platformy ASP.NET Core są aplikacji konsoli, które musi zostać uruchomiony, gdy serwer jest uruchamiany oraz ponownego uruchomienia, jeśli wystąpiła awaria aplikacji (lub serwera).</span><span class="sxs-lookup"><span data-stu-id="38781-390">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="38781-391">Menedżer procesu może służyć do automatyzacji tego procesu.</span><span class="sxs-lookup"><span data-stu-id="38781-391">A process manager can be used to automate this process.</span></span> <span data-ttu-id="38781-392">Najbardziej typowe menedżerów procesu ASP.NET Core to Nginx i Apache na systemie Linux oraz usług IIS lub usługi systemu Windows w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="38781-392">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="38781-393">Oprócz menedżerem procesu aplikacji platformy ASP.NET Core znajdującej się na serwerze sieci web Kestrel należy użyć serwera zwrotnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="38781-393">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="38781-394">Zwrotnego serwera proxy odbiera żądania HTTP z Internetem i przekazuje je do Kestrel po niektórych wstępne obsługi.</span><span class="sxs-lookup"><span data-stu-id="38781-394">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="38781-395">Serwery zwrotny serwer proxy zapewniają warstwę zabezpieczeń dla aplikacji i są wymagane dla wdrożeń krawędzi (ujawniony na ruch z Internetu).</span><span class="sxs-lookup"><span data-stu-id="38781-395">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="38781-396">Kestrel jest względnie nowe i jeszcze nie zapewnia ochronę przed atakami niektórych.</span><span class="sxs-lookup"><span data-stu-id="38781-396">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="38781-397">Kestrel nie obsługuje również obsługi wielu aplikacji na tym samym porcie, więc technik, takich jak nagłówki hosta nie można jej używać z nią do włączenia obsługi wielu aplikacji na tym samym port i adres IP.</span><span class="sxs-lookup"><span data-stu-id="38781-397">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Kestrel do Internetu](./media/image7-5.png)

<span data-ttu-id="38781-399">Rysunek 7-5 ASP.NET hostowane w Kestrel za serwerem proxy wstecznego</span><span class="sxs-lookup"><span data-stu-id="38781-399">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="38781-400">Inny scenariusz, w którym mogą być pomocne zwrotny serwer proxy jest zapewnienie wiele aplikacji przy użyciu protokołu SSL i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="38781-400">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="38781-401">W takim przypadku tylko zwrotny serwer proxy należy skonfigurować protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="38781-401">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="38781-402">Komunikacja między zwrotnego serwera proxy i Kestrel może odbywać się za pośrednictwem protokołu HTTP, jak pokazano w rysunek 7-6.</span><span class="sxs-lookup"><span data-stu-id="38781-402">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="38781-403">Rysunek 7-6 ASP.NET hostowanej za zabezpieczone HTTPS zwrotnego serwera proxy</span><span class="sxs-lookup"><span data-stu-id="38781-403">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="38781-404">Jest coraz bardziej popularne podejście do hostowania aplikacji platformy ASP.NET Core w kontenerze Docker, który następnie może być przechowywana lokalnie lub wdrożeniu na platformie Azure opartej na chmurze hostingu.</span><span class="sxs-lookup"><span data-stu-id="38781-404">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="38781-405">Kontener Docker mogą zawierać kod aplikacji uruchomionych na Kestrel i czy można wdrożyć za serwerem proxy odwrotnej zgodnie z powyższym.</span><span class="sxs-lookup"><span data-stu-id="38781-405">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="38781-406">Jeśli przechowujesz aplikacji na platformie Azure, można bramę aplikacji usługi Microsoft Azure jako dedykowane urządzenie wirtualne udostępniają kilka usług.</span><span class="sxs-lookup"><span data-stu-id="38781-406">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="38781-407">Oprócz działający jako zwrotny serwer proxy dla poszczególnych aplikacji, bramy aplikacji może również oferują następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="38781-407">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

-   <span data-ttu-id="38781-408">Równoważenie obciążenia HTTP</span><span class="sxs-lookup"><span data-stu-id="38781-408">HTTP load balancing</span></span>

-   <span data-ttu-id="38781-409">Odciążanie protokołu SSL (SSL tylko do Internetu)</span><span class="sxs-lookup"><span data-stu-id="38781-409">SSL offload (SSL only to Internet)</span></span>

-   <span data-ttu-id="38781-410">Kompleksowe SSL</span><span class="sxs-lookup"><span data-stu-id="38781-410">End to End SSL</span></span>

-   <span data-ttu-id="38781-411">Routing w wielu lokacjach (maksymalnie 20 Lokacje w jednej bramie aplikacji konsolidacji)</span><span class="sxs-lookup"><span data-stu-id="38781-411">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

-   <span data-ttu-id="38781-412">Zapora aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="38781-412">Web application firewall</span></span>

-   <span data-ttu-id="38781-413">Obsługa protokołu Websocket</span><span class="sxs-lookup"><span data-stu-id="38781-413">Websocket support</span></span>

-   <span data-ttu-id="38781-414">Zaawansowane diagnostyki</span><span class="sxs-lookup"><span data-stu-id="38781-414">Advanced diagnostics</span></span>

<span data-ttu-id="38781-415">*Dowiedz się więcej na temat opcji wdrożenia usługi Azure w rozdziale 10.*</span><span class="sxs-lookup"><span data-stu-id="38781-415">*Learn more about Azure deployment options in Chapter 10.*</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="38781-416">Odwołania — wdrożenia</span><span class="sxs-lookup"><span data-stu-id="38781-416">References – Deployment</span></span>
> - <span data-ttu-id="38781-417">**Omówienie wdrożenia i obsługi**</span><span class="sxs-lookup"><span data-stu-id="38781-417">**Hosting and Deployment Overview**</span></span>  
> <span data-ttu-id="38781-418"><https://docs.microsoft.com/aspnet/core/publishing/></span><span class="sxs-lookup"><span data-stu-id="38781-418"><https://docs.microsoft.com/aspnet/core/publishing/></span></span>
> - <span data-ttu-id="38781-419">**Kiedy należy używać Kestrel z zwrotny serwer proxy**</span><span class="sxs-lookup"><span data-stu-id="38781-419">**When to use Kestrel with a reverse proxy**</span></span>  
> <span data-ttu-id="38781-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span><span class="sxs-lookup"><span data-stu-id="38781-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span></span>
> - <span data-ttu-id="38781-421">**Host aplikacji platformy ASP.NET Core w Docker**</span><span class="sxs-lookup"><span data-stu-id="38781-421">**Host ASP.NET Core apps in Docker**</span></span>  
> <span data-ttu-id="38781-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span><span class="sxs-lookup"><span data-stu-id="38781-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span></span>
> - <span data-ttu-id="38781-423">**Wprowadzenie do bramy aplikacji Azure**</span><span class="sxs-lookup"><span data-stu-id="38781-423">**Introducing Azure Application Gateway**</span></span>  
> <span data-ttu-id="38781-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span><span class="sxs-lookup"><span data-stu-id="38781-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="38781-425">[Poprzednie] (typowe klienta-po stronie web-technologies.md) [dalej] (work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="38781-425">[Previous] (common-client-side-web-technologies.md) [Next] (work-with-data-in-asp-net-core-apps.md)</span></span>
