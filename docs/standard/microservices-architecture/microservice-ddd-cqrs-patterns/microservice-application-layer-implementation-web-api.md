---
title: Implementowanie warstwy aplikacji mikrousług przy użyciu interfejsu API sieci Web
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, wstrzykiwanie zależności i wzorce mediatora oraz ich szczegóły implementacji w warstwie aplikacji interfejsu API sieci Web.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: d37660d3e2a7640383347071adfe969325ddd77b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152115"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="e5eb7-103">Implementowanie warstwy aplikacji mikrousług przy użyciu interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="e5eb7-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="e5eb7-104">Użyj iniekcji zależności iniekcję obiektów infrastruktury do usługi warstwy aplikacji</span><span class="sxs-lookup"><span data-stu-id="e5eb7-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="e5eb7-105">Jak wspomniano wcześniej, można zaimplementować jako część artefaktu (assembly), którą tworzysz, takich jak w ramach projektu interfejsu API sieci Web lub projektu aplikacji sieci web MVC warstwy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="e5eb7-106">W przypadku mikrousług, utworzonych za pomocą platformy ASP.NET Core warstwy aplikacji będzie zazwyczaj biblioteki interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="e5eb7-107">Jeśli chcesz oddzielić wkrótce się z platformą ASP.NET Core (swoją infrastrukturę oraz kontrolerach) od kodu warstwy aplikacji niestandardowych warstwie aplikacji można także umieścić w bibliotece osobnej klasy, ale jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="e5eb7-108">Na przykład kod warstwy aplikacji mikrousług szeregowania bezpośrednio jest wdrażany jako część **Ordering.API** projektu (projekt internetowego interfejsu API platformy ASP.NET Core), rysunek jak pokazano na 7-23.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

![Widok Eksploratora rozwiązań mikrousług Ordering.API, przedstawiający podfolderów w folderze aplikacji: Zachowania, poleceń, DomainEventHandlers, IntegrationEvents, modele, zapytań i operacji sprawdzania poprawności.](./media/image20.png)

<span data-ttu-id="e5eb7-110">**Rysunek 7-23**.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-110">**Figure 7-23**.</span></span> <span data-ttu-id="e5eb7-111">Warstwa aplikacji w projekcie Ordering.API ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="e5eb7-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="e5eb7-112">Platforma ASP.NET Core obejmuje prostą [wbudowanych kontenera IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowany przez interfejsu IServiceProvider), która obsługuje iniekcji Konstruktor domyślny i ASP.NET sprawia, że niektóre usługi są dostępne za pośrednictwem DI.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="e5eb7-113">Platforma ASP.NET Core używa termin *usługi* dla każdego z typów rejestrowania, które będą wstrzyknięte przez DI.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="e5eb7-114">Możesz skonfigurować usług w kontenerze wbudowane w metodzie ConfigureServices w klasie uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="e5eb7-115">Zależności są implementowane w usługach wymaga typu i Zarejestruj w kontenerze IoC.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-115">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="e5eb7-116">Zazwyczaj mają zależności, które implementują obiektów infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="e5eb7-117">Bardzo typowy zależności do dodania to repozytorium.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="e5eb7-118">Jednak można wstawić wszelkich innych zależności infrastruktury, które mogą mieć.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="e5eb7-119">Prostsze implementacji może bezpośrednio uruchomić obiektu wzorzec jednostki pracy (obiektu EF DbContext), ponieważ kontekstu DBContext jest również implementację obiektów trwałości infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="e5eb7-120">W poniższym przykładzie można zobaczyć, jak .NET Core wprowadza obiekty wymagane repozytorium za pomocą konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="e5eb7-121">Klasa jest program obsługi poleceń, co zostanie omówione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-121">The class is a command handler, which we will cover in the next section.</span></span>

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

<span data-ttu-id="e5eb7-122">Klasa używa wprowadzonego repozytoria do wykonywania transakcji i zachować zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="e5eb7-123">Nie ma znaczenia, czy ta klasa procedurę obsługi poleceń, metodą kontroler internetowego interfejsu API platformy ASP.NET Core, czy [usługi aplikacji DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="e5eb7-124">Ostatecznie to klient jest prostą klasę, która korzysta z repozytoriów, jednostki domeny i koordynacji innych aplikacji w sposób podobny do obsługi polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="e5eb7-125">Taki sam sposób dla wszystkich wymienionych klas, tak jak w przykładzie, za pomocą DI oparte na konstruktora działa iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="e5eb7-126">Rejestrowanie typów implementacji zależności i interfejsy lub abstrakcje</span><span class="sxs-lookup"><span data-stu-id="e5eb7-126">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="e5eb7-127">Przed użyciem obiektów wprowadzonym za pomocą konstruktorów, musisz wiedzieć, gdzie można zarejestrować interfejsów i klas, które tworzą obiekty, które są wstrzykiwane do swojej klasy aplikacji za pośrednictwem DI.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="e5eb7-128">(Takich jak DI na podstawie konstruktora, jak pokazano wcześniej.)</span><span class="sxs-lookup"><span data-stu-id="e5eb7-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="e5eb7-129">Użyj wbudowanych kontenera IoC dostarczone przez platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5eb7-129">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="e5eb7-130">Korzystając z wbudowanych kontenera IoC, dostarczonego przez platformy ASP.NET Core, zarejestruj się typy, które chcesz wstawić w metodzie ConfigureServices w pliku Startup.cs, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="e5eb7-131">Najczęstszym wzorcem po rejestrowanie typów w pojemniku IoC można zarejestrować dwa typy — interfejs i jej klasy pokrewne implementacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="e5eb7-132">W przypadku żądania obiektu z kontenera IoC przez dowolny Konstruktor, następnie zażądać obiektu określonego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="e5eb7-133">Na przykład w poprzednim przykładzie, ostatni wiersz stany, gdy dowolne z konstruktorów mają zależności IMyCustomRepository (interfejs lub abstrakcji), kontenera IoC doda wystąpienia wykonania MyCustomSQLServerRepository Klasa.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="e5eb7-134">Korzystanie z biblioteki Scrutor dla typów automatycznej rejestracji</span><span class="sxs-lookup"><span data-stu-id="e5eb7-134">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="e5eb7-135">Korzystając z DI platformie .NET Core, możesz chcieć można przeskanować zestawu i automatycznie zarejestrować jego typów zgodnie z Konwencją.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="e5eb7-136">Ta funkcja nie jest obecnie dostępna w programie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="e5eb7-137">Można jednak użyć [Scrutor](https://github.com/khellang/Scrutor) biblioteki, w tym.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="e5eb7-138">To podejście jest wygodne w przypadku wielu typów, które muszą być zarejestrowani w kontenerze IoC.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e5eb7-139">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e5eb7-139">Additional resources</span></span>

- <span data-ttu-id="e5eb7-140">**Matthew King. Rejestrowanie usługi przy użyciu Scrutor** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-140">**Matthew King. Registering services with Scrutor** \\</span></span>
  [*https://www.mking.net/blog/registering-services-with-scrutor*](https://www.mking.net/blog/registering-services-with-scrutor)

- <span data-ttu-id="e5eb7-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="e5eb7-142">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-142">GitHub repo.</span></span> \
  [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="e5eb7-143">Użyj Autofac jako kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="e5eb7-143">Use Autofac as an IoC container</span></span>

<span data-ttu-id="e5eb7-144">Możesz również dodatkowe kontenery IoC i podłącz je do potoku platformy ASP.NET Core, tak jak szeregowania mikrousługi w ramach aplikacji eShopOnContainers, który używa [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="e5eb7-145">Korzystając z Autofac zwykle należy zarejestrować typy za pośrednictwem modułów, dzięki czemu można będzie podzielić typów rejestracji między wiele plików, w zależności od tego, gdzie są Twoje typy, tak samo, jak masz typy aplikacji rozproszonych w wielu bibliotek klas.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="e5eb7-146">Na przykład poniżej przedstawiono [modułu aplikacji Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) dla [interfejsu API sieci Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projektu z typami, należy wstawić.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

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

<span data-ttu-id="e5eb7-147">Autofac ma również funkcję [skanowanie zestawów i zarejestrować typy według Konwencji nazwy](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-147">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="e5eb7-148">Proces rejestracji i pojęcia są bardzo podobne do sposób typów można zarejestrować za pomocą wbudowanych kontenera ASP.NET Core IoC, ale składni, korzystając z Autofac jest nieco inna.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="e5eb7-149">W przykładowym kodzie abstrakcji IOrderRepository jest zarejestrowany wraz z implementacji klasy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="e5eb7-150">Oznacza to, że zawsze wtedy, gdy Konstruktor jest zadeklarowanie zależności za pomocą abstrakcji IOrderRepository lub interfejsu, kontenera IoC doda wystąpienia klasy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="e5eb7-151">Typ zakresu wystąpienia określa, jak wystąpienie jest współużytkowana przez żądania dla tej samej usługi lub zależności.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="e5eb7-152">Po wysłaniu żądania dla zależności, kontenera IoC może zwracać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="e5eb7-153">Jedno wystąpienie na okres istnienia, zakres (określone w kontenerze platformy ASP.NET Core IoC jako *zakresie*).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="e5eb7-154">Nowe wystąpienie na zależności (określone w kontenerze platformy ASP.NET Core IoC jako *przejściowy*).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="e5eb7-155">Pojedyncze wystąpienie udostępnione dla wszystkich obiektów za pomocą kontenera IoC (określone w kontenerze platformy ASP.NET Core IoC jako *pojedyncze*).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e5eb7-156">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e5eb7-156">Additional resources</span></span>

- <span data-ttu-id="e5eb7-157">**Wprowadzenie do iniekcji zależności w programie ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-157">**Introduction to Dependency Injection in ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="e5eb7-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-158">**Autofac.**</span></span> <span data-ttu-id="e5eb7-159">Oficjalna dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-159">Official documentation.</span></span> \
  [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

- <span data-ttu-id="e5eb7-160">**Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC - Torre'a de la Cesarowi.**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="e5eb7-161">Implementowanie wzorców polecenia i program obsługi poleceń</span><span class="sxs-lookup"><span data-stu-id="e5eb7-161">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="e5eb7-162">W przykładzie DI za pośrednictwem konstruktora pokazano w poprzedniej sekcji kontenera IoC został wprowadza repozytoriów za pośrednictwem konstruktora w klasie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-162">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="e5eb7-163">Ale dokładnie których zostały one dodane?</span><span class="sxs-lookup"><span data-stu-id="e5eb7-163">But exactly where were they injected?</span></span> <span data-ttu-id="e5eb7-164">Proste internetowego interfejsu API (na przykład mikrousług katalogu w ramach aplikacji eShopOnContainers) należy wstrzyknąć je na poziomie kontrolerów MVC w Konstruktorze kontrolera, jako część potoku żądania programu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-164">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="e5eb7-165">Jednak w kod początkowy przedstawione w tej sekcji ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy usługi Ordering.API w ramach aplikacji eShopOnContainers), iniekcja zależności odbywa się za pośrednictwem konstruktora określonego polecenia Program obsługi.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-165">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="e5eb7-166">Daj nam wyjaśniono, jakie procedurę obsługi poleceń jest i dlaczego chcesz używać go.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-166">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="e5eb7-167">Wzorzec polecenia wewnętrznie jest powiązana z wzorcem CQRS, która została wprowadzona wcześniej w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-167">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="e5eb7-168">Podejście CQRS ma dwie strony.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-168">CQRS has two sides.</span></span> <span data-ttu-id="e5eb7-169">Pierwszy obszar jest zapytań przy użyciu uproszczone zapytań przy użyciu [programem Dapper](https://github.com/StackExchange/dapper-dot-net) ORM wczesnych wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-169">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="e5eb7-170">Drugi ma polecenia, które są punkt początkowy dla transakcji i kanału wejściowego z poza usługi.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-170">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="e5eb7-171">Jak pokazano w rysunek 7-24, wzorzec jest oparty na akceptowanie poleceń po stronie klienta przetwarzanie je zgodnie z regułami modelu domeny, a na koniec utrwalania stanów z transakcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-171">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Widok wysokiego poziomu stronie zapisu we wzorcu CQRS: Aplikacja interfejsu użytkownika wysyła polecenie za pomocą interfejsu API, który pobiera commandhandler — obiekt, który zależy od modelu domeny i infrastruktury w celu aktualizacji bazy danych.](./media/image21.png)

<span data-ttu-id="e5eb7-173">**Rysunek 7-24**.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-173">**Figure 7-24**.</span></span> <span data-ttu-id="e5eb7-174">Ogólny widok poleceń lub "transakcji po stronie" we wzorcu CQRS</span><span class="sxs-lookup"><span data-stu-id="e5eb7-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="e5eb7-175">Klasy poleceń</span><span class="sxs-lookup"><span data-stu-id="e5eb7-175">The command class</span></span>

<span data-ttu-id="e5eb7-176">Polecenie to żądanie systemu do wykonania akcji, który zmienia stan systemu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="e5eb7-177">Polecenia są konieczne i mają być przetwarzane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="e5eb7-178">Ponieważ polecenia są priorytetów, są zwykle nazywane ze zleceniem ochotę imperatywnego (na przykład "Utwórz" lub "Aktualizuj"), i mogą one obejmować odpowiedni typ agregacji, takich jak CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="e5eb7-179">W przeciwieństwie do zdarzenia polecenie nie jest faktów z przeszłości; jest tylko żądania, a więc można odmówić.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="e5eb7-180">Polecenia mogą pochodzić z interfejsu użytkownika, w wyniku użytkownik inicjuje żądanie lub menedżera procesów, gdy Menedżer procesu jest kierowanie agregacji do wykonania akcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="e5eb7-181">Ważną cechą polecenie jest, że powinien on tylko raz przetwarzany przez jednego odbiorcę.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="e5eb7-182">Jest to, ponieważ polecenie jest jedna akcja lub transakcji, które mają być wykonywane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="e5eb7-183">Na przykład polecenia do tworzenia tej samej kolejności nie powinny być przetwarzane więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="e5eb7-184">Jest to ważna różnica między poleceń i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="e5eb7-185">Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług może być zainteresowany zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="e5eb7-186">Ponadto jest ważne, że polecenie być przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentna.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="e5eb7-187">Polecenie jest idempotentna, jeśli go mogą być wykonywane wiele razy bez wprowadzania zmian w wyniku ze względu na rodzaj polecenie lub ze względu na sposób system obsługuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="e5eb7-188">Jest dobrą praktyką, aby poleceń i aktualizuje idempotentne, gdy największy sens w ramach reguł biznesowych domeny i invariants.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="e5eb7-189">Na przykład aby użyć w tym samym przykładzie, jeśli jakiegokolwiek powodu (logika ponowień, stosowanie metod hakerskich itp.) to samo polecenie CreateOrder osiągnie system wielokrotnie, można identyfikację i upewnij się, że nie należy tworzyć wiele zamówień.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="e5eb7-190">Aby to zrobić, należy dołączyć pewnego rodzaju tożsamości w operacjach i ustalić, czy polecenie lub aktualizacji został już przetworzony.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="e5eb7-191">Wysłać polecenie do jednego odbiornika; nie opublikowano polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="e5eb7-192">Publikowanie jest dla zdarzeń, które podają fakt — coś się stało i mogą być interesujące dla odbiorcy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-192">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="e5eb7-193">W przypadku zdarzeń wydawca ma nie obaw, o których odbiorcy pobrać zdarzenia lub ich działania go.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="e5eb7-194">Ale zdarzeń domeny lub Integracja z innego wątku już wprowadzone w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-194">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="e5eb7-195">Polecenie jest implementowane za pomocą klasy, która nie zawiera pola danych i kolekcji wszystkie informacje, które są potrzebne w celu wykonania tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="e5eb7-196">Polecenie jest specjalnym rodzajem elementu danych transferu obiektu (DTO), taki, który jest używane wyłącznie do żądania zmiany lub transakcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="e5eb7-197">Samo polecenie opiera się na dokładnie te informacje, które są potrzebne do przetwarzania polecenia i nic więcej.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="e5eb7-198">Poniższy przykład przedstawia klasę CreateOrderCommand uproszczone.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="e5eb7-199">Jest to niezmienne polecenia, który jest używany podczas szeregowania mikrousługi w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

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
// https://msdn.microsoft.com/library/bb383979.aspx
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

<span data-ttu-id="e5eb7-200">Po prostu klasy poleceń zawiera wszystkie dane, których potrzebują do przeprowadzania transakcji biznesowych za pomocą obiektów modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="e5eb7-201">W efekcie polecenia są po prostu struktur danych, które zawierają dane tylko do odczytu i nie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="e5eb7-202">Nazwa polecenia wskazuje jej przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="e5eb7-203">W wielu językach, takich jak C\#, polecenia są reprezentowane jako klasy, ale nie mają wartość true, klasy, w tym sensie, rzeczywiste zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="e5eb7-204">Jako dodatkowe właściwości polecenia są niezmienne, ponieważ oczekiwane użycie jest, że są przetwarzane bezpośrednio przez model domeny.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="e5eb7-205">Nie ma potrzeby zmiany w okresie ich istnienia przewidywany.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="e5eb7-206">W języku C\# klasy, niezmienność można osiągnąć, nie ma żadnych metod ustawiających lub innych metod, które zmieniają stan wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="e5eb7-207">Należy pamiętać, że jeśli planowane lub oczekiwać poleceń będzie przechodzić przez proces serializacji deserializing właściwości muszą mieć prywatnej metody ustawiającej, należy sobie zdawać sprawę i `[DataMemeber]` (lub `[JsonProperty]`) atrybutów, w przeciwnym razie Deserializator nie będzie można odtworzenie obiektu w lokalizacji docelowej z wymaganymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-207">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMemeber]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="e5eb7-208">Na przykład klasy poleceń do tworzenia zamówienie przypomina prawdopodobnie pod względem danych kolejności, w której ma zostać utworzona, ale prawdopodobnie nie potrzebujesz tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-208">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="e5eb7-209">Na przykład CreateOrderCommand ma identyfikator zamówienia, ponieważ kolejność nie został jeszcze utworzony.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-209">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="e5eb7-210">Wiele klas polecenia mogą być proste, wymagania dotyczące pewnego stanu, który musi zostać zmienione tylko kilka pól.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-210">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="e5eb7-211">Byłoby w przypadku tylko w przypadku zmiany stanu zamówienia z "w toku" do "płatnych" lub "dostarczane" przy użyciu polecenia podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-211">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="e5eb7-212">Niektórzy deweloperzy wprowadzić w nich obiekty interfejsu użytkownika żądania niezależnie od ich dto polecenia, ale jest to kwestia preferencji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-212">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="e5eb7-213">Jest niewygodna separacji nie dużo wartością dodaną i obiekty są prawie dokładnie tak sam kształt.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-213">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="e5eb7-214">Na przykład w ramach aplikacji eShopOnContainers, niektóre polecenia pochodzą bezpośrednio po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-214">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="e5eb7-215">Klasy obsługi poleceń</span><span class="sxs-lookup"><span data-stu-id="e5eb7-215">The Command Handler class</span></span>

<span data-ttu-id="e5eb7-216">Należy zaimplementować klasę programu obsługi określone polecenie dla każdego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-216">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="e5eb7-217">To, jak wzorzec działa i jest to, gdzie będzie używać obiekt polecenia, obiektów domeny i obiektów repozytorium infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-217">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="e5eb7-218">Program obsługi poleceń w rzeczywistości to serce warstwy aplikacji w kontekście CQRS i DDD.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-218">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="e5eb7-219">Jednak logika domeny powinny być zawarte w obrębie klasy domeny — w ramach korzenie agregacji (głównych jednostek), jednostki podrzędne lub [usługi domenowe](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale nie w ramach programu obsługi poleceń jest klasa z aplikacji warstwy.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-219">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="e5eb7-220">Klasa procedury obsługi polecenia oferuje silnej kamień przechodzenia krok po kroku w taki sposób, aby osiągnąć pojedynczego Resposibility zasady (SRP) wymienionych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-220">The command handler class offers a strong stepping stone in the way to achieve the Single Resposibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="e5eb7-221">Program obsługi poleceń otrzymuje polecenie i uzyskuje wynik agregacji, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-221">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="e5eb7-222">Wynik powinien być pomyślne wykonanie polecenia lub wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-222">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="e5eb7-223">W przypadku wyjątku stan systemu należy bez zmian.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-223">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="e5eb7-224">Program obsługi poleceń zwykle wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-224">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="e5eb7-225">Odbiera obiekt polecenia, takie jak obiekt DTO (z [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub inny obiekt infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-225">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="e5eb7-226">Weryfikuje on, że polecenie jest nieprawidłowy (Jeśli nie jest zweryfikowany przez mediatora).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-226">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="e5eb7-227">Metoda tworzy wystąpienie głównego agregacji, które jest elementem docelowym bieżącego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-227">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="e5eb7-228">Metoda wykonuje na wystąpieniu głównego agregacji, pobierania wymaganych danych z polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-228">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="e5eb7-229">Utrzymuje nowy stan agregacji do powiązanej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-229">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="e5eb7-230">Ta ostatnia operacja jest rzeczywistych transakcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-230">This last operation is the actual transaction.</span></span>

<span data-ttu-id="e5eb7-231">Zazwyczaj obsługi polecenia obsługuje jednej wartości zagregowanej wynika z jego głównego agregacji (jednostki głównej).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-231">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="e5eb7-232">Jeśli wiele agregacji powinny mieć wpływ na odbiór jednego polecenia, można użyć zdarzeń domeny do propagowanie Agreguje wiele stanów lub akcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-232">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="e5eb7-233">Istotną kwestią jest, że podczas przetwarzania polecenia logika domeny powinny być wewnątrz modelu domeny (agregacje), w pełni hermetyzowany i gotowe do testowania jednostki.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-233">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="e5eb7-234">Procedura obsługi polecenia działa tylko jako sposób uzyskać modelu domeny z bazy danych i ostatni krok, aby poinformować warstwy infrastruktury (repozytoriów), aby utrwalić zmiany po zmianie modelu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-234">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="e5eb7-235">Zaletą tego podejścia jest refaktoryzować logika domeny w modelu domeny izolowane pełni zhermetyzowany, rozbudowane, zachowań bez konieczności zmiany kodu w aplikacji lub warstwy infrastruktury, które działają na poziomie nadmiar (programy obsługi poleceń, w przypadku interfejsu API sieci Web repozytoria itp.).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-235">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="e5eb7-236">Podczas obsługi polecenia okazać się skomplikowane, za pomocą zbyt dużo logiki, które mogą być zapachu kodu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-236">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="e5eb7-237">Zapoznaj się z nimi, a jeśli okaże się logika domeny zrefaktoryzuj kod, aby przenieść to zachowanie domeny do metod obiektów domeny (agregacji główna i podrzędna jednostki).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-237">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="e5eb7-238">Jako przykład klasę programu obsługi poleceń poniższy kod przedstawia tej samej klasie CreateOrderCommandHandler, który był wyświetlany na początku w tym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-238">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="e5eb7-239">W tym przypadku chcemy podkreślić, metoda dojścia i operacji za pomocą obiektów modelu domeny/agregacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-239">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

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

<span data-ttu-id="e5eb7-240">Poniżej przedstawiono dodatkowe kroki, które należy wykonać procedurę obsługi poleceń:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-240">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="e5eb7-241">Działanie przy użyciu metody agregacji głównego i zachowanie, należy użyć polecenia danych.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-241">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="e5eb7-242">Wewnętrznie w obiektach domeny zgłosić zdarzenia domeny podczas transakcji jest wykonywane, ale która jest przezroczysta z punktu widzenia obsługi polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-242">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="e5eb7-243">Jeśli wynik operacji agregacji zakończy się pomyślnie, a po zakończeniu transakcji, należy zgłosić zdarzenia integracji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-243">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="e5eb7-244">(Te mogą również zostać wywołane przez klasy infrastruktury, takie jak repozytoriami.)</span><span class="sxs-lookup"><span data-stu-id="e5eb7-244">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e5eb7-245">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e5eb7-245">Additional resources</span></span>

- <span data-ttu-id="e5eb7-246">**Seemann znacznika. Na granicach aplikacje są nie zorientowane obiektowo** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \\</span></span>
  [<span data-ttu-id="e5eb7-247">*https://blog.ploeh.dk/2011/05/31/AttheBoundaries, Zorientowane na ApplicationsareNotObject /*</span><span class="sxs-lookup"><span data-stu-id="e5eb7-247">*https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*</span></span>](https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

- <span data-ttu-id="e5eb7-248">**Poleceń i zdarzeń** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-248">**Commands and events** \\</span></span>
  [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

- <span data-ttu-id="e5eb7-249">**Do czego służy program obsługi poleceń?**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-249">**What does a command handler do?**</span></span> \
  [*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

- <span data-ttu-id="e5eb7-250">**Jimmy Bogard. Wzorce poleceń domeny — programy obsługi** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-250">**Jimmy Bogard. Domain Command Patterns – Handlers** \\</span></span>
  [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

- <span data-ttu-id="e5eb7-251">**Jimmy Bogard. Wzorce poleceń domeny — sprawdzanie poprawności** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-251">**Jimmy Bogard. Domain Command Patterns – Validation** \\</span></span>
  [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="e5eb7-252">Potok przetwarzania polecenia: jak wyzwolić procedurę obsługi poleceń</span><span class="sxs-lookup"><span data-stu-id="e5eb7-252">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="e5eb7-253">Następne pytanie jest jak wywołać procedurę obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-253">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="e5eb7-254">Można ręcznie wywołać go z każdego powiązane kontrolera platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-254">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="e5eb7-255">Jednak podejście byłaby zbyt powiązane i nie jest idealnym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-255">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="e5eb7-256">Pozostałe dwie główne opcje, które są zalecane opcje, są:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-256">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="e5eb7-257">Za pomocą wzorca artefakt mediatora w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-257">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="e5eb7-258">Za pomocą kolejki wiadomości asynchronicznych, Between kontrolery i obsługi.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-258">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="e5eb7-259">Użyj wzorca mediatora (w pamięci) w potoku do polecenia</span><span class="sxs-lookup"><span data-stu-id="e5eb7-259">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="e5eb7-260">Jak pokazano w rysunek 7-25, w podejście CQRS za pomocą inteligentnego mediatora, podobne do magistrali danych w pamięci, czyli inteligentnego przekierować do obsługi odpowiednie polecenia, na podstawie typu polecenia lub obiekt DTO odbierane.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-260">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="e5eb7-261">Pojedynczy czarne strzałki powodują przechodzenie między składnikami reprezentują zależności między obiektami (w wielu przypadkach wprowadzony przez DI) przy użyciu ich powiązane interakcje.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-261">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Powiększanie z poprzedniej ilustracji: kontrolera platformy ASP.NET Core wysyła polecenie do potoku polecenie MediatR firmy, dzięki czemu staną się odpowiedni program obsługi.](./media/image22.png)

<span data-ttu-id="e5eb7-263">**Rysunek 7-25**.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-263">**Figure 7-25**.</span></span> <span data-ttu-id="e5eb7-264">Przy użyciu wzorca mediatora w procesie w mikrousłudze CQRS w jednym</span><span class="sxs-lookup"><span data-stu-id="e5eb7-264">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="e5eb7-265">Przyczyna, pasującą przy użyciu wzorca mediatora jest w aplikacjach dla przedsiębiorstw, przetwarzania żądań może skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-265">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="e5eb7-266">Chcesz mieć możliwość dodawania open numerem odciąż przekrojowe zagadnienia, takie jak rejestrowanie, sprawdzanie poprawności, inspekcji i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-266">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="e5eb7-267">W takich przypadkach możesz polegać na potok mediatora (zobacz [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern)) do zapewnienia oznacza, że te dodatkowe zachowania lub odciąż przekrojowe zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-267">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="e5eb7-268">Mediatora jest obiektem, który hermetyzuje "jak" tego procesu: koordynuje jej wykonanie w oparciu o stan, wywoływaną sposób obsługi polecenia lub ładunku zapewniają do programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-268">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="e5eb7-269">Za pomocą składnika mediatora można zastosować odciąż przekrojowe zagadnienia w sposób scentralizowany i przejrzystości, stosując dekoratory (lub [potoku zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) ponieważ [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-269">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="e5eb7-270">Aby uzyskać więcej informacji, zobacz [wzorzec Dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-270">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="e5eb7-271">Dekoratory i zachowania są podobne do [aspekt zorientowanej na programowania (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)tylko zastosowane do zarządzanych przez składnik mediatora potoku określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-271">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="e5eb7-272">AOP aspektów, które implementują odciąż przekrojowe zagadnienia są stosowane na podstawie *weavers aspekt* wprowadzonym w czasie kompilacji lub w oparciu o przejęciu wywołanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-272">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="e5eb7-273">Oba typowe podejścia AOP czasami mówi się, że działania ""Magia, ponieważ nie jest łatwo sprawdzić, jak AOP wykonuje swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-273">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="e5eb7-274">Podczas pracy z poważnymi problemami i zgłaszanie usterek, AOP może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-274">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="e5eb7-275">Z drugiej strony, te dekoratory/zachowania są jawne i stosowane tylko w kontekście mediatora, dlatego debugowanie jest znacznie bardziej przewidywalna i łatwe.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-275">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="e5eb7-276">Na przykład w ramach aplikacji eShopOnContainers porządkowanie mikrousług, wprowadziliśmy dwa przykładowe zachowania, [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy i [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-276">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="e5eb7-277">Implementacja zachowania zostało wyjaśnione w następnej sekcji, pokazując, jak korzysta z ramach aplikacji eShopOnContainers [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-277">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="e5eb7-278">Użyj komunikat kolejki (poza poza procesem) w potoku do polecenia</span><span class="sxs-lookup"><span data-stu-id="e5eb7-278">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="e5eb7-279">Inną możliwością polega na użyciu wiadomości asynchronicznych, na podstawie brokerów lub kolejki komunikatów, jak pokazano w rysunek 7-26.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-279">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="e5eb7-280">Tej opcji można również łączyć za pomocą składnika mediatora bezpośrednio poprzedzający program obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-280">That option could also be combined with the mediator component right before the command handler.</span></span>

![Potok polecenia również może być obsługiwany przez kolejki komunikatów o wysokiej dostępności umożliwia umieszczanie w odpowiedni program obsługi poleceń.](./media/image23.png)

<span data-ttu-id="e5eb7-282">**Rysunek 7-26**.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-282">**Figure 7-26**.</span></span> <span data-ttu-id="e5eb7-283">Za pomocą poleceń CQRS przy użyciu kolejek komunikatów (poza procesem i komunikacji między procesami)</span><span class="sxs-lookup"><span data-stu-id="e5eb7-283">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="e5eb7-284">Za pomocą komunikatu kolejki, aby zaakceptować dodatkowo polecenia skomplikować potoku dla polecenia, ponieważ prawdopodobnie konieczne będzie rozdzielenie potoku na dwa procesy połączone za pośrednictwem kolejki komunikatów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-284">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="e5eb7-285">Nadal należy używać, jeśli chcesz mieć zwiększona skalowalność i wydajność w oparciu asynchronicznej obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-285">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="e5eb7-286">Należy wziąć pod uwagę, że w przypadku rysunek 7-26 kontrolera po prostu publikuje komunikat polecenia w kolejce i zwraca.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-286">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="e5eb7-287">Następnie programy obsługi poleceń przetwarzania komunikatów w swoim własnym tempie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-287">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="e5eb7-288">Oznacza to ogromne korzyści kolejek: kolejki komunikatów może pełnić rolę bufora w przypadkach, gdy skalowalność funkcji hyper jest wymagane, tak samo jak w przypadku zasobów lub innego scenariusza, z dużej ilości danych przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-288">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="e5eb7-289">Jednak ze względu na charakter asynchronicznego kolejek komunikatów, musisz opracować sposób komunikowania się z aplikacją klienta o powodzeniu lub niepowodzeniu polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-289">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="e5eb7-290">Zgodnie z zasadą nigdy nie należy użyć polecenia "fire and forget".</span><span class="sxs-lookup"><span data-stu-id="e5eb7-290">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="e5eb7-291">Aplikacja biznesowa, co musi wiedzieć, jeśli polecenie zostało przetworzone pomyślnie, lub były co najmniej zweryfikowane i zaakceptowane.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-291">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="e5eb7-292">Dlatego możliwość odpowiedzi do klienta po upewnieniu się, komunikat polecenia, który został przesłany do asynchronicznego kolejki zwiększa złożoność do systemu, w porównaniu do procesu poleceń w procesie, który zwraca wynik operacji po uruchomieniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-292">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="e5eb7-293">Korzystanie z kolejek, konieczne może być zwracanie wyniku procesu polecenia za pomocą innych wiadomości wynik operacji, które będzie wymagać dodatkowych składników i komunikacja z niestandardowych w systemie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-293">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="e5eb7-294">Ponadto polecenia asynchroniczne są jednokierunkowe poleceń, które w wielu przypadkach może być niepotrzebne, opisane w poniższej interesujące wymiany między Burtsev Alexey i Grega Younga w [rozmowę online](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="e5eb7-294">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="e5eb7-295">\[Burtsev Alexey\] znaleźć się części kodu, których użytkownicy korzystają z obsługi polecenia async lub jednym ze sposobów polecenia wiadomości bez jakiegokolwiek powodu, aby to zrobić (nie robią pewne długotrwałej operacji, nie są one wykonywane kod asynchroniczny zewnętrznych, ich nie nawet przechodzą aplikacji granica korzystać z magistrali komunikatów).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-295">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="e5eb7-296">Dlaczego wprowadzają tę złożoność niepotrzebne?</span><span class="sxs-lookup"><span data-stu-id="e5eb7-296">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="e5eb7-297">I w rzeczywistości mogę nie jeszcze widoczne przykładowy kod CQRS z blokowaniem programy obsługi poleceń do tej pory, chociaż będzie działać prawidłowo w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-297">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="e5eb7-298">\[Grega Younga\] \[... \] polecenia asynchronicznego nie istnieje; jest faktycznie inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-298">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="e5eb7-299">Jeśli musisz zaakceptować, co możesz Wyślij do mnie i wywołać zdarzenie, jeśli nie zgadzam się, nie jest już możesz informuje mnie coś zrobić \[oznacza to, że nie jest poleceniem\].</span><span class="sxs-lookup"><span data-stu-id="e5eb7-299">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="e5eb7-300">Chodzi o Ciebie informuje mnie, które coś, co zostało zrobione.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-300">It's you telling me something has been done.</span></span> <span data-ttu-id="e5eb7-301">To niewielka różnica na początku, ale ma wpływ wiele.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-301">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="e5eb7-302">Asynchroniczne poleceń znaczne zwiększenie złożoności systemu, ponieważ nie ma prostego sposobu wskazują błędy.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-302">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="e5eb7-303">W związku z tym polecenia asynchronicznego nie są zalecane innych niż razie wymagania dotyczące skalowania lub w szczególnych przypadkach podczas komunikacji wewnętrznej mikrousług za pomocą komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-303">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="e5eb7-304">W takich przypadkach należy projektować oddzielnego systemu raportowania i odzyskiwania na wypadek awarii.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-304">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="e5eb7-305">W pierwszej wersji w ramach aplikacji eShopOnContainers zdecydowaliśmy się użyć polecenia synchronicznego przetwarzania, pracy z żądań HTTP i opartych na podstawie wzorca mediatora.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-305">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="e5eb7-306">Łatwo pozwala to zwracać powodzenie lub niepowodzenie procesu, podobnie jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-306">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="e5eb7-307">W każdym przypadku powinna to być decyzji na podstawie swojej aplikacji lub w mikrousługach wymagań biznesowych.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-307">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="e5eb7-308">Implementowanie potok przetwarzania polecenia z wzorcem mediatora (MediatR)</span><span class="sxs-lookup"><span data-stu-id="e5eb7-308">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="e5eb7-309">Jako przykład implementacji ten przewodnik przedstawia, przy użyciu potoku w trakcie oparta na wzorcu mediatora do wprowadzania polecenia dysku i polecenia route w pamięci do obsługi polecenie right.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-309">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="e5eb7-310">Przewodnik proponuje, stosując [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) w celu oddzielenia odciąż przekrojowe zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-310">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="e5eb7-311">Do wykonania w programie .NET Core są dostępne wiele bibliotek typu open source, które implementują wzorzec mediatora.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-311">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="e5eb7-312">Biblioteka używanych w tym przewodniku jest [MediatR](https://github.com/jbogard/MediatR) biblioteki typu open source (utworzonego przez Jimmy Bogard), ale można użyć innego podejścia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-312">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="e5eb7-313">MediatR jest niewielki i prosty biblioteki, która umożliwia przetwarzanie komunikatów w pamięci, takich jak polecenia, stosując dekoratory lub zachowania.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-313">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="e5eb7-314">Przy użyciu wzorca mediatora pomaga zmniejszyć sprzężenia i aby wyizolować problemy żądanej pracy, automatycznie łącząc program obsługi, który wykonuje pracę — w tym przypadku do obsługi polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-314">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="e5eb7-315">Kolejny powód dobre, aby użyć wzorca mediatora zostało wyjaśnione przy użyciu Jimmy Bogard podczas przeglądania tego przewodnika:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-315">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="e5eb7-316">Myślę, może być warte wymienienie testowania w tym miejscu — zapewnia dobre rozwiązanie zgodne okno w zachowanie systemu.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-316">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="e5eb7-317">Żądania w poziomie w odpowiedzi. Odkryliśmy, że aspekt bardzo przydatne w budynku spójnie zachowuje się testy.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-317">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="e5eb7-318">Najpierw Przyjrzyjmy się kontrolkę webapi przykładowe faktycznie użycia obiektu mediatora.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-318">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="e5eb7-319">Obiekt mediatora nie była używana, należy wstrzyknąć wszystkie zależności dla tego kontrolera, np. obiekt rejestratora i innym osobom.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-319">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="e5eb7-320">W związku z tym Konstruktor będzie dość skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-320">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="e5eb7-321">Z drugiej strony Jeśli używasz obiektu mediatora, Konstruktor kontrolera może być znacznie prostsze, za pomocą tylko kilku zależności zamiast wiele zależności, jeśli masz jeden na przekrojowe operacji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-321">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator, 
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="e5eb7-322">Aby zobaczyć, że mediatora zapewnia czyste i zwarte Konstruktor kontrolera interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-322">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="e5eb7-323">Ponadto w ramach metody kontrolera kod, aby wysłać polecenie do obiektu mediatora jest prawie jeden wiersz:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-323">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

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

### <a name="implement-idempotent-commands"></a><span data-ttu-id="e5eb7-324">Implementowanie polecenia idempotentne</span><span class="sxs-lookup"><span data-stu-id="e5eb7-324">Implement idempotent Commands</span></span>

<span data-ttu-id="e5eb7-325">W **ramach aplikacji eShopOnContainers**, stanowi przykład bardziej zaawansowane niż powyższe przesyła obiekt CreateOrderCommand z mikrousług porządkowanie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-325">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="e5eb7-326">Ale ponieważ proces biznesowy zamówienia jest nieco bardziej skomplikowane, a w naszym przypadku faktycznie zacznie w mikrousługach koszyka, ta akcja przesyłania obiektu CreateOrderCommand jest przeprowadzane z poziomu programu obsługi zdarzeń integracji o nazwie > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) zamiast kontrolkę webapi proste wywoływane z klienta aplikacji, tak jak w poprzednim przykładzie prostsze.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-326">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="e5eb7-327">Niemniej jednak akcji przesyłania polecenie, aby MediatR jest bardzo podobne, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-327">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

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

<span data-ttu-id="e5eb7-328">Jednak ten przypadek jest również nieco bardziej zaawansowane, ponieważ również wdrażamy polecenia idempotentne.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-328">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="e5eb7-329">Proces CreateOrderCommand powinny być idempotentne, więc jeśli ten sam komunikat pochodzi zduplikowane za pośrednictwem sieci, w związku z jakiegokolwiek powodu, takie jak ponownych prób, takiej samej kolejności firm będzie przetwarzany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-329">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="e5eb7-330">To jest implementowany przez opakowanie polecenia firmy (w tym przypadku CreateOrderCommand) i osadzenie jej w IdentifiedCommand ogólnych, które są śledzone przez identyfikator każdej wiadomości przesyłanych w sieci, która ma być idempotentne.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-330">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="e5eb7-331">W poniższym kodzie widać, IdentifiedCommand to nic więcej niż obiekt DTO z i identyfikator oraz obiektu polecenia opakowana biznesowego.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-331">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

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

<span data-ttu-id="e5eb7-332">Następnie commandhandler — obiekt dla IdentifiedCommand o nazwie [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) zasadniczo sprawdzi, czy identyfikator dostępne jako część komunikatu już istnieje w tabeli.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-332">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="e5eb7-333">Jeśli już istnieje, że polecenie nie będzie on przetworzony ponownie, więc działa jako polecenia idempotentne.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-333">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="e5eb7-334">Czy infrastruktury kodu odbywa się przez `_requestManager.ExistAsync` poniżej wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-334">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

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

            // Send the embeded business command to mediator 
            // so it runs its related CommandHandler 
            var result = await _mediator.Send(message.Command);
                
            return result;
        }
    }
}
```

<span data-ttu-id="e5eb7-335">Ponieważ IdentifiedCommand zachowuje się jak koperty polecenie biznesowych, gdy polecenie firmy musi zostać przetworzona, ponieważ nie jest powtarzane identyfikator, następnie go zajmuje to polecenie wewnętrzne firmy i ponownie przesyła do mediatora, tak jak w ostatniej części kodu, gdy powyżej uruchamianie `_mediator.Send(message.Command)`, z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-335">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="e5eb7-336">Podczas tych czynności spowoduje link i uruchom program obsługi poleceń firm, w tym przypadku, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) której działa transakcje w bazie danych porządkowanie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-336">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

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

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="e5eb7-337">Zarejestruj typy używane przez MediatR</span><span class="sxs-lookup"><span data-stu-id="e5eb7-337">Register the types used by MediatR</span></span>

<span data-ttu-id="e5eb7-338">MediatR znać swojej klasy programu obsługi poleceń, należy zarejestrować klasy mediatora i klasy programu obsługi poleceń w kontenerze IoC.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-338">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="e5eb7-339">Domyślnie MediatR używa Autofac jako kontenera IoC, ale można również użyć wbudowanych kontenerów platformy ASP.NET Core IoC lub innego kontenera obsługiwane przez MediatR.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-339">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="e5eb7-340">Poniższy kod pokazuje, jak zarejestrować poleceń i typy mediatora firmy, korzystając z modułów Autofac.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-340">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

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

<span data-ttu-id="e5eb7-341">Jest to miejsce "Magia" miejsce w przypadku stron MediatR.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-341">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="e5eb7-342">Ponieważ każdy program obsługi poleceń implementuje ogólnego `IAsyncRequestHandler<T>` interfejsu, podczas rejestrowania zestawów, ten kod rejestruje `RegisteredAssemblyTypes` oznaczenie wszystkich typów `IAsyncRequestHandler` podczas odnoszących się `CommandHandlers` z ich `Commands`, dziękuję do relacji, o których wspomniano w `CommandHandler` klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-342">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="e5eb7-343">To kod, który jest odwrotnie skorelowana poleceń z programy obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-343">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="e5eb7-344">Program obsługi jest prostą klasę, ale dziedziczy `RequestHandler<T>`, gdzie T jest typem polecenia i MediatR upewnia się, zostanie wywołana z ładunkiem poprawne (polecenie).</span><span class="sxs-lookup"><span data-stu-id="e5eb7-344">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="e5eb7-345">Zastosuj odciąż przekrojowe zagadnienia podczas przetwarzania polecenia za pomocą zachowań w MediatR</span><span class="sxs-lookup"><span data-stu-id="e5eb7-345">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="e5eb7-346">Ma jedną rzecz: możliwość zastosowania odciąż przekrojowe zagadnienia do potoku mediatora.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-346">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="e5eb7-347">Widać również na końcu kod modułu rejestracji Autofac jak rejestruje typ zachowania, w szczególności klasę niestandardową LoggingBehavior i klasa ValidatorBehavior.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-347">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="e5eb7-348">Ale można dodać inne niestandardowe zachowania zbyt.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-348">But you could add other custom behaviors, too.</span></span>

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

<span data-ttu-id="e5eb7-349">Czy [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy można zaimplementować jako następujący kod, który rejestruje informacje na temat obsługi polecenia wykonywane i tego, czy zakończyło się pomyślnie lub nie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-349">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

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

<span data-ttu-id="e5eb7-350">Po prostu zaimplementowanie tej klasy zachowanie i rejestrując ją w potoku (w powyższym MediatorModule) wszystkie polecenia, które są przetwarzane przez MediatR będziesz rejestrować informacje dotyczące wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-350">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="e5eb7-351">Ramach aplikacji eShopOnContainers porządkowanie mikrousług ma zastosowanie również w drugim zachowanie dla podstawowe sprawdzanie poprawności, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy, która opiera się na [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, jak pokazano w Poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-351">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="e5eb7-352">Zachowanie w tym miejscu jest wywoływanie wyjątek, jeśli weryfikacja zakończy się niepowodzeniem, ale mogą także zwracać obiekt wyniku, zawierający wynik polecenia w przypadku powodzenia lub Sprawdzanie poprawności wiadomości w przypadku, gdy nie.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-352">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="e5eb7-353">To będzie prawdopodobnie ułatwiają wyświetlić wyniki sprawdzania poprawności dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-353">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="e5eb7-354">Następnie, na podstawie [FluentValidation](https://github.com/JeremySkinner/FluentValidation) , możemy utworzyć bibliotekę sprawdzania poprawności dla danych przekazanych z CreateOrderCommand, tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e5eb7-354">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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

<span data-ttu-id="e5eb7-355">Można utworzyć dodatkowe sprawdzanie poprawności.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-355">You could create additional validations.</span></span> <span data-ttu-id="e5eb7-356">Jest to bardzo prosty i przejrzysty sposób wdrożyć swoje polecenie walidacji.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-356">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="e5eb7-357">W podobny sposób można zaimplementować innych zachowań dodatkowe aspekty lub odciąż przekrojowe zagadnienia, które mają być stosowane do poleceń, gdy ich obsługę.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-357">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e5eb7-358">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e5eb7-358">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="e5eb7-359">Wzorzec mediatora</span><span class="sxs-lookup"><span data-stu-id="e5eb7-359">The mediator pattern</span></span>

- <span data-ttu-id="e5eb7-360">**Wzorzec mediatora** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-360">**Mediator pattern** \\</span></span>
  [*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="e5eb7-361">Wzorzec dekoratora</span><span class="sxs-lookup"><span data-stu-id="e5eb7-361">The decorator pattern</span></span>

- <span data-ttu-id="e5eb7-362">**Wzorzec dekoratora** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-362">**Decorator pattern** \\</span></span>
  [*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="e5eb7-363">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="e5eb7-363">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="e5eb7-364">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-364">**MediatR.**</span></span> <span data-ttu-id="e5eb7-365">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-365">GitHub repo.</span></span> \
  [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

- <span data-ttu-id="e5eb7-366">**Podejście CQRS z MediatR i AutoMapper** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-366">**CQRS with MediatR and AutoMapper** \\</span></span>
  [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

- <span data-ttu-id="e5eb7-367">**Umieść swoje kontrolery na diecie: Wpisy i poleceń.**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-367">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  [*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

- <span data-ttu-id="e5eb7-368">**Realizowanie odciąż przekrojowe zagadnienia z potokiem mediatora** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-368">**Tackling cross-cutting concerns with a mediator pipeline** \\</span></span>
  [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

- <span data-ttu-id="e5eb7-369">**Podejście CQRS i REST: doskonałe dopasowanie** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-369">**CQRS and REST: the perfect match** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

- <span data-ttu-id="e5eb7-370">**Przykłady MediatR potoku** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-370">**MediatR Pipeline Examples** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

- <span data-ttu-id="e5eb7-371">**Wycinek pionowy testu świetlnymi MediatR i platformy ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-371">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/*](https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/)

- <span data-ttu-id="e5eb7-372">**Rozszerzenia MediatR do wstrzykiwania zależności firmy Microsoft, wydania** \\</span><span class="sxs-lookup"><span data-stu-id="e5eb7-372">**MediatR Extensions for Microsoft Dependency Injection Released** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a><span data-ttu-id="e5eb7-373">Sprawdzanie poprawności Fluent</span><span class="sxs-lookup"><span data-stu-id="e5eb7-373">Fluent validation</span></span>

- <span data-ttu-id="e5eb7-374">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="e5eb7-374">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="e5eb7-375">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="e5eb7-375">GitHub repo.</span></span> \
  [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
><span data-ttu-id="e5eb7-376">[Poprzednie](microservice-application-layer-web-api-design.md)
>[dalej](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e5eb7-376">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
