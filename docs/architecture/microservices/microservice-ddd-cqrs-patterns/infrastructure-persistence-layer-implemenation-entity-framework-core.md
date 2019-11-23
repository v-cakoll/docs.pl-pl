---
title: Implementowanie warstwy trwałości infrastruktury za pomocą programu Entity Framework Core
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się ze szczegółami implementacji warstwy utrwalania infrastruktury przy użyciu Entity Framework Core.
ms.date: 10/08/2018
ms.openlocfilehash: b70ede6b47cbf990d0435aef841416c68f6439b4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737918"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Zaimplementuj warstwę trwałości infrastruktury za pomocą Entity Framework Core

W przypadku korzystania z relacyjnych baz danych, takich jak SQL Server, Oracle lub PostgreSQL, Zalecanym podejściem jest implementacja warstwy trwałości na podstawie Entity Framework (EF). Dr obsługuje LINQ i zapewnia obiekty silnie wpisane dla modelu, a także uproszczoną trwałość do bazy danych.

Entity Framework ma długą historię w ramach .NET Framework. W przypadku korzystania z platformy .NET Core należy również użyć Entity Framework Core, który działa w systemie Windows lub Linux w taki sam sposób, jak .NET Core. EF Core to pełny zapis Entity Framework, zaimplementowany z znacznie mniejszym wpływem i istotnymi ulepszeniami wydajności.

## <a name="introduction-to-entity-framework-core"></a>Wprowadzenie do Entity Framework Core

Entity Framework (EF) Core to lekka, rozszerzalna i wieloplatformowa wersja popularnej technologii dostępu do danych — Entity Framework. Wprowadzono ją z platformą .NET Core w połowie 2016.

Ponieważ wprowadzenie do EF Core jest już dostępne w dokumentacji firmy Microsoft, tutaj udostępniamy linki do tych informacji.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Entity Framework Core** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Wprowadzenie do ASP.NET Core i Entity Framework Core przy użyciu programu Visual Studio** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **Klasa DbContext** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **Porównanie \ EF Core & Ef6. x**
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura w Entity Framework Core z perspektywy DDD

Z punktu widzenia, ważną funkcją EF jest możliwość korzystania z jednostek domeny POCO, znanego również w terminologii EF jako jednostki POCO w *kodzie*. Jeśli używasz jednostek domeny POCO, klasy modelu domeny są trwałości-ignorujących, przestrzegając [Ignorujących trwałości](https://deviq.com/persistence-ignorance/) i zasad [ignorujących infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) .

Na wzorce DDD należy hermetyzować zachowanie domeny i reguły w samej klasie jednostki, aby można było sterować niektórymi, walidacjami i regułami podczas uzyskiwania dostępu do dowolnej kolekcji. W związku z tym nie jest dobrym zwyczajem w DDD, aby zezwalać na publiczny dostęp do kolekcji jednostek podrzędnych lub obiektów wartości. Zamiast tego należy udostępnić metody kontrolujące, jak i kiedy można aktualizować pola i kolekcje właściwości oraz jakie zachowanie i akcje powinny wystąpić, gdy wystąpi taka sytuacja.

Ponieważ EF Core 1,1, aby spełnić te wymagania dotyczące DDD, w jednostkach można używać zwykłych pól zamiast właściwości publicznych. Jeśli nie chcesz, aby pole jednostki było dostępne na zewnątrz, możesz po prostu utworzyć atrybut lub pole zamiast właściwości. Można również użyć własnych metod ustawiających właściwości.

W podobny sposób można teraz mieć dostęp tylko do odczytu do kolekcji przy użyciu właściwości publicznej wpisanej jako `IReadOnlyCollection<T>`, która jest objęta przez prywatny element członkowski dla kolekcji (na przykład `List<T>`) w jednostce, która opiera się na EF do trwałości. Poprzednie wersje Entity Framework wymaganych właściwości kolekcji do obsługi `ICollection<T>`, co oznacza, że każdy deweloper korzystający z klasy jednostki nadrzędnej może dodawać lub usuwać elementy za pośrednictwem swoich kolekcji właściwości. Taka możliwość będzie od zalecanych wzorców w DDD.

Możesz użyć prywatnej kolekcji podczas uwidaczniania obiektu `IReadOnlyCollection<T>` tylko do odczytu, jak pokazano w poniższym przykładzie kodu:

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

Należy pamiętać, że do właściwości `OrderItems` można uzyskać dostęp tylko do odczytu przy użyciu `IReadOnlyCollection<OrderItem>`. Ten typ jest tylko do odczytu, więc jest chroniony przed regularnymi aktualizacjami zewnętrznymi.

EF Core zapewnia sposób mapowania modelu domeny do fizycznej bazy danych bez "zanieczyszczania" modelu domeny. Jest to czysty kod POCO .NET, ponieważ akcja mapowania jest zaimplementowana w warstwie trwałości. W tej akcji mapowania należy skonfigurować mapowanie pola-do-bazy danych. W poniższym przykładzie metody `OnModelCreating` z `OrderingContext` i klasy `OrderEntityTypeConfiguration` wywołanie do `SetPropertyAccessMode` informuje EF Core o uzyskiwaniu dostępu do właściwości `OrderItems` za pośrednictwem pola.

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

Gdy używasz pól zamiast właściwości, jednostka `OrderItem` jest utrwalona tak, jakby miała Właściwość `List<OrderItem>`. Jednak uwidacznia on pojedynczy akcesor, metodę `AddOrderItem`, służącą do dodawania nowych elementów do zamówienia. W efekcie zachowanie i dane są powiązane ze sobą i będą spójne w całym kodzie aplikacji, który używa modelu domeny.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Implementowanie niestandardowych repozytoriów przy użyciu Entity Framework Core

Na poziomie implementacji repozytorium jest po prostu klasą z kodem trwałości danych koordynowanym przez jednostkę pracy (DbContext w EF Core) podczas przeprowadzania aktualizacji, jak pokazano w poniższej klasie:

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

Należy zauważyć, że interfejs IBuyerRepository pochodzi z warstwy modelu domeny jako kontraktu. Implementacja repozytorium jest jednak wykonywana z warstwy trwałości i infrastruktury.

Kontekst EF DBjest dostarczany przez Konstruktor poprzez wstrzyknięcie zależności. Jest ona udostępniana między wieloma repozytoriami w ramach tego samego zakresu żądania HTTP, dzięki czemu jego domyślny okres istnienia (`ServiceLifetime.Scoped`) w kontenerze IoC (który można także jawnie ustawić przy użyciu `services.AddDbContext<>`).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody implementacji w repozytorium (aktualizacje lub transakcje w porównaniu z zapytaniami)

W ramach każdej klasy repozytorium należy umieścić metody trwałości, które aktualizują stan jednostek zawartych w powiązanej agregacji. Należy pamiętać, że istnieje relacja jeden do jednego między agregacją i powiązanym repozytorium. Należy wziąć pod uwagę, że zagregowany obiekt jednostki głównej może mieć osadzone jednostki podrzędne w ramach jego grafu EF. Na przykład kupujący może mieć wiele metod płatności jako powiązanych jednostek podrzędnych.

Ponieważ podejście do mikrousługi porządkowania w eShopOnContainers opiera się również na CQS/CQRS, większość zapytań nie jest zaimplementowana w niestandardowych repozytoriach. Deweloperzy mogą uzyskać swobodę tworzenia zapytań i sprzężeń potrzebnych do warstwy prezentacji bez ograniczeń narzuconych przez agregacje, niestandardowe repozytoria na zagregowane i DDD w ogólności. Większość repozytoriów niestandardowych sugerowanych przez ten przewodnik ma kilka metod Update lub transakcyjnych, ale tylko metody zapytania potrzebne do aktualizacji danych. Na przykład repozytorium BuyerRepository implementuje metodę FindAsync, ponieważ aplikacja musi wiedzieć, czy konkretny kupujący istnieje przed utworzeniem nowego nabywcy związanego z kolejnością.

Jednak prawdziwe metody zapytań umożliwiające pobieranie danych do wysłania do warstwy prezentacji lub aplikacji klienckich są implementowane, jak wspomniano w zapytaniach CQRS na podstawie elastycznych zapytań przy użyciu Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Korzystanie z niestandardowego repozytorium i bezpośrednie używanie EF DbContext

Klasa DbContext Entity Framework dbopiera się na jednostkach wzorców pracy i repozytorium oraz może być używana bezpośrednio z poziomu kodu, na przykład z kontrolera ASP.NET Core MVC. Jest to sposób, w jaki można utworzyć najprostszy kod, tak jak w przypadku mikrousługi CRUD Catalog w eShopOnContainers. W przypadkach, gdy chcesz, aby najprostszy kod był możliwy, możesz chcieć bezpośrednio użyć klasy DbContext, tak jak wielu deweloperów.

Jednak wdrożenie repozytoriów niestandardowych zapewnia kilka korzyści w przypadku implementowania bardziej złożonych mikrousług lub aplikacji. Wzorce jednostki pracy i repozytorium są przeznaczone do hermetyzacji warstwy trwałości infrastruktury, aby była ona oddzielona od warstwy aplikacji i modelu domeny. Wdrożenie tych wzorców może ułatwić korzystanie z repozytoriów makiety, które symulują dostęp do bazy danych.

Na rysunku 7-18 można zobaczyć różnice między nieużywaniem repozytoriów (bezpośrednio przy użyciu EF DbContext), a nie za pomocą repozytoriów, które ułatwiają zasymulować te repozytoria.

![Diagram przedstawiający składniki i przepływu danych w dwóch repozytoriach.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Rysunek 7-18**. Używanie niestandardowych repozytoriów zamiast zwykłego DbContext

Rysunek 7-18 pokazuje, że za pomocą repozytorium niestandardowego dodaje warstwę abstrakcji, która może być używana do ułatwienia testowania przez imitację repozytorium. Podczas imitacji istnieje wiele wariantów. Można zasymulować tylko repozytoria lub można zasymulować całą jednostkę pracy. Zwykle imitacja tylko repozytoria jest wystarczająca, a złożoność abstrakcyjna i makieta całościowej jednostki pracy zwykle nie jest wymagana.

Później, gdy skupmy się na warstwie aplikacji, zobaczysz, jak iniekcja zależności działa w ASP.NET Core i jak jest zaimplementowana w przypadku korzystania z repozytoriów.

W krótkim przypadku niestandardowe repozytoria umożliwiają łatwiejsze testowanie kodu przy użyciu testów jednostkowych, które nie mają wpływu na stan warstwy danych. Jeśli uruchamiasz testy, które również uzyskują dostęp do rzeczywistej bazy danych za pomocą Entity Framework, nie są one testami jednostkowymi, ale testy integracji, które są znacznie wolniejsze.

Jeśli używasz DbContext bezpośrednio, musisz go zasymulować lub uruchomić testy jednostkowe za pomocą SQL Server w pamięci z przewidywalnymi danymi dla testów jednostkowych. Jednak imitacja DbContext lub kontrolowanie danych fałszywych wymaga większego działania niż imitacja na poziomie repozytorium. Oczywiście można zawsze testować kontrolery MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Okres istnienia wystąpienia elementu EF DbContext i IUnitOfWork w kontenerze IoC

Obiekt `DbContext` (uwidoczniony jako obiekt `IUnitOfWork`) powinien być współużytkowany między wieloma repozytoriami w ramach tego samego zakresu żądania HTTP. Na przykład dzieje się tak, gdy wykonywana operacja musi zająć się wieloma agregacjami lub po prostu, ponieważ jest używane wiele wystąpień repozytorium. Należy również pamiętać, że interfejs `IUnitOfWork` jest częścią warstwy domeny, a nie typu EF Core.

W tym celu wystąpienie obiektu `DbContext` musi mieć ustawiony okres istnienia usługi na wartość servicelifetime. zakres. Jest to domyślny okres istnienia podczas rejestrowania `DbContext` z `services.AddDbContext` w kontenerze IoC z metody ConfigureServices pliku `Startup.cs` w projekcie interfejsu API sieci Web ASP.NET Core. Ilustruje to poniższy kod.

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

Tryb tworzenia wystąpień DbContext nie powinien być skonfigurowany jako servicelifetime. przejściowy lub servicelifetime. singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Okres istnienia wystąpienia repozytorium w kontenerze IoC

W podobny sposób okres istnienia repozytorium powinien być zazwyczaj ustawiany jako zakres (InstancePerLifetimeScope w Autofac). Może to być również przejściowe (InstancePerDependency w Autofac), ale usługa będzie bardziej wydajna w zakresie pamięci w przypadku korzystania z okresu istnienia w zakresie.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Należy pamiętać, że użycie pojedynczego okresu istnienia dla repozytorium może spowodować poważne problemy współbieżności, gdy dla kontekstu DbContext ustawiono zakres (InstancePerLifetimeScope) okres istnienia (domyślne okresy istnienia dla kontekstu DbContext).

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Implementowanie wzorców repozytorium i jednostki pracy w aplikacji ASP.NET MVC** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathana. Strategie implementacji dla wzorca repozytorium z Entity Framework, Dapper i łańcucha** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de La Torre. Porównanie ASP.NET Core okresów istnienia usługi kontenera IoC z zakresem wystąpień kontenera Autofac IoC** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Mapowanie tabeli

Mapowanie tabeli identyfikuje dane tabeli, z których mają być wysyłane zapytania i zapisane w bazie danych. Wcześniej pokazano, jak jednostki domeny (na przykład produkt lub domena zamówienia) mogą być używane do generowania powiązanego schematu bazy danych. EF jest silnie zaprojektowana wokół koncepcji *Konwencji*. Konwencje dotyczące adresów, takich jak "Jaka będzie nazwa tabeli?" lub "Jaka właściwość jest kluczem podstawowym?" Konwencje zwykle opierają się na nazwach konwencjonalnych — na przykład, że klucz podstawowy ma być właściwością kończącą się identyfikatorem.

Zgodnie z Konwencją każda jednostka zostanie skonfigurowana do mapowania na tabelę o tej samej nazwie co Właściwość `DbSet<TEntity>`, która uwidacznia jednostkę w kontekście pochodnym. Jeśli dla danej jednostki nie podano wartości `DbSet<TEntity>`, używana jest nazwa klasy.

### <a name="data-annotations-versus-fluent-api"></a>Adnotacje danych a interfejs API Fluent

Istnieje wiele dodatkowych Konwencji EF Core i większość z nich można zmienić za pomocą adnotacji danych lub interfejsu API Fluent wdrożonych w ramach metody OnModelCreating.

Adnotacje danych muszą być używane w samych klasach modelu jednostki, co jest bardziej nieinwazyjne od drogi punktu widzenia. Dzieje się tak dlatego, że jesteś w trakcie zanieczyszczania modelu za pomocą adnotacji danych związanych z bazą danych infrastruktury. Z drugiej strony interfejs API Fluent jest wygodnym sposobem zmiany większości Konwencji i mapowań w warstwie infrastruktury trwałości danych, więc model jednostki będzie czysty i niezależny od infrastruktury trwałości.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Interfejs API Fluent i Metoda OnModelCreating

Jak wspomniano, aby zmienić konwencje i mapowania, można użyć metody OnModelCreating w klasie DbContext.

Mikrousługa porządkowania w eShopOnContainers implementuje jawne mapowanie i konfigurację, w razie konieczności, jak pokazano w poniższym kodzie.

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

Można ustawić wszystkie mapowania interfejsu API Fluent w ramach tej samej metody OnModelCreating, ale zaleca się, aby podzielić ten kod i mieć wiele klas konfiguracji, jeden na jednostkę, jak pokazano w przykładzie. Szczególnie w przypadku dużych modeli zaleca się posiadanie oddzielnych klas konfiguracji do konfigurowania różnych typów jednostek.

Kod w przykładzie pokazuje kilka jawnych deklaracji i mapowania. Jednakże konwencje EF Core automatycznie wykonują wiele mapowań, więc rzeczywisty kod, który będzie potrzebny w przypadku, może być mniejszy.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algorytm Hi/Lo w EF Core

Interesujący aspekt kodu w poprzednim przykładzie polega na tym, że używa [algorytmu Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generowania kluczy.

Algorytm Hi/Lo jest przydatny, gdy potrzebne są unikatowe klucze przed zatwierdzeniem zmian. Podsumowując, algorytm Hi-Lo przypisuje unikatowe identyfikatory do wierszy tabeli, a nie w zależności od tego, czy wiersz jest natychmiast umieszczany w bazie danych. Dzięki temu można od razu zacząć korzystać z identyfikatorów, tak jak w przypadku zwykłych sekwencyjnych identyfikatorów baz danych.

Algorytm Hi/Lo opisuje mechanizm pobierania partii unikatowych identyfikatorów z powiązanej sekwencji bazy danych. Te identyfikatory są bezpieczne, ponieważ baza danych gwarantuje unikatowość, dlatego nie będzie żadnych kolizji między użytkownikami. Ten algorytm jest interesujący z następujących powodów:

- Nie powoduje zerwania wzorca jednostki pracy.

- Uzyskuje identyfikatory sekwencji w partiach, aby zminimalizować liczbę rund do bazy danych.

- Generuje on czytelny dla człowieka identyfikator, w przeciwieństwie do technik, które używają identyfikatorów GUID.

EF Core obsługuje [Hilo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) za pomocą metody ForSqlServerUseSequenceHiLo, jak pokazano w powyższym przykładzie.

### <a name="map-fields-instead-of-properties"></a>Mapuj pola zamiast właściwości

Korzystając z tej funkcji, dostępnej od EF Core 1,1, można bezpośrednio mapować kolumny do pól. Nie można używać właściwości w klasie Entity, a jedynie do mapowania kolumn z tabeli do pól. Typowym zastosowaniem tego elementu byłyby pola prywatne dla dowolnego stanu wewnętrznego, do którego nie trzeba uzyskiwać dostępu poza jednostką.

Można to zrobić przy użyciu pojedynczych pól lub kolekcji, takich jak pole `List<>`. Ten punkt został wymieniony wcześniej podczas omawiania modelowania klas modelu domeny, ale w tym miejscu można zobaczyć, jak to mapowanie jest wykonywane z konfiguracją `PropertyAccessMode.Field` wyróżnioną w poprzednim kodzie.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Używanie właściwości cienia w EF Core, ukryte na poziomie infrastruktury

Właściwości cienia w EF Core są właściwościami, które nie istnieją w modelu klasy jednostki. Wartości i Stany tych właściwości są utrzymywane wyłącznie w klasie [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) na poziomie infrastruktury.

## <a name="implement-the-query-specification-pattern"></a>Implementowanie wzorca specyfikacji zapytania

Zgodnie z opisem we wcześniejszej części projektu wzorzec specyfikacji zapytania jest oparty na domenie Wzorzec projektowy zaprojektowany jako miejsce, w którym można umieścić definicję zapytania z opcjonalną logiką sortowania i stronicowania.

Wzorzec specyfikacji zapytania definiuje zapytanie w obiekcie. Na przykład w celu hermetyzacji zapytania stronicowanego, które wyszukuje niektóre produkty, można utworzyć specyfikację PagedProduct, która przyjmuje niezbędne parametry wejściowe (pageNumber, pageSize, Filter itp.). Następnie w ramach dowolnej metody repozytorium (zazwyczaj Przeciążenie listy () przyjmuje IQuerySpecification i uruchamia oczekiwane zapytanie na podstawie tej specyfikacji.

Przykładem interfejsu specyfikacji ogólnej jest Poniższy kod z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

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

Poniższa specyfikacja ładuje jednostkę pojedynczego koszyka z IDENTYFIKATORem koszyka lub IDENTYFIKATORem nabywcy, do którego należy koszyk. Będzie [eagerly ładowanie](https://docs.microsoft.com/ef/core/querying/related-data) kolekcji elementów koszyka.

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

Na koniec można zobaczyć poniżej, jak ogólne repozytorium EF może użyć takiej specyfikacji do filtrowania i eager danych związanych z danym typem jednostki T.

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

Oprócz hermetyzacji logiki filtrowania, Specyfikacja może określić kształt danych do zwrócenia, w tym właściwości do wypełnienia.

Chociaż nie zaleca się zwracania platformy IQueryable z repozytorium, w celu utworzenia zestawu wyników doskonale dobrze jest używać ich w ramach repozytorium. To podejście można zobaczyć w powyższej metodzie list, która używa pośrednich wyrażeń IQueryable, aby utworzyć listę instrukcji include przed wykonaniem zapytania przy użyciu kryteriów specyfikacji w ostatnim wierszu.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Mapowanie tabeli** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Użyj Hilo, aby generować klucze z Entity Framework Core** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Pola zapasowe** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Kolekcje hermetyzowane w Entity Framework Core** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Właściwości cienia** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Wzorzec specyfikacji** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Poprzedni](infrastructure-persistence-layer-design.md)
> [Następny](nosql-database-persistence-infrastructure.md)
