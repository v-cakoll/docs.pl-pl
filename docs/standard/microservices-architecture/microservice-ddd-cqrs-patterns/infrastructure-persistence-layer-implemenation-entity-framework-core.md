---
title: Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 6003252d7e87428c7f954b57c3b67a041e3f3b15
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106479"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="9fa04-103">Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9fa04-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="9fa04-104">Gdy używasz relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL zalecane podejście jest zaimplementowanie warstwę trwałości oparte na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="9fa04-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="9fa04-105">EF obsługuje LINQ i udostępnia silnie typizowanych obiektów dla modelu, jak również uproszczony trwałości do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="9fa04-106">Entity Framework zawiera długą historię w ramach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9fa04-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="9fa04-107">Gdy używasz .NET Core, należy też używać Entity Framework Core, w którym jest uruchomiona w systemie Windows lub Linux w taki sam sposób jak oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9fa04-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="9fa04-108">Podstawowe EF jest zakończenie ponownego zapisywania programu Entity Framework, implementowane za dużo mniejsze zużycie i istotne ulepszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="9fa04-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="9fa04-109">Wprowadzenie do programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9fa04-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="9fa04-110">Program Entity Framework (EF) Core to lekkie, rozszerzalny, i technologii dostępu do wersji i platform popularnych danych programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9fa04-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="9fa04-111">Został wprowadzony z platformą .NET Core w połowie 2016.</span><span class="sxs-lookup"><span data-stu-id="9fa04-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="9fa04-112">Wprowadzenie do podstawowych EF jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu udostępniamy łącza do tych informacji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9fa04-113">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9fa04-113">Additional resources</span></span>

-   <span data-ttu-id="9fa04-114">**Program Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="9fa04-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="9fa04-115">**Wprowadzenie do platformy ASP.NET Core oraz Entity Framework Core za pomocą programu Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="9fa04-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="9fa04-116">**Klasa DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="9fa04-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="9fa04-117">**Porównaj EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="9fa04-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="9fa04-118">Infrastruktura w Entity Framework Core z punktu widzenia DDD</span><span class="sxs-lookup"><span data-stu-id="9fa04-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="9fa04-119">Z punktu widzenia DDD, ważna możliwość EF jest możliwość korzystania z jednostki POCO domeny, nazywanego także w terminologii EF jako POCO *pierwszy kod jednostek*.</span><span class="sxs-lookup"><span data-stu-id="9fa04-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="9fa04-120">Jeśli używasz jednostki POCO domeny klasach modeli domeny są trwałości ignorujących, po [nieznajomości trwałości](http://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad.</span><span class="sxs-lookup"><span data-stu-id="9fa04-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="9fa04-121">Na wzorce DDD zalecaną zachowanie domeny i reguły w obrębie klasy jednostka, więc może kontrolować invariants, sprawdzanie poprawności i reguł podczas uzyskiwania dostępu do żadnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="9fa04-122">W związku z tym nie jest dobrym rozwiązaniem w DDD umożliwia publiczny dostęp do kolekcji podrzędnych obiektów lub obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="9fa04-123">Zamiast tego chcesz udostępnić metod, które kontrolują, jak i kiedy może być aktualizowana z pól i właściwości kolekcji, i jakie zachowanie i akcji powinien wystąpić, gdy tak się stanie.</span><span class="sxs-lookup"><span data-stu-id="9fa04-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="9fa04-124">Od wersji 1.1 Core EF aby spełnić te wymagania DDD mogą mieć zwykłych pól w jednostki zamiast właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="9fa04-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="9fa04-125">Jeśli nie chcesz, aby pole jednostki jako dostępne z zewnątrz, możesz utworzyć atrybutu lub pola zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="9fa04-126">Umożliwia także metody ustawiające właściwości prywatnej.</span><span class="sxs-lookup"><span data-stu-id="9fa04-126">You can also use private property setters.</span></span>

<span data-ttu-id="9fa04-127">W podobny sposób można masz teraz dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisanych jako `IReadOnlyCollection<T>`, która nie jest obsługiwana przez element pole prywatne dla kolekcji (takie jak `List<T>`) w jednostce korzystający EF trwałości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="9fa04-128">Poprzednie wersje programu Entity Framework wymaganych właściwości kolekcji do obsługi `ICollection<T>`, który oznaczało, że każdy Deweloper przy użyciu klasy nadrzędnej jednostki można dodać lub usunąć elementy za pomocą jego kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="9fa04-129">Możliwość ta będzie przed zalecane wzorce w DDD.</span><span class="sxs-lookup"><span data-stu-id="9fa04-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="9fa04-130">Można użyć kolekcji prywatnych podczas udostępnianie tylko do odczytu `IReadOnlyCollection<T>` obiektów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9fa04-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="9fa04-131">Należy pamiętać, że `OrderItems` właściwości są dostępne tylko jako tylko do odczytu za pomocą `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="9fa04-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="9fa04-132">Ten typ jest tylko do odczytu, więc jest chroniony przed regularne aktualizacje zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="9fa04-133">Podstawowe EF umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczających" modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9fa04-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="9fa04-134">Jest czysty .NET obiektów POCO kodu, ponieważ akcja mapowania jest zaimplementowana w warstwę trwałości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="9fa04-135">W tym mapowania akcji należy skonfigurować mapowanie pól w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="9fa04-136">W poniższym przykładzie metody OnModelCreating wyróżniony kod informuje Core EF dostępu do właściwości OrderItems za pomocą tego pola.</span><span class="sxs-lookup"><span data-stu-id="9fa04-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="9fa04-137">Użycie pola zamiast właściwości jednostki OrderItem jest trwały, tak jakby listy&lt;OrderItem&gt; właściwości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="9fa04-138">Jednak eksponuje jedną metodę dostępu `AddOrderItem` metoda dodawania nowych elementów do zlecenia.</span><span class="sxs-lookup"><span data-stu-id="9fa04-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="9fa04-139">W związku z tym zachowanie są ze sobą powiązane i dane będą spójne w całym kod źródłowy aplikacji, która używa modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9fa04-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="9fa04-140">Wdrażanie niestandardowe repozytoria z programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9fa04-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="9fa04-141">Na poziomie implementacji repozytorium jest po prostu klasy z kodem trwałości danych koordynowane przez jednostkę pracy (DBContext w podstawowej EF) podczas przeprowadzania aktualizacji, jak pokazano w następującej klasy:</span><span class="sxs-lookup"><span data-stu-id="9fa04-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="9fa04-142">Należy pamiętać, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9fa04-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="9fa04-143">Jednak implementacja repozytorium jest wykonywane na trwałość i warstwę infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9fa04-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="9fa04-144">EF DbContext jest dostarczany za pomocą konstruktora za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="9fa04-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="9fa04-145">Są one udostępniane między wielu repozytoriów w ramach tego samego zakresu żądania HTTP, dzięki użyciu jego istnienia domyślnego (ServiceLifetime.Scoped) w kontenerze IoC (które można również jawnie ustawić z usługami. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="9fa04-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="9fa04-146">Metody służące do implementacji w repozytorium (aktualizacje lub transakcji i zapytań)</span><span class="sxs-lookup"><span data-stu-id="9fa04-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="9fa04-147">W każdej klasie repozytorium należy umieścić metody trwałości, które zaktualizowany stan jednostek zawarty w jego powiązanych agregacji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="9fa04-148">Należy pamiętać, że istnieje relacja jeden do jednego między agregacji i jej powiązane repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9fa04-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="9fa04-149">Wziąć pod uwagę może mieć osadzonych obiektów podrzędnych w jego wykres EF do obiektu jednostki głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="9fa04-150">Na przykład kupujący może mieć wiele metod płatności jako jednostek podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="9fa04-151">Ponieważ metoda porządkowania mikrousługi w eShopOnContainers również jest oparty na CQS/CQRS, większość zapytań nie są zaimplementowane w niestandardowe repozytoria.</span><span class="sxs-lookup"><span data-stu-id="9fa04-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="9fa04-152">Deweloperzy mają swobodę tworzenia kwerend oraz sprzężenia, które są im potrzebne dla warstwy prezentacji bez ograniczeń narzuconych przez agregacje, niestandardowe repozytoria na agregacji i DDD ogólnie rzecz biorąc.</span><span class="sxs-lookup"><span data-stu-id="9fa04-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="9fa04-153">Większość niestandardowe repozytoria sugerowane w tym przewodniku ma kilka aktualizacji lub metody transakcyjnych, ale tylko metody zapytania wymagany do pobierania danych do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="9fa04-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="9fa04-154">Na przykład repozytorium BuyerRepository implementuje metodę metoda FindAsync, ponieważ aplikacja musi wiedzieć, czy konkretnego nabywcy istnieje przed utworzeniem nowego kupujący związane z kolejności.</span><span class="sxs-lookup"><span data-stu-id="9fa04-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="9fa04-155">Jednak metody rzeczywiste zapytanie w celu uzyskania danych, aby wysyłać do aplikacji klienta lub warstwy prezentacji są implementowane, jak wspomniano w zapytaniach CQRS opartych na kwerendach elastyczne przy użyciu Dapper.</span><span class="sxs-lookup"><span data-stu-id="9fa04-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="9fa04-156">Przy użyciu niestandardowego repozytorium w porównaniu z użyciem EF DbContext bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="9fa04-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="9fa04-157">Klasy Entity Framework DbContext bazuje na wzorce jednostki pracy i repozytorium i może służyć bezpośrednio w kodzie, takich jak z kontrolera ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="9fa04-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="9fa04-158">Oznacza to sposób można utworzyć najprostszym kod, tak jak mikrousługi katalogu CRUD w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9fa04-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="9fa04-159">W przypadkach, w miejscu kodu najprostsza możliwa można bezpośrednio używać klasy DbContext, jak wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="9fa04-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="9fa04-160">Jednak implementacja niestandardowe repozytoria zapewnia kilka korzyści, realizując bardziej złożonych mikrousług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="9fa04-161">Wzorce jednostki pracy i repozytorium mają Hermetyzowanie warstwę trwałości infrastruktury, więc jego jest całkowicie niezależna od aplikacji i warstwy modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9fa04-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="9fa04-162">Wdrażanie tych wzorców ułatwia użycie zasymulować repozytoria symulując dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="9fa04-163">W rysunku 9-18 lub przy użyciu magazynów, które ułatwiają mock tych repozytoria widać różnice między nie używa repozytoriów (bezpośrednio przy użyciu EF DbContext).</span><span class="sxs-lookup"><span data-stu-id="9fa04-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="9fa04-164">**Rysunek 9-18**.</span><span class="sxs-lookup"><span data-stu-id="9fa04-164">**Figure 9-18**.</span></span> <span data-ttu-id="9fa04-165">Przy użyciu niestandardowe repozytoria i zwykły DbContext</span><span class="sxs-lookup"><span data-stu-id="9fa04-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="9fa04-166">Istnieje wiele alternatyw podczas mocking.</span><span class="sxs-lookup"><span data-stu-id="9fa04-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="9fa04-167">Można mock tylko repozytoria lub można mock całą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="9fa04-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="9fa04-168">Zwykle mocking tylko repozytoria jest wystarczająca, i złożoności abstract i mock całej jednostki pracy nie jest zwykle konieczna.</span><span class="sxs-lookup"><span data-stu-id="9fa04-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="9fa04-169">Później gdy możemy skupić się na warstwie aplikacji, zobaczysz działanie iniekcji zależności w ASP.NET Core i jak jest implementowane, gdy przy użyciu repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="9fa04-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="9fa04-170">Krótko mówiąc niestandardowe repozytoria pozwalają na łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie ma wpływ na stan warstwy danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="9fa04-171">Po uruchomieniu testów, które również dostęp do rzeczywistej bazy danych za pośrednictwem programu Entity Framework nie są one testy jednostek, ale integracji testy, które są znacznie wolniejsze.</span><span class="sxs-lookup"><span data-stu-id="9fa04-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="9fa04-172">Jeśli były używane DbContext bezpośrednio, tylko wybrane trzeba byłoby do uruchamiania testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalną danych dla testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="9fa04-173">Nie będzie można kontrolować zasymulować obiektów i fałszywych danych w taki sam sposób na poziomie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9fa04-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="9fa04-174">Oczywiście należy zawsze przetestować kontrolerów MVC.</span><span class="sxs-lookup"><span data-stu-id="9fa04-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="9fa04-175">EF DbContext i IUnitOfWork okres istnienia wystąpienia w Twojej kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="9fa04-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="9fa04-176">Obiekt DbContext (widoczne jako obiekt IUnitOfWork) może być konieczne być współużytkowane przez wielu repozytoriów w ramach tego samego zakresu żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="9fa04-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="9fa04-177">Na przykład dotyczy to podczas wykonywania operacji musi uwzględniać wiele wartości zagregowanych lub po prostu ponieważ używasz wielu wystąpień repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9fa04-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="9fa04-178">Należy również podać, czy interfejs IUnitOfWork jest częścią warstwą domeny, nie EF podstawowego typu.</span><span class="sxs-lookup"><span data-stu-id="9fa04-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="9fa04-179">Aby to zrobić, wystąpienie obiektu DbContext musi mieć ustawioną wartość ServiceLifetime.Scoped jego okres istnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="9fa04-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="9fa04-180">Jest to domyślny okres istnienia podczas rejestrowania obiektu DbContext z usług. AddDbContext w Twojej kontenera IoC z metody ConfigureServices pliku Startup.cs w projekcie interfejsu API platformy ASP.NET Core sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9fa04-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="9fa04-181">Ilustruje to poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="9fa04-181">The following code illustrates this.</span></span>

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

<span data-ttu-id="9fa04-182">Tryb tworzenia wystąpienia typu DbContext nie powinna być skonfigurowana jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="9fa04-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="9fa04-183">Okres istnienia wystąpienia repozytorium w Twojej kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="9fa04-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="9fa04-184">W podobny sposób okres istnienia z repozytorium zwykle powinna być ustawiona jako zakresami (InstancePerLifetimeScope w Autofac).</span><span class="sxs-lookup"><span data-stu-id="9fa04-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="9fa04-185">Może to również być przejściowy (InstancePerDependency w Autofac), ale z usługą będzie bardziej efektywne w odniesieniu do pamięci, korzystając z zakresami okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="9fa04-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="9fa04-186">Należy pamiętać, że przy użyciu okresu istnienia singleton dla repozytorium może spowodować poważne współbieżności problemów po Twoje DbContext ma ustawioną wartość zakresu istnienia (InstancePerLifetimeScope) (domyślnych okresów istnienia dla obiektu DBContext).</span><span class="sxs-lookup"><span data-stu-id="9fa04-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9fa04-187">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9fa04-187">Additional resources</span></span>

-   <span data-ttu-id="9fa04-188">**Implementowanie repozytorium i jednostki pracy w aplikacji platformy ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="9fa04-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="9fa04-189">**Jonathanowi Allen. Strategie implementacji wzorca repozytorium Entity Framework, Dapper i łańcuch**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="9fa04-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="9fa04-190">**Torre de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="9fa04-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="9fa04-191">Mapowania tabeli</span><span class="sxs-lookup"><span data-stu-id="9fa04-191">Table mapping</span></span>

<span data-ttu-id="9fa04-192">Mapowania tabeli identyfikuje danych można wykonać zapytania z tabeli i zapisane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="9fa04-193">Wcześniej przedstawiono sposób jednostek domeny (na przykład domena produktu lub kolejność) może służyć do generowania schematu bazy danych powiązanych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="9fa04-194">EF silnie zaprojektowano z myślą *konwencje*.</span><span class="sxs-lookup"><span data-stu-id="9fa04-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="9fa04-195">Konwencje pytania, takich jak "Co nazwy tabeli zostanie?"</span><span class="sxs-lookup"><span data-stu-id="9fa04-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="9fa04-196">lub "jaką właściwość jest kluczem podstawowym"?</span><span class="sxs-lookup"><span data-stu-id="9fa04-196">or “What property is the primary key?”</span></span> <span data-ttu-id="9fa04-197">Konwencje są zwykle oparte na nazwy z konwencjonalnej — na przykład jest typowa dla klucza podstawowego właściwość, która kończy się identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="9fa04-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="9fa04-198">Według Konwencji, będzie można skonfigurować każdej jednostki do mapowania do tabeli o takiej samej nazwie jak DbSet&lt;TEntity&gt; właściwość, która przedstawia jednostek w kontekście pochodnych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="9fa04-199">Jeśli nie DbSet&lt;TEntity&gt; wartość została podana dla danej jednostki, jest używana nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="9fa04-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="9fa04-200">Adnotacje danych w porównaniu z interfejsu API Fluent</span><span class="sxs-lookup"><span data-stu-id="9fa04-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="9fa04-201">Istnieje wiele dodatkowych konwencje EF Core, a większość z nich można zmienić za pomocą interfejsu API Fluent, zaimplementowana wewnątrz metody OnModelCreating lub adnotacji danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="9fa04-202">Adnotacje danych musi być używany w klasy modelu jednostki, która jest bardziej natrętnych sposób z punktu widzenia DDD.</span><span class="sxs-lookup"><span data-stu-id="9fa04-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="9fa04-203">Jest to spowodowane są zanieczyszczających modelu przy użyciu adnotacji danych związanych z infrastrukturą bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="9fa04-204">Z drugiej strony interfejsu API Fluent to wygodny sposób zmienić większość konwencje i mapowania w ramach Twojej infrastruktury warstwę trwałości danych, więc modelu jednostki jest czysty i rozdzielonymi od infrastruktury trwałości.</span><span class="sxs-lookup"><span data-stu-id="9fa04-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="9fa04-205">Interfejsu API Fluent i metody OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="9fa04-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="9fa04-206">Jak wspomniano, aby można było zmienić konwencje i mapowania, służy metody OnModelCreating klasy DbContext.</span><span class="sxs-lookup"><span data-stu-id="9fa04-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="9fa04-207">Porządkowania mikrousługi w eShopOnContainers implementuje jawnego mapowania konfiguracji i, w razie potrzeby, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9fa04-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
            
            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

<span data-ttu-id="9fa04-208">Można ustawić mapowania interfejsu API Fluent w ramach tej samej metody OnModelCreating, ale zaleca się partycje kodu i mieć wielu klas konfiguracji, po jednym dla każdego obiektu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9fa04-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="9fa04-209">Szczególnie w przypadku modeli szczególnie duże jest posiadanie osobną konfiguracją klasy do konfigurowania typów jednostek inny.</span><span class="sxs-lookup"><span data-stu-id="9fa04-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="9fa04-210">Kod w tym przykładzie przedstawiono kilka jawne deklaracje i mapowania.</span><span class="sxs-lookup"><span data-stu-id="9fa04-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="9fa04-211">Konwencje EF Core jednak wiele z tych mapowania automatycznie, więc rzeczywisty kod, który będzie potrzebny w Twoim przypadku może być mniejszy.</span><span class="sxs-lookup"><span data-stu-id="9fa04-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="9fa04-212">Algorytm Hi/Lo EF główną</span><span class="sxs-lookup"><span data-stu-id="9fa04-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="9fa04-213">Interesujących aspektów kodu w poprzednim przykładzie jest, że używa [algorytm Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9fa04-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="9fa04-214">Algorytm Hi/Lo jest przydatne, gdy potrzebne są klucze unikatowe.</span><span class="sxs-lookup"><span data-stu-id="9fa04-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="9fa04-215">Jako podsumowanie algorytm Hi-Lo przypisuje unikatowe identyfikatory wierszy tabeli a nie w zależności od natychmiast przechowywania wiersza w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="9fa04-216">Dzięki temu można Rozpocznij od razu, za pomocą identyfikatorów, jak się dzieje z bazą danych sekwencyjnych regularne identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="9fa04-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="9fa04-217">Algorytm Hi/Lo opisuje mechanizm służący do generowania identyfikatorów bezpieczne po stronie klienta, a nie w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9fa04-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="9fa04-218">*Bezpieczne* w tym kontekście oznacza bez kolizji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="9fa04-219">Ten algorytm jest ciekawe tych powodów:</span><span class="sxs-lookup"><span data-stu-id="9fa04-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="9fa04-220">Nie powodować utraty wzorzec jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="9fa04-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="9fa04-221">Nie wymaga się, że rund generatory sekwencji sposób jak w innych systemach DBMS.</span><span class="sxs-lookup"><span data-stu-id="9fa04-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="9fa04-222">Generuje on człowieka identyfikator do odczytu, w odróżnieniu od techniki, które używają identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="9fa04-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="9fa04-223">Jądro EF obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) przy użyciu metody ForSqlServerUseSequenceHiLo, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9fa04-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="9fa04-224">Mapowanie pól zamiast właściwości</span><span class="sxs-lookup"><span data-stu-id="9fa04-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="9fa04-225">Przy użyciu tej funkcji dostępne od wersji 1.1 Core EF, możesz bezpośrednio mapować kolumn do pól.</span><span class="sxs-lookup"><span data-stu-id="9fa04-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="9fa04-226">Istnieje możliwość, aby nie używać właściwości w klasie jednostki i tylko w celu mapowania kolumn z tabeli do pola.</span><span class="sxs-lookup"><span data-stu-id="9fa04-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="9fa04-227">Użycia który będą pól prywatnych dla stanów wewnętrznych, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="9fa04-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="9fa04-228">Można to zrobić z jednego pola lub kolekcji, takie jak `List<>` pola.</span><span class="sxs-lookup"><span data-stu-id="9fa04-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="9fa04-229">Ten punkt wspomniano wcześniej Rozmawialiśmy modelowania klasy modelu domeny, ale tutaj można zobaczyć, jak mapowania jest wykonywane z `PropertyAccessMode.Field` konfiguracji wyróżnione poprzedni kod.</span><span class="sxs-lookup"><span data-stu-id="9fa04-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="9fa04-230">Za pomocą właściwości cienia w podstawowej EF ukryte na poziomie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="9fa04-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="9fa04-231">Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki.</span><span class="sxs-lookup"><span data-stu-id="9fa04-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="9fa04-232">Wartości i stanów te właściwości, które są obsługiwane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9fa04-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="9fa04-233">Implementacja wzorca specyfikacji</span><span class="sxs-lookup"><span data-stu-id="9fa04-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="9fa04-234">Jak wprowadzone wcześniej w sekcji projektu, wzorzec specyfikacji (pełną nazwę byłoby wzorzec specyfikacji zapytania) jest wzorca projektowego Domain-Driven zaprojektowany jako miejsce, w którym można umieścić definicji zapytania opcjonalne, sortowanie i stronicowanie logiki.</span><span class="sxs-lookup"><span data-stu-id="9fa04-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="9fa04-235">Wzorzec specyfikacja definiuje kwerendę w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9fa04-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="9fa04-236">Na przykład aby hermetyzować stronicowane zapytanie, które wyszukuje niektórych produktów, można utworzyć specyfikację PagedProduct, która pobiera niezbędne parametry wejściowe (pageNumber pageSize, filtr, itp.).</span><span class="sxs-lookup"><span data-stu-id="9fa04-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="9fa04-237">Następnie metoda z repozytorium (zazwyczaj przeciążenia List()) Zaakceptuj ISpecification i uruchom zapytanie oczekiwanych na podstawie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa04-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="9fa04-238">Przykładowy ogólny interfejs specyfikacji jest następujący kod z [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="9fa04-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

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

<span data-ttu-id="9fa04-239">Następnie implementacji klasy podstawowej specyfikacji ogólnego jest poniżej.</span><span class="sxs-lookup"><span data-stu-id="9fa04-239">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="9fa04-240">Następującą specyfikację ładuje podmiot koszyka pojedynczy identyfikator koszyka lub identyfikator nabywców, do którego należy koszyka.</span><span class="sxs-lookup"><span data-stu-id="9fa04-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="9fa04-241">Będzie on [wczesny obciążenia](https://docs.microsoft.com/en-us/ef/core/querying/related-data) koszyka kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="9fa04-241">It will [eager load](https://docs.microsoft.com/en-us/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="9fa04-242">A na koniec są wyświetlane poniżej ogólnego repozytorium EF służy specyfikacja filtru i obciążenia eager danych związanych z typem danej jednostki T.</span><span class="sxs-lookup"><span data-stu-id="9fa04-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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
<span data-ttu-id="9fa04-243">Oprócz hermetyzując logiki filtrowania, specyfikację można określić kształtu danych ma zostać zwrócona, łącznie z właściwości, które można wypełnić.</span><span class="sxs-lookup"><span data-stu-id="9fa04-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="9fa04-244">Mimo że firma Microsoft nie jest zalecane, aby zwracać IQueryable z repozytorium, jest doskonale poprawnie z nich korzystać w repozytorium w celu zbudowania zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="9fa04-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="9fa04-245">Takie podejście używany na liście zawiera metodę powyżej, która używa wyrażenia IQueryable pośredniego stworzenie listy kwerendy przed wykonaniem kwerendy z kryteriami specyfikacji w ostatnim wierszu jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="9fa04-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="9fa04-246">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9fa04-246">Additional resources</span></span>

-   <span data-ttu-id="9fa04-247">**Mapowania tabeli**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="9fa04-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="9fa04-248">**Generuj klucze z programu Entity Framework Core za pomocą HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="9fa04-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="9fa04-249">**Pola zapasowego**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="9fa04-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="9fa04-250">**Steve Smith. Hermetyzowany kolekcje w programie Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="9fa04-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="9fa04-251">**Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="9fa04-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="9fa04-252">**Wzorzec specyfikacji**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="9fa04-252">**The Specification pattern**
[*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="9fa04-253">[Poprzednie](infrastructure-persistence-layer-design.md)
[dalej](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="9fa04-253">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
