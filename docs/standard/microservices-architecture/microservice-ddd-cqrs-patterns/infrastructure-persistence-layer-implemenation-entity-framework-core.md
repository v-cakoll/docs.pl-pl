---
title: "Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="02726-104">Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="02726-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="02726-105">Gdy używasz relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL zalecane podejście jest zaimplementowanie warstwę trwałości oparte na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="02726-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="02726-106">EF obsługuje LINQ i udostępnia silnie typizowanych obiektów dla modelu, jak również uproszczony trwałości do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="02726-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="02726-107">Entity Framework zawiera długą historię w ramach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02726-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="02726-108">Gdy używasz .NET Core, należy też używać Entity Framework Core, w którym jest uruchomiona w systemie Windows lub Linux w taki sam sposób jak oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02726-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="02726-109">Podstawowe EF jest zakończenie ponownego zapisywania programu Entity Framework, implementowane za dużo mniejsze zużycie i istotne ulepszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="02726-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="02726-110">Wprowadzenie do programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="02726-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="02726-111">Program Entity Framework (EF) Core to lekkie, rozszerzalny, i technologii dostępu do wersji i platform popularnych danych programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="02726-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="02726-112">Został wprowadzony z platformą .NET Core w połowie 2016.</span><span class="sxs-lookup"><span data-stu-id="02726-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="02726-113">Wprowadzenie do podstawowych EF jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu udostępniamy łącza do tych informacji.</span><span class="sxs-lookup"><span data-stu-id="02726-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="02726-114">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="02726-114">Additional resources</span></span>

-   <span data-ttu-id="02726-115">**Program Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="02726-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="02726-116">**Wprowadzenie do programu Entity Framework Core za pomocą programu Visual Studio i ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="02726-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="02726-117">**Klasa DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="02726-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="02726-118">**Porównanie EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="02726-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="02726-119">Infrastruktura w Entity Framework Core z punktu widzenia DDD</span><span class="sxs-lookup"><span data-stu-id="02726-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="02726-120">Z punktu widzenia DDD, ważna możliwość EF jest możliwość korzystania z jednostki POCO domeny, nazywanego także w terminologii EF jako POCO *pierwszy kod jednostek*.</span><span class="sxs-lookup"><span data-stu-id="02726-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="02726-121">Jeśli używasz jednostki POCO domeny klasach modeli domeny są trwałości ignorujących, po [nieznajomości trwałości](http://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad.</span><span class="sxs-lookup"><span data-stu-id="02726-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="02726-122">Na wzorce DDD zalecaną zachowanie domeny i reguły w obrębie klasy jednostka, więc może kontrolować invariants, sprawdzanie poprawności i reguł podczas uzyskiwania dostępu do żadnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="02726-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="02726-123">W związku z tym nie jest dobrym rozwiązaniem w DDD umożliwia publiczny dostęp do kolekcji podrzędnych obiektów lub obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="02726-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="02726-124">Zamiast tego chcesz udostępnić metod, które kontrolują, jak i kiedy może być aktualizowana z pól i właściwości kolekcji, i jakie zachowanie i akcji powinien wystąpić, gdy tak się stanie.</span><span class="sxs-lookup"><span data-stu-id="02726-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="02726-125">W wersji 1.1 Core EF by spełnić te wymagania DDD mogą mieć zwykłych pól w jednostki zamiast właściwości za pomocą metody ustawiające publiczne i prywatne.</span><span class="sxs-lookup"><span data-stu-id="02726-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="02726-126">Jeśli nie chcesz, aby pole jednostki jako dostępne z zewnątrz, możesz utworzyć atrybutu lub pola zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="02726-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="02726-127">Nie istnieje potrzeba do użycia prywatnej metody ustawiające, jeśli wolisz tej metody czyszczącej.</span><span class="sxs-lookup"><span data-stu-id="02726-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="02726-128">W podobny sposób można teraz mają dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej typu IEnumerable&lt;T&gt;, która nie jest obsługiwana przez element pole prywatne dla kolekcji (takie jak listy&lt;&gt;) w sieci Jednostka, która zależy od EF trwałości.</span><span class="sxs-lookup"><span data-stu-id="02726-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="02726-129">Poprzednie wersje programu Entity Framework wymaganych właściwości kolekcji do obsługi kolekcji ICollection&lt;T&gt;, który oznaczało, że każdy Deweloper przy użyciu klasy nadrzędnej jednostki można dodać lub usunąć elementy z jego kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="02726-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="02726-130">Możliwość ta będzie przed zalecane wzorce w DDD.</span><span class="sxs-lookup"><span data-stu-id="02726-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="02726-131">Można użyć prywatnych kolekcji podczas udostępnianie obiektu IEnumerable tylko do odczytu, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="02726-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

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
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="02726-132">Należy pamiętać, że właściwość OrderItems są dostępne tylko jako tylko do odczytu przy użyciu listy&lt;&gt;. AsReadOnly().</span><span class="sxs-lookup"><span data-stu-id="02726-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="02726-133">Ta metoda tworzy tylko do odczytu otokę prywatnej listy, aby jest chroniony przed aktualizacje zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="02726-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="02726-134">Jest znacznie tańszy niż przy użyciu metody tolist —, ponieważ nie trzeba skopiować wszystkie elementy w nowej kolekcji; Zamiast tego wykonuje tylko jedną operację alokacji sterty dla wystąpienia otoki.</span><span class="sxs-lookup"><span data-stu-id="02726-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="02726-135">Podstawowe EF umożliwia mapowanie modelu domeny do fizycznej bazy danych bez zanieczyszczających modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="02726-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="02726-136">Jest czysty .NET obiektów POCO kodu, ponieważ akcja mapowania jest zaimplementowana w warstwę trwałości.</span><span class="sxs-lookup"><span data-stu-id="02726-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="02726-137">W tym mapowania akcji należy skonfigurować mapowanie pól w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="02726-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="02726-138">W poniższym przykładzie metody OnModelCreating wyróżniony kod informuje Core EF dostępu do właściwości OrderItems za pomocą tego pola.</span><span class="sxs-lookup"><span data-stu-id="02726-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

<span data-ttu-id="02726-139">Użycie pola zamiast właściwości jednostki OrderItem jest trwały, tak jakby listy&lt;OrderItem&gt; właściwości.</span><span class="sxs-lookup"><span data-stu-id="02726-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="02726-140">Jednak przedstawia jedną metodę dostępu (metoda AddOrderItem) do dodawania nowych elementów do zlecenia.</span><span class="sxs-lookup"><span data-stu-id="02726-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="02726-141">W związku z tym zachowanie są ze sobą powiązane i dane będą spójne w całym kod źródłowy aplikacji, która używa modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="02726-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="02726-142">Wdrażanie niestandardowe repozytoria z programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="02726-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="02726-143">Na poziomie implementacji repozytorium jest po prostu klasy z kodem trwałości danych koordynowane przez jednostkę pracy (DBContext w podstawowej EF) podczas przeprowadzania aktualizacji, jak pokazano w następującej klasy:</span><span class="sxs-lookup"><span data-stu-id="02726-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

<span data-ttu-id="02726-144">Należy pamiętać, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="02726-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="02726-145">Jednak implementacja repozytorium jest wykonywane na trwałość i warstwę infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="02726-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="02726-146">EF DbContext jest dostarczany za pomocą konstruktora za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="02726-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="02726-147">Są one udostępniane między wielu repozytoriów w ramach tego samego zakresu żądania HTTP, dzięki użyciu jego istnienia domyślnego (ServiceLifetime.Scoped) w kontenerze IoC (które można również jawnie ustawić z usługami. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="02726-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="02726-148">Metody służące do implementacji w repozytorium (aktualizacje lub transakcji i zapytań)</span><span class="sxs-lookup"><span data-stu-id="02726-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="02726-149">W każdej klasie repozytorium należy umieścić metody trwałości, które zaktualizowany stan jednostek zawarty w jego powiązanych agregacji.</span><span class="sxs-lookup"><span data-stu-id="02726-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="02726-150">Należy pamiętać, że istnieje relacja jeden do jednego między agregacji i jej powiązane repozytorium.</span><span class="sxs-lookup"><span data-stu-id="02726-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="02726-151">Wziąć pod uwagę może mieć osadzonych obiektów podrzędnych w jego wykres EF do obiektu jednostki głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="02726-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="02726-152">Na przykład kupujący może mieć wiele metod płatności jako jednostek podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="02726-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="02726-153">Ponieważ metoda porządkowania mikrousługi w eShopOnContainers również jest oparty na CQS/CQRS, większość zapytań nie są zaimplementowane w niestandardowe repozytoria.</span><span class="sxs-lookup"><span data-stu-id="02726-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="02726-154">Deweloperzy mają swobodę tworzenia kwerend oraz sprzężenia, które są im potrzebne dla warstwy prezentacji bez ograniczeń narzuconych przez agregacje, niestandardowe repozytoria na agregacji i DDD ogólnie rzecz biorąc.</span><span class="sxs-lookup"><span data-stu-id="02726-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="02726-155">Większość niestandardowe repozytoria sugerowane w tym przewodniku ma kilka aktualizacji lub metody transakcyjnych, ale tylko metody zapytania wymagany do pobierania danych do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="02726-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="02726-156">Na przykład repozytorium BuyerRepository implementuje metodę metoda FindAsync, ponieważ aplikacja musi wiedzieć, czy konkretnego nabywcy istnieje przed utworzeniem nowego kupujący związane z kolejności.</span><span class="sxs-lookup"><span data-stu-id="02726-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="02726-157">Jednak metody rzeczywiste zapytanie w celu uzyskania danych, aby wysyłać do aplikacji klienta lub warstwy prezentacji są implementowane, jak wspomniano w zapytaniach CQRS opartych na kwerendach elastyczne przy użyciu Dapper.</span><span class="sxs-lookup"><span data-stu-id="02726-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="02726-158">Przy użyciu niestandardowego repozytorium w porównaniu z użyciem EF DbContext bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="02726-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="02726-159">Klasy Entity Framework DbContext bazuje na wzorce jednostki pracy i repozytorium i może służyć bezpośrednio w kodzie, takich jak z kontrolera ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="02726-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="02726-160">Oznacza to sposób można utworzyć najprostszym kod, tak jak mikrousługi katalogu CRUD w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="02726-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="02726-161">W przypadkach, w miejscu kodu najprostsza możliwa można bezpośrednio używać klasy DbContext, jak wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="02726-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="02726-162">Jednak implementacja niestandardowe repozytoria zapewnia kilka korzyści, realizując bardziej złożonych mikrousług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02726-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="02726-163">Wzorce jednostki pracy i repozytorium mają Hermetyzowanie warstwę trwałości infrastruktury, więc jego jest całkowicie niezależna od aplikacji i warstwy modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="02726-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="02726-164">Wdrażanie tych wzorców ułatwia użycie zasymulować repozytoria symulując dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="02726-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="02726-165">W rysunku 9-18 lub przy użyciu magazynów, które ułatwiają mock tych repozytoria widać różnice między nie używa repozytoriów (bezpośrednio przy użyciu EF DbContext).</span><span class="sxs-lookup"><span data-stu-id="02726-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="02726-166">**Rysunek 9-18**.</span><span class="sxs-lookup"><span data-stu-id="02726-166">**Figure 9-18**.</span></span> <span data-ttu-id="02726-167">Przy użyciu niestandardowe repozytoria i zwykły DbContext</span><span class="sxs-lookup"><span data-stu-id="02726-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="02726-168">Istnieje wiele alternatyw podczas mocking.</span><span class="sxs-lookup"><span data-stu-id="02726-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="02726-169">Można mock tylko repozytoria lub można mock całą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="02726-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="02726-170">Zwykle mocking tylko repozytoria jest wystarczająca, i złożoności abstract i mock całej jednostki pracy nie jest zwykle konieczna.</span><span class="sxs-lookup"><span data-stu-id="02726-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="02726-171">Później gdy możemy skupić się na warstwie aplikacji, zobaczysz działanie iniekcji zależności w ASP.NET Core i jak jest implementowane, gdy przy użyciu repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="02726-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="02726-172">Krótko mówiąc niestandardowe repozytoria pozwalają na łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie ma wpływ na stan warstwy danych.</span><span class="sxs-lookup"><span data-stu-id="02726-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="02726-173">Po uruchomieniu testów, które również dostęp do rzeczywistej bazy danych za pośrednictwem programu Entity Framework nie są one testy jednostek, ale integracji testy, które są znacznie wolniejsze.</span><span class="sxs-lookup"><span data-stu-id="02726-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="02726-174">Jeśli były używane DbContext bezpośrednio, tylko wybrane trzeba byłoby do uruchamiania testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalną danych dla testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="02726-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="02726-175">Nie będzie można kontrolować zasymulować obiektów i fałszywych danych w taki sam sposób na poziomie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="02726-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="02726-176">Oczywiście należy zawsze przetestować kontrolerów MVC.</span><span class="sxs-lookup"><span data-stu-id="02726-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="02726-177">EF DbContext i IUnitOfWork okres istnienia wystąpienia w Twojej kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="02726-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="02726-178">Obiekt DbContext (widoczne jako obiekt IUnitOfWork) może być konieczne być współużytkowane przez wielu repozytoriów w ramach tego samego zakresu żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="02726-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="02726-179">Na przykład dotyczy to podczas wykonywania operacji musi uwzględniać wiele wartości zagregowanych lub po prostu ponieważ używasz wielu wystąpień repozytorium.</span><span class="sxs-lookup"><span data-stu-id="02726-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="02726-180">Należy również podać, czy interfejs IUnitOfWork jest częścią domeny, a nie typu EF.</span><span class="sxs-lookup"><span data-stu-id="02726-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="02726-181">Aby to zrobić, wystąpienie obiektu DbContext musi mieć ustawioną wartość ServiceLifetime.Scoped jego okres istnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="02726-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="02726-182">Jest to domyślny okres istnienia podczas rejestrowania obiektu DbContext z usług. AddDbContext w Twojej kontenera IoC z metody ConfigureServices pliku Startup.cs w projekcie interfejsu API platformy ASP.NET Core sieci Web.</span><span class="sxs-lookup"><span data-stu-id="02726-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="02726-183">Ilustruje to poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="02726-183">The following code illustrates this.</span></span>

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
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
        Assembly.GetName().Name));
    },
    ServiceLifetime.Scoped // Note that Scoped is the default choice
    // in AddDbContext. It is shown here only for
    // pedagogic purposes.
    );
}
```

<span data-ttu-id="02726-184">Tryb tworzenia wystąpienia typu DbContext nie powinna być skonfigurowana jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="02726-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="02726-185">Okres istnienia wystąpienia repozytorium w Twojej kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="02726-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="02726-186">W podobny sposób okres istnienia z repozytorium zwykle powinna być ustawiona jako zakresami (InstancePerLifetimeScope w Autofac).</span><span class="sxs-lookup"><span data-stu-id="02726-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="02726-187">Może to również być przejściowy (InstancePerDependency w Autofac), ale z usługą będzie bardziej efektywne w odniesieniu do pamięci, korzystając z zakresami okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="02726-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="02726-188">Należy pamiętać, że przy użyciu okresu istnienia singleton dla repozytorium może spowodować poważne współbieżności problemów po Twoje DbContext ma ustawioną wartość zakresu istnienia (InstancePerLifetimeScope) (domyślnych okresów istnienia dla obiektu DBContext).</span><span class="sxs-lookup"><span data-stu-id="02726-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="02726-189">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="02726-189">Additional resources</span></span>

-   <span data-ttu-id="02726-190">**Implementowanie repozytorium i jednostki pracy w aplikacji platformy ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="02726-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="02726-191">**Jonathanowi Allen. Strategie implementacji dla repozytorium wzorca z programu Entity Framework, Dapper i łańcucha**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="02726-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="02726-192">**Torre de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="02726-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="02726-193">Mapowania tabeli</span><span class="sxs-lookup"><span data-stu-id="02726-193">Table mapping</span></span>

<span data-ttu-id="02726-194">Mapowania tabeli identyfikuje danych można wykonać zapytania z tabeli i zapisane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="02726-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="02726-195">Wcześniej przedstawiono sposób jednostek domeny (na przykład domena produktu lub kolejność) może służyć do generowania schematu bazy danych powiązanych.</span><span class="sxs-lookup"><span data-stu-id="02726-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="02726-196">EF silnie zaprojektowano z myślą *konwencje*.</span><span class="sxs-lookup"><span data-stu-id="02726-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="02726-197">Konwencje pytania, takich jak "Co nazwy tabeli zostanie?"</span><span class="sxs-lookup"><span data-stu-id="02726-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="02726-198">lub "jaką właściwość jest kluczem podstawowym"?</span><span class="sxs-lookup"><span data-stu-id="02726-198">or “What property is the primary key?”</span></span> <span data-ttu-id="02726-199">Konwencje są zwykle oparte na nazwy z konwencjonalnej — na przykład jest typowa dla klucza podstawowego właściwość, która kończy się identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="02726-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="02726-200">Według Konwencji, będzie można skonfigurować każdej jednostki do mapowania do tabeli o takiej samej nazwie jak DbSet&lt;TEntity&gt; właściwość, która przedstawia jednostek w kontekście pochodnych.</span><span class="sxs-lookup"><span data-stu-id="02726-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="02726-201">Jeśli nie DbSet&lt;TEntity&gt; wartość została podana dla danej jednostki, jest używana nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="02726-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="02726-202">Adnotacje danych w porównaniu z interfejsu API Fluent</span><span class="sxs-lookup"><span data-stu-id="02726-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="02726-203">Istnieje wiele dodatkowych konwencje EF Core, a większość z nich można zmienić za pomocą interfejsu API Fluent, zaimplementowana wewnątrz metody OnModelCreating lub adnotacji danych.</span><span class="sxs-lookup"><span data-stu-id="02726-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="02726-204">Adnotacje danych musi być używany w klasy modelu jednostki, która jest bardziej natrętnych sposób z punktu widzenia DDD.</span><span class="sxs-lookup"><span data-stu-id="02726-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="02726-205">Jest to spowodowane są zanieczyszczających modelu przy użyciu adnotacji danych związanych z infrastrukturą bazy danych.</span><span class="sxs-lookup"><span data-stu-id="02726-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="02726-206">Z drugiej strony interfejsu API Fluent to wygodny sposób zmienić większość konwencje i mapowania w ramach Twojej infrastruktury warstwę trwałości danych, więc modelu jednostki jest czysty i rozdzielonymi od infrastruktury trwałości.</span><span class="sxs-lookup"><span data-stu-id="02726-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="02726-207">Interfejsu API Fluent i metody OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="02726-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="02726-208">Jak wspomniano, aby można było zmienić konwencje i mapowania, służy metody OnModelCreating klasy DbContext.</span><span class="sxs-lookup"><span data-stu-id="02726-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="02726-209">W poniższym przykładzie pokazano, jak firma Microsoft to zrobić w porządkowania mikrousługi w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="02726-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

<span data-ttu-id="02726-210">Można ustawić mapowania interfejsu API Fluent w ramach tej samej metody OnModelCreating, ale zaleca się partycji kodu i mają wiele submethods, po jednym dla każdego obiektu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="02726-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="02726-211">Dla modeli szczególnie duże nawet może być wskazane mieć osobne pliki źródłowe (klas statycznych) konfigurowania typów jednostek inny.</span><span class="sxs-lookup"><span data-stu-id="02726-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="02726-212">Kod w tym przykładzie jest jawne.</span><span class="sxs-lookup"><span data-stu-id="02726-212">The code in the example is explicit.</span></span> <span data-ttu-id="02726-213">Konwencje EF Core jednak większość to automatycznie, więc rzeczywisty kod będzie potrzebny do zapisania do osiągnięcia samo będzie znacznie mniejszy.</span><span class="sxs-lookup"><span data-stu-id="02726-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="02726-214">Algorytm Hi/Lo EF główną</span><span class="sxs-lookup"><span data-stu-id="02726-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="02726-215">Interesujących aspektów kodu w poprzednim przykładzie jest, że używa [algorytm Hi/Lo](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) jako strategii generowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="02726-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="02726-216">Algorytm Hi/Lo jest przydatne, gdy potrzebne są klucze unikatowe.</span><span class="sxs-lookup"><span data-stu-id="02726-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="02726-217">Jako podsumowanie algorytm Hi-Lo przypisuje unikatowe identyfikatory wierszy tabeli a nie w zależności od natychmiast przechowywania wiersza w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="02726-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="02726-218">Dzięki temu można Rozpocznij od razu, za pomocą identyfikatorów, jak się dzieje z bazą danych sekwencyjnych regularne identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="02726-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="02726-219">Algorytm Hi/Lo opisuje mechanizm służący do generowania identyfikatorów bezpieczne po stronie klienta, a nie w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="02726-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="02726-220">*Bezpieczne* w tym kontekście oznacza bez kolizji.</span><span class="sxs-lookup"><span data-stu-id="02726-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="02726-221">Ten algorytm jest ciekawe tych powodów:</span><span class="sxs-lookup"><span data-stu-id="02726-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="02726-222">Nie powodować utraty wzorzec jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="02726-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="02726-223">Nie wymaga się, że rund generatory sekwencji sposób jak w innych systemach DBMS.</span><span class="sxs-lookup"><span data-stu-id="02726-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="02726-224">Generuje on człowieka identyfikator do odczytu, w odróżnieniu od techniki, które używają identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="02726-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="02726-225">Jądro EF obsługuje [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) przy użyciu metody ForSqlServerUseSequenceHiLo, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="02726-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="02726-226">Mapowanie pól zamiast właściwości</span><span class="sxs-lookup"><span data-stu-id="02726-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="02726-227">Dzięki funkcji EF Core 1.1, mapująca kolumn do pól jest możliwe, aby nie używać żadnych właściwości w klasie jednostki i tylko w celu mapowania kolumn z tabeli do pola.</span><span class="sxs-lookup"><span data-stu-id="02726-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="02726-228">Użycia który będą pól prywatnych dla stanów wewnętrznych, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="02726-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="02726-229">EF 1.1 obsługuje mapują pole bez właściwości powiązanych z kolumną w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="02726-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="02726-230">Można to zrobić, kolekcje, takie jak listy z jednego pola lub również&lt; &gt; pola.</span><span class="sxs-lookup"><span data-stu-id="02726-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="02726-231">Ten punkt wspomniano wcześniej, gdy Rozmawialiśmy modelowania klasy modelu domeny, ale tutaj można zobaczyć, jak mapowania odbywa się przy użyciu konfiguracji PropertyAccessMode.Field wyróżnione poprzedni kod.</span><span class="sxs-lookup"><span data-stu-id="02726-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="02726-232">Przy użyciu właściwości cienia w obiektach wartości identyfikatorów ukryte na poziomie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="02726-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="02726-233">Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki.</span><span class="sxs-lookup"><span data-stu-id="02726-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="02726-234">Wartości i stanów te właściwości, które są obsługiwane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="02726-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="02726-235">Z punktu widzenia DDD cień właściwości są wygodny sposób zaimplementować obiekty wartości ukrywając identyfikator jako klucz podstawowy właściwości cienia.</span><span class="sxs-lookup"><span data-stu-id="02726-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="02726-236">Jest to ważne, ponieważ obiekt wartości nie powinna mieć tożsamości (co najmniej nie powinno być identyfikator warstwy modelu domeny podczas kształtowania obiekty wartości).</span><span class="sxs-lookup"><span data-stu-id="02726-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="02726-237">Punkt, w tym miejscu jest począwszy od bieżącej wersji EF Core EF Core nie sposób implementowania obiekty wartości jako [typów złożonych](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), jak to możliwe w EF 6.x.</span><span class="sxs-lookup"><span data-stu-id="02726-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="02726-238">To jest aktualnie muszą implementować obiekt wartości jako jednostki o identyfikatorze ukryte (klucz podstawowy) ustawiona jako wartość właściwości cienia.</span><span class="sxs-lookup"><span data-stu-id="02726-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="02726-239">Jak widać w [adres obiektu wartości](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) w eShopOnContainers, w modelu adresów nie ma Identyfikatora:</span><span class="sxs-lookup"><span data-stu-id="02726-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

<span data-ttu-id="02726-240">Jednak w tle, należy podać identyfikator tak, aby EF Core jest w stanie zachować te dane w tabelach bazy danych.</span><span class="sxs-lookup"><span data-stu-id="02726-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="02726-241">Przejdziemy w metodzie ConfigureAddress [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) klasy na poziomie infrastruktury, więc firma Microsoft nie charakteryzują się z kodem infrastruktury EF modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="02726-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a><span data-ttu-id="02726-242">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="02726-242">Additional resources</span></span>

-   <span data-ttu-id="02726-243">**Tabela mapowania**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="02726-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="02726-244">**Generuj klucze z programu Entity Framework Core za pomocą HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="02726-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="02726-245">**Tworzenie kopii pola**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="02726-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="02726-246">**Steve Smith. Hermetyzowany kolekcje w programie Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="02726-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="02726-247">**Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="02726-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="02726-248">[Poprzednie] (infrastruktury trwałości warstwy design.md) [dalej] (nosql — bazy danych — trwałości infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="02726-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
