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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementowanie warstwy trwałości infrastruktury za pomocą platformy Entity Framework Core

Korzystając z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, zalecanym podejściem jest implementowanie warstwy trwałości, oparte na Entity Framework (EF). EF obsługuje LINQ i udostępnia silnie typizowanych obiektów dla modelu, jak również uproszczone trwałości do bazy danych.

Entity Framework od dawna jako część programu .NET Framework. Korzystając z platformy .NET Core, możesz także użyć platformy Entity Framework Core, która działa w systemie Windows lub Linux w taki sam sposób jak .NET Core. EF Core jest pełne ponowne zapisywanie adresów platformy Entity Framework implementowane za pomocą znacznie mniejszych rozmiarów i istotne ulepszenia wydajności.

## <a name="introduction-to-entity-framework-core"></a>Wprowadzenie do platformy Entity Framework Core

Entity Framework (EF) Core to lekkie, rozszerzalne, i technologii dostępu do popularnych danych Entity Framework w wersji dla wielu platform. Został wprowadzony przy użyciu platformy .NET Core w połowie 2016.

Wprowadzenie do programu EF Core jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu udostępniamy łącza do tych informacji.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **Wprowadzenie do platformy ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **Klasy DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **Porównanie programów EF Core i EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Z punktu widzenia DDD infrastruktury platformy Entity Framework Core

Z punktu widzenia DDD, to ważny czynnik EF jest możliwość korzystania z jednostki domeny POCO, zwane w terminologii programu EF jako POCO *najpierw kod jednostki*. Jeśli używasz jednostki domeny POCO, klasach modeli domeny są trwałości zakresu, zgodnie z [nieznajomości trwałości](https://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad.

Na wzorców DDD powinna hermetyzować zachowanie domeny i reguł w klasie jednostki, dzięki czemu podczas uzyskiwania dostępu do żadnej kolekcji może kontrolować invariants, sprawdzanie poprawności i reguł. W związku z tym nie jest dobrym rozwiązaniem DDD, aby zezwolić na publiczny dostęp do kolekcji podrzędnej obiektów lub obiekty wartości. Zamiast tego chcesz udostępnić, metody, które kontrolują, jak i kiedy Twoja pola i kolekcje właściwości mogą być aktualizowane, i jakie zachowanie i akcji powinny być wykonywane, kiedy tak się stanie.

Od programu EF Core 1.1 spełnienie tych wymagań DDD może mieć zwykły pól w jednostkach zamiast właściwości publiczne. Jeśli nie mają być dostępne z zewnątrz pole jednostki, po prostu utworzyć atrybutu lub pola zamiast właściwości. Można również użyć metod ustawiających właściwości prywatnej.

W podobny sposób można teraz masz dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisanych w formie `IReadOnlyCollection<T>`, która jest wspierana przez członka pole prywatne dla kolekcji (np. `List<T>`) w jednostce, która opiera się na EF na potrzeby stanu trwałego. Poprzednie wersje programu Entity Framework wymaganych właściwości kolekcji do obsługi `ICollection<T>`, która rozumie, Każdy deweloper może przy użyciu klasy nadrzędnej jednostki można dodać lub usunąć elementy za pomocą jego właściwości kolekcji. Tę możliwość byłoby względem zalecane wzorce w DDD.

Możesz użyć prywatnego kolekcji przedstawiania tylko do odczytu `IReadOnlyCollection<T>` obiektu, jak pokazano w poniższym przykładzie kodu:

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

Należy pamiętać, że `OrderItems` właściwość może zostać oceniony jedynie jako tylko do odczytu przy użyciu `IReadOnlyCollection<OrderItem>`. Ten typ jest tylko do odczytu, więc jest chroniony przed regularne aktualizacje zewnętrznych. 

EF Core umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczenia" model domeny. Jest czysty .NET obiektów POCO kodu, ponieważ akcji mapowanie jest zaimplementowana w warstwy trwałości. W tym działaniu mapowania należy skonfigurować mapowanie pól w bazie danych. W poniższym przykładzie metoda OnModelCreating wyróżniony kod informuje programu EF Core dostęp do właściwości OrderItems za pośrednictwem jej pola.

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

Używając pola zamiast właściwości jednostki OrderItem są utrwalane tylko tak, jakby był listy&lt;OrderItem&gt; właściwości. Jednak udostępnia ona pojedynczy akcesora `AddOrderItem` metody dodawania nowych elementów do zamówienia. W rezultacie zachowanie i dane są ze sobą powiązane i będzie spójny we kod źródłowy aplikacji, która używa modelu domeny.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Implementowanie niestandardowego repozytoriów za pomocą platformy Entity Framework Core

Na poziomie implementacji repozytorium jest po prostu klasy z kodem stanu trwałego danych koordynowane przez jednostka pracy (typu DBContext w programie EF Core) podczas przeprowadzania aktualizacji, jak pokazano na następującej klasy:

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

Należy pamiętać, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako umowę. Jednak implementacja repozytorium odbywa się na trwałość i warstwy infrastruktury.

Kontekst DbContext EF jest dostarczany za pośrednictwem konstruktora przy użyciu iniekcji zależności. Jest udostępniana między wieloma repozytoriami w obrębie tego samego zakresu żądania HTTP, dzięki jego istnienia domyślne (ServiceLifetime.Scoped) w kontenerze IoC (która może też być jawnie ustawione przy użyciu usługi. AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody służące do implementacji w repozytorium (aktualizacje lub transakcje w stosunku do zapytania)

W każdej klasie repozytorium należy umieszczać metod trwałości, które aktualizują stan jednostki zawarty w jego powiązane agregacji. Należy pamiętać, że istnieje bezpośredni związek pomiędzy agregacji i jego powiązanym repozytorium. Weź pod uwagę może zostały osadzone jednostki podrzędne w ramach jego EF wykres obiektu jednostki głównego agregacji. Na przykład kupujący może mieć wiele metod płatności jako jednostki podrzędne powiązane.

Ponieważ podejście do szeregowania mikrousługi w ramach aplikacji eShopOnContainers również opiera się na CQS/CQRS, większość zapytań nie są implementowane w repozytoriach niestandardowych. Deweloperzy mają możliwość tworzenia kwerend i sprzężeń, które są im potrzebne dla warstwy prezentacji bez ograniczeń nałożonych przez agregacje, niestandardowe repozytoriów na agregację i DDD ogólnie rzecz biorąc. Większość repozytoriów niestandardowych, zaproponowana przez ten przewodnik ma kilka aktualizacji lub transakcyjnych metody, ale po prostu metody zapytań, konieczne zaktualizowanie danych. Na przykład repozytorium BuyerRepository implementuje metodę metoda findasync dla, ponieważ aplikacja musi wiedzieć, czy konkretnego nabywcy istnieje przed utworzeniem nowego kupujący związanych z zamówieniem.

Jednak metody rzeczywiste zapytanie w celu uzyskania danych, aby wysyłać do aplikacji klienta lub warstwy prezentacji są implementowane, jak wspomniano w zapytaniach CQRS opartych na kwerendach elastyczne korzystanie z programem Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Przy użyciu niestandardowych repozytorium, w przeciwieństwie do użycia bezpośrednio EF DbContext

Klasy Entity Framework DbContext opiera się na jednostce pracy i repozytorium wzorce i może służyć bezpośrednio w kodzie, takich jak z kontroler składnika ASP.NET Core MVC. Oznacza to sposób możesz utworzyć najprostszą kodu, tak jak mikrousługi CRUD katalogu, w ramach aplikacji eShopOnContainers. W przypadkach, w miejscu kodu najprostsza możliwa można bezpośrednio korzystać z wystąpień klasy DbContext, jak wielu deweloperów.

Jednak implementacja niestandardowego repozytoriów zapewnia kilka korzyści, podczas wykonywania bardziej złożonych z mikrousług lub aplikacji. Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, dzięki czemu jej jest całkowicie niezależny od aplikacji i warstwy modelu domeny. Implementacji tych wzorców może ułatwić użytkowania makiety repozytoriów, symulując dostępu do bazy danych.

W rysunek 9-18 możesz zobaczyć różnice nie przy użyciu repozytoriów (bezpośrednio przy użyciu typu DbContext EF) w porównaniu z użyciem repozytoria, które ułatwiają testowanie tych repozytoriów.

![](./media/image19.png)

**Rysunek 9-18**. Przy użyciu niestandardowych repozytoriów i zwykłego typu DbContext

Gdy pozorowanie istnieje wiele alternatyw. Można testowanie po prostu repozytoriów lub można testowanie całej jednostki pracy. Zazwyczaj pozorowanie po prostu repozytoriów jest wystarczająca, i złożoności abstrakcyjnej i testowanie całej jednostki pracy nie jest zwykle konieczna.

Później gdy skupimy się na warstwie aplikacji, zobaczysz działania wstrzykiwanie zależności w programie ASP.NET Core i jak jest implementowane, gdy przy użyciu repozytoriów.

Krótko mówiąc niestandardowe repozytoria pozwalają na łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie mają wpływ stan warstwy danych. Jeśli uruchamiasz testy, które również dostęp do rzeczywistej bazy danych za pomocą programu Entity Framework, nie są one testy jednostkowe, ale testy integracji, które są znacznie wolniejsze.

Jeśli kontekst DbContext była używana bezpośrednio, tylko wybranego typu trzeba byłoby Uruchamianie testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalną danych dla testów jednostkowych. Nie będzie można kontrolować makiety obiekty i dane fikcyjne w taki sam sposób na poziomie repozytorium. Oczywiście należy zawsze przetestować kontrolerów MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Kontekst DbContext EF i IUnitOfWork okres istnienia wystąpienia w kontenera IoC

Obiekt typu DbContext (udostępniane jako obiekt IUnitOfWork) może być konieczne być współużytkowane przez wiele repozytoriów w obrębie tego samego zakresu żądania HTTP. Na przykład, jest to wartość true, gdy podczas wykonywania operacji muszą zajmować się przy użyciu wielu agregacje lub po prostu ponieważ korzysta z wielu wystąpień repozytorium. Jest również ważne, aby wspomnieć, że interfejs IUnitOfWork stanowi część warstwy usługi domeny, a nie typu programu EF Core.

Aby to zrobić, wystąpienie obiektu DbContext musi mieć wartość ServiceLifetime.Scoped jego okres istnienia usługi. Jest to domyślny okres istnienia, podczas rejestrowania DbContext z usług. AddDbContext w kontenerze IoC z metody ConfigureServices pliku Startup.cs w projekcie internetowego interfejsu API platformy ASP.NET Core. Ilustruje to poniższy kod.

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

Tryb tworzenia wystąpienia typu DbContext nie powinien być skonfigurowany jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Okres istnienia wystąpienia repozytorium w kontenerze IoC

W podobny sposób okres istnienia repozytorium zwykle należy ustawić jako zakresie (InstancePerLifetimeScope w Autofac). Może być również przejściowy (InstancePerDependency w Autofac), ale usługa będzie bardziej wydajne w odniesieniu do pamięci, korzystając z zakresami okresu istnienia.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Należy zauważyć, że przy użyciu okres istnienia pojedyncze repozytorium, może spowodować poważne współbieżności problemy po Twojej DbContext jest ustawiona na ograniczony okres istnienia (InstancePerLifetimeScope) (okresy domyślnego typu DBContext).

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wdrażanie z repozytorium i jednostki pracy w aplikacji ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Strategie implementacji wzorca repozytorium z platformą Entity Framework, programem Dapper i łańcuch**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Torre'a de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mapowanie tabeli

Mapowanie tabeli identyfikuje dane tabeli, aby być odpytywane i zapisane w bazie danych. Wcześniej pokazano, jak jednostki domeny (na przykład domena produktu lub zamówienia) może służyć do generowania schematu powiązanej bazy danych. EF silnie zaprojektowany pod kątem koncepcji *konwencje*. Konwencje adresów pytania "Co nazwy tabeli zostanie?" lub "jakie właściwości klucza podstawowego?" Konwencje są zazwyczaj na podstawie konwencjonalne nazw — na przykład jest typowe dla klucza podstawowego, jako właściwość, która kończy się za pomocą identyfikatora.

Zgodnie z Konwencją każdej jednostki będą konfigurowane tak, aby zamapować na tabelę z taką samą nazwę jak DbSet&lt;TEntity&gt; właściwość, która udostępnia jednostki w kontekście pochodnych. Jeśli nie DbSet&lt;TEntity&gt; wartość zostanie podana dla danej jednostki, nazwa klasy jest używana.

### <a name="data-annotations-versus-fluent-api"></a>Adnotacje danych w porównaniu z interfejsu API Fluent

Istnieje wiele dodatkowych konwencje programu EF Core, a większość z nich można zmienić przy użyciu adnotacji danych lub interfejsu API Fluent, zaimplementowane w metodzie OnModelCreating.

Adnotacje danych należy można użyć klasy modelu jednostek, która określa sposób bardziej natrętnych z punktu widzenia DDD. Jest to spowodowane są zanieczyszczenia modelu przy użyciu adnotacji danych związanych z infrastrukturą bazy danych. Z drugiej strony interfejs Fluent API to wygodny sposób zmiany większość konwencje i mapowania w ramach swojej infrastruktury warstwę trwałości danych, dlatego model jednostki będą odłączony od infrastruktury trwałości i przejrzysty.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Interfejs API Fluent, a także metoda OnModelCreating

Jak wspomniano wcześniej, aby zmienić mapowania i konwencje służy metoda OnModelCreating klasy DbContext. 

Szeregowania mikrousługi w ramach aplikacji eShopOnContainers implementuje jawnego mapowania konfiguracji i, w razie potrzeby, jak pokazano w poniższym kodzie.

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

Można ustawić mapowania Fluent API w ramach tej samej metody OnModelCreating, ale zaleca się partycji kod i posiadania wielu klas konfiguracji, jeden na jednostkę, jak pokazano w przykładzie. Szczególnie w przypadku szczególnie dużych modeli zalecane jest posiadanie klas osobną konfiguracją dla konfigurowania jednostek różnych typów.

Kodem w przykładzie pokazano kilka jawne deklaracje i mapowania. Konwencje programu EF Core jednak wiele z tych mapowania automatycznie, więc rzeczywisty kod, który trzeba by w Twoim przypadku może być mniejszy.


### <a name="the-hilo-algorithm-in-ef-core"></a>Algorytm Hi/Lo w programie EF Core

Ciekawszych aspektów kodu w powyższym przykładzie to, że używa on [algorytm Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategia generowania klucza.

Algorytm Hi/Lo jest przydatne, gdy wymagane są unikatowe klucze. Jako podsumowanie algorytm Hi-Lo przypisuje unikatowych identyfikatorów wiersze tabeli a nie w zależności od natychmiast przechowywania wiersz w bazie danych. Dzięki temu można rozpocząć natychmiast, za pomocą identyfikatorów, jak to się dzieje z regularnych sekwencyjne identyfikatorów baz danych.

Algorytm Hi/Lo opisuje mechanizm służący do generowania identyfikatorów bezpieczne po stronie klienta, a nie w bazie danych. *Bezpieczne* w tym kontekście oznacza bez kolizji. Ten algorytm stanowi interesujące tych powodów:

-   Nie zprzerywa wzorzec jednostki pracy.

-   Nie wymaga rund generatorów sekwencji sposób czy w innych systemów DBMS.

-   Generuje on identyfikatorem można odczytać ludzi, w odróżnieniu od technik, które używają identyfikatorów GUID.

EF Core obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) przy użyciu metody ForSqlServerUseSequenceHiLo, jak pokazano w powyższym przykładzie.

### <a name="mapping-fields-instead-of-properties"></a>Mapowanie pól zamiast właściwości

Dzięki tej funkcji dostępne od EF Core 1.1, można mapować bezpośrednio kolumn na pola. Jest to możliwe, nie korzystać z właściwości w klasie jednostki, a tylko można mapować kolumny z tabeli pola. Typowym zastosowaniem tego będzie pola prywatne dla stanów wewnętrznych, które nie muszą być dostępne spoza jednostki. 

Można to zrobić za pomocą jednego pola lub kolekcji, takie jak `List<>` pola. Ten punkt został wspomniano wcześniej, gdy Omówiliśmy modelowania klasy modelu domeny, ale tutaj można zobaczyć, jak mapowanie odbywa się za pomocą `PropertyAccessMode.Field` konfiguracji wyróżnione w poprzednim kodzie.

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Korzystając z właściwości w tle w programie EF Core ukryte na poziomie infrastruktury

Właściwości w tle w programie EF Core są właściwości, które nie istnieją w modelu entity klasy. Wartości i Stany te właściwości są obsługiwane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.


## <a name="implementing-the-specification-pattern"></a>Implementacja wzorca specyfikacji

Jak wprowadzona wcześniej w sekcji dotyczącej projektu, wzorzec specyfikacji (jego pełna nazwa jest wzorzec specyfikacji zapytania) jest wzorzec projektowania driven zaprojektowany jako miejsce, w którym można umieścić definicji zapytania za pomocą opcjonalnych, sortowanie i stronicowanie logiki. Wzorzec specyfikacja definiuje zapytanie w obiekcie. Na przykład w celu hermetyzacji stronicowane zapytanie, które wyszukuje niektórych produktów, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber pageSize, filtr, itp.). Następnie metoda dowolnego repozytorium (zazwyczaj przeciążenie List()) Zaakceptuj ISpecification i uruchom zapytanie oczekiwany, na podstawie tej specyfikacji.

Przykładem ogólny interfejs specyfikacji jest następujący kod z [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb). 

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

Następnie w implementacji klasy podstawowej specyfikacji ogólnego jest następująca.

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

Specyfikację ładuje jednostka pojedynczego koszyka koszyka identyfikator lub identyfikator nabywców, do którego należy koszyka. Będzie ono [eager obciążenia](https://docs.microsoft.com/ef/core/querying/related-data) kolekcji elementów z koszyka.

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

A na koniec można zobaczyć poniżej ogólnego repozytorium EF służy specyfikacja filtru i obciążenia eager danych związane z danej jednostki typu T.

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
Oprócz enkapsulacji logikę filtrowania, Specyfikacja można określić kształt danych ma zostać zwrócone, w tym właściwości, które można wypełnić. 

Mimo że firma Microsoft nie jest zalecane jest, aby zwrócić IQueryable z repozytorium, jest idealnie możesz ich używać w ramach repozytorium do utworzenia zestawu wyników. Widać to podejście używany na liście powyżej, metodę, która używa wyrażeń pośrednich IQueryable, do utworzenia listy zapytania zawiera przed wykonaniem kwerendy z kryteriami specyfikacji w ostatnim wierszu.


#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Mapowanie tabeli**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Użyj HiLo, aby wygenerować klucze za pomocą platformy Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Pola zapasowe**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Hermetyzowany kolekcje w programie Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Wzorzec specyfikacji**
    [*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)
    

>[!div class="step-by-step"]
[Poprzednie](infrastructure-persistence-layer-design.md)
[dalej](nosql-database-persistence-infrastructure.md)
