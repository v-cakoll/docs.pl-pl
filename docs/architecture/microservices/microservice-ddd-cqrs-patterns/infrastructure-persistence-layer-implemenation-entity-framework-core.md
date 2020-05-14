---
title: Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się ze szczegółami implementacji warstwy trwałości infrastruktury przy użyciu Entity Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: c91980504b0f9de859c6d211f3a1f47435b2d3cc
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396256"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="9a94b-103">Zaimplementuj warstwę trwałości infrastruktury za pomocą Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9a94b-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="9a94b-104">W przypadku korzystania z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, Zalecanym podejściem jest implementacja warstwy trwałości na podstawie Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="9a94b-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="9a94b-105">Dr obsługuje LINQ i zapewnia obiekty silnie wpisane dla modelu, a także uproszczoną trwałość do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="9a94b-106">Entity Framework ma długą historię w ramach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a94b-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="9a94b-107">W przypadku korzystania z platformy .NET Core należy również użyć Entity Framework Core, który działa w systemie Windows lub Linux w taki sam sposób, jak .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a94b-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="9a94b-108">EF Core to pełny zapis Entity Framework, który jest implementowany z znacznie mniejszym wpływem i istotnymi ulepszeniami wydajności.</span><span class="sxs-lookup"><span data-stu-id="9a94b-108">EF Core is a complete rewrite of Entity Framework that's implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="9a94b-109">Wprowadzenie do Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9a94b-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="9a94b-110">Entity Framework (EF) Core to lekka, rozszerzalna i wieloplatformowa wersja popularnej Entity Framework technologii dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="9a94b-111">Wprowadzono ją z platformą .NET Core w połowie 2016.</span><span class="sxs-lookup"><span data-stu-id="9a94b-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="9a94b-112">Ponieważ wprowadzenie do EF Core jest już dostępne w dokumentacji firmy Microsoft, tutaj udostępniamy linki do tych informacji.</span><span class="sxs-lookup"><span data-stu-id="9a94b-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9a94b-113">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9a94b-113">Additional resources</span></span>

- <span data-ttu-id="9a94b-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="9a94b-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="9a94b-115">**Wprowadzenie do ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="9a94b-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="9a94b-116">**DbContext — Klasa** </span><span class="sxs-lookup"><span data-stu-id="9a94b-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="9a94b-117">**Porównaj EF Core & EF6. x** </span><span class="sxs-lookup"><span data-stu-id="9a94b-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="9a94b-118">Infrastruktura w Entity Framework Core z perspektywy DDD</span><span class="sxs-lookup"><span data-stu-id="9a94b-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="9a94b-119">Z punktu widzenia, ważną funkcją EF jest możliwość korzystania z jednostek domeny POCO, znanego również w terminologii EF jako jednostki POCO w *kodzie*.</span><span class="sxs-lookup"><span data-stu-id="9a94b-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="9a94b-120">Jeśli używasz jednostek domeny POCO, klasy modelu domeny są trwałości-ignorujących, przestrzegając [Ignorujących trwałości](https://deviq.com/persistence-ignorance/) i zasad [ignorujących infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) .</span><span class="sxs-lookup"><span data-stu-id="9a94b-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="9a94b-121">Na wzorce DDD należy hermetyzować zachowanie domeny i reguły w samej klasie jednostki, aby można było sterować niektórymi, walidacjami i regułami podczas uzyskiwania dostępu do dowolnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9a94b-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="9a94b-122">W związku z tym nie jest dobrym zwyczajem w DDD, aby zezwalać na publiczny dostęp do kolekcji jednostek podrzędnych lub obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="9a94b-123">Zamiast tego należy udostępnić metody kontrolujące, jak i kiedy można aktualizować pola i kolekcje właściwości oraz jakie zachowanie i akcje powinny wystąpić, gdy wystąpi taka sytuacja.</span><span class="sxs-lookup"><span data-stu-id="9a94b-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="9a94b-124">Ponieważ EF Core 1,1, aby spełnić te wymagania dotyczące DDD, w jednostkach można używać zwykłych pól zamiast właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="9a94b-125">Jeśli nie chcesz, aby pole jednostki było dostępne na zewnątrz, możesz po prostu utworzyć atrybut lub pole zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="9a94b-126">Można również użyć własnych metod ustawiających właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-126">You can also use private property setters.</span></span>

<span data-ttu-id="9a94b-127">W podobny sposób można teraz mieć dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisanej jako `IReadOnlyCollection<T>` , która jest objęta przez prywatny element członkowski dla kolekcji (na przykład `List<T>` ) w jednostce, która opiera się na EF dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="9a94b-128">Poprzednie wersje Entity Framework wymaganych właściwości kolekcji do obsługi `ICollection<T>` , co oznacza, że każdy deweloper korzystający z klasy jednostki nadrzędnej może dodawać lub usuwać elementy za pośrednictwem swoich kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="9a94b-129">Taka możliwość będzie od zalecanych wzorców w DDD.</span><span class="sxs-lookup"><span data-stu-id="9a94b-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="9a94b-130">Możesz użyć prywatnej kolekcji podczas udostępniania obiektu tylko do odczytu `IReadOnlyCollection<T>` , jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="9a94b-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="9a94b-131">`OrderItems`Dostęp do właściwości można uzyskać tylko do odczytu przy użyciu `IReadOnlyCollection<OrderItem>` .</span><span class="sxs-lookup"><span data-stu-id="9a94b-131">The `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="9a94b-132">Ten typ jest tylko do odczytu, więc jest chroniony przed regularnymi aktualizacjami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="9a94b-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="9a94b-133">EF Core zapewnia sposób mapowania modelu domeny do fizycznej bazy danych bez "zanieczyszczania" modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9a94b-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="9a94b-134">Jest to czysty kod POCO .NET, ponieważ akcja mapowania jest zaimplementowana w warstwie trwałości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="9a94b-135">W tej akcji mapowania należy skonfigurować mapowanie pola-do-bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="9a94b-136">W poniższym przykładzie `OnModelCreating` metody z `OrderingContext` i `OrderEntityTypeConfiguration` klasy, wywołanie do `SetPropertyAccessMode` instruuje EF Core, aby uzyskać dostęp do `OrderItems` właściwości za pośrednictwem pola.</span><span class="sxs-lookup"><span data-stu-id="9a94b-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
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

<span data-ttu-id="9a94b-137">Gdy używasz pól zamiast właściwości, `OrderItem` jednostka jest utrwalona tak, jakby miała `List<OrderItem>` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="9a94b-137">When you use fields instead of properties, the `OrderItem` entity is persisted as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="9a94b-138">Jednak udostępnia on pojedynczy akcesor, `AddOrderItem` metodę, służącą do dodawania nowych elementów do zamówienia.</span><span class="sxs-lookup"><span data-stu-id="9a94b-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="9a94b-139">W efekcie zachowanie i dane są powiązane ze sobą i będą spójne w całym kodzie aplikacji, który używa modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9a94b-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="9a94b-140">Implementowanie niestandardowych repozytoriów przy użyciu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9a94b-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="9a94b-141">Na poziomie implementacji repozytorium jest po prostu klasą z kodem trwałości danych koordynowanym przez jednostkę pracy (DbContext w EF Core) podczas przeprowadzania aktualizacji, jak pokazano w poniższej klasie:</span><span class="sxs-lookup"><span data-stu-id="9a94b-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using directives...
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

<span data-ttu-id="9a94b-142">`IBuyerRepository`Interfejs pochodzi z warstwy modelu domeny jako kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9a94b-142">The `IBuyerRepository` interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="9a94b-143">Implementacja repozytorium jest jednak wykonywana z warstwy trwałości i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9a94b-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="9a94b-144">Kontekst EF DBjest dostarczany przez Konstruktor poprzez wstrzyknięcie zależności.</span><span class="sxs-lookup"><span data-stu-id="9a94b-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="9a94b-145">Jest ona udostępniana między wieloma repozytoriami w ramach tego samego zakresu żądania HTTP, dzięki czemu jego domyślny okres istnienia ( `ServiceLifetime.Scoped` ) w kontenerze IOC (który można także jawnie ustawić przy użyciu `services.AddDbContext<>` ).</span><span class="sxs-lookup"><span data-stu-id="9a94b-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="9a94b-146">Metody implementacji w repozytorium (aktualizacje lub transakcje w porównaniu z zapytaniami)</span><span class="sxs-lookup"><span data-stu-id="9a94b-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="9a94b-147">W ramach każdej klasy repozytorium należy umieścić metody trwałości, które aktualizują stan jednostek zawartych w powiązanej agregacji.</span><span class="sxs-lookup"><span data-stu-id="9a94b-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="9a94b-148">Należy pamiętać, że istnieje relacja jeden do jednego między agregacją i powiązanym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9a94b-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="9a94b-149">Należy wziąć pod uwagę, że zagregowany obiekt jednostki głównej może mieć osadzone jednostki podrzędne w ramach jego grafu EF.</span><span class="sxs-lookup"><span data-stu-id="9a94b-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="9a94b-150">Na przykład kupujący może mieć wiele metod płatności jako powiązanych jednostek podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="9a94b-151">Ponieważ podejście do mikrousługi porządkowania w eShopOnContainers opiera się również na CQS/CQRS, większość zapytań nie jest zaimplementowana w niestandardowych repozytoriach.</span><span class="sxs-lookup"><span data-stu-id="9a94b-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="9a94b-152">Deweloperzy mogą uzyskać swobodę tworzenia zapytań i sprzężeń potrzebnych do warstwy prezentacji bez ograniczeń narzuconych przez agregacje, niestandardowe repozytoria na zagregowane i DDD w ogólności.</span><span class="sxs-lookup"><span data-stu-id="9a94b-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="9a94b-153">Większość repozytoriów niestandardowych sugerowanych przez ten przewodnik ma kilka metod Update lub transakcyjnych, ale tylko metody zapytania potrzebne do aktualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="9a94b-154">Na przykład repozytorium BuyerRepository implementuje metodę FindAsync, ponieważ aplikacja musi wiedzieć, czy konkretny kupujący istnieje przed utworzeniem nowego nabywcy związanego z kolejnością.</span><span class="sxs-lookup"><span data-stu-id="9a94b-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="9a94b-155">Jednak prawdziwe metody zapytań umożliwiające pobieranie danych do wysłania do warstwy prezentacji lub aplikacji klienckich są implementowane, jak wspomniano w zapytaniach CQRS na podstawie elastycznych zapytań przy użyciu Dapper.</span><span class="sxs-lookup"><span data-stu-id="9a94b-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="9a94b-156">Korzystanie z niestandardowego repozytorium i bezpośrednie używanie EF DbContext</span><span class="sxs-lookup"><span data-stu-id="9a94b-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="9a94b-157">Entity Framework DbContext jest oparta na wzorcach wzorców pracy i repozytorium i może być używana bezpośrednio w kodzie, na przykład z kontrolera ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="9a94b-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="9a94b-158">Wzorce jednostki pracy i repozytorium powodują powstanie najprostszego kodu, tak jak w przypadku mikrousługi CRUD Catalog w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9a94b-158">The Unit of Work and Repository patterns result in the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="9a94b-159">W przypadkach, gdy chcesz, aby najprostszy kod był możliwy, możesz chcieć bezpośrednio użyć klasy DbContext, tak jak wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="9a94b-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="9a94b-160">Jednak wdrożenie repozytoriów niestandardowych zapewnia kilka korzyści w przypadku implementowania bardziej złożonych mikrousług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a94b-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="9a94b-161">Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, aby była ona oddzielona od warstw aplikacji i modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9a94b-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain-model layers.</span></span> <span data-ttu-id="9a94b-162">Wdrożenie tych wzorców może ułatwić korzystanie z repozytoriów makiety, które symulują dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="9a94b-163">Na rysunku 7-18 można zobaczyć różnice między nieużywaniem repozytoriów (bezpośrednio przy użyciu EF DbContext) zamiast korzystać z repozytoriów, co ułatwia zasymulować te repozytoria.</span><span class="sxs-lookup"><span data-stu-id="9a94b-163">In Figure 7-18, you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories, which makes it easier to mock those repositories.</span></span>

![Diagram przedstawiający składniki i przepływu danych w dwóch repozytoriach.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="9a94b-165">**Rysunek 7-18**.</span><span class="sxs-lookup"><span data-stu-id="9a94b-165">**Figure 7-18**.</span></span> <span data-ttu-id="9a94b-166">Używanie niestandardowych repozytoriów zamiast zwykłego DbContext</span><span class="sxs-lookup"><span data-stu-id="9a94b-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="9a94b-167">Rysunek 7-18 pokazuje, że za pomocą repozytorium niestandardowego dodaje warstwę abstrakcji, która może być używana do ułatwienia testowania przez imitację repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9a94b-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="9a94b-168">Podczas imitacji istnieje wiele wariantów.</span><span class="sxs-lookup"><span data-stu-id="9a94b-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="9a94b-169">Można zasymulować tylko repozytoria lub można zasymulować całą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="9a94b-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="9a94b-170">Zwykle imitacja tylko repozytoria jest wystarczająca, a złożoność abstrakcyjna i makieta całościowej jednostki pracy zwykle nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="9a94b-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="9a94b-171">Później, gdy skupmy się na warstwie aplikacji, zobaczysz, jak iniekcja zależności działa w ASP.NET Core i jak jest zaimplementowana w przypadku korzystania z repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="9a94b-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="9a94b-172">W krótkim przypadku niestandardowe repozytoria umożliwiają łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie mają wpływu na stan warstwy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="9a94b-173">Jeśli uruchamiasz testy, które również uzyskują dostęp do rzeczywistej bazy danych za pomocą Entity Framework, nie są one testami jednostkowymi, ale testy integracji, które są znacznie wolniejsze.</span><span class="sxs-lookup"><span data-stu-id="9a94b-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="9a94b-174">Jeśli używasz DbContext bezpośrednio, musisz go zasymulować lub uruchomić testy jednostkowe za pomocą SQL Server w pamięci z przewidywalnymi danymi dla testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="9a94b-175">Jednak imitacja DbContext lub kontrolowanie danych fałszywych wymaga większego działania niż imitacja na poziomie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9a94b-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="9a94b-176">Oczywiście można zawsze testować kontrolery MVC.</span><span class="sxs-lookup"><span data-stu-id="9a94b-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="9a94b-177">Okres istnienia wystąpienia elementu EF DbContext i IUnitOfWork w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="9a94b-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="9a94b-178">`DbContext`Obiekt (uwidoczniony jako `IUnitOfWork` obiekt) powinien być współużytkowany między wieloma repozytoriami w ramach tego samego zakresu żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="9a94b-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="9a94b-179">Na przykład dzieje się tak, gdy wykonywana operacja musi zająć się wieloma agregacjami lub po prostu, ponieważ jest używane wiele wystąpień repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9a94b-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="9a94b-180">Należy również pamiętać, że `IUnitOfWork` interfejs jest częścią warstwy domeny, a nie typu EF Core.</span><span class="sxs-lookup"><span data-stu-id="9a94b-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="9a94b-181">Aby to zrobić, wystąpienie `DbContext` obiektu musi mieć ustawiony okres istnienia usługi jako servicelifetime. zakres.</span><span class="sxs-lookup"><span data-stu-id="9a94b-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="9a94b-182">Jest to domyślny okres istnienia rejestracji w `DbContext` usłudze `services.AddDbContext` w kontenerze IOC z metody ConfigureServices `Startup.cs` pliku w projekcie interfejsu API sieci Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a94b-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="9a94b-183">Ilustruje to poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="9a94b-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="9a94b-184">Tryb tworzenia wystąpień DbContext nie powinien być skonfigurowany jako servicelifetime. przejściowy lub servicelifetime. singleton.</span><span class="sxs-lookup"><span data-stu-id="9a94b-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="9a94b-185">Okres istnienia wystąpienia repozytorium w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="9a94b-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="9a94b-186">W podobny sposób okres istnienia repozytorium powinien być zazwyczaj ustawiany jako zakres (InstancePerLifetimeScope w Autofac).</span><span class="sxs-lookup"><span data-stu-id="9a94b-186">In a similar way, repository's lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="9a94b-187">Może to być również przejściowe (InstancePerDependency w Autofac), ale usługa będzie bardziej wydajna w zakresie pamięci w przypadku korzystania z okresu istnienia w zakresie.</span><span class="sxs-lookup"><span data-stu-id="9a94b-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="9a94b-188">Użycie pojedynczego okresu istnienia dla repozytorium może spowodować poważne problemy współbieżności, gdy dla kontekstu DbContext ustawiono zakres (InstancePerLifetimeScope) okres istnienia (domyślne okresy istnienia dla kontekstu DbContext).</span><span class="sxs-lookup"><span data-stu-id="9a94b-188">Using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9a94b-189">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9a94b-189">Additional resources</span></span>

- <span data-ttu-id="9a94b-190">**Implementacja wzorców repozytorium i jednostki pracy w aplikacji ASP.NET MVC** </span><span class="sxs-lookup"><span data-stu-id="9a94b-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="9a94b-191">**Jonathana. Strategie implementacji dla wzorca repozytorium z Entity Framework, Dapper i łańcuchem** </span><span class="sxs-lookup"><span data-stu-id="9a94b-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="9a94b-192">**Cesar de La Torre. Porównanie ASP.NET Core okresów istnienia usługi kontenera IoC z zakresem wystąpień kontenera Autofac IoC** </span><span class="sxs-lookup"><span data-stu-id="9a94b-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="9a94b-193">Mapowanie tabeli</span><span class="sxs-lookup"><span data-stu-id="9a94b-193">Table mapping</span></span>

<span data-ttu-id="9a94b-194">Mapowanie tabeli identyfikuje dane tabeli, z których mają być wysyłane zapytania i zapisane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="9a94b-195">Wcześniej pokazano, jak jednostki domeny (na przykład produkt lub domena zamówienia) mogą być używane do generowania powiązanego schematu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="9a94b-196">EF jest silnie zaprojektowana wokół koncepcji *Konwencji*.</span><span class="sxs-lookup"><span data-stu-id="9a94b-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="9a94b-197">Konwencje dotyczące adresów, takich jak "Jaka będzie nazwa tabeli?"</span><span class="sxs-lookup"><span data-stu-id="9a94b-197">Conventions address questions like "What will the name of a table be?"</span></span> <span data-ttu-id="9a94b-198">lub "Jaka właściwość jest kluczem podstawowym?"</span><span class="sxs-lookup"><span data-stu-id="9a94b-198">or "What property is the primary key?"</span></span> <span data-ttu-id="9a94b-199">Konwencje zwykle opierają się na nazwach konwencjonalnych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-199">Conventions are typically based on conventional names.</span></span> <span data-ttu-id="9a94b-200">Na przykład typowym dla klucza podstawowego jest właściwość kończąca się na `Id` .</span><span class="sxs-lookup"><span data-stu-id="9a94b-200">For example, it is typical for the primary key to be a property that ends with `Id`.</span></span>

<span data-ttu-id="9a94b-201">Zgodnie z Konwencją każda jednostka zostanie skonfigurowana do mapowania na tabelę o tej samej nazwie co `DbSet<TEntity>` Właściwość, która uwidacznia jednostkę w kontekście pochodnym.</span><span class="sxs-lookup"><span data-stu-id="9a94b-201">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="9a94b-202">Jeśli nie podano `DbSet<TEntity>` wartości dla danej jednostki, używana jest nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="9a94b-202">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="9a94b-203">Adnotacje danych a interfejs API Fluent</span><span class="sxs-lookup"><span data-stu-id="9a94b-203">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="9a94b-204">Istnieje wiele dodatkowych Konwencji EF Core i większość z nich można zmienić za pomocą adnotacji danych lub interfejsu API Fluent wdrożonych w ramach metody OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="9a94b-204">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="9a94b-205">Adnotacje danych muszą być używane w samych klasach modelu jednostki, co jest bardziej nieinwazyjne od drogi punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="9a94b-205">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="9a94b-206">Dzieje się tak dlatego, że jesteś w trakcie zanieczyszczania modelu za pomocą adnotacji danych związanych z bazą danych infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9a94b-206">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="9a94b-207">Z drugiej strony interfejs API Fluent jest wygodnym sposobem zmiany większości Konwencji i mapowań w warstwie infrastruktury trwałości danych, więc model jednostki będzie czysty i niezależny od infrastruktury trwałości.</span><span class="sxs-lookup"><span data-stu-id="9a94b-207">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="9a94b-208">Interfejs API Fluent i Metoda OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="9a94b-208">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="9a94b-209">Jak wspomniano, aby zmienić konwencje i mapowania, można użyć metody OnModelCreating w klasie DbContext.</span><span class="sxs-lookup"><span data-stu-id="9a94b-209">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="9a94b-210">Mikrousługa porządkowania w eShopOnContainers implementuje jawne mapowanie i konfigurację, w razie konieczności, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9a94b-210">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
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

<span data-ttu-id="9a94b-211">Można ustawić wszystkie mapowania interfejsu API Fluent w ramach tej samej `OnModelCreating` metody, ale zaleca się, aby podzielić ten kod i wiele klas konfiguracji, jeden na jednostkę, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9a94b-211">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="9a94b-212">Szczególnie w przypadku dużych modeli zaleca się posiadanie oddzielnych klas konfiguracji do konfigurowania różnych typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="9a94b-212">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="9a94b-213">Kod w przykładzie pokazuje kilka jawnych deklaracji i mapowania.</span><span class="sxs-lookup"><span data-stu-id="9a94b-213">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="9a94b-214">Jednakże konwencje EF Core automatycznie wykonują wiele mapowań, więc rzeczywisty kod, który będzie potrzebny w przypadku, może być mniejszy.</span><span class="sxs-lookup"><span data-stu-id="9a94b-214">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="9a94b-215">Algorytm Hi/Lo w EF Core</span><span class="sxs-lookup"><span data-stu-id="9a94b-215">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="9a94b-216">Interesujący aspekt kodu w poprzednim przykładzie polega na tym, że używa [algorytmu Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9a94b-216">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="9a94b-217">Algorytm Hi/Lo jest przydatny, gdy potrzebne są unikatowe klucze przed zatwierdzeniem zmian.</span><span class="sxs-lookup"><span data-stu-id="9a94b-217">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="9a94b-218">Podsumowując, algorytm Hi-Lo przypisuje unikatowe identyfikatory do wierszy tabeli, a nie w zależności od tego, czy wiersz jest natychmiast umieszczany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-218">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="9a94b-219">Dzięki temu można od razu zacząć korzystać z identyfikatorów, tak jak w przypadku zwykłych sekwencyjnych identyfikatorów baz danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-219">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="9a94b-220">Algorytm Hi/Lo opisuje mechanizm pobierania partii unikatowych identyfikatorów z powiązanej sekwencji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-220">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="9a94b-221">Te identyfikatory są bezpieczne, ponieważ baza danych gwarantuje unikatowość, dlatego nie będzie żadnych kolizji między użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="9a94b-221">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="9a94b-222">Ten algorytm jest interesujący z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="9a94b-222">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="9a94b-223">Nie powoduje zerwania wzorca jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="9a94b-223">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="9a94b-224">Uzyskuje identyfikatory sekwencji w partiach, aby zminimalizować liczbę rund do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a94b-224">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="9a94b-225">Generuje on czytelny dla człowieka identyfikator, w przeciwieństwie do technik, które używają identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="9a94b-225">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="9a94b-226">EF Core obsługuje [Hilo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) z `UseHiLo` metodą, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9a94b-226">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="9a94b-227">Mapuj pola zamiast właściwości</span><span class="sxs-lookup"><span data-stu-id="9a94b-227">Map fields instead of properties</span></span>

<span data-ttu-id="9a94b-228">Korzystając z tej funkcji, dostępnej od EF Core 1,1, można bezpośrednio mapować kolumny do pól.</span><span class="sxs-lookup"><span data-stu-id="9a94b-228">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="9a94b-229">Nie można używać właściwości w klasie Entity, a jedynie do mapowania kolumn z tabeli do pól.</span><span class="sxs-lookup"><span data-stu-id="9a94b-229">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="9a94b-230">Typowym zastosowaniem tego elementu byłyby pola prywatne dla dowolnego stanu wewnętrznego, do którego nie trzeba uzyskiwać dostępu poza jednostką.</span><span class="sxs-lookup"><span data-stu-id="9a94b-230">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="9a94b-231">Można to zrobić przy użyciu pojedynczych pól lub kolekcji, takich jak `List<>` pole.</span><span class="sxs-lookup"><span data-stu-id="9a94b-231">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="9a94b-232">Ten punkt został wymieniony wcześniej podczas omawiania modelowania klas modelu domeny, ale w tym miejscu można zobaczyć, jak to mapowanie jest wykonywane z `PropertyAccessMode.Field` konfiguracją wyróżnioną w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="9a94b-232">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="9a94b-233">Używanie właściwości cienia w EF Core, ukryte na poziomie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="9a94b-233">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="9a94b-234">Właściwości cienia w EF Core są właściwościami, które nie istnieją w modelu klasy jednostki.</span><span class="sxs-lookup"><span data-stu-id="9a94b-234">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="9a94b-235">Wartości i Stany tych właściwości są utrzymywane wyłącznie w klasie [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) na poziomie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9a94b-235">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="9a94b-236">Implementowanie wzorca specyfikacji zapytania</span><span class="sxs-lookup"><span data-stu-id="9a94b-236">Implement the Query Specification pattern</span></span>

<span data-ttu-id="9a94b-237">Zgodnie z opisem we wcześniejszej części projektu wzorzec specyfikacji zapytania jest oparty na domenie Wzorzec projektowy zaprojektowany jako miejsce, w którym można umieścić definicję zapytania z opcjonalną logiką sortowania i stronicowania.</span><span class="sxs-lookup"><span data-stu-id="9a94b-237">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="9a94b-238">Wzorzec specyfikacji zapytania definiuje zapytanie w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9a94b-238">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="9a94b-239">Na przykład w celu hermetyzacji zapytania stronicowanego, które wyszukuje niektóre produkty, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber, pageSize, Filter itp.).</span><span class="sxs-lookup"><span data-stu-id="9a94b-239">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="9a94b-240">Następnie w ramach dowolnej metody repozytorium (zazwyczaj Przeciążenie listy () przyjmuje IQuerySpecification i uruchamia oczekiwane zapytanie na podstawie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="9a94b-240">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="9a94b-241">Przykładem interfejsu specyfikacji ogólnej jest Poniższy kod z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="9a94b-241">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="9a94b-242">Następnie implementacja klasy podstawowej specyfikacji ogólnej jest następująca.</span><span class="sxs-lookup"><span data-stu-id="9a94b-242">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="9a94b-243">Poniższa specyfikacja ładuje jednostkę pojedynczego koszyka z IDENTYFIKATORem koszyka lub IDENTYFIKATORem nabywcy, do którego należy koszyk.</span><span class="sxs-lookup"><span data-stu-id="9a94b-243">The following specification loads a single basket entity given either the basket's ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="9a94b-244">Zostanie [eagerly załadowanie](/ef/core/querying/related-data) kolekcji koszyka `Items` .</span><span class="sxs-lookup"><span data-stu-id="9a94b-244">It will [eagerly load](/ef/core/querying/related-data) the basket's `Items` collection.</span></span>

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

<span data-ttu-id="9a94b-245">Na koniec można zobaczyć poniżej, jak ogólne repozytorium EF może użyć takiej specyfikacji do filtrowania i eager danych związanych z danym typem jednostki T.</span><span class="sxs-lookup"><span data-stu-id="9a94b-245">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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

<span data-ttu-id="9a94b-246">Oprócz hermetyzacji logiki filtrowania, Specyfikacja może określić kształt danych do zwrócenia, w tym właściwości do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="9a94b-246">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="9a94b-247">Chociaż nie zalecamy powrotu `IQueryable` z repozytorium, doskonale dobrze jest użyć ich w repozytorium, aby utworzyć zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="9a94b-247">Although we don't recommend returning `IQueryable` from a repository, it's perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="9a94b-248">To podejście można zobaczyć w powyższej metodzie list, która używa wyrażeń pośrednich w `IQueryable` celu utworzenia listy instrukcji include przed wykonaniem zapytania przy użyciu kryteriów specyfikacji w ostatnim wierszu.</span><span class="sxs-lookup"><span data-stu-id="9a94b-248">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query's list of includes before executing the query with the specification's criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9a94b-249">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9a94b-249">Additional resources</span></span>

- <span data-ttu-id="9a94b-250">**Mapowanie tabeli** </span><span class="sxs-lookup"><span data-stu-id="9a94b-250">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="9a94b-251">**Użyj HiLo, aby generować klucze z Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="9a94b-251">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="9a94b-252">**Pola zapasowe** </span><span class="sxs-lookup"><span data-stu-id="9a94b-252">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="9a94b-253">**Steve Smith. Hermetyzowane kolekcje w Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="9a94b-253">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="9a94b-254">**Właściwości cienia** </span><span class="sxs-lookup"><span data-stu-id="9a94b-254">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="9a94b-255">**Wzorzec specyfikacji** </span><span class="sxs-lookup"><span data-stu-id="9a94b-255">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="9a94b-256">[Poprzedni](infrastructure-persistence-layer-design.md) 
>  [Dalej](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="9a94b-256">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
