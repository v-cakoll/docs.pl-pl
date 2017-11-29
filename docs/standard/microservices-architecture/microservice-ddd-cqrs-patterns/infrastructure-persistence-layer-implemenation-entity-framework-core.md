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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementowanie warstwę trwałości infrastruktury z programu Entity Framework Core

Gdy używasz relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL zalecane podejście jest zaimplementowanie warstwę trwałości oparte na Entity Framework (EF). EF obsługuje LINQ i udostępnia silnie typizowanych obiektów dla modelu, jak również uproszczony trwałości do bazy danych.

Entity Framework zawiera długą historię w ramach programu .NET Framework. Gdy używasz .NET Core, należy też używać Entity Framework Core, w którym jest uruchomiona w systemie Windows lub Linux w taki sam sposób jak oprogramowanie .NET Core. Podstawowe EF jest zakończenie ponownego zapisywania programu Entity Framework, implementowane za dużo mniejsze zużycie i istotne ulepszenia wydajności.

## <a name="introduction-to-entity-framework-core"></a>Wprowadzenie do programu Entity Framework Core

Program Entity Framework (EF) Core to lekkie, rozszerzalny, i technologii dostępu do wersji i platform popularnych danych programu Entity Framework. Został wprowadzony z platformą .NET Core w połowie 2016.

Wprowadzenie do podstawowych EF jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu udostępniamy łącza do tych informacji.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Program Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **Wprowadzenie do programu Entity Framework Core za pomocą programu Visual Studio i ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **Klasa DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **Porównanie EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura w Entity Framework Core z punktu widzenia DDD

Z punktu widzenia DDD, ważna możliwość EF jest możliwość korzystania z jednostki POCO domeny, nazywanego także w terminologii EF jako POCO *pierwszy kod jednostek*. Jeśli używasz jednostki POCO domeny klasach modeli domeny są trwałości ignorujących, po [nieznajomości trwałości](http://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad.

Na wzorce DDD zalecaną zachowanie domeny i reguły w obrębie klasy jednostka, więc może kontrolować invariants, sprawdzanie poprawności i reguł podczas uzyskiwania dostępu do żadnej kolekcji. W związku z tym nie jest dobrym rozwiązaniem w DDD umożliwia publiczny dostęp do kolekcji podrzędnych obiektów lub obiekty wartości. Zamiast tego chcesz udostępnić metod, które kontrolują, jak i kiedy może być aktualizowana z pól i właściwości kolekcji, i jakie zachowanie i akcji powinien wystąpić, gdy tak się stanie.

W wersji 1.1 Core EF by spełnić te wymagania DDD mogą mieć zwykłych pól w jednostki zamiast właściwości za pomocą metody ustawiające publiczne i prywatne. Jeśli nie chcesz, aby pole jednostki jako dostępne z zewnątrz, możesz utworzyć atrybutu lub pola zamiast właściwości. Nie istnieje potrzeba do użycia prywatnej metody ustawiające, jeśli wolisz tej metody czyszczącej.

W podobny sposób można teraz mają dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej typu IEnumerable&lt;T&gt;, która nie jest obsługiwana przez element pole prywatne dla kolekcji (takie jak listy&lt;&gt;) w sieci Jednostka, która zależy od EF trwałości. Poprzednie wersje programu Entity Framework wymaganych właściwości kolekcji do obsługi kolekcji ICollection&lt;T&gt;, który oznaczało, że każdy Deweloper przy użyciu klasy nadrzędnej jednostki można dodać lub usunąć elementy z jego kolekcji właściwości. Możliwość ta będzie przed zalecane wzorce w DDD.

Można użyć prywatnych kolekcji podczas udostępnianie obiektu IEnumerable tylko do odczytu, jak pokazano w poniższym przykładzie kodu:

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

Należy pamiętać, że właściwość OrderItems są dostępne tylko jako tylko do odczytu przy użyciu listy&lt;&gt;. AsReadOnly(). Ta metoda tworzy tylko do odczytu otokę prywatnej listy, aby jest chroniony przed aktualizacje zewnętrznych. Jest znacznie tańszy niż przy użyciu metody tolist —, ponieważ nie trzeba skopiować wszystkie elementy w nowej kolekcji; Zamiast tego wykonuje tylko jedną operację alokacji sterty dla wystąpienia otoki.

Podstawowe EF umożliwia mapowanie modelu domeny do fizycznej bazy danych bez zanieczyszczających modelu domeny. Jest czysty .NET obiektów POCO kodu, ponieważ akcja mapowania jest zaimplementowana w warstwę trwałości. W tym mapowania akcji należy skonfigurować mapowanie pól w bazie danych. W poniższym przykładzie metody OnModelCreating wyróżniony kod informuje Core EF dostępu do właściwości OrderItems za pomocą tego pola.

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

Użycie pola zamiast właściwości jednostki OrderItem jest trwały, tak jakby listy&lt;OrderItem&gt; właściwości. Jednak przedstawia jedną metodę dostępu (metoda AddOrderItem) do dodawania nowych elementów do zlecenia. W związku z tym zachowanie są ze sobą powiązane i dane będą spójne w całym kod źródłowy aplikacji, która używa modelu domeny.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Wdrażanie niestandardowe repozytoria z programu Entity Framework Core

Na poziomie implementacji repozytorium jest po prostu klasy z kodem trwałości danych koordynowane przez jednostkę pracy (DBContext w podstawowej EF) podczas przeprowadzania aktualizacji, jak pokazano w następującej klasy:

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

Należy pamiętać, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny. Jednak implementacja repozytorium jest wykonywane na trwałość i warstwę infrastruktury.

EF DbContext jest dostarczany za pomocą konstruktora za pomocą iniekcji zależności. Są one udostępniane między wielu repozytoriów w ramach tego samego zakresu żądania HTTP, dzięki użyciu jego istnienia domyślnego (ServiceLifetime.Scoped) w kontenerze IoC (które można również jawnie ustawić z usługami. AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody służące do implementacji w repozytorium (aktualizacje lub transakcji i zapytań)

W każdej klasie repozytorium należy umieścić metody trwałości, które zaktualizowany stan jednostek zawarty w jego powiązanych agregacji. Należy pamiętać, że istnieje relacja jeden do jednego między agregacji i jej powiązane repozytorium. Wziąć pod uwagę może mieć osadzonych obiektów podrzędnych w jego wykres EF do obiektu jednostki głównego agregacji. Na przykład kupujący może mieć wiele metod płatności jako jednostek podrzędnych.

Ponieważ metoda porządkowania mikrousługi w eShopOnContainers również jest oparty na CQS/CQRS, większość zapytań nie są zaimplementowane w niestandardowe repozytoria. Deweloperzy mają swobodę tworzenia kwerend oraz sprzężenia, które są im potrzebne dla warstwy prezentacji bez ograniczeń narzuconych przez agregacje, niestandardowe repozytoria na agregacji i DDD ogólnie rzecz biorąc. Większość niestandardowe repozytoria sugerowane w tym przewodniku ma kilka aktualizacji lub metody transakcyjnych, ale tylko metody zapytania wymagany do pobierania danych do zaktualizowania. Na przykład repozytorium BuyerRepository implementuje metodę metoda FindAsync, ponieważ aplikacja musi wiedzieć, czy konkretnego nabywcy istnieje przed utworzeniem nowego kupujący związane z kolejności.

Jednak metody rzeczywiste zapytanie w celu uzyskania danych, aby wysyłać do aplikacji klienta lub warstwy prezentacji są implementowane, jak wspomniano w zapytaniach CQRS opartych na kwerendach elastyczne przy użyciu Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Przy użyciu niestandardowego repozytorium w porównaniu z użyciem EF DbContext bezpośrednio

Klasy Entity Framework DbContext bazuje na wzorce jednostki pracy i repozytorium i może służyć bezpośrednio w kodzie, takich jak z kontrolera ASP.NET Core MVC. Oznacza to sposób można utworzyć najprostszym kod, tak jak mikrousługi katalogu CRUD w eShopOnContainers. W przypadkach, w miejscu kodu najprostsza możliwa można bezpośrednio używać klasy DbContext, jak wielu deweloperów.

Jednak implementacja niestandardowe repozytoria zapewnia kilka korzyści, realizując bardziej złożonych mikrousług lub aplikacji. Wzorce jednostki pracy i repozytorium mają Hermetyzowanie warstwę trwałości infrastruktury, więc jego jest całkowicie niezależna od aplikacji i warstwy modelu domeny. Wdrażanie tych wzorców ułatwia użycie zasymulować repozytoria symulując dostępu do bazy danych.

W rysunku 9-18 lub przy użyciu magazynów, które ułatwiają mock tych repozytoria widać różnice między nie używa repozytoriów (bezpośrednio przy użyciu EF DbContext).

![](./media/image19.png)

**Rysunek 9-18**. Przy użyciu niestandardowe repozytoria i zwykły DbContext

Istnieje wiele alternatyw podczas mocking. Można mock tylko repozytoria lub można mock całą jednostkę pracy. Zwykle mocking tylko repozytoria jest wystarczająca, i złożoności abstract i mock całej jednostki pracy nie jest zwykle konieczna.

Później gdy możemy skupić się na warstwie aplikacji, zobaczysz działanie iniekcji zależności w ASP.NET Core i jak jest implementowane, gdy przy użyciu repozytoriów.

Krótko mówiąc niestandardowe repozytoria pozwalają na łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie ma wpływ na stan warstwy danych. Po uruchomieniu testów, które również dostęp do rzeczywistej bazy danych za pośrednictwem programu Entity Framework nie są one testy jednostek, ale integracji testy, które są znacznie wolniejsze.

Jeśli były używane DbContext bezpośrednio, tylko wybrane trzeba byłoby do uruchamiania testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalną danych dla testów jednostkowych. Nie będzie można kontrolować zasymulować obiektów i fałszywych danych w taki sam sposób na poziomie repozytorium. Oczywiście należy zawsze przetestować kontrolerów MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>EF DbContext i IUnitOfWork okres istnienia wystąpienia w Twojej kontenera IoC

Obiekt DbContext (widoczne jako obiekt IUnitOfWork) może być konieczne być współużytkowane przez wielu repozytoriów w ramach tego samego zakresu żądania HTTP. Na przykład dotyczy to podczas wykonywania operacji musi uwzględniać wiele wartości zagregowanych lub po prostu ponieważ używasz wielu wystąpień repozytorium. Należy również podać, czy interfejs IUnitOfWork jest częścią domeny, a nie typu EF.

Aby to zrobić, wystąpienie obiektu DbContext musi mieć ustawioną wartość ServiceLifetime.Scoped jego okres istnienia usługi. Jest to domyślny okres istnienia podczas rejestrowania obiektu DbContext z usług. AddDbContext w Twojej kontenera IoC z metody ConfigureServices pliku Startup.cs w projekcie interfejsu API platformy ASP.NET Core sieci Web. Ilustruje to poniższy kod.

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

Tryb tworzenia wystąpienia typu DbContext nie powinna być skonfigurowana jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Okres istnienia wystąpienia repozytorium w Twojej kontenera IoC

W podobny sposób okres istnienia z repozytorium zwykle powinna być ustawiona jako zakresami (InstancePerLifetimeScope w Autofac). Może to również być przejściowy (InstancePerDependency w Autofac), ale z usługą będzie bardziej efektywne w odniesieniu do pamięci, korzystając z zakresami okres istnienia.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Należy pamiętać, że przy użyciu okresu istnienia singleton dla repozytorium może spowodować poważne współbieżności problemów po Twoje DbContext ma ustawioną wartość zakresu istnienia (InstancePerLifetimeScope) (domyślnych okresów istnienia dla obiektu DBContext).

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Implementowanie repozytorium i jednostki pracy w aplikacji platformy ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathanowi Allen. Strategie implementacji dla repozytorium wzorca z programu Entity Framework, Dapper i łańcucha**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Torre de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mapowania tabeli

Mapowania tabeli identyfikuje danych można wykonać zapytania z tabeli i zapisane w bazie danych. Wcześniej przedstawiono sposób jednostek domeny (na przykład domena produktu lub kolejność) może służyć do generowania schematu bazy danych powiązanych. EF silnie zaprojektowano z myślą *konwencje*. Konwencje pytania, takich jak "Co nazwy tabeli zostanie?" lub "jaką właściwość jest kluczem podstawowym"? Konwencje są zwykle oparte na nazwy z konwencjonalnej — na przykład jest typowa dla klucza podstawowego właściwość, która kończy się identyfikatorem.

Według Konwencji, będzie można skonfigurować każdej jednostki do mapowania do tabeli o takiej samej nazwie jak DbSet&lt;TEntity&gt; właściwość, która przedstawia jednostek w kontekście pochodnych. Jeśli nie DbSet&lt;TEntity&gt; wartość została podana dla danej jednostki, jest używana nazwa klasy.

### <a name="data-annotations-versus-fluent-api"></a>Adnotacje danych w porównaniu z interfejsu API Fluent

Istnieje wiele dodatkowych konwencje EF Core, a większość z nich można zmienić za pomocą interfejsu API Fluent, zaimplementowana wewnątrz metody OnModelCreating lub adnotacji danych.

Adnotacje danych musi być używany w klasy modelu jednostki, która jest bardziej natrętnych sposób z punktu widzenia DDD. Jest to spowodowane są zanieczyszczających modelu przy użyciu adnotacji danych związanych z infrastrukturą bazy danych. Z drugiej strony interfejsu API Fluent to wygodny sposób zmienić większość konwencje i mapowania w ramach Twojej infrastruktury warstwę trwałości danych, więc modelu jednostki jest czysty i rozdzielonymi od infrastruktury trwałości.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Interfejsu API Fluent i metody OnModelCreating

Jak wspomniano, aby można było zmienić konwencje i mapowania, służy metody OnModelCreating klasy DbContext. W poniższym przykładzie pokazano, jak firma Microsoft to zrobić w porządkowania mikrousługi w eShopOnContainers.

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

Można ustawić mapowania interfejsu API Fluent w ramach tej samej metody OnModelCreating, ale zaleca się partycji kodu i mają wiele submethods, po jednym dla każdego obiektu, jak pokazano w przykładzie. Dla modeli szczególnie duże nawet może być wskazane mieć osobne pliki źródłowe (klas statycznych) konfigurowania typów jednostek inny.

Kod w tym przykładzie jest jawne. Konwencje EF Core jednak większość to automatycznie, więc rzeczywisty kod będzie potrzebny do zapisania do osiągnięcia samo będzie znacznie mniejszy.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algorytm Hi/Lo EF główną

Interesujących aspektów kodu w poprzednim przykładzie jest, że używa [algorytm Hi/Lo](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) jako strategii generowania kluczy.

Algorytm Hi/Lo jest przydatne, gdy potrzebne są klucze unikatowe. Jako podsumowanie algorytm Hi-Lo przypisuje unikatowe identyfikatory wierszy tabeli a nie w zależności od natychmiast przechowywania wiersza w bazie danych. Dzięki temu można Rozpocznij od razu, za pomocą identyfikatorów, jak się dzieje z bazą danych sekwencyjnych regularne identyfikatorów.

Algorytm Hi/Lo opisuje mechanizm służący do generowania identyfikatorów bezpieczne po stronie klienta, a nie w bazie danych. *Bezpieczne* w tym kontekście oznacza bez kolizji. Ten algorytm jest ciekawe tych powodów:

-   Nie powodować utraty wzorzec jednostki pracy.

-   Nie wymaga się, że rund generatory sekwencji sposób jak w innych systemach DBMS.

-   Generuje on człowieka identyfikator do odczytu, w odróżnieniu od techniki, które używają identyfikatorów GUID.

Jądro EF obsługuje [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) przy użyciu metody ForSqlServerUseSequenceHiLo, jak pokazano w poprzednim przykładzie.

### <a name="mapping-fields-instead-of-properties"></a>Mapowanie pól zamiast właściwości

Dzięki funkcji EF Core 1.1, mapująca kolumn do pól jest możliwe, aby nie używać żadnych właściwości w klasie jednostki i tylko w celu mapowania kolumn z tabeli do pola. Użycia który będą pól prywatnych dla stanów wewnętrznych, które nie muszą być dostępne spoza jednostki.

EF 1.1 obsługuje mapują pole bez właściwości powiązanych z kolumną w bazie danych. Można to zrobić, kolekcje, takie jak listy z jednego pola lub również&lt; &gt; pola. Ten punkt wspomniano wcześniej, gdy Rozmawialiśmy modelowania klasy modelu domeny, ale tutaj można zobaczyć, jak mapowania odbywa się przy użyciu konfiguracji PropertyAccessMode.Field wyróżnione poprzedni kod.

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>Przy użyciu właściwości cienia w obiektach wartości identyfikatorów ukryte na poziomie infrastruktury

Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki. Wartości i stanów te właściwości, które są obsługiwane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.

Z punktu widzenia DDD cień właściwości są wygodny sposób zaimplementować obiekty wartości ukrywając identyfikator jako klucz podstawowy właściwości cienia. Jest to ważne, ponieważ obiekt wartości nie powinna mieć tożsamości (co najmniej nie powinno być identyfikator warstwy modelu domeny podczas kształtowania obiekty wartości). Punkt, w tym miejscu jest począwszy od bieżącej wersji EF Core EF Core nie sposób implementowania obiekty wartości jako [typów złożonych](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), jak to możliwe w EF 6.x. To jest aktualnie muszą implementować obiekt wartości jako jednostki o identyfikatorze ukryte (klucz podstawowy) ustawiona jako wartość właściwości cienia.

Jak widać w [adres obiektu wartości](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) w eShopOnContainers, w modelu adresów nie ma Identyfikatora:

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

Jednak w tle, należy podać identyfikator tak, aby EF Core jest w stanie zachować te dane w tabelach bazy danych. Przejdziemy w metodzie ConfigureAddress [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) klasy na poziomie infrastruktury, więc firma Microsoft nie charakteryzują się z kodem infrastruktury EF modelu domeny.

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

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tabela mapowania**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Generuj klucze z programu Entity Framework Core za pomocą HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Tworzenie kopii pola**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Hermetyzowany kolekcje w programie Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[Poprzednie] (infrastruktury trwałości warstwy design.md) [dalej] (nosql — bazy danych — trwałości infrastructure.md)
