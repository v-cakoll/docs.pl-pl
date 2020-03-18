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
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core

W przypadku korzystania z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, zaleca się wdrożenie warstwy trwałości na podstawie entity framework (EF). EF obsługuje LINQ i zapewnia silnie typowane obiekty dla modelu, a także uproszczone trwałości w bazie danych.

Entity Framework ma długą historię jako część .NET Framework. Korzystając z programu .NET Core, należy również użyć entity framework core, który działa w systemie Windows lub Linux w taki sam sposób jak .NET Core. EF Core jest kompletnym przepisaniem frameworku jednostek, zaimplementowanym o znacznie mniejszym rozmiarze i istotnych ulepszeniach w wydajności.

## <a name="introduction-to-entity-framework-core"></a>Wprowadzenie do rdzenia frameworkencji

Entity Framework (EF) Core jest lekką, rozszerzalne i międzyplatformowej wersji popularnej technologii dostępu do danych entity framework. Został on wprowadzony z .NET Core w połowie 2016 roku.

Ponieważ wprowadzenie do EF Core jest już dostępne w dokumentacji firmy Microsoft, tutaj po prostu podajemy łącza do tych informacji.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Rdzeń frameworku jednostki** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Wprowadzenie do ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **Klasa DbContext** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **Porównaj EF Core & EF6.x** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura w rdzeniu frameworkowym jednostek z perspektywy DDD

Z punktu widzenia DDD ważną zdolnością EF jest możliwość używania jednostek domeny POCO, znanych również w terminologii EF jako *jednostki poco code-first*. Jeśli używasz jednostek domeny POCO, klasy modelu domeny są nieświadomi trwałości, po [nieznajomości trwałości](https://deviq.com/persistence-ignorance/) i zasady [ignorancji infrastruktury.](https://ayende.com/blog/3137/infrastructure-ignorance)

Zgodnie z wzorcami DDD należy hermetyzować zachowanie domeny i reguły w samej klasie jednostki, dzięki czemu można kontrolować niezmienne, sprawdzania poprawności i reguły podczas uzyskiwania dostępu do dowolnej kolekcji. W związku z tym nie jest dobrą praktyką w DDD, aby umożliwić publiczny dostęp do kolekcji jednostek podrzędnych lub obiektów wartości. Zamiast tego chcesz udostępnić metody, które kontrolują, jak i kiedy pola i kolekcje właściwości mogą być aktualizowane i jakie zachowanie i akcje powinny wystąpić, gdy tak się stanie.

Ponieważ EF Core 1.1, aby spełnić te wymagania DDD, można mieć proste pola w jednostkach zamiast właściwości publicznych. Jeśli nie chcesz, aby pole encji było dostępne zewnętrznie, możesz po prostu utworzyć atrybut lub pole zamiast właściwości. Można również użyć wartości ustawiaczy własności prywatnej.

W podobny sposób można teraz mieć dostęp tylko do odczytu do `IReadOnlyCollection<T>`kolekcji przy użyciu właściwości publicznej wpisane jako `List<T>`, który jest wspierany przez członka pola prywatnego dla kolekcji (jak ) w jednostce, która opiera się na EF dla trwałości. Poprzednie wersje entity framework wymagane właściwości `ICollection<T>`kolekcji do obsługi , co oznaczało, że każdy deweloper przy użyciu klasy jednostki nadrzędnej można dodać lub usunąć elementy za pośrednictwem swoich kolekcji właściwości. Taka możliwość byłaby sprzeczna z zalecanymi wzorcami w DDD.

Kolekcji prywatnej można użyć podczas eksponowania obiektu tylko do `IReadOnlyCollection<T>` odczytu, jak pokazano w poniższym przykładzie kodu:

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

Należy pamiętać, że `OrderItems` właściwość jest dostępna tylko `IReadOnlyCollection<OrderItem>`jako tylko do odczytu przy użyciu . Ten typ jest tylko do odczytu, więc jest chroniony przed regularnymi aktualizacjami zewnętrznymi.

EF Core umożliwia mapowanie modelu domeny do fizycznej bazy danych bez "zanieczyszczania" modelu domeny. Jest to czysty kod .NET POCO, ponieważ akcja mapowania jest implementowana w warstwie trwałości. W tej akcji mapowania należy skonfigurować mapowanie pól do bazy danych. W poniższym przykładzie `OnModelCreating` metody `OrderingContext` from `OrderEntityTypeConfiguration` i klasy `SetPropertyAccessMode` wywołanie mówi EF `OrderItems` Core, aby uzyskać dostęp do właściwości za pośrednictwem jego pola.

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

W przypadku używania pól zamiast `OrderItem` właściwości jednostka jest zachowywana tak, jakby miała `List<OrderItem>` właściwość. Jednak udostępnia jeden akcesor, `AddOrderItem` metoda dodawania nowych elementów do zamówienia. W rezultacie zachowanie i dane są powiązane ze sobą i będą spójne w całym kodzie aplikacji, który używa modelu domeny.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Implementowanie niestandardowych repozytoriów za pomocą programu Entity Framework Core

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

Należy zauważyć, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako kontrakt. Jednak implementacja repozytorium odbywa się w warstwie trwałości i infrastruktury.

EF DbContext jest za pośrednictwem konstruktora za pomocą iniekcji zależności. Jest współużytkowany przez wiele repozytoriów w tym samym zakresie`ServiceLifetime.Scoped`żądania HTTP, dzięki jego domyślnemu okresowi istnienia ( ) w kontenerze IoC (który można również jawnie ustawić). `services.AddDbContext<>`

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody implementacji w repozytorium (aktualizacje lub transakcje a kwerendy)

W ramach każdej klasy repozytorium należy umieścić metody trwałości, które aktualizują stan jednostek zawartych w powiązanych agregacji. Pamiętaj, że istnieje relacja jeden-do-jednego między agregacji i powiązanych repozytorium. Należy wziąć pod uwagę, że obiekt jednostki głównej agregacji może mieć osadzone jednostki podrzędne w jego wykresie EF. Na przykład kupujący może mieć wiele metod płatności jako powiązane jednostki podrzędne.

Ponieważ podejście do mikrousługi zamawiania w eShopOnContainers jest również oparty na CQS/CQRS, większość zapytań nie są implementowane w repozytoriach niestandardowych. Deweloperzy mają swobodę tworzenia zapytań i sprzężeń potrzebnych do warstwy prezentacji bez ograniczeń nałożonych przez agregaty, niestandardowe repozytoria na agregato i Ogólnie DDD. Większość niestandardowych repozytoriów sugerowanych w tym przewodniku ma kilka metod aktualizacji lub transakcyjnych, ale tylko metody zapytania potrzebne do uzyskania danych do aktualizacji. Na przykład repozytorium BuyerRepository implementuje Metodę FindAsync, ponieważ aplikacja musi wiedzieć, czy istnieje określony nabywca przed utworzeniem nowego nabywcy związanego z zamówieniem.

Jednak prawdziwe metody kwerendy, aby uzyskać dane do wysyłania do warstwy prezentacji lub aplikacji klienckich są implementowane, jak wspomniano, w kwerendach CQRS na podstawie elastycznych zapytań przy użyciu Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Korzystanie z niestandardowego repozytorium w porównaniu z użyciem EF DbContext bezpośrednio

Klasa DbContext framework jednostki jest oparta na wzorcach Jednostki pracy i repozytorium i może być używana bezpośrednio z kodu, na przykład z ASP.NET kontrolera Core MVC. W ten sposób można utworzyć najprostszy kod, jak w mikrousługi katalogu CRUD w eShopOnContainers. W przypadkach, gdy chcesz najprostszy kod możliwe, można bezpośrednio użyć DbContext klasy, jak wielu deweloperów zrobić.

Jednak implementowanie niestandardowych repozytoriów zapewnia kilka korzyści podczas implementowania bardziej złożonych mikrousług lub aplikacji. Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, dzięki czemu jest oddzielona od warstwy modelu aplikacji i domeny. Implementowanie tych wzorców może ułatwić korzystanie z makiety repozytoriów symulujących dostęp do bazy danych.

Na rysunku 7-18 można zobaczyć różnice między nie przy użyciu repozytoriów (bezpośrednio przy użyciu EF DbContext) w porównaniu do korzystania z repozytoriów, które ułatwiają makiety tych repozytoriów.

![Diagram przedstawiający składniki i przepływ danych w dwóch repozytoriach.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Rysunek 7-18**. Korzystanie z niestandardowych repozytoriów w porównaniu z zwykłym DbContext

Rysunek 7-18 pokazuje, że za pomocą niestandardowego repozytorium dodaje warstwę abstrakcji, która może służyć do ułatwienia testowania przez szyderstwo repozytorium. Istnieje wiele alternatyw podczas szyderstwa. Można drwić tylko repozytoria lub można drwić całą jednostkę pracy. Zwykle wystarczy szyderczy tylko repozytoria, a złożoność do abstrakcyjnych i makiety całej jednostki pracy zwykle nie jest potrzebne.

Później, gdy skupimy się na warstwie aplikacji, zobaczysz, jak działa iniekcja zależności w ASP.NET Core i jak jest implementowana podczas korzystania z repozytoriów.

Krótko mówiąc, niestandardowe repozytoria umożliwiają łatwiejsze testowanie kodu za pomocą testów jednostkowych, na które nie ma wpływu stan warstwy danych. Po uruchomieniu testów, które również dostęp do rzeczywistej bazy danych za pośrednictwem struktury jednostki, nie są to testy jednostkowe, ale testy integracji, które są znacznie wolniejsze.

Jeśli używasz DbContext bezpośrednio, trzeba by makiety go lub do uruchamiania testów jednostkowych przy użyciu programu SQL Server w pamięci z przewidywalnych danych dla testów jednostkowych. Ale szyderczy DbContext lub kontrolowania fałszywych danych wymaga więcej pracy niż szyderczy na poziomie repozytorium. Oczywiście zawsze można przetestować kontrolery MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>EF DbContext i iUnitOfWork okres istnienia wystąpienia w kontenerze IoC

Obiekt `DbContext` (uwidaczni jako obiekt) `IUnitOfWork` powinny być współużytkowane przez wiele repozytoriów w tym samym zakresie żądania HTTP. Na przykład jest to prawda, gdy wykonywana operacja musi radzić sobie z wieloma agregatami lub po prostu dlatego, że używasz wielu wystąpień repozytorium. Należy również wspomnieć, `IUnitOfWork` że interfejs jest częścią warstwy domeny, a nie typu EF Core.

Aby to zrobić, wystąpienie `DbContext` obiektu musi mieć jego okres istnienia usługi ustawiony na ServiceLifetime.Scoped. Jest to domyślny okres istnienia podczas rejestrowania z `DbContext` w `services.AddDbContext` kontenerze `Startup.cs` IoC z ConfigureServices metody pliku w projekcie interfejsu API sieci Web ASP.NET. Ilustruje to poniższy kod.

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

W podobny sposób okres istnienia repozytorium zwykle powinny być ustawione jako zakres (InstancePerLifetimeScope w Autofac). Może to być również przejściowe (InstancePerDependency w Autofac), ale usługa będzie bardziej efektywne w odniesieniu do pamięci podczas korzystania z okresu istnienia o zakresie.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Należy zauważyć, że przy użyciu okresu istnienia singleton dla repozytorium może spowodować poważne problemy współbieżności, gdy DbContext jest ustawiony na zakres (InstancePerLifetimeScope) okres istnienia (domyślne okresy istnienia dla DBContext).

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Implementowanie repozytorium i jednostki wzorców pracy w ASP.NET aplikacji MVC** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathan Allen. Strategie wdrażania wzorca repozytorium z frameworkiem jednostek, dapperi i łańcuchem** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. Porównanie ASP.NET okresy istnienia kontenera Core IoC z zakresami wystąpienia kontenera Autofac IoC** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Mapowanie tabeli

Mapowanie tabeli identyfikuje dane tabeli, z których mają być przeszukiwane i zapisywane w bazie danych. Wcześniej widziałeś, jak jednostki domeny (na przykład domeny produktu lub zamówienia) mogą być używane do generowania schematu powiązanej bazy danych. EF jest silnie zaprojektowany wokół koncepcji *konwencji*. Konwencje dotyczą pytań takich jak "Jaka będzie nazwa tabeli?" lub "Jaka właściwość jest kluczem podstawowym?" Konwencje są zazwyczaj oparte na konwencjonalnych nazw, na przykład jest typowe dla klucza podstawowego, aby być właściwością, która kończy się identyfikatorem.

Zgodnie z konwencją każda jednostka zostanie skonfigurowana do mapowania `DbSet<TEntity>` do tabeli o tej samej nazwie co właściwość, która udostępnia jednostkę w kontekście pochodnym. Jeśli `DbSet<TEntity>` dla danej jednostki nie podano żadnej wartości, używana jest nazwa klasy.

### <a name="data-annotations-versus-fluent-api"></a>Adnotacje danych a interfejs API fluent

Istnieje wiele dodatkowych konwencji EF Core, a większość z nich można zmienić przy użyciu adnotacji danych lub fluent Interfejsu API, zaimplementowane w onmodelcreating metody.

Adnotacje danych muszą być używane w samych klasach modelu jednostki, co jest bardziej inwazyjnym sposobem z punktu widzenia DDD. Dzieje się tak, ponieważ zanieczyszczasz model adnotacjami danych związanymi z bazą danych infrastruktury. Z drugiej strony fluent interfejsu API jest wygodny sposób, aby zmienić większość konwencji i mapowania w warstwie infrastruktury trwałości danych, więc model jednostki będzie czysty i oddzielone od infrastruktury trwałości.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API i OnModelCreating metoda

Jak wspomniano, w celu zmiany konwencji i mapowania, można użyć OnModelCreating metody w DbContext klasy.

Mikrousługi zamawiania w eShopOnContainers implementuje jawne mapowanie i konfigurację, gdy jest to konieczne, jak pokazano w poniższym kodzie.

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

Można ustawić wszystkie mapowania interfejsu API `OnModelCreating` fluent w ramach tej samej metody, ale wskazane jest, aby podzielić ten kod i mieć wiele klas konfiguracji, po jednej na jednostkę, jak pokazano w przykładzie. Specjalnie dla dużych modeli zaleca się oddzielne klasy konfiguracji do konfigurowania różnych typów jednostek.

Kod w przykładzie pokazuje kilka jawnych deklaracji i mapowania. Jednak konwencje EF Core automatycznie wykonują wiele z tych mapowań, więc rzeczywisty kod, który będzie potrzebny w twoim przypadku, może być mniejszy.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algorytm Hi/Lo w EF Core

Ciekawym aspektem kodu w poprzednim przykładzie jest to, że używa [algorytmu Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.

Algorytm Hi/Lo jest przydatny, gdy potrzebujesz unikatowych kluczy przed zatwierdzeniem zmian. Jako podsumowanie algorytm Hi-Lo przypisuje unikatowe identyfikatory do wierszy tabeli, a nie w zależności od natychmiastowego przechowywania wiersza w bazie danych. Dzięki temu można rozpocząć korzystanie z identyfikatorów od razu, jak to się dzieje w przypadku regularnych sekwencyjnych identyfikatorów bazy danych.

Algorytm Hi/Lo opisuje mechanizm uzyskiwania partii unikatowych identyfikatorów z sekwencji powiązanej bazy danych. Identyfikatory te są bezpieczne w użyciu, ponieważ baza danych gwarantuje unikatowość, więc nie będzie żadnych kolizji między użytkownikami. Algorytm ten jest interesujący z tych powodów:

- Nie powoduje przerwania wzorca jednostki pracy.

- Pobiera identyfikatory sekwencji w partiach, aby zminimalizować rund do bazy danych.

- Generuje identyfikator czytelny dla człowieka, w przeciwieństwie do technik, które używają identyfikatorów GUID.

EF Core obsługuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) z `UseHiLo` metodą, jak pokazano w poprzednim przykładzie.

### <a name="map-fields-instead-of-properties"></a>Mapowanie pól zamiast właściwości

Dzięki tej funkcji, dostępnej od EF Core 1.1, można bezpośrednio mapować kolumny na pola. Istnieje możliwość nie używania właściwości w klasie jednostki i tylko do mapowania kolumn z tabeli na pola. Typowym zastosowaniem dla tego byłoby prywatne pola dla każdego stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.

Można to zrobić za pomocą pojedynczych pól `List<>` lub kolekcji, takich jak pole. Ten punkt został wymieniony wcześniej, gdy omówiliśmy modelowanie klas modelu domeny, ale tutaj `PropertyAccessMode.Field` można zobaczyć, jak to mapowanie jest wykonywane z konfiguracją wyróżnioną w poprzednim kodzie.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Użyj właściwości cienia w EF Core, ukrytych na poziomie infrastruktury

Właściwości cienia w EF Core są właściwości, które nie istnieją w modelu klasy jednostki. Wartości i stany tych właściwości są zachowywane wyłącznie w [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) klasy na poziomie infrastruktury.

## <a name="implement-the-query-specification-pattern"></a>Implementowanie wzorca specyfikacji kwerendy

Jak wprowadzono wcześniej w sekcji projektowania, wzorzec specyfikacji kwerendy jest wzorcem projektu opartym na domenie zaprojektowanym jako miejsce, w którym można umieścić definicję kwerendy z opcjonalną logiką sortowania i stronicowania.

Wzorzec specyfikacji kwerendy definiuje kwerendę w obiekcie. Na przykład, aby zhermetyzować stronicowane zapytanie, które wyszukuje niektóre produkty, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber, pageSize, filter itp.). Następnie w ramach dowolnej metody repozytorium (zwykle przeciążenia List() zaakceptuje specyfikację zapytania IQuerySpecification i uruchomi oczekiwane zapytanie na podstawie tej specyfikacji.

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

Następująca specyfikacja ładuje pojedynczy element koszyka, który otrzymuje identyfikator koszyka lub identyfikator kupującego, do którego należy koszyk. Z [niecierpliwością załaduje](https://docs.microsoft.com/ef/core/querying/related-data) kolekcję przedmiotów kosza.

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

I na koniec można zobaczyć poniżej, jak ogólne repozytorium EF można użyć takiej specyfikacji do filtrowania i chętnie ładowania danych związanych z danym typu jednostki T.

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

Oprócz logiki hermetyzacji filtrowania specyfikacja może określić kształt danych, które mają być zwracane, w tym właściwości do wypełnienia.

Chociaż nie zaleca się `IQueryable` powrotu z repozytorium, doskonale jest używać ich w repozytorium w celu zbudowania zestawu wyników. Można zobaczyć to podejście używane w List metody `IQueryable` powyżej, który używa wyrażeń pośrednich do tworzenia listy zapytań zawiera przed wykonaniem kwerendy z kryteriów specyfikacji w ostatnim wierszu.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Mapowanie tabeli** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Użyj Funkcji HiLo do generowania kluczy z rdzeniem struktury jednostek** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Pola podkładu** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Hermetyzowane kolekcje w rdzeniu frameworku jednostek** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Właściwości cienia** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Wzór specyfikacji** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Poprzedni](infrastructure-persistence-layer-design.md)
> [następny](nosql-database-persistence-infrastructure.md)
