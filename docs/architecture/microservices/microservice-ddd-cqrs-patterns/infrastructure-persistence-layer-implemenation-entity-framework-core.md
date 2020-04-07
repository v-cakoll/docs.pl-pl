---
title: Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami implementacji warstwy trwałości infrastruktury przy użyciu programu Entity Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: 7ab3be0d6a5affda478f7ec8f6c356571e304759
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805481"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core

Korzystając z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, zalecanym podejściem jest zaimplementowanie warstwy trwałości opartej na entity framework (EF). EF obsługuje LINQ i zapewnia silnie typizowane obiekty dla modelu, a także uproszczoną trwałość w bazie danych.

Entity Framework ma długą historię jako część programu .NET Framework. Korzystając z programu .NET Core, należy również użyć programu Entity Framework Core, który działa w systemie Windows lub Linux w taki sam sposób, jak program .NET Core. EF Core jest kompletnym przepisać entity framework, który jest implementowany ze znacznie mniejszym rozmiarem i ważne ulepszenia wydajności.

## <a name="introduction-to-entity-framework-core"></a>Wprowadzenie do core struktury encji

Entity Framework (EF) Core to lekka, rozszerzalna i wieloplatformowa wersja popularnej technologii dostępu do danych entity framework. Został wprowadzony z .NET Core w połowie 2016 roku.

Ponieważ wprowadzenie do EF Core jest już dostępne w dokumentacji firmy Microsoft, w tym miejscu po prostu podamy łącza do tych informacji.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Rdzeń struktury encji** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Wprowadzenie do ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **Klasa DbContext** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **Porównaj EF Core & EF6.x** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura w ramach entity framework core z perspektywy DDD

Z punktu widzenia DDD ważną możliwością EF jest możliwość używania jednostek domeny POCO, znanych również w terminologii EF jako *jednostki poco oparte na kodzie.* Jeśli używasz jednostek domeny POCO, klasy modelu domeny są niewiedzą dotyczące trwałości, zgodnie z [zasadami ignorancji trwałości](https://deviq.com/persistence-ignorance/) i [ignorancji infrastruktury.](https://ayende.com/blog/3137/infrastructure-ignorance)

Na wzorce DDD należy hermetyzować zachowanie domeny i reguły w samej klasie jednostki, dzięki czemu można kontrolować invariants, sprawdzania poprawności i reguł podczas uzyskiwania dostępu do dowolnej kolekcji. W związku z tym nie jest dobrą praktyką w DDD, aby umożliwić publiczny dostęp do kolekcji jednostek podrzędnych lub obiektów wartości. Zamiast tego chcesz udostępnić metody, które kontrolują, jak i kiedy pola i kolekcje właściwości mogą być aktualizowane i jakie zachowanie i akcje powinny wystąpić, gdy tak się stanie.

Ponieważ EF Core 1.1, aby spełnić te wymagania DDD, można mieć zwykłych pól w jednostkach zamiast właściwości publicznych. Jeśli nie chcesz, aby pole encji było dostępne z zewnątrz, można po prostu utworzyć atrybut lub pole zamiast właściwości. Można również użyć ustawiaczów właściwości prywatnych.

W podobny sposób można teraz mieć dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisane `IReadOnlyCollection<T>`jako `List<T>`, który jest wspierany przez prywatnego elementu członkowskiego pola dla kolekcji (jak a) w jednostce, która opiera się na EF dla trwałości. Poprzednie wersje entity framework wymagane właściwości `ICollection<T>`kolekcji do obsługi , co oznaczało, że każdy deweloper przy użyciu klasy jednostki nadrzędnej można dodać lub usunąć elementy za pośrednictwem jego kolekcji właściwości. Taka możliwość byłaby sprzeczna z zalecanymi wzorami w DDD.

Kolekcję prywatną można używać podczas ujawniania `IReadOnlyCollection<T>` obiektu tylko do odczytu, jak pokazano w poniższym przykładzie kodu:

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

Do `OrderItems` obiektu można uzyskać dostęp tylko `IReadOnlyCollection<OrderItem>`do odczytu za pomocą . Ten typ jest tylko do odczytu, więc jest chroniony przed regularnymi aktualizacjami zewnętrznymi.

EF Core umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczania" modelu domeny. Jest to czysty kod POCO .NET, ponieważ akcja mapowania jest implementowana w warstwie trwałości. W tej akcji mapowania należy skonfigurować mapowanie pól do bazy danych. W poniższym `OnModelCreating` przykładzie `OrderingContext` metody `OrderEntityTypeConfiguration` z i klasy `SetPropertyAccessMode` wywołanie nakazuje `OrderItems` EF Core dostęp do właściwości za pośrednictwem jego pola.

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

Podczas korzystania z pól zamiast właściwości, `OrderItem` jednostka jest utrwalona tak, jakby miała `List<OrderItem>` właściwość. Jednak udostępnia pojedynczy akcesor, `AddOrderItem` metoda dodawania nowych elementów do zamówienia. W rezultacie zachowanie i dane są powiązane ze sobą i będą spójne w całym kodzie aplikacji, który używa modelu domeny.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Implementowanie repozytoriów niestandardowych za pomocą programu Entity Framework Core

Na poziomie implementacji repozytorium jest po prostu klasą z kodem trwałości danych koordynowanym przez jednostkę pracy (DBContext w EF Core) podczas wykonywania aktualizacji, jak pokazano w następującej klasie:

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

Interfejs `IBuyerRepository` pochodzi z warstwy modelu domeny jako kontrakt. Jednak implementacja repozytorium odbywa się w warstwie trwałości i infrastruktury.

Ef DbContext pochodzi za pośrednictwem konstruktora za pośrednictwem iniekcji zależności. Jest on współużytkowane przez wiele repozytoriów w`ServiceLifetime.Scoped`tym samym zakresie żądań HTTP, dzięki jego `services.AddDbContext<>`domyślnemu okresowi istnienia ( ) w kontenerze IoC (który można również jawnie ustawić za pomocą ).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody implementacji w repozytorium (aktualizacje lub transakcje w porównaniu z kwerendami)

W ramach każdej klasy repozytorium należy umieścić metody trwałości, które aktualizują stan jednostek zawartych przez powiązane zagregowane. Pamiętaj, że istnieje relacja jeden do jednego między agregacją a powiązanym repozytorium. Należy wziąć pod uwagę, że obiekt jednostki głównej agregacji może mieć osadzone jednostki podrzędne w jego wykres EF. Na przykład kupujący może mieć wiele metod płatności jako powiązane jednostki podrzędne.

Ponieważ podejście do zamawiania mikrousługi w eShopOnContainers jest również oparte na CQS/CQRS, większość zapytań nie są implementowane w repozytoriach niestandardowych. Deweloperzy mają swobodę tworzenia zapytań i sprzężeń, których potrzebują dla warstwy prezentacji bez ograniczeń nałożonych przez agregaty, niestandardowe repozytoria na agregację i DDD w ogóle. Większość niestandardowych repozytoriów sugerowanych w tym przewodniku ma kilka metod aktualizacji lub transakcyjnych, ale tylko metody kwerendy potrzebne do uzyskania danych do aktualizacji. Na przykład repozytorium Nabywcy Repozytorium repozytorium implementuje FindAsync metody, ponieważ aplikacja musi wiedzieć, czy dany nabywca istnieje przed utworzeniem nowego nabywcy związane z zamówieniem.

Jednak metody rzeczywistych zapytań, aby uzyskać dane do wysłania do warstwy prezentacji lub aplikacji klienckich są implementowane, jak wspomniano, w zapytaniach CQRS na podstawie elastycznych zapytań przy użyciu Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Korzystanie z repozytorium niestandardowego a bezpośrednio przy użyciu EF DbContext

Entity Framework DbContext Klasa jest oparta na jednostki pracy i repozytorium wzorców i może być używany bezpośrednio z kodu, takich jak z ASP.NET core kontrolera MVC. Wzorce jednostki pracy i repozytorium powodują najprostszy kod, jak w mikrousługach katalogu CRUD w eShopOnContainers. W przypadkach, gdy chcesz najprostszy kod możliwe, można bezpośrednio użyć DbContext klasy, jak wielu deweloperów zrobić.

Jednak implementowanie repozytoriów niestandardowych zapewnia kilka korzyści podczas implementowania bardziej złożonych mikrousług lub aplikacji. Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, dzięki czemu jest oddzielona od warstw aplikacji i modelu domeny. Implementowanie tych wzorców może ułatwić korzystanie z repozytoriów makiety symulujących dostęp do bazy danych.

Na rysunku 7-18 widać różnice między nie przy użyciu repozytoriów (bezpośrednio przy użyciu EF DbContext) w porównaniu przy użyciu repozytoriów, co ułatwia mock tych repozytoriów.

![Diagram przedstawiający składniki i przepływ danych w dwóch repozytoriach.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Rysunek 7-18**. Używanie niestandardowych repozytoriów w porównaniu do zwykłego DbContext

Rysunek 7-18 pokazuje, że przy użyciu niestandardowego repozytorium dodaje warstwę abstrakcji, która może służyć do ułatwienia testowania przez szyderczy repozytorium. Istnieje wiele alternatyw podczas szyderstwa. Możesz drwić tylko repozytoria lub można drwić z całej jednostki pracy. Zwykle szydzenie tylko repozytoria wystarczy, a złożoność do abstrakcyjnego i pozorować całą jednostkę pracy zwykle nie jest potrzebna.

Później, gdy koncentrujemy się na warstwie aplikacji, zobaczysz, jak wstrzykiwanie zależności działa w ASP.NET Core i jak jest implementowany podczas korzystania z repozytoriów.

Krótko mówiąc, niestandardowe repozytoria umożliwiają łatwiejsze testowanie kodu za pomocą testów jednostkowych, na które stan warstwy danych nie ma wpływu. Jeśli uruchomisz testy, które również uzyskać dostęp do rzeczywistej bazy danych za pośrednictwem entity framework, nie są one testy jednostkowe, ale testy integracji, które są znacznie wolniejsze.

Jeśli używasz DbContext bezpośrednio, trzeba by mock go lub uruchomić testy jednostkowe przy użyciu programu SQL Server w pamięci z przewidywalnych danych dla testów jednostkowych. Ale szydzenie z DbContext lub kontrolowanie fałszywych danych wymaga więcej pracy niż szydzenie na poziomie repozytorium. Oczywiście zawsze można przetestować kontrolery MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Ef DbContext i IUnitOfPraca istnienia wystąpienia w kontenerze IoC

Obiekt `DbContext` (udostępniany `IUnitOfWork` jako obiekt) powinien być współużytkowane przez wiele repozytoriów w tym samym zakresie żądań HTTP. Na przykład jest to prawdą, gdy wykonywana operacja musi dotyczyć wielu agregatów lub po prostu dlatego, że używasz wielu wystąpień repozytorium. Należy również wspomnieć, `IUnitOfWork` że interfejs jest częścią warstwy domeny, a nie typu EF Core.

Aby to zrobić, wystąpienie `DbContext` obiektu musi mieć jego okres istnienia usługi ustawiona na ServiceLifetime.Scoped. Jest to domyślny okres `DbContext` istnienia `services.AddDbContext` podczas rejestrowania w kontenerze IoC `Startup.cs` z Metody ConfigureServices pliku w projekcie interfejsu API sieci Web ASP.NET Core. Ilustruje to poniższy kod.

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

Tryb wystąpienia DbContext nie powinien być skonfigurowany jako ServiceLifetime.Transient lub ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Okres istnienia wystąpienia repozytorium w kontenerze IoC

W podobny sposób okres istnienia repozytorium powinien być zwykle ustawiony jako zakres (InstancePerLifetimeScope w autofac). Może to być również przejściowy (InstancePerDependency w Autofac), ale usługa będzie bardziej wydajne w odniesieniu do pamięci podczas korzystania z okresu istnienia o określonym zakresie.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Przy użyciu okresu istnienia pojedynczego dla repozytorium może spowodować poważne problemy współbieżności, gdy DbContext jest ustawiona na zakres (InstancePerLifetimeScope) okres istnienia (domyślne okresy istnienia dla DBContext).

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Implementowanie repozytorium i jednostki wzorców pracy w ASP.NET aplikacji MVC** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathan Allen. Strategie wdrażania wzorca repozytorium z entity framework, dapper i łańcuch** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. Porównywanie okresów istnienia usługi kontenera core ASP.NET core z zakresami wystąpień kontenera IoC autofac** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Mapowanie tabeli

Mapowanie tabel identyfikuje dane tabeli, z których mają być wyszukiwane i zapisywane w bazie danych. Wcześniej był używany sposób, w jaki jednostki domeny (na przykład domena produktu lub zamówienia) mogą być używane do generowania schematu powiązanej bazy danych. EF jest silnie zaprojektowany wokół koncepcji *konwencji*. Konwencje odnoszą się do pytań takich jak "Jaka będzie nazwa stołu?" lub "Jaka właściwość jest kluczem podstawowym?" Konwencje są zazwyczaj oparte na nazwach konwencjonalnych. Na przykład jest to typowe dla klucza podstawowego, aby być właściwość, która kończy `Id`się .

Zgodnie z konwencją każda jednostka zostanie skonfigurowana do mapowania `DbSet<TEntity>` do tabeli o takiej samej nazwie jak właściwość, która udostępnia jednostkę w kontekście pochodnym. Jeśli `DbSet<TEntity>` dla danej jednostki nie jest podana żadna wartość, używana jest nazwa klasy.

### <a name="data-annotations-versus-fluent-api"></a>Adnotacje danych a płynny interfejs API

Istnieje wiele dodatkowych konwencji EF Core, a większość z nich można zmienić za pomocą adnotacji danych lub fluent API, zaimplementowane w ramach OnModelCreating metody.

Adnotacje danych muszą być używane w klasach modelu jednostki, co jest bardziej inwazyjny sposób z punktu widzenia DDD. Jest to spowodowane zanieczyszczone modelu adnotacjami danych związanych z bazy danych infrastruktury. Z drugiej strony Fluent interfejsu API jest wygodnym sposobem, aby zmienić większość konwencji i mapowania w warstwie infrastruktury trwałości danych, więc model jednostki będzie czysty i oddzielone od infrastruktury trwałości.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API i OnModelCreating metody

Jak wspomniano, w celu zmiany konwencji i mapowania, można użyć OnModelCreating metody w DbContext klasy.

Mikrousługa zamawiania w eShopOnContainers implementuje jawne mapowanie i konfigurację, w razie potrzeby, jak pokazano w poniższym kodzie.

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

Można ustawić wszystkie mapowania interfejsu API `OnModelCreating` Fluent w ramach tej samej metody, ale wskazane jest partycjonowanie tego kodu i wiele klas konfiguracji, po jednej na jednostkę, jak pokazano w przykładzie. Szczególnie w przypadku dużych modeli zaleca się, aby mieć oddzielne klasy konfiguracji do konfigurowania różnych typów jednostek.

Kod w przykładzie pokazuje kilka jawnych deklaracji i mapowania. Jednak ef core konwencje zrobić wiele z tych mapowań automatycznie, więc rzeczywisty kod, który będzie potrzebny w twoim przypadku może być mniejsza.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algorytm Hi/Lo w EF Core

Ciekawym aspektem kodu w poprzednim przykładzie jest to, że używa [algorytmu Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.

Algorytm Hi/Lo jest przydatny, gdy potrzebujesz unikatowych kluczy przed zatwierdzeniem zmian. Podsumowując, algorytm Hi-Lo przypisuje unikatowe identyfikatory do wierszy tabeli, nie będąc w zależności od natychmiastowego przechowywania wiersza w bazie danych. Dzięki temu można rozpocząć korzystanie z identyfikatorów od razu, jak to się dzieje w przypadku regularnych identyfikatorów sekwencyjnej bazy danych.

Algorytm Hi/Lo opisuje mechanizm uzyskiwania partii unikatowych identyfikatorów z powiązanej sekwencji bazy danych. Te identyfikatory są bezpieczne w użyciu, ponieważ baza danych gwarantuje unikatowość, więc nie będzie żadnych kolizji między użytkownikami. Algorytm ten jest interesujący z następujących powodów:

- Nie przerywa wzorca jednostki pracy.

- Pobiera identyfikatory sekwencji w partiach, aby zminimalizować rund do bazy danych.

- Generuje identyfikator czytelny dla człowieka, w przeciwieństwie do technik, które używają identyfikatorów GUID.

EF Core obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) z `UseHiLo` metodą, jak pokazano w poprzednim przykładzie.

### <a name="map-fields-instead-of-properties"></a>Mapuj pola zamiast właściwości

Dzięki tej funkcji, dostępnej od ef core 1.1, można bezpośrednio mapować kolumny do pól. Istnieje możliwość nie używać właściwości w klasie jednostki i tylko do mapowania kolumn z tabeli do pól. Typowym zastosowaniem dla tego byłoby pola prywatne dla każdego stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.

Można to zrobić za pomocą pojedynczych pól `List<>` lub kolekcji, takich jak pole. Ten punkt został wymieniony wcześniej, gdy omówiliśmy modelowanie klas modelu domeny, ale tutaj `PropertyAccessMode.Field` można zobaczyć, jak to mapowanie jest wykonywane z konfiguracją wyróżnioną w poprzednim kodzie.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Użyj właściwości cienia w EF Core, ukrytych na poziomie infrastruktury

Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki. Wartości i stany tych właściwości są utrzymywane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.

## <a name="implement-the-query-specification-pattern"></a>Implementowanie wzorca specyfikacji kwerendy

Jak wprowadzono wcześniej w sekcji projektu, wzorzec specyfikacji kwerendy jest wzorzec projektu opartego na domenie zaprojektowany jako miejsce, w którym można umieścić definicję kwerendy z opcjonalną logiką sortowania i stronicowania.

Wzorzec specyfikacji kwerendy definiuje kwerendę w obiekcie. Na przykład w celu hermetyzacji sstronicowanego zapytania, które wyszukuje niektóre produkty, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber, pageSize, filter itp.). Następnie w ramach dowolnej metody repozytorium (zwykle przeciążenie List() zaakceptuje IQuerySpecification i uruchomi oczekiwane zapytanie na podstawie tej specyfikacji.

Przykładem ogólnego interfejsu specyfikacji jest następujący kod z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

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

Następnie implementacja klasy podstawowej specyfikacji ogólnej jest następująca.

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

Poniższa specyfikacja ładuje jednostkę pojedynczego koszyka, pod którą podano identyfikator koszyka lub identyfikator kupującego, do którego należy koszyk. Chętnie [załaduje](/ef/core/querying/related-data) kolekcję `Items` kosza.

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

I wreszcie, można zobaczyć poniżej, jak ogólne repozytorium EF można użyć takiej specyfikacji do filtrowania i chętnie załadować dane związane z danego typu jednostki T.

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

Oprócz hermetyzacji logiki filtrowania, specyfikacja można określić kształt danych, które mają być zwracane, w tym właściwości, które mają być wypełniane.

Mimo że nie zaleca `IQueryable` się zwracania z repozytorium, jest całkowicie w porządku, aby użyć ich w repozytorium do tworzenia zestawu wyników. Możesz zobaczyć to podejście używane w List metody `IQueryable` powyżej, który używa wyrażeń pośrednich do tworzenia listy kwerendy zawiera przed wykonaniem kwerendy z kryteriami specyfikacji w ostatnim wierszu.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Mapowanie tabel** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Używanie HiLo do generowania kluczy za pomocą programu Entity Framework Core** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Pola zapasowe** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Zhermetyzowane kolekcje w core ramach encji** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Właściwości cienia** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Wzór specyfikacji** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Poprzedni](infrastructure-persistence-layer-design.md)
> [następny](nosql-database-persistence-infrastructure.md)
