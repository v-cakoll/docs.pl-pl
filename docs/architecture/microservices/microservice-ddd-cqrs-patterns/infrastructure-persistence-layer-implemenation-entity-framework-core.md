---
title: Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się szczegóły implementacji dla warstwy trwałości infrastruktury przy użyciu jednostki Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: 63579dc74ba52551bc1ee02a57337c1b17fdf396
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401628"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="49952-103">Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="49952-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="49952-104">W przypadku korzystania z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, zaleca się wdrożenie warstwy trwałości na podstawie entity framework (EF).</span><span class="sxs-lookup"><span data-stu-id="49952-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="49952-105">EF obsługuje LINQ i zapewnia silnie typowane obiekty dla modelu, a także uproszczone trwałości w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="49952-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="49952-106">Entity Framework ma długą historię jako część .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49952-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="49952-107">Korzystając z programu .NET Core, należy również użyć entity framework core, który działa w systemie Windows lub Linux w taki sam sposób jak .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49952-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="49952-108">EF Core jest kompletnym przepisaniem frameworku jednostek, zaimplementowanym o znacznie mniejszym rozmiarze i istotnych ulepszeniach w wydajności.</span><span class="sxs-lookup"><span data-stu-id="49952-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="49952-109">Wprowadzenie do rdzenia frameworkencji</span><span class="sxs-lookup"><span data-stu-id="49952-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="49952-110">Entity Framework (EF) Core jest lekką, rozszerzalne i międzyplatformowej wersji popularnej technologii dostępu do danych entity framework.</span><span class="sxs-lookup"><span data-stu-id="49952-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="49952-111">Został on wprowadzony z .NET Core w połowie 2016 roku.</span><span class="sxs-lookup"><span data-stu-id="49952-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="49952-112">Ponieważ wprowadzenie do EF Core jest już dostępne w dokumentacji firmy Microsoft, tutaj po prostu podajemy łącza do tych informacji.</span><span class="sxs-lookup"><span data-stu-id="49952-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="49952-113">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="49952-113">Additional resources</span></span>

- <span data-ttu-id="49952-114">**Rdzeń frameworku jednostki** </span><span class="sxs-lookup"><span data-stu-id="49952-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="49952-115">**Wprowadzenie do ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="49952-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="49952-116">**Klasa DbContext** </span><span class="sxs-lookup"><span data-stu-id="49952-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="49952-117">**Porównaj EF Core & EF6.x** </span><span class="sxs-lookup"><span data-stu-id="49952-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="49952-118">Infrastruktura w rdzeniu frameworkowym jednostek z perspektywy DDD</span><span class="sxs-lookup"><span data-stu-id="49952-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="49952-119">Z punktu widzenia DDD ważną zdolnością EF jest możliwość używania jednostek domeny POCO, znanych również w terminologii EF jako *jednostki poco code-first*.</span><span class="sxs-lookup"><span data-stu-id="49952-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="49952-120">Jeśli używasz jednostek domeny POCO, klasy modelu domeny są nieświadomi trwałości, po [nieznajomości trwałości](https://deviq.com/persistence-ignorance/) i zasady [ignorancji infrastruktury.](https://ayende.com/blog/3137/infrastructure-ignorance)</span><span class="sxs-lookup"><span data-stu-id="49952-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="49952-121">Zgodnie z wzorcami DDD należy hermetyzować zachowanie domeny i reguły w samej klasie jednostki, dzięki czemu można kontrolować niezmienne, sprawdzania poprawności i reguły podczas uzyskiwania dostępu do dowolnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49952-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="49952-122">W związku z tym nie jest dobrą praktyką w DDD, aby umożliwić publiczny dostęp do kolekcji jednostek podrzędnych lub obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="49952-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="49952-123">Zamiast tego chcesz udostępnić metody, które kontrolują, jak i kiedy pola i kolekcje właściwości mogą być aktualizowane i jakie zachowanie i akcje powinny wystąpić, gdy tak się stanie.</span><span class="sxs-lookup"><span data-stu-id="49952-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="49952-124">Ponieważ EF Core 1.1, aby spełnić te wymagania DDD, można mieć proste pola w jednostkach zamiast właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="49952-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="49952-125">Jeśli nie chcesz, aby pole encji było dostępne zewnętrznie, możesz po prostu utworzyć atrybut lub pole zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="49952-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="49952-126">Można również użyć wartości ustawiaczy własności prywatnej.</span><span class="sxs-lookup"><span data-stu-id="49952-126">You can also use private property setters.</span></span>

<span data-ttu-id="49952-127">W podobny sposób można teraz mieć dostęp tylko do odczytu do `IReadOnlyCollection<T>`kolekcji przy użyciu właściwości publicznej wpisane jako `List<T>`, który jest wspierany przez członka pola prywatnego dla kolekcji (jak ) w jednostce, która opiera się na EF dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="49952-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="49952-128">Poprzednie wersje entity framework wymagane właściwości `ICollection<T>`kolekcji do obsługi , co oznaczało, że każdy deweloper przy użyciu klasy jednostki nadrzędnej można dodać lub usunąć elementy za pośrednictwem swoich kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="49952-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="49952-129">Taka możliwość byłaby sprzeczna z zalecanymi wzorcami w DDD.</span><span class="sxs-lookup"><span data-stu-id="49952-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="49952-130">Kolekcji prywatnej można użyć podczas eksponowania obiektu tylko do `IReadOnlyCollection<T>` odczytu, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="49952-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="49952-131">Należy pamiętać, że `OrderItems` właściwość jest dostępna tylko `IReadOnlyCollection<OrderItem>`jako tylko do odczytu przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="49952-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="49952-132">Ten typ jest tylko do odczytu, więc jest chroniony przed regularnymi aktualizacjami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="49952-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="49952-133">EF Core umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczania" modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="49952-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="49952-134">Jest to czysty kod .NET POCO, ponieważ akcja mapowania jest implementowana w warstwie trwałości.</span><span class="sxs-lookup"><span data-stu-id="49952-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="49952-135">W tej akcji mapowania należy skonfigurować mapowanie pól do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="49952-136">W poniższym przykładzie `OnModelCreating` metody `OrderingContext` from `OrderEntityTypeConfiguration` i klasy `SetPropertyAccessMode` wywołanie mówi EF `OrderItems` Core, aby uzyskać dostęp do właściwości za pośrednictwem jego pola.</span><span class="sxs-lookup"><span data-stu-id="49952-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="49952-137">W przypadku używania pól zamiast `OrderItem` właściwości jednostka jest zachowywana tak, jakby miała `List<OrderItem>` właściwość.</span><span class="sxs-lookup"><span data-stu-id="49952-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="49952-138">Jednak udostępnia jeden akcesor, `AddOrderItem` metoda dodawania nowych elementów do zamówienia.</span><span class="sxs-lookup"><span data-stu-id="49952-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="49952-139">W rezultacie zachowanie i dane są powiązane ze sobą i będą spójne w całym kodzie aplikacji, który używa modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="49952-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="49952-140">Implementowanie niestandardowych repozytoriów za pomocą programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="49952-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="49952-141">Na poziomie implementacji repozytorium jest po prostu klasą z kodem trwałości danych koordynowanym przez jednostkę pracy (DBContext w EF Core) podczas wykonywania aktualizacji, jak pokazano w następującej klasie:</span><span class="sxs-lookup"><span data-stu-id="49952-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="49952-142">Należy zauważyć, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako kontrakt.</span><span class="sxs-lookup"><span data-stu-id="49952-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="49952-143">Jednak implementacja repozytorium odbywa się w warstwie trwałości i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="49952-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="49952-144">EF DbContext jest za pośrednictwem konstruktora za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="49952-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="49952-145">Jest współużytkowany przez wiele repozytoriów w tym samym zakresie`ServiceLifetime.Scoped`żądania HTTP, dzięki jego domyślnemu okresowi istnienia ( ) w kontenerze IoC (który można również jawnie ustawić). `services.AddDbContext<>`</span><span class="sxs-lookup"><span data-stu-id="49952-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="49952-146">Metody implementacji w repozytorium (aktualizacje lub transakcje a kwerendy)</span><span class="sxs-lookup"><span data-stu-id="49952-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="49952-147">W ramach każdej klasy repozytorium należy umieścić metody trwałości, które aktualizują stan jednostek zawartych w powiązanych agregacji.</span><span class="sxs-lookup"><span data-stu-id="49952-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="49952-148">Pamiętaj, że istnieje relacja jeden-do-jednego między agregacji i powiązanych repozytorium.</span><span class="sxs-lookup"><span data-stu-id="49952-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="49952-149">Należy wziąć pod uwagę, że obiekt jednostki głównej agregacji może mieć osadzone jednostki podrzędne w jego wykresie EF.</span><span class="sxs-lookup"><span data-stu-id="49952-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="49952-150">Na przykład kupujący może mieć wiele metod płatności jako powiązane jednostki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="49952-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="49952-151">Ponieważ podejście do mikrousługi zamawiania w eShopOnContainers jest również oparty na CQS/CQRS, większość zapytań nie są implementowane w repozytoriach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="49952-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="49952-152">Deweloperzy mają swobodę tworzenia zapytań i sprzężeń potrzebnych do warstwy prezentacji bez ograniczeń nałożonych przez agregaty, niestandardowe repozytoria na agregato i Ogólnie DDD.</span><span class="sxs-lookup"><span data-stu-id="49952-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="49952-153">Większość niestandardowych repozytoriów sugerowanych w tym przewodniku ma kilka metod aktualizacji lub transakcyjnych, ale tylko metody zapytania potrzebne do uzyskania danych do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="49952-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="49952-154">Na przykład repozytorium BuyerRepository implementuje Metodę FindAsync, ponieważ aplikacja musi wiedzieć, czy istnieje określony nabywca przed utworzeniem nowego nabywcy związanego z zamówieniem.</span><span class="sxs-lookup"><span data-stu-id="49952-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="49952-155">Jednak prawdziwe metody kwerendy, aby uzyskać dane do wysyłania do warstwy prezentacji lub aplikacji klienckich są implementowane, jak wspomniano, w kwerendach CQRS na podstawie elastycznych zapytań przy użyciu Dapper.</span><span class="sxs-lookup"><span data-stu-id="49952-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="49952-156">Korzystanie z niestandardowego repozytorium w porównaniu z użyciem EF DbContext bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="49952-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="49952-157">Klasa DbContext framework jednostki jest oparta na wzorcach Jednostki pracy i repozytorium i może być używana bezpośrednio z kodu, na przykład z ASP.NET kontrolera Core MVC.</span><span class="sxs-lookup"><span data-stu-id="49952-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="49952-158">W ten sposób można utworzyć najprostszy kod, jak w mikrousługi katalogu CRUD w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="49952-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="49952-159">W przypadkach, gdy chcesz najprostszy kod możliwe, można bezpośrednio użyć DbContext klasy, jak wielu deweloperów zrobić.</span><span class="sxs-lookup"><span data-stu-id="49952-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="49952-160">Jednak implementowanie niestandardowych repozytoriów zapewnia kilka korzyści podczas implementowania bardziej złożonych mikrousług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49952-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="49952-161">Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, dzięki czemu jest oddzielona od warstwy modelu aplikacji i domeny.</span><span class="sxs-lookup"><span data-stu-id="49952-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="49952-162">Implementowanie tych wzorców może ułatwić korzystanie z makiety repozytoriów symulujących dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="49952-163">Na rysunku 7-18 można zobaczyć różnice między nie przy użyciu repozytoriów (bezpośrednio przy użyciu EF DbContext) w porównaniu do korzystania z repozytoriów, które ułatwiają makiety tych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="49952-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![Diagram przedstawiający składniki i przepływ danych w dwóch repozytoriach.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="49952-165">**Rysunek 7-18**.</span><span class="sxs-lookup"><span data-stu-id="49952-165">**Figure 7-18**.</span></span> <span data-ttu-id="49952-166">Korzystanie z niestandardowych repozytoriów w porównaniu z zwykłym DbContext</span><span class="sxs-lookup"><span data-stu-id="49952-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="49952-167">Rysunek 7-18 pokazuje, że za pomocą niestandardowego repozytorium dodaje warstwę abstrakcji, która może służyć do ułatwienia testowania przez szyderstwo repozytorium.</span><span class="sxs-lookup"><span data-stu-id="49952-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="49952-168">Istnieje wiele alternatyw podczas szyderstwa.</span><span class="sxs-lookup"><span data-stu-id="49952-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="49952-169">Można drwić tylko repozytoria lub można drwić całą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="49952-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="49952-170">Zwykle wystarczy szyderczy tylko repozytoria, a złożoność do abstrakcyjnych i makiety całej jednostki pracy zwykle nie jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="49952-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="49952-171">Później, gdy skupimy się na warstwie aplikacji, zobaczysz, jak działa iniekcja zależności w ASP.NET Core i jak jest implementowana podczas korzystania z repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="49952-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="49952-172">Krótko mówiąc, niestandardowe repozytoria umożliwiają łatwiejsze testowanie kodu za pomocą testów jednostkowych, na które nie ma wpływu stan warstwy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="49952-173">Po uruchomieniu testów, które również dostęp do rzeczywistej bazy danych za pośrednictwem struktury jednostki, nie są to testy jednostkowe, ale testy integracji, które są znacznie wolniejsze.</span><span class="sxs-lookup"><span data-stu-id="49952-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="49952-174">Jeśli używasz DbContext bezpośrednio, trzeba by makiety go lub do uruchamiania testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalnych danych dla testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="49952-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="49952-175">Ale szyderczy DbContext lub kontrolowania fałszywych danych wymaga więcej pracy niż szyderczy na poziomie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="49952-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="49952-176">Oczywiście zawsze można przetestować kontrolery MVC.</span><span class="sxs-lookup"><span data-stu-id="49952-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="49952-177">EF DbContext i iUnitOfWork okres istnienia wystąpienia w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="49952-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="49952-178">Obiekt `DbContext` (uwidaczni jako obiekt) `IUnitOfWork` powinny być współużytkowane przez wiele repozytoriów w tym samym zakresie żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="49952-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="49952-179">Na przykład jest to prawda, gdy wykonywana operacja musi radzić sobie z wieloma agregatami lub po prostu dlatego, że używasz wielu wystąpień repozytorium.</span><span class="sxs-lookup"><span data-stu-id="49952-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="49952-180">Należy również wspomnieć, `IUnitOfWork` że interfejs jest częścią warstwy domeny, a nie typu EF Core.</span><span class="sxs-lookup"><span data-stu-id="49952-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="49952-181">Aby to zrobić, wystąpienie `DbContext` obiektu musi mieć jego okres istnienia usługi ustawiony na ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="49952-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="49952-182">Jest to domyślny okres istnienia podczas rejestrowania z `DbContext` w `services.AddDbContext` kontenerze `Startup.cs` IoC z ConfigureServices metody pliku w projekcie interfejsu API sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="49952-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="49952-183">Ilustruje to poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="49952-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="49952-184">Tryb wystąpienia DbContext nie powinien być skonfigurowany jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="49952-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="49952-185">Okres istnienia wystąpienia repozytorium w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="49952-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="49952-186">W podobny sposób okres istnienia repozytorium zwykle powinny być ustawione jako zakres (InstancePerLifetimeScope w Autofac).</span><span class="sxs-lookup"><span data-stu-id="49952-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="49952-187">Może to być również przejściowe (InstancePerDependency w Autofac), ale usługa będzie bardziej efektywne w odniesieniu do pamięci podczas korzystania z okresu istnienia o zakresie.</span><span class="sxs-lookup"><span data-stu-id="49952-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="49952-188">Należy zauważyć, że przy użyciu okresu istnienia singleton dla repozytorium może spowodować poważne problemy współbieżności, gdy DbContext jest ustawiony na zakres (InstancePerLifetimeScope) okres istnienia (domyślne okresy istnienia dla DBContext).</span><span class="sxs-lookup"><span data-stu-id="49952-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="49952-189">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="49952-189">Additional resources</span></span>

- <span data-ttu-id="49952-190">**Implementowanie repozytorium i jednostki wzorców pracy w ASP.NET aplikacji MVC** </span><span class="sxs-lookup"><span data-stu-id="49952-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="49952-191">**Jonathan Allen. Strategie wdrażania wzorca repozytorium z frameworkiem jednostek, dapperi i łańcuchem** </span><span class="sxs-lookup"><span data-stu-id="49952-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="49952-192">**Cesar de la Torre. Porównanie ASP.NET okresy istnienia kontenera Core IoC z zakresami wystąpienia kontenera Autofac IoC** </span><span class="sxs-lookup"><span data-stu-id="49952-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="49952-193">Mapowanie tabeli</span><span class="sxs-lookup"><span data-stu-id="49952-193">Table mapping</span></span>

<span data-ttu-id="49952-194">Mapowanie tabeli identyfikuje dane tabeli, z których mają być przeszukiwane i zapisywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="49952-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="49952-195">Wcześniej widziałeś, jak jednostki domeny (na przykład domeny produktu lub zamówienia) mogą być używane do generowania schematu powiązanej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="49952-196">EF jest silnie zaprojektowany wokół koncepcji *konwencji*.</span><span class="sxs-lookup"><span data-stu-id="49952-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="49952-197">Konwencje dotyczą pytań takich jak "Jaka będzie nazwa tabeli?"</span><span class="sxs-lookup"><span data-stu-id="49952-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="49952-198">lub "Jaka właściwość jest kluczem podstawowym?"</span><span class="sxs-lookup"><span data-stu-id="49952-198">or “What property is the primary key?”</span></span> <span data-ttu-id="49952-199">Konwencje są zazwyczaj oparte na konwencjonalnych nazw, na przykład jest typowe dla klucza podstawowego, aby być właściwością, która kończy się identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="49952-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="49952-200">Zgodnie z konwencją każda jednostka zostanie skonfigurowana do mapowania `DbSet<TEntity>` do tabeli o tej samej nazwie co właściwość, która udostępnia jednostkę w kontekście pochodnym.</span><span class="sxs-lookup"><span data-stu-id="49952-200">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="49952-201">Jeśli `DbSet<TEntity>` dla danej jednostki nie podano żadnej wartości, używana jest nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="49952-201">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="49952-202">Adnotacje danych a interfejs API fluent</span><span class="sxs-lookup"><span data-stu-id="49952-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="49952-203">Istnieje wiele dodatkowych konwencji EF Core, a większość z nich można zmienić przy użyciu adnotacji danych lub fluent Interfejsu API, zaimplementowane w onmodelcreating metody.</span><span class="sxs-lookup"><span data-stu-id="49952-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="49952-204">Adnotacje danych muszą być używane w samych klasach modelu jednostki, co jest bardziej inwazyjnym sposobem z punktu widzenia DDD.</span><span class="sxs-lookup"><span data-stu-id="49952-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="49952-205">Dzieje się tak, ponieważ zanieczyszczasz model adnotacjami danych związanymi z bazą danych infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="49952-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="49952-206">Z drugiej strony fluent interfejsu API jest wygodny sposób, aby zmienić większość konwencji i mapowania w warstwie infrastruktury trwałości danych, więc model jednostki będzie czysty i oddzielone od infrastruktury trwałości.</span><span class="sxs-lookup"><span data-stu-id="49952-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="49952-207">Fluent API i OnModelCreating metoda</span><span class="sxs-lookup"><span data-stu-id="49952-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="49952-208">Jak wspomniano, w celu zmiany konwencji i mapowania, można użyć OnModelCreating metody w DbContext klasy.</span><span class="sxs-lookup"><span data-stu-id="49952-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="49952-209">Mikrousługi zamawiania w eShopOnContainers implementuje jawne mapowanie i konfigurację, gdy jest to konieczne, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="49952-209">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

        orderConfiguration.HasKey(o => o.Id);

        orderConfiguration.Ignore(b => b.DomainEvents);

        orderConfiguration.Property(o => o.Id)
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

<span data-ttu-id="49952-210">Można ustawić wszystkie mapowania interfejsu API `OnModelCreating` fluent w ramach tej samej metody, ale wskazane jest, aby podzielić ten kod i mieć wiele klas konfiguracji, po jednej na jednostkę, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="49952-210">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="49952-211">Specjalnie dla dużych modeli zaleca się oddzielne klasy konfiguracji do konfigurowania różnych typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="49952-211">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="49952-212">Kod w przykładzie pokazuje kilka jawnych deklaracji i mapowania.</span><span class="sxs-lookup"><span data-stu-id="49952-212">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="49952-213">Jednak konwencje EF Core automatycznie wykonują wiele z tych mapowań, więc rzeczywisty kod, który będzie potrzebny w twoim przypadku, może być mniejszy.</span><span class="sxs-lookup"><span data-stu-id="49952-213">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="49952-214">Algorytm Hi/Lo w EF Core</span><span class="sxs-lookup"><span data-stu-id="49952-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="49952-215">Ciekawym aspektem kodu w poprzednim przykładzie jest to, że używa [algorytmu Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="49952-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="49952-216">Algorytm Hi/Lo jest przydatny, gdy potrzebujesz unikatowych kluczy przed zatwierdzeniem zmian.</span><span class="sxs-lookup"><span data-stu-id="49952-216">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="49952-217">Jako podsumowanie algorytm Hi-Lo przypisuje unikatowe identyfikatory do wierszy tabeli, a nie w zależności od natychmiastowego przechowywania wiersza w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="49952-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="49952-218">Dzięki temu można rozpocząć korzystanie z identyfikatorów od razu, jak to się dzieje w przypadku regularnych sekwencyjnych identyfikatorów bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="49952-219">Algorytm Hi/Lo opisuje mechanizm uzyskiwania partii unikatowych identyfikatorów z sekwencji powiązanej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-219">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="49952-220">Identyfikatory te są bezpieczne w użyciu, ponieważ baza danych gwarantuje unikatowość, więc nie będzie żadnych kolizji między użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="49952-220">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="49952-221">Algorytm ten jest interesujący z tych powodów:</span><span class="sxs-lookup"><span data-stu-id="49952-221">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="49952-222">Nie powoduje przerwania wzorca jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="49952-222">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="49952-223">Pobiera identyfikatory sekwencji w partiach, aby zminimalizować rund do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49952-223">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="49952-224">Generuje identyfikator czytelny dla człowieka, w przeciwieństwie do technik, które używają identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="49952-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="49952-225">EF Core obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) z `UseHiLo` metodą, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="49952-225">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="49952-226">Mapowanie pól zamiast właściwości</span><span class="sxs-lookup"><span data-stu-id="49952-226">Map fields instead of properties</span></span>

<span data-ttu-id="49952-227">Dzięki tej funkcji, dostępnej od EF Core 1.1, można bezpośrednio mapować kolumny na pola.</span><span class="sxs-lookup"><span data-stu-id="49952-227">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="49952-228">Istnieje możliwość nie używania właściwości w klasie jednostki i tylko do mapowania kolumn z tabeli na pola.</span><span class="sxs-lookup"><span data-stu-id="49952-228">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="49952-229">Typowym zastosowaniem dla tego byłoby prywatne pola dla każdego stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="49952-229">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="49952-230">Można to zrobić za pomocą pojedynczych pól `List<>` lub kolekcji, takich jak pole.</span><span class="sxs-lookup"><span data-stu-id="49952-230">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="49952-231">Ten punkt został wymieniony wcześniej, gdy omówiliśmy modelowanie klas modelu domeny, ale tutaj `PropertyAccessMode.Field` można zobaczyć, jak to mapowanie jest wykonywane z konfiguracją wyróżnioną w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="49952-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="49952-232">Użyj właściwości cienia w EF Core, ukrytych na poziomie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="49952-232">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="49952-233">Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki.</span><span class="sxs-lookup"><span data-stu-id="49952-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="49952-234">Wartości i stany tych właściwości są zachowywane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="49952-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="49952-235">Implementowanie wzorca specyfikacji kwerendy</span><span class="sxs-lookup"><span data-stu-id="49952-235">Implement the Query Specification pattern</span></span>

<span data-ttu-id="49952-236">Jak wprowadzono wcześniej w sekcji projektowania, wzorzec specyfikacji kwerendy jest wzorcem projektu opartym na domenie zaprojektowanym jako miejsce, w którym można umieścić definicję kwerendy z opcjonalną logiką sortowania i stronicowania.</span><span class="sxs-lookup"><span data-stu-id="49952-236">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="49952-237">Wzorzec specyfikacji kwerendy definiuje kwerendę w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="49952-237">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="49952-238">Na przykład, aby zhermetyzować stronicowane zapytanie, które wyszukuje niektóre produkty, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber, pageSize, filter itp.).</span><span class="sxs-lookup"><span data-stu-id="49952-238">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="49952-239">Następnie w ramach dowolnej metody repozytorium (zwykle przeciążenia List() zaakceptuje specyfikację zapytania IQuerySpecification i uruchomi oczekiwane zapytanie na podstawie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="49952-239">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="49952-240">Przykładem ogólnego interfejsu specyfikacji jest następujący kod z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="49952-240">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="49952-241">Następnie implementacja klasy podstawowej specyfikacji ogólnej jest następująca.</span><span class="sxs-lookup"><span data-stu-id="49952-241">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="49952-242">Następująca specyfikacja ładuje pojedynczy element koszyka, który otrzymuje identyfikator koszyka lub identyfikator kupującego, do którego należy koszyk.</span><span class="sxs-lookup"><span data-stu-id="49952-242">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="49952-243">Z [niecierpliwością załaduje](https://docs.microsoft.com/ef/core/querying/related-data) kolekcję przedmiotów kosza.</span><span class="sxs-lookup"><span data-stu-id="49952-243">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }

    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="49952-244">I na koniec można zobaczyć poniżej, jak ogólne repozytorium EF można użyć takiej specyfikacji do filtrowania i chętnie ładowania danych związanych z danym typu jednostki T.</span><span class="sxs-lookup"><span data-stu-id="49952-244">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="49952-245">Oprócz logiki hermetyzacji filtrowania specyfikacja może określić kształt danych, które mają być zwracane, w tym właściwości do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="49952-245">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="49952-246">Chociaż nie zaleca się `IQueryable` powrotu z repozytorium, doskonale jest używać ich w repozytorium w celu zbudowania zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="49952-246">Although we don’t recommend to return `IQueryable` from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="49952-247">Można zobaczyć to podejście używane w List metody `IQueryable` powyżej, który używa wyrażeń pośrednich do tworzenia listy zapytań zawiera przed wykonaniem kwerendy z kryteriów specyfikacji w ostatnim wierszu.</span><span class="sxs-lookup"><span data-stu-id="49952-247">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="49952-248">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="49952-248">Additional resources</span></span>

- <span data-ttu-id="49952-249">**Mapowanie tabeli** </span><span class="sxs-lookup"><span data-stu-id="49952-249">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="49952-250">**Użyj Funkcji HiLo do generowania kluczy z rdzeniem struktury jednostek** </span><span class="sxs-lookup"><span data-stu-id="49952-250">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="49952-251">**Pola podkładu** </span><span class="sxs-lookup"><span data-stu-id="49952-251">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="49952-252">**Steve Smith. Hermetyzowane kolekcje w rdzeniu frameworku jednostek** </span><span class="sxs-lookup"><span data-stu-id="49952-252">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="49952-253">**Właściwości cienia** </span><span class="sxs-lookup"><span data-stu-id="49952-253">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="49952-254">**Wzór specyfikacji** </span><span class="sxs-lookup"><span data-stu-id="49952-254">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="49952-255">[Poprzedni](infrastructure-persistence-layer-design.md)
> [następny](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="49952-255">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
