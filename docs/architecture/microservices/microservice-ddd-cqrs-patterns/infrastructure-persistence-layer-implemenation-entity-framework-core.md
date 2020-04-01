---
title: Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami implementacji warstwy trwałości infrastruktury przy użyciu programu Entity Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: 2d28d9246be3e102625ed5bb67ee1ccede03c942
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523323"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="d68fa-103">Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="d68fa-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="d68fa-104">Korzystając z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, zalecanym podejściem jest zaimplementowanie warstwy trwałości opartej na entity framework (EF).</span><span class="sxs-lookup"><span data-stu-id="d68fa-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="d68fa-105">EF obsługuje LINQ i zapewnia silnie typizowane obiekty dla modelu, a także uproszczoną trwałość w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="d68fa-106">Entity Framework ma długą historię jako część programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d68fa-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="d68fa-107">Korzystając z programu .NET Core, należy również użyć programu Entity Framework Core, który działa w systemie Windows lub Linux w taki sam sposób, jak program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d68fa-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="d68fa-108">EF Core jest kompletnym przepisaniem entity framework, zaimplementowanym ze znacznie mniejszym rozmiarem i istotną poprawą wydajności.</span><span class="sxs-lookup"><span data-stu-id="d68fa-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="d68fa-109">Wprowadzenie do core struktury encji</span><span class="sxs-lookup"><span data-stu-id="d68fa-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="d68fa-110">Entity Framework (EF) Core to lekka, rozszerzalna i wieloplatformowa wersja popularnej technologii dostępu do danych entity framework.</span><span class="sxs-lookup"><span data-stu-id="d68fa-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="d68fa-111">Został wprowadzony z .NET Core w połowie 2016 roku.</span><span class="sxs-lookup"><span data-stu-id="d68fa-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="d68fa-112">Ponieważ wprowadzenie do EF Core jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu podamy łącza do tych informacji.</span><span class="sxs-lookup"><span data-stu-id="d68fa-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d68fa-113">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d68fa-113">Additional resources</span></span>

- <span data-ttu-id="d68fa-114">**Rdzeń struktury encji** </span><span class="sxs-lookup"><span data-stu-id="d68fa-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="d68fa-115">**Wprowadzenie do ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="d68fa-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="d68fa-116">**Klasa DbContext** </span><span class="sxs-lookup"><span data-stu-id="d68fa-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="d68fa-117">**Porównaj EF Core & EF6.x** </span><span class="sxs-lookup"><span data-stu-id="d68fa-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="d68fa-118">Infrastruktura w ramach entity framework core z perspektywy DDD</span><span class="sxs-lookup"><span data-stu-id="d68fa-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="d68fa-119">Z punktu widzenia DDD ważną możliwością EF jest możliwość używania jednostek domeny POCO, znanych również w terminologii EF jako *jednostki poco oparte na kodzie.*</span><span class="sxs-lookup"><span data-stu-id="d68fa-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="d68fa-120">Jeśli używasz jednostek domeny POCO, klasy modelu domeny są niewiedzą dotyczące trwałości, zgodnie z [zasadami ignorancji trwałości](https://deviq.com/persistence-ignorance/) i [ignorancji infrastruktury.](https://ayende.com/blog/3137/infrastructure-ignorance)</span><span class="sxs-lookup"><span data-stu-id="d68fa-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="d68fa-121">Na wzorce DDD należy hermetyzować zachowanie domeny i reguły w samej klasie jednostki, dzięki czemu można kontrolować invariants, sprawdzania poprawności i reguł podczas uzyskiwania dostępu do dowolnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d68fa-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="d68fa-122">W związku z tym nie jest dobrą praktyką w DDD, aby umożliwić publiczny dostęp do kolekcji jednostek podrzędnych lub obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="d68fa-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="d68fa-123">Zamiast tego chcesz udostępnić metody, które kontrolują, jak i kiedy pola i kolekcje właściwości mogą być aktualizowane i jakie zachowanie i akcje powinny wystąpić, gdy tak się stanie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="d68fa-124">Ponieważ EF Core 1.1, aby spełnić te wymagania DDD, można mieć zwykłych pól w jednostkach zamiast właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="d68fa-125">Jeśli nie chcesz, aby pole encji było dostępne z zewnątrz, można po prostu utworzyć atrybut lub pole zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="d68fa-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="d68fa-126">Można również użyć ustawiaczów właściwości prywatnych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-126">You can also use private property setters.</span></span>

<span data-ttu-id="d68fa-127">W podobny sposób można teraz mieć dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisane `IReadOnlyCollection<T>`jako `List<T>`, który jest wspierany przez prywatnego elementu członkowskiego pola dla kolekcji (jak a) w jednostce, która opiera się na EF dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="d68fa-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="d68fa-128">Poprzednie wersje entity framework wymagane właściwości `ICollection<T>`kolekcji do obsługi , co oznaczało, że każdy deweloper przy użyciu klasy jednostki nadrzędnej można dodać lub usunąć elementy za pośrednictwem jego kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="d68fa-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="d68fa-129">Taka możliwość byłaby sprzeczna z zalecanymi wzorami w DDD.</span><span class="sxs-lookup"><span data-stu-id="d68fa-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="d68fa-130">Kolekcję prywatną można używać podczas ujawniania `IReadOnlyCollection<T>` obiektu tylko do odczytu, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="d68fa-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="d68fa-131">Należy pamiętać, że `OrderItems` dostęp do właściwości jest `IReadOnlyCollection<OrderItem>`dostępny tylko jako tylko do odczytu przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="d68fa-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="d68fa-132">Ten typ jest tylko do odczytu, więc jest chroniony przed regularnymi aktualizacjami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="d68fa-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="d68fa-133">EF Core umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczania" modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="d68fa-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="d68fa-134">Jest to czysty kod POCO .NET, ponieważ akcja mapowania jest implementowana w warstwie trwałości.</span><span class="sxs-lookup"><span data-stu-id="d68fa-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="d68fa-135">W tej akcji mapowania należy skonfigurować mapowanie pól do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="d68fa-136">W poniższym `OnModelCreating` przykładzie `OrderingContext` metody `OrderEntityTypeConfiguration` z i klasy `SetPropertyAccessMode` wywołanie nakazuje `OrderItems` EF Core dostęp do właściwości za pośrednictwem jego pola.</span><span class="sxs-lookup"><span data-stu-id="d68fa-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

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

<span data-ttu-id="d68fa-137">Podczas korzystania z pól zamiast właściwości, `OrderItem` jednostka jest utrwalona `List<OrderItem>` tak, jakby miała właściwość.</span><span class="sxs-lookup"><span data-stu-id="d68fa-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="d68fa-138">Jednak udostępnia pojedynczy akcesor, `AddOrderItem` metoda dodawania nowych elementów do zamówienia.</span><span class="sxs-lookup"><span data-stu-id="d68fa-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="d68fa-139">W rezultacie zachowanie i dane są powiązane ze sobą i będą spójne w całym kodzie aplikacji, który używa modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="d68fa-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="d68fa-140">Implementowanie repozytoriów niestandardowych za pomocą programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="d68fa-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="d68fa-141">Na poziomie implementacji repozytorium jest po prostu klasą z kodem trwałości danych koordynowanym przez jednostkę pracy (DBContext w EF Core) podczas wykonywania aktualizacji, jak pokazano w następującej klasie:</span><span class="sxs-lookup"><span data-stu-id="d68fa-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="d68fa-142">Należy zauważyć, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d68fa-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="d68fa-143">Jednak implementacja repozytorium odbywa się w warstwie trwałości i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="d68fa-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="d68fa-144">Ef DbContext pochodzi za pośrednictwem konstruktora za pośrednictwem iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="d68fa-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="d68fa-145">Jest on współużytkowane przez wiele repozytoriów w`ServiceLifetime.Scoped`tym samym zakresie żądań HTTP, dzięki jego `services.AddDbContext<>`domyślnemu okresowi istnienia ( ) w kontenerze IoC (który można również jawnie ustawić za pomocą ).</span><span class="sxs-lookup"><span data-stu-id="d68fa-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="d68fa-146">Metody implementacji w repozytorium (aktualizacje lub transakcje w porównaniu z kwerendami)</span><span class="sxs-lookup"><span data-stu-id="d68fa-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="d68fa-147">W ramach każdej klasy repozytorium należy umieścić metody trwałości, które aktualizują stan jednostek zawartych przez powiązane zagregowane.</span><span class="sxs-lookup"><span data-stu-id="d68fa-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="d68fa-148">Pamiętaj, że istnieje relacja jeden do jednego między agregacją a powiązanym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="d68fa-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="d68fa-149">Należy wziąć pod uwagę, że obiekt jednostki głównej agregacji może mieć osadzone jednostki podrzędne w jego wykres EF.</span><span class="sxs-lookup"><span data-stu-id="d68fa-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="d68fa-150">Na przykład kupujący może mieć wiele metod płatności jako powiązane jednostki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="d68fa-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="d68fa-151">Ponieważ podejście do zamawiania mikrousługi w eShopOnContainers jest również oparte na CQS/CQRS, większość zapytań nie są implementowane w repozytoriach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="d68fa-152">Deweloperzy mają swobodę tworzenia zapytań i sprzężeń, których potrzebują dla warstwy prezentacji bez ograniczeń nałożonych przez agregaty, niestandardowe repozytoria na agregację i DDD w ogóle.</span><span class="sxs-lookup"><span data-stu-id="d68fa-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="d68fa-153">Większość niestandardowych repozytoriów sugerowanych w tym przewodniku ma kilka metod aktualizacji lub transakcyjnych, ale tylko metody kwerendy potrzebne do uzyskania danych do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="d68fa-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="d68fa-154">Na przykład repozytorium Nabywcy Repozytorium repozytorium implementuje FindAsync metody, ponieważ aplikacja musi wiedzieć, czy dany nabywca istnieje przed utworzeniem nowego nabywcy związane z zamówieniem.</span><span class="sxs-lookup"><span data-stu-id="d68fa-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="d68fa-155">Jednak metody rzeczywistych zapytań, aby uzyskać dane do wysłania do warstwy prezentacji lub aplikacji klienckich są implementowane, jak wspomniano, w zapytaniach CQRS na podstawie elastycznych zapytań przy użyciu Dapper.</span><span class="sxs-lookup"><span data-stu-id="d68fa-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="d68fa-156">Korzystanie z repozytorium niestandardowego a bezpośrednio przy użyciu EF DbContext</span><span class="sxs-lookup"><span data-stu-id="d68fa-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="d68fa-157">Entity Framework DbContext Klasa jest oparta na jednostki pracy i repozytorium wzorców i może być używany bezpośrednio z kodu, takich jak z ASP.NET core kontrolera MVC.</span><span class="sxs-lookup"><span data-stu-id="d68fa-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="d68fa-158">W ten sposób można utworzyć najprostszy kod, jak w mikrousługi katalogu CRUD w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d68fa-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="d68fa-159">W przypadkach, gdy chcesz najprostszy kod możliwe, można bezpośrednio użyć DbContext klasy, jak wielu deweloperów zrobić.</span><span class="sxs-lookup"><span data-stu-id="d68fa-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="d68fa-160">Jednak implementowanie repozytoriów niestandardowych zapewnia kilka korzyści podczas implementowania bardziej złożonych mikrousług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d68fa-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="d68fa-161">Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, dzięki czemu jest oddzielona od warstwy modelu aplikacji i domeny.</span><span class="sxs-lookup"><span data-stu-id="d68fa-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="d68fa-162">Implementowanie tych wzorców może ułatwić korzystanie z repozytoriów makiety symulujących dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="d68fa-163">Na rysunku 7-18 widać różnice między nie przy użyciu repozytoriów (bezpośrednio przy użyciu EF DbContext) w porównaniu przy użyciu repozytoriów, które ułatwiają mock tych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="d68fa-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![Diagram przedstawiający składniki i przepływ danych w dwóch repozytoriach.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="d68fa-165">**Rysunek 7-18**.</span><span class="sxs-lookup"><span data-stu-id="d68fa-165">**Figure 7-18**.</span></span> <span data-ttu-id="d68fa-166">Używanie niestandardowych repozytoriów w porównaniu do zwykłego DbContext</span><span class="sxs-lookup"><span data-stu-id="d68fa-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="d68fa-167">Rysunek 7-18 pokazuje, że przy użyciu niestandardowego repozytorium dodaje warstwę abstrakcji, która może służyć do ułatwienia testowania przez szyderczy repozytorium.</span><span class="sxs-lookup"><span data-stu-id="d68fa-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="d68fa-168">Istnieje wiele alternatyw podczas szyderstwa.</span><span class="sxs-lookup"><span data-stu-id="d68fa-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="d68fa-169">Możesz drwić tylko repozytoria lub można drwić z całej jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="d68fa-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="d68fa-170">Zwykle szydzenie tylko repozytoria wystarczy, a złożoność do abstrakcyjnego i pozorować całą jednostkę pracy zwykle nie jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="d68fa-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="d68fa-171">Później, gdy koncentrujemy się na warstwie aplikacji, zobaczysz, jak wstrzykiwanie zależności działa w ASP.NET Core i jak jest implementowany podczas korzystania z repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="d68fa-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="d68fa-172">Krótko mówiąc, niestandardowe repozytoria umożliwiają łatwiejsze testowanie kodu za pomocą testów jednostkowych, na które stan warstwy danych nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="d68fa-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="d68fa-173">Jeśli uruchomisz testy, które również uzyskać dostęp do rzeczywistej bazy danych za pośrednictwem entity framework, nie są one testy jednostkowe, ale testy integracji, które są znacznie wolniejsze.</span><span class="sxs-lookup"><span data-stu-id="d68fa-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="d68fa-174">Jeśli używasz DbContext bezpośrednio, trzeba by mock go lub uruchomić testy jednostkowe przy użyciu programu SQL Server w pamięci z przewidywalnych danych dla testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="d68fa-175">Ale szydzenie z DbContext lub kontrolowanie fałszywych danych wymaga więcej pracy niż szydzenie na poziomie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="d68fa-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="d68fa-176">Oczywiście zawsze można przetestować kontrolery MVC.</span><span class="sxs-lookup"><span data-stu-id="d68fa-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="d68fa-177">Ef DbContext i IUnitOfPraca istnienia wystąpienia w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="d68fa-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="d68fa-178">Obiekt `DbContext` (udostępniany `IUnitOfWork` jako obiekt) powinien być współużytkowane przez wiele repozytoriów w tym samym zakresie żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="d68fa-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="d68fa-179">Na przykład jest to prawdą, gdy wykonywana operacja musi dotyczyć wielu agregatów lub po prostu dlatego, że używasz wielu wystąpień repozytorium.</span><span class="sxs-lookup"><span data-stu-id="d68fa-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="d68fa-180">Należy również wspomnieć, `IUnitOfWork` że interfejs jest częścią warstwy domeny, a nie typu EF Core.</span><span class="sxs-lookup"><span data-stu-id="d68fa-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="d68fa-181">Aby to zrobić, wystąpienie `DbContext` obiektu musi mieć jego okres istnienia usługi ustawiona na ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="d68fa-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="d68fa-182">Jest to domyślny okres `DbContext` istnienia `services.AddDbContext` podczas rejestrowania w kontenerze IoC `Startup.cs` z Metody ConfigureServices pliku w projekcie interfejsu API sieci Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d68fa-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="d68fa-183">Ilustruje to poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="d68fa-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="d68fa-184">Tryb wystąpienia DbContext nie powinien być skonfigurowany jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="d68fa-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="d68fa-185">Okres istnienia wystąpienia repozytorium w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="d68fa-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="d68fa-186">W podobny sposób okres istnienia repozytorium powinien być zwykle ustawiony jako zakres (InstancePerLifetimeScope w autofac).</span><span class="sxs-lookup"><span data-stu-id="d68fa-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="d68fa-187">Może to być również przejściowy (InstancePerDependency w Autofac), ale usługa będzie bardziej wydajne w odniesieniu do pamięci podczas korzystania z okresu istnienia o określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="d68fa-188">Należy zauważyć, że przy użyciu okresu istnienia singla dla repozytorium może spowodować poważne problemy współbieżności, gdy DbContext jest ustawiona na zakres (InstancePerLifetimeScope) okres istnienia (domyślne okresy istnienia dla DBContext).</span><span class="sxs-lookup"><span data-stu-id="d68fa-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d68fa-189">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d68fa-189">Additional resources</span></span>

- <span data-ttu-id="d68fa-190">**Implementowanie repozytorium i jednostki wzorców pracy w ASP.NET aplikacji MVC** </span><span class="sxs-lookup"><span data-stu-id="d68fa-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="d68fa-191">**Jonathan Allen. Strategie wdrażania wzorca repozytorium z entity framework, dapper i łańcuch** </span><span class="sxs-lookup"><span data-stu-id="d68fa-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="d68fa-192">**Cesar de la Torre. Porównywanie okresów istnienia usługi kontenera core ASP.NET core z zakresami wystąpień kontenera IoC autofac** </span><span class="sxs-lookup"><span data-stu-id="d68fa-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="d68fa-193">Mapowanie tabeli</span><span class="sxs-lookup"><span data-stu-id="d68fa-193">Table mapping</span></span>

<span data-ttu-id="d68fa-194">Mapowanie tabel identyfikuje dane tabeli, z których mają być wyszukiwane i zapisywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="d68fa-195">Wcześniej był używany sposób, w jaki jednostki domeny (na przykład domena produktu lub zamówienia) mogą być używane do generowania schematu powiązanej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="d68fa-196">EF jest silnie zaprojektowany wokół koncepcji *konwencji*.</span><span class="sxs-lookup"><span data-stu-id="d68fa-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="d68fa-197">Konwencje odnoszą się do pytań takich jak "Jaka będzie nazwa stołu?"</span><span class="sxs-lookup"><span data-stu-id="d68fa-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="d68fa-198">lub "Jaka właściwość jest kluczem podstawowym?"</span><span class="sxs-lookup"><span data-stu-id="d68fa-198">or “What property is the primary key?”</span></span> <span data-ttu-id="d68fa-199">Konwencje są zazwyczaj oparte na konwencjonalnych nazw — na przykład jest typowe dla klucza podstawowego, aby być właściwość, która kończy się identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="d68fa-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="d68fa-200">Zgodnie z konwencją każda jednostka zostanie skonfigurowana do mapowania `DbSet<TEntity>` do tabeli o takiej samej nazwie jak właściwość, która udostępnia jednostkę w kontekście pochodnym.</span><span class="sxs-lookup"><span data-stu-id="d68fa-200">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="d68fa-201">Jeśli `DbSet<TEntity>` dla danej jednostki nie jest podana żadna wartość, używana jest nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="d68fa-201">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="d68fa-202">Adnotacje danych a płynny interfejs API</span><span class="sxs-lookup"><span data-stu-id="d68fa-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="d68fa-203">Istnieje wiele dodatkowych konwencji EF Core, a większość z nich można zmienić za pomocą adnotacji danych lub fluent API, zaimplementowane w ramach OnModelCreating metody.</span><span class="sxs-lookup"><span data-stu-id="d68fa-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="d68fa-204">Adnotacje danych muszą być używane w klasach modelu jednostki, co jest bardziej inwazyjny sposób z punktu widzenia DDD.</span><span class="sxs-lookup"><span data-stu-id="d68fa-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="d68fa-205">Jest to spowodowane zanieczyszczone modelu adnotacjami danych związanych z bazy danych infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="d68fa-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="d68fa-206">Z drugiej strony Fluent interfejsu API jest wygodnym sposobem, aby zmienić większość konwencji i mapowania w warstwie infrastruktury trwałości danych, więc model jednostki będzie czysty i oddzielone od infrastruktury trwałości.</span><span class="sxs-lookup"><span data-stu-id="d68fa-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="d68fa-207">Fluent API i OnModelCreating metody</span><span class="sxs-lookup"><span data-stu-id="d68fa-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="d68fa-208">Jak wspomniano, w celu zmiany konwencji i mapowania, można użyć OnModelCreating metody w DbContext klasy.</span><span class="sxs-lookup"><span data-stu-id="d68fa-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="d68fa-209">Mikrousługa zamawiania w eShopOnContainers implementuje jawne mapowanie i konfigurację, w razie potrzeby, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-209">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="d68fa-210">Można ustawić wszystkie mapowania interfejsu API `OnModelCreating` Fluent w ramach tej samej metody, ale wskazane jest partycjonowanie tego kodu i wiele klas konfiguracji, po jednej na jednostkę, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-210">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="d68fa-211">Szczególnie w przypadku dużych modeli zaleca się, aby mieć oddzielne klasy konfiguracji do konfigurowania różnych typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="d68fa-211">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="d68fa-212">Kod w przykładzie pokazuje kilka jawnych deklaracji i mapowania.</span><span class="sxs-lookup"><span data-stu-id="d68fa-212">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="d68fa-213">Jednak ef core konwencje zrobić wiele z tych mapowań automatycznie, więc rzeczywisty kod, który będzie potrzebny w twoim przypadku może być mniejsza.</span><span class="sxs-lookup"><span data-stu-id="d68fa-213">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="d68fa-214">Algorytm Hi/Lo w EF Core</span><span class="sxs-lookup"><span data-stu-id="d68fa-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="d68fa-215">Ciekawym aspektem kodu w poprzednim przykładzie jest to, że używa [algorytmu Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="d68fa-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="d68fa-216">Algorytm Hi/Lo jest przydatny, gdy potrzebujesz unikatowych kluczy przed zatwierdzeniem zmian.</span><span class="sxs-lookup"><span data-stu-id="d68fa-216">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="d68fa-217">Podsumowując, algorytm Hi-Lo przypisuje unikatowe identyfikatory do wierszy tabeli, nie będąc w zależności od natychmiastowego przechowywania wiersza w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="d68fa-218">Dzięki temu można rozpocząć korzystanie z identyfikatorów od razu, jak to się dzieje w przypadku regularnych identyfikatorów sekwencyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="d68fa-219">Algorytm Hi/Lo opisuje mechanizm uzyskiwania partii unikatowych identyfikatorów z powiązanej sekwencji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-219">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="d68fa-220">Te identyfikatory są bezpieczne w użyciu, ponieważ baza danych gwarantuje unikatowość, więc nie będzie żadnych kolizji między użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="d68fa-220">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="d68fa-221">Algorytm ten jest interesujący z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="d68fa-221">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="d68fa-222">Nie przerywa wzorca jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="d68fa-222">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="d68fa-223">Pobiera identyfikatory sekwencji w partiach, aby zminimalizować rund do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d68fa-223">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="d68fa-224">Generuje identyfikator czytelny dla człowieka, w przeciwieństwie do technik, które używają identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="d68fa-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="d68fa-225">EF Core obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) z `UseHiLo` metodą, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-225">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="d68fa-226">Mapuj pola zamiast właściwości</span><span class="sxs-lookup"><span data-stu-id="d68fa-226">Map fields instead of properties</span></span>

<span data-ttu-id="d68fa-227">Dzięki tej funkcji, dostępnej od ef core 1.1, można bezpośrednio mapować kolumny do pól.</span><span class="sxs-lookup"><span data-stu-id="d68fa-227">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="d68fa-228">Istnieje możliwość nie używać właściwości w klasie jednostki i tylko do mapowania kolumn z tabeli do pól.</span><span class="sxs-lookup"><span data-stu-id="d68fa-228">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="d68fa-229">Typowym zastosowaniem dla tego byłoby pola prywatne dla każdego stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="d68fa-229">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="d68fa-230">Można to zrobić za pomocą pojedynczych pól `List<>` lub kolekcji, takich jak pole.</span><span class="sxs-lookup"><span data-stu-id="d68fa-230">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="d68fa-231">Ten punkt został wymieniony wcześniej, gdy omówiliśmy modelowanie klas modelu domeny, ale tutaj `PropertyAccessMode.Field` można zobaczyć, jak to mapowanie jest wykonywane z konfiguracją wyróżnioną w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="d68fa-232">Użyj właściwości cienia w EF Core, ukrytych na poziomie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="d68fa-232">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="d68fa-233">Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki.</span><span class="sxs-lookup"><span data-stu-id="d68fa-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="d68fa-234">Wartości i stany tych właściwości są utrzymywane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="d68fa-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="d68fa-235">Implementowanie wzorca specyfikacji kwerendy</span><span class="sxs-lookup"><span data-stu-id="d68fa-235">Implement the Query Specification pattern</span></span>

<span data-ttu-id="d68fa-236">Jak wprowadzono wcześniej w sekcji projektu, wzorzec specyfikacji kwerendy jest wzorzec projektu opartego na domenie zaprojektowany jako miejsce, w którym można umieścić definicję kwerendy z opcjonalną logiką sortowania i stronicowania.</span><span class="sxs-lookup"><span data-stu-id="d68fa-236">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="d68fa-237">Wzorzec specyfikacji kwerendy definiuje kwerendę w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="d68fa-237">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="d68fa-238">Na przykład w celu hermetyzacji sstronicowanego zapytania, które wyszukuje niektóre produkty, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber, pageSize, filter itp.).</span><span class="sxs-lookup"><span data-stu-id="d68fa-238">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="d68fa-239">Następnie w ramach dowolnej metody repozytorium (zwykle przeciążenie List() zaakceptuje IQuerySpecification i uruchomi oczekiwane zapytanie na podstawie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="d68fa-239">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="d68fa-240">Przykładem ogólnego interfejsu specyfikacji jest następujący kod z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="d68fa-240">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="d68fa-241">Następnie implementacja klasy podstawowej specyfikacji ogólnej jest następująca.</span><span class="sxs-lookup"><span data-stu-id="d68fa-241">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="d68fa-242">Poniższa specyfikacja ładuje jednostkę pojedynczego koszyka, pod którą podano identyfikator koszyka lub identyfikator kupującego, do którego należy koszyk.</span><span class="sxs-lookup"><span data-stu-id="d68fa-242">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="d68fa-243">Chętnie [załaduje](https://docs.microsoft.com/ef/core/querying/related-data) kolekcję przedmiotów koszyka.</span><span class="sxs-lookup"><span data-stu-id="d68fa-243">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="d68fa-244">I wreszcie, można zobaczyć poniżej, jak ogólne repozytorium EF można użyć takiej specyfikacji do filtrowania i chętnie załadować dane związane z danego typu jednostki T.</span><span class="sxs-lookup"><span data-stu-id="d68fa-244">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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

<span data-ttu-id="d68fa-245">Oprócz hermetyzacji logiki filtrowania, specyfikacja można określić kształt danych, które mają być zwracane, w tym właściwości, które mają być wypełniane.</span><span class="sxs-lookup"><span data-stu-id="d68fa-245">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="d68fa-246">Mimo że nie zaleca `IQueryable` się zwracać z repozytorium, jest całkowicie w porządku, aby użyć ich w repozytorium do tworzenia zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="d68fa-246">Although we don’t recommend to return `IQueryable` from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="d68fa-247">Możesz zobaczyć to podejście używane w List metody `IQueryable` powyżej, który używa wyrażeń pośrednich do tworzenia listy kwerendy zawiera przed wykonaniem kwerendy z kryteriami specyfikacji w ostatnim wierszu.</span><span class="sxs-lookup"><span data-stu-id="d68fa-247">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d68fa-248">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d68fa-248">Additional resources</span></span>

- <span data-ttu-id="d68fa-249">**Mapowanie tabel** </span><span class="sxs-lookup"><span data-stu-id="d68fa-249">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="d68fa-250">**Używanie HiLo do generowania kluczy za pomocą programu Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="d68fa-250">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="d68fa-251">**Pola zapasowe** </span><span class="sxs-lookup"><span data-stu-id="d68fa-251">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="d68fa-252">**Steve Smith. Zhermetyzowane kolekcje w core ramach encji** </span><span class="sxs-lookup"><span data-stu-id="d68fa-252">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="d68fa-253">**Właściwości cienia** </span><span class="sxs-lookup"><span data-stu-id="d68fa-253">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="d68fa-254">**Wzór specyfikacji** </span><span class="sxs-lookup"><span data-stu-id="d68fa-254">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="d68fa-255">[Poprzedni](infrastructure-persistence-layer-design.md)
> [następny](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="d68fa-255">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
