---
title: Implementowanie warstwy trwałości infrastruktury za pomocą platformy Entity Framework Core
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie warstwy trwałości infrastruktury za pomocą platformy Entity Framework Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 663515e0a863ef703006df0f96b4bc8a2976ca78
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205298"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="77cda-103">Implementowanie warstwy trwałości infrastruktury za pomocą platformy Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="77cda-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="77cda-104">Korzystając z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, zalecanym podejściem jest implementowanie warstwy trwałości, oparte na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="77cda-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="77cda-105">EF obsługuje LINQ i udostępnia silnie typizowanych obiektów dla modelu, jak również uproszczone trwałości do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="77cda-106">Entity Framework od dawna jako część programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77cda-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="77cda-107">Korzystając z platformy .NET Core, możesz także użyć platformy Entity Framework Core, która działa w systemie Windows lub Linux w taki sam sposób jak .NET Core.</span><span class="sxs-lookup"><span data-stu-id="77cda-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="77cda-108">EF Core jest pełne ponowne zapisywanie adresów platformy Entity Framework implementowane za pomocą znacznie mniejszych rozmiarów i istotne ulepszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="77cda-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="77cda-109">Wprowadzenie do platformy Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="77cda-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="77cda-110">Entity Framework (EF) Core to lekkie, rozszerzalne, i technologii dostępu do popularnych danych Entity Framework w wersji dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="77cda-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="77cda-111">Został wprowadzony przy użyciu platformy .NET Core w połowie 2016.</span><span class="sxs-lookup"><span data-stu-id="77cda-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="77cda-112">Wprowadzenie do programu EF Core jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu udostępniamy łącza do tych informacji.</span><span class="sxs-lookup"><span data-stu-id="77cda-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="77cda-113">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="77cda-113">Additional resources</span></span>

-   <span data-ttu-id="77cda-114">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="77cda-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="77cda-115">**Wprowadzenie do platformy ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="77cda-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="77cda-116">**Klasy DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="77cda-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="77cda-117">**Porównanie programów EF Core i EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="77cda-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="77cda-118">Z punktu widzenia DDD infrastruktury platformy Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="77cda-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="77cda-119">Z punktu widzenia DDD, to ważny czynnik EF jest możliwość korzystania z jednostki domeny POCO, zwane w terminologii programu EF jako POCO *najpierw kod jednostki*.</span><span class="sxs-lookup"><span data-stu-id="77cda-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="77cda-120">Jeśli używasz jednostki domeny POCO, klasach modeli domeny są trwałości zakresu, zgodnie z [nieznajomości trwałości](https://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad.</span><span class="sxs-lookup"><span data-stu-id="77cda-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="77cda-121">Na wzorców DDD powinna hermetyzować zachowanie domeny i reguł w klasie jednostki, dzięki czemu podczas uzyskiwania dostępu do żadnej kolekcji może kontrolować invariants, sprawdzanie poprawności i reguł.</span><span class="sxs-lookup"><span data-stu-id="77cda-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="77cda-122">W związku z tym nie jest dobrym rozwiązaniem DDD, aby zezwolić na publiczny dostęp do kolekcji podrzędnej obiektów lub obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="77cda-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="77cda-123">Zamiast tego chcesz udostępnić, metody, które kontrolują, jak i kiedy Twoja pola i kolekcje właściwości mogą być aktualizowane, i jakie zachowanie i akcji powinny być wykonywane, kiedy tak się stanie.</span><span class="sxs-lookup"><span data-stu-id="77cda-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="77cda-124">Od programu EF Core 1.1 spełnienie tych wymagań DDD może mieć zwykły pól w jednostkach zamiast właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="77cda-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="77cda-125">Jeśli nie mają być dostępne z zewnątrz pole jednostki, po prostu utworzyć atrybutu lub pola zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="77cda-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="77cda-126">Można również użyć metod ustawiających właściwości prywatnej.</span><span class="sxs-lookup"><span data-stu-id="77cda-126">You can also use private property setters.</span></span>

<span data-ttu-id="77cda-127">W podobny sposób można teraz masz dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisanych w formie `IReadOnlyCollection<T>`, która jest wspierana przez członka pole prywatne dla kolekcji (np. `List<T>`) w jednostce, która opiera się na EF na potrzeby stanu trwałego.</span><span class="sxs-lookup"><span data-stu-id="77cda-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="77cda-128">Poprzednie wersje programu Entity Framework wymaganych właściwości kolekcji do obsługi `ICollection<T>`, która rozumie, Każdy deweloper może przy użyciu klasy nadrzędnej jednostki można dodać lub usunąć elementy za pomocą jego właściwości kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77cda-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="77cda-129">Tę możliwość byłoby względem zalecane wzorce w DDD.</span><span class="sxs-lookup"><span data-stu-id="77cda-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="77cda-130">Możesz użyć prywatnego kolekcji przedstawiania tylko do odczytu `IReadOnlyCollection<T>` obiektu, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="77cda-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="77cda-131">Należy pamiętać, że `OrderItems` właściwość może zostać oceniony jedynie jako tylko do odczytu przy użyciu `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="77cda-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="77cda-132">Ten typ jest tylko do odczytu, więc jest chroniony przed regularne aktualizacje zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="77cda-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="77cda-133">EF Core umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczenia" model domeny.</span><span class="sxs-lookup"><span data-stu-id="77cda-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="77cda-134">Jest czysty .NET obiektów POCO kodu, ponieważ akcji mapowanie jest zaimplementowana w warstwy trwałości.</span><span class="sxs-lookup"><span data-stu-id="77cda-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="77cda-135">W tym działaniu mapowania należy skonfigurować mapowanie pól w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="77cda-136">W poniższym przykładzie metoda OnModelCreating wyróżniony kod informuje programu EF Core dostęp do właściwości OrderItems za pośrednictwem jej pola.</span><span class="sxs-lookup"><span data-stu-id="77cda-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="77cda-137">Używając pola zamiast właściwości jednostki OrderItem są utrwalane tylko tak, jakby był listy&lt;OrderItem&gt; właściwości.</span><span class="sxs-lookup"><span data-stu-id="77cda-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="77cda-138">Jednak udostępnia ona pojedynczy akcesora `AddOrderItem` metody dodawania nowych elementów do zamówienia.</span><span class="sxs-lookup"><span data-stu-id="77cda-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="77cda-139">W rezultacie zachowanie i dane są ze sobą powiązane i będzie spójny we kod źródłowy aplikacji, która używa modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="77cda-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="77cda-140">Implementowanie niestandardowego repozytoriów za pomocą platformy Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="77cda-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="77cda-141">Na poziomie implementacji repozytorium jest po prostu klasy z kodem stanu trwałego danych koordynowane przez jednostka pracy (typu DBContext w programie EF Core) podczas przeprowadzania aktualizacji, jak pokazano na następującej klasy:</span><span class="sxs-lookup"><span data-stu-id="77cda-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="77cda-142">Należy pamiętać, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako umowę.</span><span class="sxs-lookup"><span data-stu-id="77cda-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="77cda-143">Jednak implementacja repozytorium odbywa się na trwałość i warstwy infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="77cda-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="77cda-144">Kontekst DbContext EF jest dostarczany za pośrednictwem konstruktora przy użyciu iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="77cda-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="77cda-145">Jest udostępniana między wieloma repozytoriami w obrębie tego samego zakresu żądania HTTP, dzięki jego istnienia domyślne (ServiceLifetime.Scoped) w kontenerze IoC (która może też być jawnie ustawione przy użyciu usługi. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="77cda-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="77cda-146">Metody służące do implementacji w repozytorium (aktualizacje lub transakcje w stosunku do zapytania)</span><span class="sxs-lookup"><span data-stu-id="77cda-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="77cda-147">W każdej klasie repozytorium należy umieszczać metod trwałości, które aktualizują stan jednostki zawarty w jego powiązane agregacji.</span><span class="sxs-lookup"><span data-stu-id="77cda-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="77cda-148">Należy pamiętać, że istnieje bezpośredni związek pomiędzy agregacji i jego powiązanym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="77cda-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="77cda-149">Weź pod uwagę może zostały osadzone jednostki podrzędne w ramach jego EF wykres obiektu jednostki głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="77cda-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="77cda-150">Na przykład kupujący może mieć wiele metod płatności jako jednostki podrzędne powiązane.</span><span class="sxs-lookup"><span data-stu-id="77cda-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="77cda-151">Ponieważ podejście do szeregowania mikrousługi w ramach aplikacji eShopOnContainers również opiera się na CQS/CQRS, większość zapytań nie są implementowane w repozytoriach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="77cda-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="77cda-152">Deweloperzy mają możliwość tworzenia kwerend i sprzężeń, które są im potrzebne dla warstwy prezentacji bez ograniczeń nałożonych przez agregacje, niestandardowe repozytoriów na agregację i DDD ogólnie rzecz biorąc.</span><span class="sxs-lookup"><span data-stu-id="77cda-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="77cda-153">Większość repozytoriów niestandardowych, zaproponowana przez ten przewodnik ma kilka aktualizacji lub transakcyjnych metody, ale po prostu metody zapytań, konieczne zaktualizowanie danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="77cda-154">Na przykład repozytorium BuyerRepository implementuje metodę metoda findasync dla, ponieważ aplikacja musi wiedzieć, czy konkretnego nabywcy istnieje przed utworzeniem nowego kupujący związanych z zamówieniem.</span><span class="sxs-lookup"><span data-stu-id="77cda-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="77cda-155">Jednak metody rzeczywiste zapytanie w celu uzyskania danych, aby wysyłać do aplikacji klienta lub warstwy prezentacji są implementowane, jak wspomniano w zapytaniach CQRS opartych na kwerendach elastyczne korzystanie z programem Dapper.</span><span class="sxs-lookup"><span data-stu-id="77cda-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="77cda-156">Przy użyciu niestandardowych repozytorium, w przeciwieństwie do użycia bezpośrednio EF DbContext</span><span class="sxs-lookup"><span data-stu-id="77cda-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="77cda-157">Klasy Entity Framework DbContext opiera się na jednostce pracy i repozytorium wzorce i może służyć bezpośrednio w kodzie, takich jak z kontroler składnika ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="77cda-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="77cda-158">Oznacza to sposób możesz utworzyć najprostszą kodu, tak jak mikrousługi CRUD katalogu, w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="77cda-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="77cda-159">W przypadkach, w miejscu kodu najprostsza możliwa można bezpośrednio korzystać z wystąpień klasy DbContext, jak wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="77cda-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="77cda-160">Jednak implementacja niestandardowego repozytoriów zapewnia kilka korzyści, podczas wykonywania bardziej złożonych z mikrousług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77cda-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="77cda-161">Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, dzięki czemu jej jest całkowicie niezależny od aplikacji i warstwy modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="77cda-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="77cda-162">Implementacji tych wzorców może ułatwić użytkowania makiety repozytoriów, symulując dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="77cda-163">W rysunek 9-18 możesz zobaczyć różnice nie przy użyciu repozytoriów (bezpośrednio przy użyciu typu DbContext EF) w porównaniu z użyciem repozytoria, które ułatwiają testowanie tych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="77cda-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="77cda-164">**Rysunek 9-18**.</span><span class="sxs-lookup"><span data-stu-id="77cda-164">**Figure 9-18**.</span></span> <span data-ttu-id="77cda-165">Przy użyciu niestandardowych repozytoriów i zwykłego typu DbContext</span><span class="sxs-lookup"><span data-stu-id="77cda-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="77cda-166">Gdy pozorowanie istnieje wiele alternatyw.</span><span class="sxs-lookup"><span data-stu-id="77cda-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="77cda-167">Można testowanie po prostu repozytoriów lub można testowanie całej jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="77cda-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="77cda-168">Zazwyczaj pozorowanie po prostu repozytoriów jest wystarczająca, i złożoności abstrakcyjnej i testowanie całej jednostki pracy nie jest zwykle konieczna.</span><span class="sxs-lookup"><span data-stu-id="77cda-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="77cda-169">Później gdy skupimy się na warstwie aplikacji, zobaczysz działania wstrzykiwanie zależności w programie ASP.NET Core i jak jest implementowane, gdy przy użyciu repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="77cda-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="77cda-170">Krótko mówiąc niestandardowe repozytoria pozwalają na łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie mają wpływ stan warstwy danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="77cda-171">Jeśli uruchamiasz testy, które również dostęp do rzeczywistej bazy danych za pomocą programu Entity Framework, nie są one testy jednostkowe, ale testy integracji, które są znacznie wolniejsze.</span><span class="sxs-lookup"><span data-stu-id="77cda-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="77cda-172">Jeśli kontekst DbContext była używana bezpośrednio, tylko wybranego typu trzeba byłoby Uruchamianie testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalną danych dla testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="77cda-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="77cda-173">Nie będzie można kontrolować makiety obiekty i dane fikcyjne w taki sam sposób na poziomie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="77cda-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="77cda-174">Oczywiście należy zawsze przetestować kontrolerów MVC.</span><span class="sxs-lookup"><span data-stu-id="77cda-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="77cda-175">Kontekst DbContext EF i IUnitOfWork okres istnienia wystąpienia w kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="77cda-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="77cda-176">Obiekt typu DbContext (udostępniane jako obiekt IUnitOfWork) może być konieczne być współużytkowane przez wiele repozytoriów w obrębie tego samego zakresu żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="77cda-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="77cda-177">Na przykład, jest to wartość true, gdy podczas wykonywania operacji muszą zajmować się przy użyciu wielu agregacje lub po prostu ponieważ korzysta z wielu wystąpień repozytorium.</span><span class="sxs-lookup"><span data-stu-id="77cda-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="77cda-178">Jest również ważne, aby wspomnieć, że interfejs IUnitOfWork stanowi część warstwy usługi domeny, a nie typu programu EF Core.</span><span class="sxs-lookup"><span data-stu-id="77cda-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="77cda-179">Aby to zrobić, wystąpienie obiektu DbContext musi mieć wartość ServiceLifetime.Scoped jego okres istnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="77cda-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="77cda-180">Jest to domyślny okres istnienia, podczas rejestrowania DbContext z usług. AddDbContext w kontenerze IoC z metody ConfigureServices pliku Startup.cs w projekcie internetowego interfejsu API platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="77cda-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="77cda-181">Ilustruje to poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="77cda-181">The following code illustrates this.</span></span>

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

<span data-ttu-id="77cda-182">Tryb tworzenia wystąpienia typu DbContext nie powinien być skonfigurowany jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="77cda-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="77cda-183">Okres istnienia wystąpienia repozytorium w kontenerze IoC</span><span class="sxs-lookup"><span data-stu-id="77cda-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="77cda-184">W podobny sposób okres istnienia repozytorium zwykle należy ustawić jako zakresie (InstancePerLifetimeScope w Autofac).</span><span class="sxs-lookup"><span data-stu-id="77cda-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="77cda-185">Może być również przejściowy (InstancePerDependency w Autofac), ale usługa będzie bardziej wydajne w odniesieniu do pamięci, korzystając z zakresami okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="77cda-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="77cda-186">Należy zauważyć, że przy użyciu okres istnienia pojedyncze repozytorium, może spowodować poważne współbieżności problemy po Twojej DbContext jest ustawiona na ograniczony okres istnienia (InstancePerLifetimeScope) (okresy domyślnego typu DBContext).</span><span class="sxs-lookup"><span data-stu-id="77cda-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="77cda-187">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="77cda-187">Additional resources</span></span>

-   <span data-ttu-id="77cda-188">**Wdrażanie z repozytorium i jednostki pracy w aplikacji ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="77cda-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="77cda-189">**Jonathan Allen. Strategie implementacji wzorca repozytorium z platformą Entity Framework, programem Dapper i łańcuch**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="77cda-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="77cda-190">**Torre'a de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="77cda-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="77cda-191">Mapowanie tabeli</span><span class="sxs-lookup"><span data-stu-id="77cda-191">Table mapping</span></span>

<span data-ttu-id="77cda-192">Mapowanie tabeli identyfikuje dane tabeli, aby być odpytywane i zapisane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="77cda-193">Wcześniej pokazano, jak jednostki domeny (na przykład domena produktu lub zamówienia) może służyć do generowania schematu powiązanej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="77cda-194">EF silnie zaprojektowany pod kątem koncepcji *konwencje*.</span><span class="sxs-lookup"><span data-stu-id="77cda-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="77cda-195">Konwencje adresów pytania "Co nazwy tabeli zostanie?"</span><span class="sxs-lookup"><span data-stu-id="77cda-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="77cda-196">lub "jakie właściwości klucza podstawowego?"</span><span class="sxs-lookup"><span data-stu-id="77cda-196">or “What property is the primary key?”</span></span> <span data-ttu-id="77cda-197">Konwencje są zazwyczaj na podstawie konwencjonalne nazw — na przykład jest typowe dla klucza podstawowego, jako właściwość, która kończy się za pomocą identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="77cda-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="77cda-198">Zgodnie z Konwencją każdej jednostki będą konfigurowane tak, aby zamapować na tabelę z taką samą nazwę jak DbSet&lt;TEntity&gt; właściwość, która udostępnia jednostki w kontekście pochodnych.</span><span class="sxs-lookup"><span data-stu-id="77cda-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="77cda-199">Jeśli nie DbSet&lt;TEntity&gt; wartość zostanie podana dla danej jednostki, nazwa klasy jest używana.</span><span class="sxs-lookup"><span data-stu-id="77cda-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="77cda-200">Adnotacje danych w porównaniu z interfejsu API Fluent</span><span class="sxs-lookup"><span data-stu-id="77cda-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="77cda-201">Istnieje wiele dodatkowych konwencje programu EF Core, a większość z nich można zmienić przy użyciu adnotacji danych lub interfejsu API Fluent, zaimplementowane w metodzie OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="77cda-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="77cda-202">Adnotacje danych należy można użyć klasy modelu jednostek, która określa sposób bardziej natrętnych z punktu widzenia DDD.</span><span class="sxs-lookup"><span data-stu-id="77cda-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="77cda-203">Jest to spowodowane są zanieczyszczenia modelu przy użyciu adnotacji danych związanych z infrastrukturą bazy danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="77cda-204">Z drugiej strony interfejs Fluent API to wygodny sposób zmiany większość konwencje i mapowania w ramach swojej infrastruktury warstwę trwałości danych, dlatego model jednostki będą odłączony od infrastruktury trwałości i przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="77cda-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="77cda-205">Interfejs API Fluent, a także metoda OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="77cda-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="77cda-206">Jak wspomniano wcześniej, aby zmienić mapowania i konwencje służy metoda OnModelCreating klasy DbContext.</span><span class="sxs-lookup"><span data-stu-id="77cda-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="77cda-207">Szeregowania mikrousługi w ramach aplikacji eShopOnContainers implementuje jawnego mapowania konfiguracji i, w razie potrzeby, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="77cda-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="77cda-208">Można ustawić mapowania Fluent API w ramach tej samej metody OnModelCreating, ale zaleca się partycji kod i posiadania wielu klas konfiguracji, jeden na jednostkę, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="77cda-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="77cda-209">Szczególnie w przypadku szczególnie dużych modeli zalecane jest posiadanie klas osobną konfiguracją dla konfigurowania jednostek różnych typów.</span><span class="sxs-lookup"><span data-stu-id="77cda-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="77cda-210">Kodem w przykładzie pokazano kilka jawne deklaracje i mapowania.</span><span class="sxs-lookup"><span data-stu-id="77cda-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="77cda-211">Konwencje programu EF Core jednak wiele z tych mapowania automatycznie, więc rzeczywisty kod, który trzeba by w Twoim przypadku może być mniejszy.</span><span class="sxs-lookup"><span data-stu-id="77cda-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="77cda-212">Algorytm Hi/Lo w programie EF Core</span><span class="sxs-lookup"><span data-stu-id="77cda-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="77cda-213">Ciekawszych aspektów kodu w powyższym przykładzie to, że używa on [algorytm Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategia generowania klucza.</span><span class="sxs-lookup"><span data-stu-id="77cda-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="77cda-214">Algorytm Hi/Lo jest przydatne, gdy wymagane są unikatowe klucze.</span><span class="sxs-lookup"><span data-stu-id="77cda-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="77cda-215">Jako podsumowanie algorytm Hi-Lo przypisuje unikatowych identyfikatorów wiersze tabeli a nie w zależności od natychmiast przechowywania wiersz w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="77cda-216">Dzięki temu można rozpocząć natychmiast, za pomocą identyfikatorów, jak to się dzieje z regularnych sekwencyjne identyfikatorów baz danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="77cda-217">Algorytm Hi/Lo opisuje mechanizm służący do generowania identyfikatorów bezpieczne po stronie klienta, a nie w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="77cda-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="77cda-218">*Bezpieczne* w tym kontekście oznacza bez kolizji.</span><span class="sxs-lookup"><span data-stu-id="77cda-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="77cda-219">Ten algorytm stanowi interesujące tych powodów:</span><span class="sxs-lookup"><span data-stu-id="77cda-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="77cda-220">Nie zprzerywa wzorzec jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="77cda-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="77cda-221">Nie wymaga rund generatorów sekwencji sposób czy w innych systemów DBMS.</span><span class="sxs-lookup"><span data-stu-id="77cda-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="77cda-222">Generuje on identyfikatorem można odczytać ludzi, w odróżnieniu od technik, które używają identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="77cda-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="77cda-223">EF Core obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) przy użyciu metody ForSqlServerUseSequenceHiLo, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="77cda-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="77cda-224">Mapowanie pól zamiast właściwości</span><span class="sxs-lookup"><span data-stu-id="77cda-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="77cda-225">Dzięki tej funkcji dostępne od EF Core 1.1, można mapować bezpośrednio kolumn na pola.</span><span class="sxs-lookup"><span data-stu-id="77cda-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="77cda-226">Jest to możliwe, nie korzystać z właściwości w klasie jednostki, a tylko można mapować kolumny z tabeli pola.</span><span class="sxs-lookup"><span data-stu-id="77cda-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="77cda-227">Typowym zastosowaniem tego będzie pola prywatne dla stanów wewnętrznych, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="77cda-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="77cda-228">Można to zrobić za pomocą jednego pola lub kolekcji, takie jak `List<>` pola.</span><span class="sxs-lookup"><span data-stu-id="77cda-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="77cda-229">Ten punkt został wspomniano wcześniej, gdy Omówiliśmy modelowania klasy modelu domeny, ale tutaj można zobaczyć, jak mapowanie odbywa się za pomocą `PropertyAccessMode.Field` konfiguracji wyróżnione w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="77cda-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="77cda-230">Korzystając z właściwości w tle w programie EF Core ukryte na poziomie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="77cda-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="77cda-231">Właściwości w tle w programie EF Core są właściwości, które nie istnieją w modelu entity klasy.</span><span class="sxs-lookup"><span data-stu-id="77cda-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="77cda-232">Wartości i Stany te właściwości są obsługiwane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="77cda-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="77cda-233">Implementacja wzorca specyfikacji</span><span class="sxs-lookup"><span data-stu-id="77cda-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="77cda-234">Jak wprowadzona wcześniej w sekcji dotyczącej projektu, wzorzec specyfikacji (jego pełna nazwa jest wzorzec specyfikacji zapytania) jest wzorzec projektowania driven zaprojektowany jako miejsce, w którym można umieścić definicji zapytania za pomocą opcjonalnych, sortowanie i stronicowanie logiki.</span><span class="sxs-lookup"><span data-stu-id="77cda-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="77cda-235">Wzorzec specyfikacja definiuje zapytanie w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="77cda-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="77cda-236">Na przykład w celu hermetyzacji stronicowane zapytanie, które wyszukuje niektórych produktów, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber pageSize, filtr, itp.).</span><span class="sxs-lookup"><span data-stu-id="77cda-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="77cda-237">Następnie metoda dowolnego repozytorium (zazwyczaj przeciążenie List()) Zaakceptuj ISpecification i uruchom zapytanie oczekiwany, na podstawie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="77cda-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="77cda-238">Przykładem ogólny interfejs specyfikacji jest następujący kod z [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="77cda-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

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

<span data-ttu-id="77cda-239">Następnie w implementacji klasy podstawowej specyfikacji ogólnego jest następująca.</span><span class="sxs-lookup"><span data-stu-id="77cda-239">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="77cda-240">Specyfikację ładuje jednostka pojedynczego koszyka koszyka identyfikator lub identyfikator nabywców, do którego należy koszyka.</span><span class="sxs-lookup"><span data-stu-id="77cda-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="77cda-241">Będzie ono [eager obciążenia](https://docs.microsoft.com/ef/core/querying/related-data) kolekcji elementów z koszyka.</span><span class="sxs-lookup"><span data-stu-id="77cda-241">It will [eager load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="77cda-242">A na koniec można zobaczyć poniżej ogólnego repozytorium EF służy specyfikacja filtru i obciążenia eager danych związane z danej jednostki typu T.</span><span class="sxs-lookup"><span data-stu-id="77cda-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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
<span data-ttu-id="77cda-243">Oprócz enkapsulacji logikę filtrowania, Specyfikacja można określić kształt danych ma zostać zwrócone, w tym właściwości, które można wypełnić.</span><span class="sxs-lookup"><span data-stu-id="77cda-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="77cda-244">Mimo że firma Microsoft nie jest zalecane jest, aby zwrócić IQueryable z repozytorium, jest idealnie możesz ich używać w ramach repozytorium do utworzenia zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="77cda-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="77cda-245">Widać to podejście używany na liście powyżej, metodę, która używa wyrażeń pośrednich IQueryable, do utworzenia listy zapytania zawiera przed wykonaniem kwerendy z kryteriami specyfikacji w ostatnim wierszu.</span><span class="sxs-lookup"><span data-stu-id="77cda-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="77cda-246">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="77cda-246">Additional resources</span></span>

-   <span data-ttu-id="77cda-247">**Mapowanie tabeli**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="77cda-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="77cda-248">**Użyj HiLo, aby wygenerować klucze za pomocą platformy Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="77cda-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="77cda-249">**Pola zapasowe**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="77cda-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="77cda-250">**Steve Smith. Hermetyzowany kolekcje w programie Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="77cda-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="77cda-251">**Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="77cda-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="77cda-252">**Wzorzec specyfikacji**
    [*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="77cda-252">**The Specification pattern**
[*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="77cda-253">[Poprzednie](infrastructure-persistence-layer-design.md)
[dalej](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="77cda-253">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
