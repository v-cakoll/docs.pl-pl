---
title: Implementowanie warstwy aplikacji mikrousług za pomocą internetowego interfejsu API
description: Zrozumienie iniekcji zależności i wzorców mediatora i ich szczegóły implementacji w warstwie aplikacji interfejsu API sieci Web.
ms.date: 01/30/2020
ms.openlocfilehash: a88f3bfd11ea06df085ca82ed7265cb37006fc31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502447"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="f76c7-103">Implementowanie warstwy aplikacji mikrousług przy użyciu interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="f76c7-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="f76c7-104">Użyj funkcji Iniekcji zależności, aby wstrzyknąć obiekty infrastruktury do warstwy aplikacji</span><span class="sxs-lookup"><span data-stu-id="f76c7-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="f76c7-105">Jak wspomniano wcześniej, warstwa aplikacji może być zaimplementowana jako część artefaktu (zestawu), który budujesz, na przykład w ramach projektu interfejsu API sieci Web lub projektu aplikacji sieci Web MVC.</span><span class="sxs-lookup"><span data-stu-id="f76c7-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="f76c7-106">W przypadku mikrousługi zbudowanej z ASP.NET Core warstwa aplikacji będzie zwykle biblioteką interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f76c7-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="f76c7-107">Jeśli chcesz oddzielić to, co pochodzi z ASP.NET Core (jego infrastruktury oraz kontrolerów) od niestandardowego kodu warstwy aplikacji, można również umieścić warstwę aplikacji w oddzielnej bibliotece klas, ale jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f76c7-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="f76c7-108">Na przykład kod warstwy aplikacji mikrousługi zamawiania jest bezpośrednio implementowany jako część projektu **Ordering.API** (ASP.NET core web api projektu), jak pokazano na rysunku 7-23.</span><span class="sxs-lookup"><span data-stu-id="f76c7-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Zrzut ekranu przedstawiający mikrousługę Ordering.API w Eksploratorze rozwiązań.":::
<span data-ttu-id="f76c7-110">Widok Eksploratora rozwiązań mikrousługi Ordering.API, przedstawiający podfoldery w folderze Aplikacji: Zachowania, Polecenia, DomainEventHandlers, IntegrationEvents, Models, Queries i Validations.</span><span class="sxs-lookup"><span data-stu-id="f76c7-110">The Solution Explorer view of the Ordering.API microservice, showing the sub-folders under the Application folder: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries and Validations.</span></span>
:::image-end:::

<span data-ttu-id="f76c7-111">**Rysunek 7-23**.</span><span class="sxs-lookup"><span data-stu-id="f76c7-111">**Figure 7-23**.</span></span> <span data-ttu-id="f76c7-112">Warstwa aplikacji w projekcie interfejsu API interfejsu API ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f76c7-112">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="f76c7-113">ASP.NET Core zawiera prosty [wbudowany kontener IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowany przez interfejs IServiceProvider), który domyślnie obsługuje iniekcji konstruktora i ASP.NET udostępnia niektóre usługi za pośrednictwem DI.</span><span class="sxs-lookup"><span data-stu-id="f76c7-113">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="f76c7-114">ASP.NET Core używa *terminu usługa* dla każdego z typów, które rejestrują, które zostaną wstrzyknięte za pośrednictwem DI.</span><span class="sxs-lookup"><span data-stu-id="f76c7-114">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="f76c7-115">Skonfigurować wbudowane usługi kontenera w ConfigureServices metody w klasie startowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-115">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="f76c7-116">Zależności są implementowane w usługach, które wymaga typu i że można zarejestrować się w kontenerze IoC.</span><span class="sxs-lookup"><span data-stu-id="f76c7-116">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="f76c7-117">Zazwyczaj chcesz wstrzyknąć zależności, które implementują obiekty infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f76c7-117">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="f76c7-118">Bardzo typowa zależność do wstrzykiwania jest repozytorium.</span><span class="sxs-lookup"><span data-stu-id="f76c7-118">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="f76c7-119">Ale można wstrzyknąć wszelkie inne zależności infrastruktury, które mogą mieć.</span><span class="sxs-lookup"><span data-stu-id="f76c7-119">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="f76c7-120">Dla prostszych implementacji można bezpośrednio wstrzyknąć jednostki pracy obiektu wzorca (EF DbContext obiektu), ponieważ DBContext jest również implementacja obiektów trwałości infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f76c7-120">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="f76c7-121">W poniższym przykładzie można zobaczyć, jak .NET Core jest wstrzykiwanie wymaganych obiektów repozytorium za pośrednictwem konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-121">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="f76c7-122">Klasa jest program obsługi poleceń, które omówimy w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-122">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="f76c7-123">Klasa używa wstrzykuje repozytoriów do wykonania transakcji i utrwalić zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-123">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="f76c7-124">Nie ma znaczenia, czy ta klasa jest programobsługi poleceń, ASP.NET core web api metody kontrolera lub [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="f76c7-124">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="f76c7-125">Ostatecznie jest to prosta klasa, która używa repozytoriów, jednostek domeny i innych koordynacji aplikacji w sposób podobny do programu obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-125">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="f76c7-126">Iniekcji zależności działa w ten sam sposób dla wszystkich wymienionych klas, jak w przykładzie przy użyciu DI na podstawie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-126">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="f76c7-127">Rejestrowanie typów implementacji zależności i interfejsów lub abstrakcji</span><span class="sxs-lookup"><span data-stu-id="f76c7-127">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="f76c7-128">Przed użyciem obiektów wstrzykuje za pomocą konstruktorów, musisz wiedzieć, gdzie zarejestrować interfejsy i klasy, które produkują obiekty wstrzykiwane do klas aplikacji za pośrednictwem DI.</span><span class="sxs-lookup"><span data-stu-id="f76c7-128">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="f76c7-129">(Podobnie jak DI na podstawie konstruktora, jak pokazano wcześniej.)</span><span class="sxs-lookup"><span data-stu-id="f76c7-129">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="f76c7-130">Użyj wbudowanego kontenera IoC dostarczonego przez ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f76c7-130">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="f76c7-131">Korzystając z wbudowanego kontenera IoC dostarczonego przez ASP.NET Core, należy zarejestrować typy, które mają zostać wstrzyknięte w metodzie ConfigureServices w pliku Startup.cs, tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f76c7-131">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="f76c7-132">Najczęstszym wzorcem podczas rejestrowania typów w kontenerze IoC jest zarejestrowanie pary typów — interfejsu i powiązanej z nim klasy implementacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-132">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="f76c7-133">Następnie podczas żądania obiektu z kontenera IoC za pośrednictwem dowolnego konstruktora, należy zażądać obiektu określonego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-133">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="f76c7-134">Na przykład w poprzednim przykładzie ostatni wiersz stwierdza, że gdy którykolwiek z konstruktorów mają zależność od IMyCustomRepository (interfejs lub abstrakcji), kontener IoC wstrzyknie wystąpienie implementacji MyCustomSQLServerRepository Klasa.</span><span class="sxs-lookup"><span data-stu-id="f76c7-134">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="f76c7-135">Używanie biblioteki Scrutor do automatycznej rejestracji typów</span><span class="sxs-lookup"><span data-stu-id="f76c7-135">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="f76c7-136">Korzystając z DI w .NET Core, można mieć możliwość skanowania zestawu i automatycznie zarejestrować jego typy zgodnie z konwencją.</span><span class="sxs-lookup"><span data-stu-id="f76c7-136">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="f76c7-137">Ta funkcja nie jest obecnie dostępna w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f76c7-137">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="f76c7-138">Można jednak użyć biblioteki [Scrutor](https://github.com/khellang/Scrutor) do tego celu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-138">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="f76c7-139">Takie podejście jest wygodne, gdy masz dziesiątki typów, które muszą być zarejestrowane w kontenerze IoC.</span><span class="sxs-lookup"><span data-stu-id="f76c7-139">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f76c7-140">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="f76c7-140">Additional resources</span></span>

- <span data-ttu-id="f76c7-141">**Mateusz Król. Rejestracja usług w Scrutor** </span><span class="sxs-lookup"><span data-stu-id="f76c7-141">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="f76c7-142">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="f76c7-142">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="f76c7-143">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f76c7-143">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="f76c7-144">Użyj Autofac jako pojemnika IoC</span><span class="sxs-lookup"><span data-stu-id="f76c7-144">Use Autofac as an IoC container</span></span>

<span data-ttu-id="f76c7-145">Można również użyć dodatkowych kontenerów IoC i podłączyć je do potoku ASP.NET Core, jak w mikrousługi zamawiania w eShopOnContainers, który używa [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="f76c7-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="f76c7-146">Korzystając z Autofac zazwyczaj zarejestrować typy za pomocą modułów, które umożliwiają dzielenie typów rejestracji między wiele plików w zależności od tego, gdzie są typy, tak jak można mieć typy aplikacji rozproszone w wielu bibliotekach klas.</span><span class="sxs-lookup"><span data-stu-id="f76c7-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="f76c7-147">Na przykład poniżej przedstawiono [moduł aplikacji Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) dla projektu [interfejsu API sieci Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) z typami, które chcesz wstrzyknąć.</span><span class="sxs-lookup"><span data-stu-id="f76c7-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="f76c7-148">Autofac posiada również funkcję [skanowania złożeń i rejestrowania typów według konwencji nazw.](https://autofac.readthedocs.io/en/latest/register/scanning.html)</span><span class="sxs-lookup"><span data-stu-id="f76c7-148">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="f76c7-149">Proces rejestracji i pojęcia są bardzo podobne do sposobu rejestrowania typów za pomocą wbudowanego kontenera ASP.NET Core IoC, ale składnia podczas korzystania z Autofac jest nieco inna.</span><span class="sxs-lookup"><span data-stu-id="f76c7-149">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="f76c7-150">W przykładowym kodzie abstrakcji IOrderRepository jest rejestrowany wraz z klasy implementacji OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="f76c7-150">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="f76c7-151">Oznacza to, że za każdym razem, gdy konstruktor deklaruje zależność za pośrednictwem abstrakcji iOrderRepository lub interfejsu, kontener IoC wstrzyknie wystąpienie OrderRepository klasy.</span><span class="sxs-lookup"><span data-stu-id="f76c7-151">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="f76c7-152">Typ zakresu wystąpienia określa sposób, w jaki wystąpienie jest współużytkowane między żądaniami dla tej samej usługi lub zależności.</span><span class="sxs-lookup"><span data-stu-id="f76c7-152">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="f76c7-153">Po nałożeniu żądania zależności kontener IoC może zwrócić następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="f76c7-153">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="f76c7-154">Pojedyncze wystąpienie na zakres istnienia (określone w ASP.NET kontenerze Core IoC jako *zakres).*</span><span class="sxs-lookup"><span data-stu-id="f76c7-154">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="f76c7-155">Nowe wystąpienie na zależność (określane w ASP.NET kontenerze Core IoC jako *przejściowe).*</span><span class="sxs-lookup"><span data-stu-id="f76c7-155">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="f76c7-156">Pojedyncze wystąpienie współużytkowane przez wszystkie obiekty przy użyciu kontenera IoC (określane go w kontenerze ASP.NET Core IoC jako *singleton).*</span><span class="sxs-lookup"><span data-stu-id="f76c7-156">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f76c7-157">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="f76c7-157">Additional resources</span></span>

- <span data-ttu-id="f76c7-158">**Wprowadzenie do wstrzykiwań zależności w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="f76c7-158">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="f76c7-159">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="f76c7-159">**Autofac.**</span></span> <span data-ttu-id="f76c7-160">Oficjalna dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="f76c7-160">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="f76c7-161">**Porównanie ASP.NET okresy istnienia kontenera Core IoC z zakresami wystąpienia kontenera Autofac IoC — Cesar de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="f76c7-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="f76c7-162">Implementowanie wzorców obsługi poleceń i poleceń</span><span class="sxs-lookup"><span data-stu-id="f76c7-162">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="f76c7-163">W przykładzie Konstruktora DI-through pokazano w poprzedniej sekcji kontener IoC wstrzykiwania repozytoriów za pośrednictwem konstruktora w klasie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="f76c7-164">Ale dokładnie, gdzie były wstrzykiwane?</span><span class="sxs-lookup"><span data-stu-id="f76c7-164">But exactly where were they injected?</span></span> <span data-ttu-id="f76c7-165">W prostym interfejsie API sieci Web (na przykład mikrousługi katalogu w eShopOnContainers) wstrzyknąć je na poziomie kontrolerów MVC, w konstruktorze kontrolera, jako część potoku żądania ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f76c7-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="f76c7-166">Jednak w początkowym kodzie tej sekcji [(CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy z Usługi Ordering.API w eShopOnContainers), wstrzyknięcie zależności odbywa się za pośrednictwem konstruktora określonego programu obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="f76c7-167">Wyjaśnijmy, czym jest program obsługi poleceń i dlaczego chcesz go używać.</span><span class="sxs-lookup"><span data-stu-id="f76c7-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="f76c7-168">Wzorzec polecenia jest nierozerwalnie związane z wzorcem CQRS, który został wprowadzony wcześniej w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="f76c7-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="f76c7-169">CQRS ma dwie strony.</span><span class="sxs-lookup"><span data-stu-id="f76c7-169">CQRS has two sides.</span></span> <span data-ttu-id="f76c7-170">Pierwszym obszarem są zapytania, za pomocą uproszczonych zapytań z [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, co zostało wyjaśnione wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f76c7-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="f76c7-171">Drugi obszar to polecenia, które są punktem wyjścia dla transakcji, a kanał wejściowy spoza usługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="f76c7-172">Jak pokazano na rysunku 7-24, wzorzec jest oparty na akceptowaniu poleceń od strony klienta, przetwarzaniu ich na podstawie reguł modelu domeny i wreszcie utrwalania stanów z transakcjami.</span><span class="sxs-lookup"><span data-stu-id="f76c7-172">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Diagram przedstawiający przepływ danych wysokiego poziomu z klienta do bazy danych.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

<span data-ttu-id="f76c7-174">**Rysunek 7-24**.</span><span class="sxs-lookup"><span data-stu-id="f76c7-174">**Figure 7-24**.</span></span> <span data-ttu-id="f76c7-175">Widok wysokiego poziomu poleceń lub "po stronie transakcyjnej" we wzorcu CQRS</span><span class="sxs-lookup"><span data-stu-id="f76c7-175">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

<span data-ttu-id="f76c7-176">Rysunek 7-24 pokazuje, że aplikacja interfejsu ze strony interfejsu `CommandHandler`i zesłania za pośrednictwem interfejsu API, który pobiera do , który zależy od modelu domeny i infrastruktury, aby zaktualizować bazę danych.</span><span class="sxs-lookup"><span data-stu-id="f76c7-176">Figure 7-24 shows that the UI app sends a command through the API that gets to a `CommandHandler`, that depends on the Domain model and the Infrastructure, to update the database.</span></span>

### <a name="the-command-class"></a><span data-ttu-id="f76c7-177">Klasa polecenia</span><span class="sxs-lookup"><span data-stu-id="f76c7-177">The command class</span></span>

<span data-ttu-id="f76c7-178">Polecenie jest żądaniem dla systemu do wykonania akcji, która zmienia stan systemu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-178">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="f76c7-179">Polecenia są konieczne i powinny być przetwarzane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f76c7-179">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="f76c7-180">Ponieważ polecenia są imperatywami, są one zazwyczaj nazwane z czasownikiem w nastroju imperatywu (na przykład "create" lub "update" i mogą zawierać typ agregacji, takich jak CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="f76c7-180">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="f76c7-181">W przeciwieństwie do zdarzenia, polecenie nie jest faktem z przeszłości; jest to tylko wniosek, a zatem można go odmów odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="f76c7-181">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="f76c7-182">Polecenia mogą pochodzić z interfejsu użytkownika w wyniku zainicjowania żądania przez użytkownika lub od menedżera procesów, gdy menedżer procesów kieruje agregat do wykonania akcji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-182">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="f76c7-183">Ważną cechą polecenia jest to, że powinno być przetwarzane tylko raz przez jednego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="f76c7-183">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="f76c7-184">Dzieje się tak, ponieważ polecenie jest pojedynczą akcją lub transakcją, którą chcesz wykonać w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-184">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="f76c7-185">Na przykład to samo polecenie tworzenia zamówienia nie powinny być przetwarzane więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="f76c7-185">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="f76c7-186">Jest to istotna różnica między poleceniami i zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="f76c7-186">This is an important difference between commands and events.</span></span> <span data-ttu-id="f76c7-187">Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług może być zainteresowanych zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="f76c7-187">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="f76c7-188">Ponadto ważne jest, aby polecenie było przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentnością.</span><span class="sxs-lookup"><span data-stu-id="f76c7-188">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="f76c7-189">Polecenie jest idempotentności, jeśli można go wykonać wiele razy bez zmiany wyniku, ze względu na charakter polecenia lub ze względu na sposób, w jaki system obsługuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-189">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="f76c7-190">Dobrą praktyką jest wykonywanie poleceń i aktualizacji idempotentności, gdy ma to sens zgodnie z regułami biznesowymi i niezmiennymi regułami domeny.</span><span class="sxs-lookup"><span data-stu-id="f76c7-190">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="f76c7-191">Na przykład, aby użyć tego samego przykładu, jeśli z jakiegokolwiek powodu (logika ponawiania prób, hacking, itp.) to samo polecenie CreateOrder dociera do systemu wiele razy, powinieneś być w stanie go zidentyfikować i upewnić się, że nie tworzysz wielu zamówień.</span><span class="sxs-lookup"><span data-stu-id="f76c7-191">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="f76c7-192">Aby to zrobić, należy dołączyć pewnego rodzaju tożsamości w operacjach i określić, czy polecenie lub aktualizacja została już przetworzona.</span><span class="sxs-lookup"><span data-stu-id="f76c7-192">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="f76c7-193">Polecenie wysyłasz do jednego odbiornika; nie publikujesz polecenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-193">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="f76c7-194">Publikowanie jest dla zdarzeń, które stwierdzają fakt, że coś się stało i może być interesujące dla odbiorców zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-194">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="f76c7-195">W przypadku zdarzeń wydawca nie ma wątpliwości co do tego, które odbiorniki otrzymują zdarzenie lub co robią.</span><span class="sxs-lookup"><span data-stu-id="f76c7-195">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="f76c7-196">Ale zdarzenia domeny lub integracji to inna historia już wprowadzona w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="f76c7-196">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="f76c7-197">Polecenie jest implementowane z klasą, która zawiera pola danych lub kolekcje ze wszystkimi informacjami, które są potrzebne do wykonania tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-197">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="f76c7-198">Polecenie jest specjalnym rodzajem obiektu transferu danych (DTO), który jest specjalnie używany do żądania zmian lub transakcji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-198">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="f76c7-199">Samo polecenie jest oparte na dokładnie tych informacjach, które są potrzebne do przetwarzania polecenia i nic więcej.</span><span class="sxs-lookup"><span data-stu-id="f76c7-199">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="f76c7-200">W poniższym przykładzie `CreateOrderCommand` przedstawiono klasę uproszczoną.</span><span class="sxs-lookup"><span data-stu-id="f76c7-200">The following example shows the simplified `CreateOrderCommand` class.</span></span> <span data-ttu-id="f76c7-201">Jest to niezmienne polecenie, które jest używane w mikrousługi porządkowania w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f76c7-201">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="f76c7-202">Zasadniczo klasa polecenia zawiera wszystkie dane potrzebne do wykonywania transakcji biznesowych przy użyciu obiektów modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="f76c7-202">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="f76c7-203">W związku z tym polecenia są po prostu struktury danych, które zawierają dane tylko do odczytu i nie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-203">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="f76c7-204">Nazwa polecenia wskazuje jego przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-204">The command’s name indicates its purpose.</span></span> <span data-ttu-id="f76c7-205">W wielu językach, takich jak C#, polecenia są reprezentowane jako klasy, ale nie są prawdziwe klasy w sensie rzeczywistym obiektowych.</span><span class="sxs-lookup"><span data-stu-id="f76c7-205">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="f76c7-206">Jako dodatkową cechę polecenia są niezmienne, ponieważ oczekiwane użycie polega na tym, że są one przetwarzane bezpośrednio przez model domeny.</span><span class="sxs-lookup"><span data-stu-id="f76c7-206">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="f76c7-207">Nie muszą się zmieniać w przewidywanym okresie życia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-207">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="f76c7-208">W klasie C# niezmienność można osiągnąć, nie mając żadnych ustawiających lub innych metod, które zmieniają stan wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="f76c7-208">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="f76c7-209">Należy pamiętać, że jeśli zamierzasz lub oczekujesz poleceń, aby przejść przez proces serializacji/deserializacji, właściwości muszą mieć private setter i `[DataMember]` (lub `[JsonProperty]`) atrybut.</span><span class="sxs-lookup"><span data-stu-id="f76c7-209">Keep in mind that if you intend or expect commands to go through a serializing/deserializing process, the properties must have a private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute.</span></span> <span data-ttu-id="f76c7-210">W przeciwnym razie deserializator nie będzie mógł zrekonstruować obiektu w miejscu docelowym z wymaganymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="f76c7-210">Otherwise, the deserializer won't be able to reconstruct the object at destination with the required values.</span></span> <span data-ttu-id="f76c7-211">Można również użyć prawdziwie tylko do odczytu właściwości, jeśli klasa ma konstruktora z parametrami dla wszystkich właściwości, ze `[JsonConstructor]`zwykłą konwencją nazewnictwa wielbłądacase i adnotować konstruktora jako .</span><span class="sxs-lookup"><span data-stu-id="f76c7-211">You can also use truly read-only properties if the class has a constructor with parameters for all properties, with the usual camelCase naming convention, and annotate the constructor as `[JsonConstructor]`.</span></span> <span data-ttu-id="f76c7-212">Jednak ta opcja wymaga więcej kodu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-212">However, this option requires more code.</span></span>

<span data-ttu-id="f76c7-213">Na przykład klasa polecenia do tworzenia zamówienia jest prawdopodobnie podobna pod względem danych do kolejności, którą chcesz utworzyć, ale prawdopodobnie nie potrzebujesz tych samych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f76c7-213">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="f76c7-214">Na przykład `CreateOrderCommand` nie ma identyfikatora zamówienia, ponieważ zamówienie nie zostało jeszcze utworzone.</span><span class="sxs-lookup"><span data-stu-id="f76c7-214">For instance, `CreateOrderCommand` does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="f76c7-215">Wiele klas poleceń może być proste, wymaga tylko kilka pól o niektórych stan, który musi zostać zmieniony.</span><span class="sxs-lookup"><span data-stu-id="f76c7-215">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="f76c7-216">Miałoby to miejsce, gdyby tylko zmieniłeś status zamówienia z "w toku" na "płatny" lub "wysłany", używając polecenia podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="f76c7-216">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="f76c7-217">Niektórzy deweloperzy sprawiają, że ich obiekty żądania interfejsu i systemu ui oddzielnie od ich polecenia DTOs, ale to tylko kwestia preferencji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-217">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="f76c7-218">Jest to żmudna separacja z niedużą wartością dodaną, a obiekty mają prawie dokładnie ten sam kształt.</span><span class="sxs-lookup"><span data-stu-id="f76c7-218">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="f76c7-219">Na przykład w eShopOnContainers niektóre polecenia pochodzą bezpośrednio od strony klienta.</span><span class="sxs-lookup"><span data-stu-id="f76c7-219">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="f76c7-220">Klasa obsługi polecenia</span><span class="sxs-lookup"><span data-stu-id="f76c7-220">The Command handler class</span></span>

<span data-ttu-id="f76c7-221">Należy zaimplementować klasę obsługi określonego polecenia dla każdego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-221">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="f76c7-222">Tak działa wzorzec i w tym miejscu użyjesz obiektu polecenia, obiektów domeny i obiektów repozytorium infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f76c7-222">That is how the pattern works, and it's where you'll use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="f76c7-223">Program obsługi poleceń jest w rzeczywistości sercem warstwy aplikacji pod względem CQRS i DDD.</span><span class="sxs-lookup"><span data-stu-id="f76c7-223">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="f76c7-224">Jednak cała logika domeny powinna być zawarta w klasach domeny — w obrębie zagregowanych katalogów głównych (jednostek głównych), jednostek podrzędnych lub [usług domeny,](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)ale nie w programie obsługi poleceń, który jest klasą z warstwy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-224">However, all the domain logic should be contained in the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="f76c7-225">Klasa obsługi poleceń oferuje silny krok w drodze do osiągnięcia zasady pojedynczej odpowiedzialności (SRP) wymienione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-225">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="f76c7-226">Program obsługi poleceń odbiera polecenie i uzyskuje wynik z agregacji, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="f76c7-226">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="f76c7-227">Wynik powinien być pomyślne wykonanie polecenia lub wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f76c7-227">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="f76c7-228">W przypadku wyjątku stan systemu powinien być niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="f76c7-228">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="f76c7-229">Program obsługi poleceń zwykle wykonuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f76c7-229">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="f76c7-230">Odbiera obiekt polecenia, jak DTO (od [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub innego obiektu infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="f76c7-230">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="f76c7-231">Sprawdza, czy polecenie jest prawidłowe (jeśli nie zostanie zweryfikowane przez mediatora).</span><span class="sxs-lookup"><span data-stu-id="f76c7-231">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="f76c7-232">Tworzy wystąpienia agregacji głównej, która jest celem bieżącego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-232">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="f76c7-233">Wykonuje metodę w wystąpieniu głównego agregacji, uzyskując wymagane dane z polecenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-233">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="f76c7-234">Utrzymuje nowy stan agregacji do powiązanej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f76c7-234">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="f76c7-235">Ta ostatnia operacja jest rzeczywistą transakcją.</span><span class="sxs-lookup"><span data-stu-id="f76c7-235">This last operation is the actual transaction.</span></span>

<span data-ttu-id="f76c7-236">Zazwyczaj program obsługi poleceń dotyczy pojedynczej agregacji napędzanej przez jego zagregowanego roota (jednostki głównej).</span><span class="sxs-lookup"><span data-stu-id="f76c7-236">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="f76c7-237">Jeśli odbiór pojedynczego polecenia ma wpływ na wiele agregatów, można użyć zdarzeń domeny do propagowania stanów lub akcji w wielu agregatach.</span><span class="sxs-lookup"><span data-stu-id="f76c7-237">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="f76c7-238">Ważną kwestią jest to, że podczas przetwarzania polecenia, wszystkie logiki domeny powinny być wewnątrz modelu domeny (agregaty), w pełni hermetyzowane i gotowe do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="f76c7-238">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="f76c7-239">Program obsługi poleceń działa tylko jako sposób na uzyskanie modelu domeny z bazy danych i jako ostatni krok, aby poinformować warstwę infrastruktury (repozytoria), aby utrwalić zmiany po zmianie modelu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-239">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="f76c7-240">Zaletą tego podejścia jest to, że można refaktoryzacji logiki domeny w izolowanym, w pełni hermetyzowane, bogate, behawioralne modelu domeny bez zmiany kodu w warstwach aplikacji lub infrastruktury, które są poziom instalacji wodno-kanalizacyjnej (programy obsługi poleceń, Interfejs API sieci Web, repozytoriów itp.).</span><span class="sxs-lookup"><span data-stu-id="f76c7-240">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="f76c7-241">Gdy programy obsługi poleceń stają się złożone, z zbyt dużą logiką, która może być zapachem kodu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-241">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="f76c7-242">Przejrzyj je, a jeśli znajdziesz logikę domeny, refaktoryzuj kod, aby przenieść to zachowanie domeny do metod obiektów domeny (jednostki głównej agregacji i podrzędnej).</span><span class="sxs-lookup"><span data-stu-id="f76c7-242">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="f76c7-243">Jako przykład klasy obsługi poleceń, poniższy kod `CreateOrderCommandHandler` pokazuje tę samą klasę, która została wyświetlona na początku tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="f76c7-243">As an example of a command handler class, the following code shows the same `CreateOrderCommandHandler` class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="f76c7-244">W takim przypadku chcemy wyróżnić Handle metody i operacje z obiektów modelu domeny/agregacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-244">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="f76c7-245">Są to dodatkowe kroki, które powinien wykonać program obsługi poleceń:</span><span class="sxs-lookup"><span data-stu-id="f76c7-245">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="f76c7-246">Użyj danych polecenia do pracy z zagregowanych metod i zachowania roota.</span><span class="sxs-lookup"><span data-stu-id="f76c7-246">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="f76c7-247">Wewnętrznie w obrębie obiektów domeny, podnieść zdarzenia domeny podczas wykonywania transakcji, ale jest przezroczysty z punktu widzenia obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-247">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="f76c7-248">Jeśli wynik operacji agregacji zakończy się pomyślnie i po zakończeniu transakcji, podnieść zdarzenia integracji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-248">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="f76c7-249">(Mogą one również być wywoływane przez klasy infrastruktury, takie jak repozytoria).</span><span class="sxs-lookup"><span data-stu-id="f76c7-249">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f76c7-250">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="f76c7-250">Additional resources</span></span>

- <span data-ttu-id="f76c7-251">**Mark Seemann. Na granicach aplikacje nie są zorientowane obiektowe** </span><span class="sxs-lookup"><span data-stu-id="f76c7-251">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** </span></span>\
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="f76c7-252">**Polecenia i zdarzenia** </span><span class="sxs-lookup"><span data-stu-id="f76c7-252">**Commands and events** </span></span>\
  <https://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="f76c7-253">**Co robi program obsługi poleceń?**</span><span class="sxs-lookup"><span data-stu-id="f76c7-253">**What does a command handler do?**</span></span> \
  <https://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="f76c7-254">**Jimmy Bogard. Wzorce poleceń domeny — programy obsługi** </span><span class="sxs-lookup"><span data-stu-id="f76c7-254">**Jimmy Bogard. Domain Command Patterns – Handlers** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="f76c7-255">**Jimmy Bogard. Wzorce poleceń domeny — sprawdzanie poprawności** </span><span class="sxs-lookup"><span data-stu-id="f76c7-255">**Jimmy Bogard. Domain Command Patterns – Validation** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="f76c7-256">Potok procesu polecenia: jak wyzwolić program obsługi poleceń</span><span class="sxs-lookup"><span data-stu-id="f76c7-256">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="f76c7-257">Następne pytanie brzmi, jak wywołać program obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-257">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="f76c7-258">Można ręcznie wywołać go z każdego powiązanego kontrolera ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f76c7-258">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="f76c7-259">Jednak takie podejście byłoby zbyt powiązane i nie jest idealne.</span><span class="sxs-lookup"><span data-stu-id="f76c7-259">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="f76c7-260">Pozostałe dwie główne opcje, które są zalecanymi opcjami, to:</span><span class="sxs-lookup"><span data-stu-id="f76c7-260">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="f76c7-261">Za pośrednictwem artefaktu wzorca mediatora w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f76c7-261">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="f76c7-262">Z kolejki komunikatów asynchronicznych, pomiędzy kontrolerów i programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-262">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="f76c7-263">Użyj wzorca mediatora (w pamięci) w potoku poleceń</span><span class="sxs-lookup"><span data-stu-id="f76c7-263">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="f76c7-264">Jak pokazano na rysunku 7-25, w podejściu CQRS używasz inteligentnego mediatora, podobnego do magistrali w pamięci, która jest wystarczająco inteligentna, aby przekierować do prawego programu obsługi poleceń na podstawie typu odbieranego polecenia lub DTO.</span><span class="sxs-lookup"><span data-stu-id="f76c7-264">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="f76c7-265">Pojedyncze czarne strzałki między składnikami reprezentują zależności między obiektami (w wielu przypadkach wstrzykuje się przez DI) z ich powiązanych interakcji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-265">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Diagram przedstawiający bardziej szczegółowy przepływ danych z klienta do bazy danych.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

<span data-ttu-id="f76c7-267">**Rysunek 7-25**.</span><span class="sxs-lookup"><span data-stu-id="f76c7-267">**Figure 7-25**.</span></span> <span data-ttu-id="f76c7-268">Używanie wzorca mediatora w procesie w jednej mikrousłudze CQRS</span><span class="sxs-lookup"><span data-stu-id="f76c7-268">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="f76c7-269">Powyższy diagram przedstawia powiększenie z obrazu 7-24: kontroler ASP.NET Core wysyła polecenie do potoku poleceń MediatR, dzięki czemu udają się do odpowiedniego programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-269">The above diagram shows a zoom-in from image 7-24: the ASP.NET Core controller sends the command to MediatR's command pipeline, so they get to the appropriate handler.</span></span>

<span data-ttu-id="f76c7-270">Powodem, dla którego użycie wzorca mediatora ma sens, jest to, że w aplikacjach przedsiębiorstwa żądania przetwarzania mogą się komplikować.</span><span class="sxs-lookup"><span data-stu-id="f76c7-270">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="f76c7-271">Chcesz mieć możliwość dodania otwartej liczby problemów przekrojowych, takich jak rejestrowanie, sprawdzanie poprawności, inspekcje i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-271">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="f76c7-272">W takich przypadkach można polegać na potoku mediatora (patrz [wzorzec mediatora),](https://en.wikipedia.org/wiki/Mediator_pattern)aby zapewnić środki dla tych dodatkowych zachowań lub problemów przekrojowych.</span><span class="sxs-lookup"><span data-stu-id="f76c7-272">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="f76c7-273">Mediator jest obiektem, który hermetyzuje "jak" tego procesu: koordynuje wykonywanie na podstawie stanu, sposób obsługi poleceń jest wywoływany lub ładunku, który podajesz do obsługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-273">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="f76c7-274">Za pomocą składnika mediatora można stosować problemy przekrojowe w sposób scentralizowany i przejrzysty, stosując dekoratory (lub [zachowania potoku](https://github.com/jbogard/MediatR/wiki/Behaviors) od [MediatR 3).](https://www.nuget.org/packages/MediatR/3.0.0)</span><span class="sxs-lookup"><span data-stu-id="f76c7-274">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="f76c7-275">Aby uzyskać więcej informacji, zobacz [wzorzec dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="f76c7-275">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="f76c7-276">Dekoratory i zachowania są podobne do [programowania zorientowanego na aspekty (AOP),](https://en.wikipedia.org/wiki/Aspect-oriented_programming)stosowane tylko do określonego potoku procesu zarządzanego przez składnik mediatora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-276">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="f76c7-277">Aspekty w aop, które implementują przekrojowe problemy są stosowane na podstawie *aspektu tkaczy* wstrzykiwanych w czasie kompilacji lub na podstawie przechwytywania wywołania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-277">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="f76c7-278">Oba typowe podejścia AOP są czasami mówi się, że działa "jak magia", ponieważ nie jest łatwo zobaczyć, jak AOP wykonuje swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="f76c7-278">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="f76c7-279">Podczas radzenia sobie z poważnymi problemami lub błędami, AOP może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="f76c7-279">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="f76c7-280">Z drugiej strony te dekoratory/zachowania są jawne i stosowane tylko w kontekście mediatora, więc debugowanie jest znacznie bardziej przewidywalne i łatwe.</span><span class="sxs-lookup"><span data-stu-id="f76c7-280">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="f76c7-281">Na przykład w eShopOnContainers zamawiania mikrousługi, zaimplementowaliśmy dwa przykładowe zachowania, [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy i [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy.</span><span class="sxs-lookup"><span data-stu-id="f76c7-281">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="f76c7-282">Implementacja zachowań jest wyjaśnione w następnej sekcji, pokazując, jak eShopOnContainers używa [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors).</span><span class="sxs-lookup"><span data-stu-id="f76c7-282">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="f76c7-283">Używanie kolejek komunikatów (poza proc) w potoku polecenia</span><span class="sxs-lookup"><span data-stu-id="f76c7-283">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="f76c7-284">Innym wyborem jest użycie komunikatów asynchronicznych opartych na brokerach lub kolejkach komunikatów, jak pokazano na rysunku 7-26.</span><span class="sxs-lookup"><span data-stu-id="f76c7-284">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="f76c7-285">Ta opcja może być również połączona ze składnikiem mediatora tuż przed programem obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-285">That option could also be combined with the mediator component right before the command handler.</span></span>

![Diagram przedstawiający przepływ danych przy użyciu kolejki komunikatów ha.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

<span data-ttu-id="f76c7-287">**Rysunek 7-26**.</span><span class="sxs-lookup"><span data-stu-id="f76c7-287">**Figure 7-26**.</span></span> <span data-ttu-id="f76c7-288">Korzystanie z kolejek komunikatów (poza procesem i komunikacji międzyprocesowej) z poleceniami CQRS</span><span class="sxs-lookup"><span data-stu-id="f76c7-288">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="f76c7-289">Potok polecenia może być również obsługiwany przez kolejkę komunikatów o wysokiej dostępności, aby dostarczyć polecenia do odpowiedniego programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-289">Command's pipeline can also be handled by a high availability message queue to deliver the commands to the appropriate handler.</span></span> <span data-ttu-id="f76c7-290">Za pomocą kolejek komunikatów do akceptowania poleceń może dodatkowo skomplikować potoku polecenia, ponieważ prawdopodobnie trzeba będzie podzielić potoku na dwa procesy połączone za pośrednictwem kolejki komunikatów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f76c7-290">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="f76c7-291">Mimo to należy go używać, jeśli trzeba mieć lepszą skalowalność i wydajność na podstawie asynchronicznych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f76c7-291">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="f76c7-292">Należy wziąć pod uwagę, że w przypadku rysunku 7-26 kontroler po prostu księguje komunikat polecenia w kolejce i zwraca.</span><span class="sxs-lookup"><span data-stu-id="f76c7-292">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="f76c7-293">Następnie programy obsługi poleceń przetwarzają wiadomości we własnym tempie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-293">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="f76c7-294">Jest to bardzo korzystne dla kolejek: kolejka komunikatów może działać jako bufor w przypadkach, gdy potrzebna jest hiperskalowalność, na przykład dla zapasów lub innego scenariusza z dużą ilością danych przychodzących.</span><span class="sxs-lookup"><span data-stu-id="f76c7-294">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="f76c7-295">Jednak ze względu na asynchroniczny charakter kolejek komunikatów, należy dowiedzieć się, jak komunikować się z aplikacją kliencką o powodzeniu lub niepowodzeniu procesu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-295">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="f76c7-296">Z reguły nigdy nie należy używać poleceń "ogień i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="f76c7-296">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="f76c7-297">Każda aplikacja biznesowa musi wiedzieć, czy polecenie zostało przetworzone pomyślnie, a przynajmniej zatwierdzone i zaakceptowane.</span><span class="sxs-lookup"><span data-stu-id="f76c7-297">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="f76c7-298">W związku z tym jest w stanie odpowiedzieć na klienta po poważaniu komunikatu polecenia, który został przesłany do kolejki asynchronicznej zwiększa złożoność systemu, w porównaniu do procesu polecenia w procesie, który zwraca wynik operacji po uruchomieniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-298">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="f76c7-299">Przy użyciu kolejek może być konieczne zwrócenie wyniku procesu polecenia za pomocą innych komunikatów wyników operacji, które będą wymagały dodatkowych składników i komunikacji niestandardowej w systemie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-299">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="f76c7-300">Dodatkowo, async polecenia są jednokierunkowe polecenia, które w wielu przypadkach mogą nie być potrzebne, jak wyjaśniono w następujących ciekawych wymiany między Burtsev Alexey i Greg Young w [rozmowie online:](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)</span><span class="sxs-lookup"><span data-stu-id="f76c7-300">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="f76c7-301">\[Burtsev Alexey\] znajduję wiele kodu, w którym ludzie używają obsługi poleceń asynchronicznej lub jednokierunkowych komunikatów poleceń bez żadnego powodu ( nie wykonują długiej operacji, nie wykonują zewnętrznego kodu asynchronicznego, nawet nie przekraczają granicy aplikacji, aby używać magistrali komunikatów).</span><span class="sxs-lookup"><span data-stu-id="f76c7-301">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="f76c7-302">Dlaczego wprowadzają tę niepotrzebną złożoność?</span><span class="sxs-lookup"><span data-stu-id="f76c7-302">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="f76c7-303">I rzeczywiście, nie widziałem przykład kodu CQRS z blokowania obsługi poleceń do tej pory, choć będzie działać dobrze w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="f76c7-303">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="f76c7-304">\[Greg\] \[Young ... \] asynchroniczne polecenie nie istnieje; to kolejne wydarzenie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-304">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="f76c7-305">Jeśli muszę zaakceptować to, co mi wysłać i podnieść zdarzenie, jeśli się nie \[zgadzam, to już nie\]mówisz mi zrobić coś, co jest, to nie jest polecenie .</span><span class="sxs-lookup"><span data-stu-id="f76c7-305">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="f76c7-306">Mówisz mi, że coś zostało zrobione.</span><span class="sxs-lookup"><span data-stu-id="f76c7-306">It's you telling me something has been done.</span></span> <span data-ttu-id="f76c7-307">Na początku wydaje się to niewielką różnicą, ale ma wiele implikacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-307">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="f76c7-308">Polecenia asynchroniczne znacznie zwiększają złożoność systemu, ponieważ nie ma prostego sposobu wskazywania błędów.</span><span class="sxs-lookup"><span data-stu-id="f76c7-308">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="f76c7-309">W związku z tym asynchroniczne polecenia nie są zalecane inne niż wtedy, gdy wymagania skalowania są potrzebne lub w szczególnych przypadkach podczas komunikowania mikrousług wewnętrznych za pośrednictwem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f76c7-309">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="f76c7-310">W takich przypadkach należy zaprojektować oddzielny system raportowania i odzyskiwania dla awarii.</span><span class="sxs-lookup"><span data-stu-id="f76c7-310">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="f76c7-311">W początkowej wersji eShopOnContainers zdecydowaliśmy się użyć synchronicznego przetwarzania poleceń, rozpoczęte z żądań HTTP i napędzane przez wzorzec mediatora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-311">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="f76c7-312">To łatwo pozwala na zwrócenie sukcesu lub niepowodzenia procesu, jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.</span><span class="sxs-lookup"><span data-stu-id="f76c7-312">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="f76c7-313">W każdym przypadku powinna to być decyzja oparta na wymaganiach biznesowych aplikacji lub mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-313">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="f76c7-314">Implementowanie potoku procesu poleceń za pomocą wzorca mediatora (MediatR)</span><span class="sxs-lookup"><span data-stu-id="f76c7-314">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="f76c7-315">Jako przykładową implementację, ten przewodnik proponuje przy użyciu potoku w procesie na podstawie wzorca mediatora do kierowania poleceń polecenia i polecenia trasy, w pamięci, do obsługi poleceń po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-315">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="f76c7-316">W przewodniku zaproponowano również stosowanie [zachowań](https://github.com/jbogard/MediatR/wiki/Behaviors) w celu oddzielenia problemów przekrojowych.</span><span class="sxs-lookup"><span data-stu-id="f76c7-316">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="f76c7-317">Do implementacji w .NET Core dostępnych jest wiele bibliotek open source, które implementują wzorzec mediatora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-317">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="f76c7-318">Biblioteka używana w tym przewodniku jest biblioteką open source [MediatR](https://github.com/jbogard/MediatR) (utworzoną przez Jimmy'ego Bogarda), ale można użyć innego podejścia.</span><span class="sxs-lookup"><span data-stu-id="f76c7-318">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="f76c7-319">MediatR to mała i prosta biblioteka, która umożliwia przetwarzanie wiadomości w pamięci, takich jak polecenie, podczas stosowania dekoratorów lub zachowań.</span><span class="sxs-lookup"><span data-stu-id="f76c7-319">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="f76c7-320">Za pomocą wzorca mediatora pomaga zmniejszyć sprzężenia i izolować obawy żądanej pracy, podczas automatycznego łączenia się z obsługi, która wykonuje tę pracę — w tym przypadku do obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-320">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="f76c7-321">Innym dobrym powodem, aby korzystać z wzoru Mediator został wyjaśniony przez Jimmy Bogard podczas przeglądu tego przewodnika:</span><span class="sxs-lookup"><span data-stu-id="f76c7-321">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="f76c7-322">Myślę, że warto wspomnieć o testach tutaj - zapewnia ładne spójne okno na zachowanie systemu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-322">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="f76c7-323">Żądanie w, odpowiedź-out. Odkryliśmy, że ten aspekt jest dość cenny w budowaniu konsekwentnie zachowujących się testów.</span><span class="sxs-lookup"><span data-stu-id="f76c7-323">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="f76c7-324">Najpierw przyjrzyjmy się przykładowemu kontrolerowi WebAPI, w którym faktycznie użyjesz obiektu mediatora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-324">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="f76c7-325">Jeśli nie używasz obiektu mediatora, należy wstrzyknąć wszystkie zależności dla tego kontrolera, takie rzeczy jak obiekt rejestratora i inne.</span><span class="sxs-lookup"><span data-stu-id="f76c7-325">If you weren't using the mediator object, you'd need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="f76c7-326">W związku z tym konstruktor będzie dość skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="f76c7-326">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="f76c7-327">Z drugiej strony, jeśli używasz obiektu mediatora, konstruktor kontrolera może być o wiele prostsze, z zaledwie kilku zależności zamiast wielu zależności, jeśli miał jeden na operację przekrojową, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f76c7-327">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

<span data-ttu-id="f76c7-328">Widać, że mediator zapewnia czysty i chudego konstruktora kontrolera interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f76c7-328">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="f76c7-329">Ponadto w ramach metod kontrolera kod wysyłania polecenia do obiektu mediatora jest prawie jeden wiersz:</span><span class="sxs-lookup"><span data-stu-id="f76c7-329">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="f76c7-330">Implementowanie poleceń idempotentności</span><span class="sxs-lookup"><span data-stu-id="f76c7-330">Implement idempotent Commands</span></span>

<span data-ttu-id="f76c7-331">W **eShopOnContainers**, bardziej zaawansowany przykład niż powyżej jest przesyłanie CreateOrderCommand obiektu z mikrousługi zamawiania.</span><span class="sxs-lookup"><span data-stu-id="f76c7-331">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="f76c7-332">Ale ponieważ proces biznesowy zamawiania jest nieco bardziej skomplikowane i, w naszym przypadku, faktycznie rozpoczyna się w mikrousługi koszyka, ta akcja przesyłania CreateOrderCommand obiekt jest wykonywany z integration-event handler o nazwie [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) zamiast prostego kontrolera WebAPI wywoływane z aplikacji klienta, jak w poprzednim przykładzie prostsze.</span><span class="sxs-lookup"><span data-stu-id="f76c7-332">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="f76c7-333">Niemniej jednak akcja przesyłania polecenia do MediatR jest bardzo podobna, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-333">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="f76c7-334">Jednak ten przypadek jest również nieco bardziej zaawansowany, ponieważ implementujemy również polecenia idempotentności.</span><span class="sxs-lookup"><span data-stu-id="f76c7-334">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="f76c7-335">Proces CreateOrderCommand powinien być idempotentny, więc jeśli ten sam komunikat zostanie zduplikowany za pośrednictwem sieci, z jakiegokolwiek powodu, takiego jak ponownych prób, to samo zlecenie biznesowe zostanie przetworzone tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f76c7-335">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="f76c7-336">Jest to realizowane przez zawijanie polecenia biznesowego (w tym przypadku CreateOrderCommand) i osadzanie go w ogólnym IdentifiedCommand, który jest śledzony przez identyfikator każdej wiadomości przychodzącej przez sieć, która musi być idempotentna.</span><span class="sxs-lookup"><span data-stu-id="f76c7-336">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="f76c7-337">W poniższym kodzie widać, że IdentifiedCommand jest niczym więcej niż DTO z i identyfikatorplus opakowany obiekt polecenia biznesowego.</span><span class="sxs-lookup"><span data-stu-id="f76c7-337">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="f76c7-338">Następnie CommandHandler dla IdentifiedCommand o nazwie [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) będzie w zasadzie sprawdzić, czy identyfikator najbliższych jako część wiadomości już istnieje w tabeli.</span><span class="sxs-lookup"><span data-stu-id="f76c7-338">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="f76c7-339">Jeśli już istnieje, to polecenie nie zostanie ponownie przetworzone, więc zachowuje się jako polecenie idempotentności.</span><span class="sxs-lookup"><span data-stu-id="f76c7-339">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="f76c7-340">Ten kod infrastruktury jest `_requestManager.ExistAsync` wykonywany przez wywołanie metody poniżej.</span><span class="sxs-lookup"><span data-stu-id="f76c7-340">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="f76c7-341">Ponieważ IdentifiedCommand działa jak koperta polecenia biznesowego, gdy polecenie biznesowe musi zostać przetworzone, ponieważ nie jest to identyfikator wielokrotny, to przyjmuje to wewnętrzne polecenie biznesowe i `_mediator.Send(message.Command)`ponownie przesyła je do mediatora, jak w ostatniej części kodu pokazanego powyżej podczas uruchamiania , z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="f76c7-341">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="f76c7-342">W ten sposób będzie łączyć i uruchamiać program obsługi poleceń biznesowych, w tym przypadku [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) który jest uruchomiony transakcji względem bazy danych zamawiania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-342">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="f76c7-343">Rejestrowanie typów używanych przez MediatR</span><span class="sxs-lookup"><span data-stu-id="f76c7-343">Register the types used by MediatR</span></span>

<span data-ttu-id="f76c7-344">Aby MediatR zdawać sobie sprawę z klas obsługi poleceń, należy zarejestrować klas mediatora i klasy obsługi poleceń w kontenerze IoC.</span><span class="sxs-lookup"><span data-stu-id="f76c7-344">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="f76c7-345">Domyślnie MediatR używa Autofac jako kontenerii IoC, ale można również użyć wbudowanego kontenera ASP.NET Core IoC lub dowolnego innego kontenera obsługiwanego przez MediatR.</span><span class="sxs-lookup"><span data-stu-id="f76c7-345">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="f76c7-346">Poniższy kod pokazuje, jak zarejestrować typy i polecenia mediatora podczas korzystania z modułów Autofac.</span><span class="sxs-lookup"><span data-stu-id="f76c7-346">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="f76c7-347">To jest, gdy "magia dzieje się" z MediatR.</span><span class="sxs-lookup"><span data-stu-id="f76c7-347">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="f76c7-348">Ponieważ każdy program obsługi `IAsyncRequestHandler<T>` poleceń implementuje ogólny interfejs, podczas rejestrowania zestawów, `IAsyncRequestHandler` kod rejestruje `CommandHandlers` się `Commands`ze `CommandHandler` `RegisteredAssemblyTypes` wszystkimi typami oznaczonymi jako podczas ich, dzięki relacji podanej w klasie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f76c7-348">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="f76c7-349">Jest to kod, który koreluje polecenia z programami obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-349">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="f76c7-350">Program obsługi jest tylko prostą klasą, `RequestHandler<T>`ale dziedziczy z , gdzie T jest typem polecenia, a MediatR upewnia się, że jest wywoływany przy poprawnym ładunku (polecenie).</span><span class="sxs-lookup"><span data-stu-id="f76c7-350">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="f76c7-351">Stosowanie problemów przekrojowych podczas przetwarzania poleceń za pomocą zachowań w MediatR</span><span class="sxs-lookup"><span data-stu-id="f76c7-351">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="f76c7-352">Jest jeszcze jedna rzecz: możliwość zastosowania przekrojowych problemów do rurociągu mediatora.</span><span class="sxs-lookup"><span data-stu-id="f76c7-352">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="f76c7-353">Można również zobaczyć na końcu kodu modułu rejestracji Autofac, jak rejestruje typ zachowania, w szczególności niestandardowe loggingbehavior klasy i ValidatorBehavior klasy.</span><span class="sxs-lookup"><span data-stu-id="f76c7-353">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="f76c7-354">Ale można dodać inne zachowania niestandardowe, zbyt.</span><span class="sxs-lookup"><span data-stu-id="f76c7-354">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="f76c7-355">Że [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy można zaimplementować jako następujący kod, który rejestruje informacje o programie obsługi poleceń są wykonywane i czy zakończyło się pomyślnie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-355">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="f76c7-356">Wystarczy implementując tę klasę zachowania i rejestrując ją w potoku (w mediatormodule powyżej), wszystkie polecenia przetwarzane za pośrednictwem MediatR będą rejestrowania informacji o wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="f76c7-356">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="f76c7-357">EShopOnContainers zamawiania mikrousługi stosuje również drugie zachowanie dla podstawowych sprawdzania poprawności, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy, która opiera się na [fluentvalidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f76c7-357">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="f76c7-358">Zachowanie w tym miejscu jest zgłaszanie wyjątku, jeśli sprawdzanie poprawności nie powiedzie się, ale można również zwrócić obiekt wynik, zawierający wynik polecenia, jeśli się powiedzie lub komunikaty sprawdzania poprawności w przypadku, gdy nie.</span><span class="sxs-lookup"><span data-stu-id="f76c7-358">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="f76c7-359">Prawdopodobnie ułatwiłoby to użytkownikowi wyświetlanie wyników sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f76c7-359">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="f76c7-360">Następnie, na podstawie biblioteki [FluentValidation,](https://github.com/JeremySkinner/FluentValidation) utworzyliśmy sprawdzanie poprawności danych przekazanych za pomocą CreateOrderCommand, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f76c7-360">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="f76c7-361">Można utworzyć dodatkowe sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f76c7-361">You could create additional validations.</span></span> <span data-ttu-id="f76c7-362">Jest to bardzo czysty i elegancki sposób implementacji sprawdzania poprawności poleceń.</span><span class="sxs-lookup"><span data-stu-id="f76c7-362">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="f76c7-363">W podobny sposób można zaimplementować inne zachowania dla dodatkowych aspektów lub problemów przekrojowych, które mają być stosowane do poleceń podczas ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="f76c7-363">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f76c7-364">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="f76c7-364">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="f76c7-365">Wzór mediatora</span><span class="sxs-lookup"><span data-stu-id="f76c7-365">The mediator pattern</span></span>

- <span data-ttu-id="f76c7-366">**Wzór mediatora** </span><span class="sxs-lookup"><span data-stu-id="f76c7-366">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="f76c7-367">Wzór dekoratora</span><span class="sxs-lookup"><span data-stu-id="f76c7-367">The decorator pattern</span></span>

- <span data-ttu-id="f76c7-368">**Wzór dekoratora** </span><span class="sxs-lookup"><span data-stu-id="f76c7-368">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="f76c7-369">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="f76c7-369">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="f76c7-370">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="f76c7-370">**MediatR.**</span></span> <span data-ttu-id="f76c7-371">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f76c7-371">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="f76c7-372">**CQRS z MediatR i AutoMapper** </span><span class="sxs-lookup"><span data-stu-id="f76c7-372">**CQRS with MediatR and AutoMapper** </span></span>\
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="f76c7-373">**Umieść kontrolery na diecie: POSTs i poleceń.**</span><span class="sxs-lookup"><span data-stu-id="f76c7-373">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="f76c7-374">**Rozwiązywanie problemów przekrojowych za pomocą rurociągu mediatora** </span><span class="sxs-lookup"><span data-stu-id="f76c7-374">**Tackling cross-cutting concerns with a mediator pipeline** </span></span>\
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="f76c7-375">**CQRS i REST: idealne dopasowanie** </span><span class="sxs-lookup"><span data-stu-id="f76c7-375">**CQRS and REST: the perfect match** </span></span>\
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="f76c7-376">**Przykłady potoku MediatR** </span><span class="sxs-lookup"><span data-stu-id="f76c7-376">**MediatR Pipeline Examples** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="f76c7-377">**Pionowe oprawy testowe plasterków dla MediatR i ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="f76c7-377">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="f76c7-378">**Rozszerzeń MediatR dla iniekcji zależności firmy Microsoft zwolniony** </span><span class="sxs-lookup"><span data-stu-id="f76c7-378">**MediatR Extensions for Microsoft Dependency Injection Released** </span></span>\
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="f76c7-379">Sprawna walidacja</span><span class="sxs-lookup"><span data-stu-id="f76c7-379">Fluent validation</span></span>

- <span data-ttu-id="f76c7-380">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="f76c7-380">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="f76c7-381">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f76c7-381">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="f76c7-382">[Poprzedni](microservice-application-layer-web-api-design.md)
> [następny](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="f76c7-382">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
