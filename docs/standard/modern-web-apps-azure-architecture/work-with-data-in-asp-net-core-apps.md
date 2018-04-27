---
title: Praca z danymi w aplikacjach Core ASP.NET
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Praca z danymi w asp
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7d160d23808832ff6456e5c95f6e5ed5f4d44fa5
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Praca z danymi w aplikacjach platformy ASP.NET Core

> "Danych należy cenny i trwa dłużej niż samych systemów".

Timowi Berners Lewandowski

## <a name="summary"></a>Podsumowanie

Dostęp do danych jest ważnym elementem prawie każdej aplikacji. Platformy ASP.NET Core obsługuje wiele różnych opcji dostępu do danych, w tym Entity Framework Core (a także Entity Framework 6) i pracować z dowolnego .NET framework dostępu do danych. Wybór danych dostęp framework do użycia zależy od potrzeb aplikacji. Abstrakcyjność te wybory w projektach ApplicationCore i interfejsu użytkownika i hermetyzuje szczegóły implementacji w infrastrukturze, pomaga utworzyć luźno powiązanych, testować oprogramowania.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (w przypadku relacyjnych baz danych)

Jeśli piszesz nowej aplikacji platformy ASP.NET Core, który wymaga do pracy z danych relacyjnych Entity Framework Core (EF rdzeń) jest zalecany sposób dostępu do danych aplikacji. Podstawowe EF jest obiektów relacyjnych mapowania (O/RM), który umożliwia deweloperom platformy .NET utrwalania obiektów do i z źródła danych. Eliminuje potrzebę większość kodu dostępu do danych, deweloperzy zazwyczaj musi zapisać. Podobnie jak platformy ASP.NET Core EF Core została ponownie napisana od podstaw Obsługa modularnej aplikacji dla wielu platform. Dodaj go do aplikacji jako pakietu NuGet, ją skonfigurować w uruchamiania i żądania za pomocą iniekcji zależności wszędzie tam, gdzie będzie potrzebny.

Aby używać EF Core z bazy danych programu SQL Server, uruchom następujące polecenie dotnet w interfejsu wiersza polecenia:

Pakiet Microsoft.EntityFrameworkCore.SqlServer dodać DotNet

Aby dodać obsługę InMemory źródła danych, do testowania:

Pakiet Microsoft.EntityFrameworkCore.InMemory dodać DotNet

### <a name="the-dbcontext"></a>DbContext

Aby pracować z EF Core, konieczne jest podklasą klasy DbContext. Ta klasa zawiera reprezentujący kolekcje jednostek, który aplikacja będzie działać z właściwości. Przykładowe eShopOnWeb obejmuje CatalogContext z kolekcji elementów, marek i typy:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

Twoje DbContext musi mieć konstruktora akceptującego DbContextOptions i przekazać ten argument do konstruktora podstawowego typu DbContext. Należy pamiętać, że jeśli masz tylko jedną DbContext w aplikacji, można przekazać wystąpienia DbContextOptions, ale jeśli masz więcej niż jeden należy użyć ogólnego DbContextOptions<T> typu, przekazując danego typu DbContext jako parametr ogólny.

### <a name="configuring-ef-core"></a>Konfigurowanie EF Core

W aplikacji platformy ASP.NET Core zwykle skonfigurujesz EF Core w metodę ConfigureServices. Podstawowe EF używa DbContextOptionsBuilder, która obsługuje kilka metod rozszerzenia przydatne uprościć konfigurację. Aby skonfigurować CatalogContext do korzystania z bazy danych programu SQL Server z użyciem parametrów połączenia określonych w konfiguracji, czy Dodaj następujący kod do ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Korzystanie z bazy danych w pamięci:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po zainstalowaniu Core EF, typ podrzędny typu DbContext utworzone i skonfigurowane w ConfigureServices, można przystąpić do użycia EF Core. Wystąpienie typu DbContext, w dowolnej usługi, który musi on zażądać i rozpocząć pracę z utrwalonego za pomocą LINQ, tak jakby były to po prostu w kolekcji jednostek. Podstawowe EF działa tłumaczenia wyrażenia LINQ do zapytania SQL do przechowywania i pobierania danych.

Widać zapytania EF Core jest wykonywany, konfigurując Rejestrator i zapewnienia jego poziom jest ustawiony na co najmniej informacje, jak pokazano w rysunek 8-1.

![](./media/image8-1.png)

Rysunek 8-1 rejestrowanie podstawowych EF zapytania do konsoli

### <a name="fetching-and-storing-data"></a>Trwa pobieranie i zapisywanie danych

Pobieranie danych z EF Core, dostęp do odpowiedniej właściwości i użyj rozszerzenia LINQ, aby przefiltrować wynik. Umożliwia także LINQ do wykonywania projekcji, przekształcanie wyników z jednego typu na inny. Poniższy przykład czy pobrać CatalogBrands, uporządkowanych według nazwy, filtrowane według ich właściwości Enabled i rzutowany na typ SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Jest ważne w powyższym przykładzie, aby dodać wywołanie ToListAsync Aby natychmiast wykonać zapytanie. W przeciwnym razie instrukcji przypisze IQueryable<SelectListItem> do brandItems, które nie zostaną wykonane do czasu jej wyliczeniu. Brak zalet i wad do zwracania wyników IQueryable z metod. Dzięki temu zapytania, które utworzy EF Core dalsze można zmodyfikować, ale może również spowodować błędy występujące tylko w czasie wykonywania, jeśli działania są dodawane do zapytania, które nie może dokonywać translacji EF Core. Zazwyczaj bezpieczniej do przekazania wszystkie filtry do metody wykonywania dostępu do danych, a następnie powrót z powrotem kolekcji w pamięci (na przykład<T>) w wyniku.

Podstawowe EF śledzi zmiany na jednostek, który pobiera go z magazynu trwałego. Można zapisać zmian śledzonych jednostki, po prostu Wywołaj metodę SaveChanges dla kontekstu DbContext, upewniając się, że jest to samo wystąpienie typu DbContext, które zostało użyte do pobierania jednostki. Dodawanie i usuwanie jednostek jest bezpośrednio na odpowiedniej właściwości DbSet ponownie w wyniku wywołania metody SaveChanges można wykonać polecenia bazy danych. W poniższym przykładzie pokazano, dodawanie, aktualizowanie i usuwanie jednostek z magazynu trwałego.

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

Jądro EF obsługuje zarówno synchroniczne i metod asynchronicznych pobieranie i zapisywanie. W aplikacji sieci web zaleca się wzorca async/await za pomocą metody asynchroniczne, dzięki czemu wątków serwera sieci web nie są blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.

### <a name="fetching-related-data"></a>Pobieranie danych pokrewne

Gdy EF Core pobiera jednostki, wypełnienie wszystkich właściwości, które są przechowywane bezpośrednio z tego obiektu w bazie danych. Właściwości nawigacji, takie jak listy z powiązanych jednostek nie są wypełnione i może być ich ma wartość null. Dzięki temu EF Core nie pobieranie więcej danych niż jest potrzebny, który jest szczególnie ważne w przypadku aplikacji sieci web, które musi szybko przetwarzają żądania i zwracać odpowiedzi wydajne. Aby uwzględnić relacje z jednostki przy użyciu *wczesny ładowania*, określ właściwość przy użyciu metody rozszerzenia Include w zapytaniu, jak pokazano:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Może zawierać wiele relacji i mogą również obejmować relacje podrzędne za pomocą ThenInclude. Podstawowe EF wykona pojedynczego zapytania można pobrać Wynikowy zestaw jednostek.

Inną opcją w przypadku ładowania danych pokrewnych jest użycie *jawnego ładowania*. Jawne ładowania umożliwia ładowanie dodatkowe dane do jednostki, który już został pobrany. Ponieważ ten proces obejmuje oddzielne żądanie do bazy danych, nie jest zalecane dla aplikacji sieci web, które należy zminimalizować liczbę baz danych rund wprowadzone na żądanie.

*Powolne ładowanie* jest funkcją, która automatycznie ładuje powiązanych danych, ponieważ jest odwoływany przez aplikację. Nie jest aktualnie Nieobsługiwany przez podstawowe EF, ale jako z jawnego ładowania powinien zwykle zostać wyłączony dla aplikacji sieci web.

### <a name="resilient-connections"></a>Elastyczne połączenia

Zasobów zewnętrznych, takich jak bazy danych SQL co pewien czas mogą być niedostępne. W wypadku tymczasowej niedostępności aplikacje mogą używać logika ponowień, aby uniknąć, który wywołał wyjątek. Ta metoda jest często określana jako *elastyczności połączenia*. Można zaimplementować Twojej [własnych ponownie za pomocą wykładniczego wycofywania](https://docs.microsoft.com/azure/architecture/patterns/retry) technika, próbując rety z rośnie wykładniczo czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób. Ta metoda obejmuje fakt, że zasobów w chmurze mogą sporadycznie być niedostępne w krótkich okresach czasu, co spowoduje niepowodzenie niektórych żądań.

Dla bazy danych SQL Azure programu Entity Framework Core zawiera już logiki odporności i ponów próbę połączenia wewnętrznej bazy danych. Jednak musisz włączyć strategia wykonywania programu Entity Framework dla każdego połączenia DbContext, jeśli mają odporność połączeń EF Core.

Na przykład następujący kod na poziomie połączenia EF Core umożliwia elastyczne połączeń z serwerem SQL, które są zwalniane, jeśli połączenie nie powiedzie się.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie wykonywania i jawnych transakcji przy użyciu BeginTransaction i wielu DbContexts 
  
  Po włączeniu ponownych prób w połączeniach EF Core każdej operacji wykonywanych przy użyciu EF Core staje się działania można spróbować ponownie. Jeśli wystąpi błąd przejściowy, każdego zapytania i każde wywołanie metody SaveChanges zostanie ponowiona jako jednostka.
  
  Jednak jeśli kod inicjuje transakcji za pomocą BeginTransaction, definiowania grupy działań, które muszą być traktowane jako jednostka — wszystkie elementy wewnątrz transakcji została wycofana, jeśli wystąpi błąd. Jeśli próba wykonania tej transakcji, używając strategii wykonywania EF (zasady ponawiania) i obejmują SaveChanges kilka z wielu DbContexts w nim, zostanie wyświetlony następujący wyjątek.

System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostki można spróbować ponownie.

Rozwiązanie to ręczne wywoływanie strategia wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana. Jeśli wystąpi błąd przejściowy, strategia wykonywania zostaną wywołane delegat ponownie. Poniższy kod przedstawia sposób wykonania tego podejścia:

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

Jest first DbContext \_catalogContext, a drugi DbContext znajduje się w \_integrationEventLogService obiektu. Na koniec zatwierdzenia akcji, będzie można wykonać wiele DbContexts i używanie strategii wykonywania EF.

> ### <a name="references--entity-framework-core"></a>Odwołania — Entity Framework Core
> - **Dokumentacja Core EF**  
> <https://docs.microsoft.com/ef/>
> - **EF rdzeni: Dane dotyczące**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Unikaj ładowania opóźnionego jednostek w aplikacjach ASPNET**  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>Podstawowych funkcji EF lub micro ORM?

Podstawowe EF jest doskonałym wyborem do zarządzania trwałości i w większości przypadków hermetyzuje Szczegóły bazy danych z deweloperzy aplikacji, nie jest to tylko możliwe. Popularne typu open source alternatywą jest [Dapper](https://github.com/StackExchange/Dapper), tak zwane ORM micro. Micro-ORM to lekkie, mniej kompletne narzędzie do mapowania obiektów struktur danych. W przypadku Dapper jego celów skupić się na wydajność, a nie w pełni hermetyzując odpowiadającego jej zapytania projekt używa do pobierania i aktualizowania danych. Ponieważ go nie jako abstract SQL od dewelopera, Dapper "zbliżonej do systemu operacyjnego" i umożliwia deweloperom pisanie dokładnie operacja dostępu do zapytań, które mają być użyte dla podanych danych.

Podstawowe EF ma dwie funkcje znaczących zapewnia które oddzieli go od Dapper, ale również dodać do jego zmniejszenie wydajności. Pierwsza to tłumaczenia z wyrażenia LINQ do SQL. Te tłumaczenia są buforowane, ale mimo tego istnieje narzut przy wykonywaniu ich po raz pierwszy. Drugim jest śledzenia zmian jednostek (dzięki czemu można wygenerować instrukcji update wydajne). To zachowanie można wyłączyć dla określonego zapytania za pomocą rozszerzenia AsNotTracking. Podstawowe EF generuje również zapytania SQL, które są zazwyczaj bardzo wydajny i w każdym przypadku doskonale akceptowalne z punktu widzenia wydajności, ale jeśli konieczne drobne kontrolę nad dokładne zapytanie do wykonania, można przekazać niestandardowe SQL (lub procedurę składowaną) przy użyciu EF Podstawowe, zbyt. W takim przypadku nadal Dapper outperforms EF Core, ale tylko nieznacznie. Przedstawia Julie Lerman niektóre dane dotyczące wydajności w jej może artykuł w witrynie MSDN 2016 [Dapper, Entity Framework oraz aplikacje hybrydowe](https://msdn.microsoft.com/magazine/mt703432.aspx). Dodatkowych testów porównawczych danych o wydajności dla różnych metod dostępu do danych można znaleźć w [Dapper lokacji](https://github.com/StackExchange/Dapper).

Aby zobaczyć, jak składnia Dapper różni się od wartości podstawowej EF, należy wziąć pod uwagę następujące dwie wersje tej samej metody do pobierania listy elementów:

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

Potrzebne do utworzenia bardziej złożonych wykresów obiektów z Dapper, należy napisać samodzielnie skojarzonych kwerend (w przeciwieństwie do dodawania dołączania, jak w programie EF Core). Jest to obsługiwane za pomocą różnych składni, włączając funkcję Multi mapowania umożliwiające mapowania poszczególnych wierszy na wiele obiektów mapowane. Przykładowo podana klasy Post z właściwością właściciela typu użytkownika, następujące instrukcje SQL zwróci wszystkich niezbędnych danych:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Każdego zwróconego wiersza zawiera dane użytkownika i Post. Ponieważ dane użytkownika powinien być dołączony do danych Post za pomocą właściwości jego właściciel, jest używana następująca funkcja:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Listy pełnego kodu mają być zwracane zbiór wpisów z ich właściwości Owner wypełniony danymi skojarzonego użytkownika mogą być następujące:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Ponieważ zapewnia hermetyzację mniej Dapper wymaga deweloperzy dowiedzieć się więcej o jak są przechowywane ich dane, jak skutecznie wysyłać zapytania i zapisać więcej kod, aby go pobrać. Po zmianie modelu, a nie po prostu tworzenie nowych migracji (inna funkcja EF Core) i/lub aktualizowanie informacji o mapowaniu w jednym miejscu DbContext, należy zaktualizować każdego zapytania, które jest w pełni funkcjonalne. Te zapytania ma nie gwarancje czas kompilacji, w związku z ich mogą być dzielone w czasie wykonywania w odpowiedzi na zmiany do modelu lub bazy danych, co utrudnia szybko wykrywać błędy. W zamian za te kompromisy Dapper oferuje bardzo duża wydajność.

Dla większości aplikacji, a większość części prawie wszystkie aplikacje EF Core oferuje akceptowalną wydajność. W związku z tym korzyści produktywności deweloperów prawdopodobnie przeważają jego zmniejszenie wydajności. Dla zapytania, które mogą korzystać z pamięci podręcznej, rzeczywiste zapytanie może można wykonywać tylko niewielki procent czasu, wprowadzenie niewielkich zapytania moot różnic w wydajności.

## <a name="sql-or-nosql"></a>Bazy danych SQL lub NoSQL

Tradycyjnie relacyjnych baz danych, takich jak SQL Server ma zdominowany witryny marketplace w celu przechowywania danych, ale nie są dostępne rozwiązania tylko. Bazy danych NoSQL, takich jak [MongoDB](https://www.mongodb.com/what-is-mongodb) oferują różne podejścia do przechowywania obiektów. Zamiast obiektów mapowania tabel oraz wiersze, inną opcją jest serializować wykres całego obiektu, a następnie zapisz wynik. Zalety tego podejścia są co najmniej początkowo prostoty i wydajności. Jest oczywiście łatwiejsze do przechowywania pojedynczego serializacji obiektu z kluczem niż aby Rozłóż obiekt na wiele tabel z relacjami i aktualizacji oraz wiersze, które zostały zmienione od ostatniego obiektu pobrany z bazy danych. Podobnie Pobieranie i deserializację pojedynczego obiektu z magazynu opartego na kluczach jest zwykle szybsze i prostsze niż złożonych sprzężeń lub wiele zapytań bazy danych, wymagane pełni utworzenie tego samego obiektu z relacyjnej bazy danych. Brak blokad lub transakcji lub stałego schematu powoduje bazy danych NoSQL bardzo nadającymi się do skalowania obejmującego wiele maszyn, obsługa bardzo dużych zestawów danych.

Z drugiej strony bazy danych NoSQL (zwykle są one nazywane) mają swoje wady. Relacyjnych baz danych użyj normalizacji, aby wymusić spójność i uniknąć duplikowania danych. Zmniejsza całkowity rozmiar bazy danych i zapewnia, że aktualizacje do udostępnionych danych są dostępne natychmiast w całej bazy danych. Relacyjnej bazy danych tabeli adresów może odwołać się do kraju tabeli przez identyfikator, taki sposób, że jeśli zmieniono nazwę kraju, rekordów adresów będą korzystać z aktualizacji bez sobą konieczności aktualizacji. Jednak w bazie danych NoSQL adres i skojarzone kraj może można serializować wiele obiektów przechowywanych w ramach. Aktualizacja nazwy kraju wymagają wszystkie takie obiekty zaktualizowane, zamiast pojedynczy wiersz. Relacyjnych baz danych można również zapewnienia integralności relacyjne wymuszania reguł, takich jak klucze obce. Bazy danych NoSQL nie oferują zwykle takie ograniczenia dotyczące ich danych.

Inny złożoności musi uwzględniać bazy danych NoSQL jest przechowywanie wersji. Po zmianie właściwości obiektów, nie można możliwość wykonania deserializacji do poprzednich wersji, które były przechowywane. W związku z tym aby był zgodny ze schematem nowe należy zaktualizować wszystkich istniejących obiektów serializowanych wersję (poprzedni) obiektu. To nie jest koncepcyjnie różnych z relacyjnej bazy danych, w przypadku, gdy zmiany schematu czasami wymagają skryptów aktualizacji lub mapowania aktualizacji. Jednak liczbę wpisów, które muszą zostać zmodyfikowane często jest znacznie większa w ujęciu NoSQL, ponieważ istnieje więcej zduplikowanie danych.

Jest to możliwe w bazach danych NoSQL, aby przechowywać wiele wersji obiektów, zwykle nie obsługują coś stałego schematu relacyjnych baz danych. Jednak w takim przypadku kod aplikacji należy konta istnienie poprzednie wersje obiektów oraz dodawanie dodatkowej złożoności.

Zwykle nie Wymuszaj bazy danych NoSQL [kwasu](https://en.wikipedia.org/wiki/ACID), co oznacza, że mają one korzyści skalowalność i wydajność za pośrednictwem relacyjnych baz danych. Są one odpowiednie do bardzo dużych zestawów danych i obiektów, które nie są odpowiednie do magazynu w strukturach znormalizowane tabeli. To nie ma powodu Dlaczego pojedynczej aplikacji nie może korzystać z obu relacyjnych i bazy danych NoSQL, przy użyciu których najlepiej nadaje się.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB to w pełni zarządzana usługa bazy danych NoSQL, oferująca magazynu oparte na chmurze dane bez schematu. Usługa DocumentDB jest skompilowany dla szybkie przetwarzanie, przewidywalną wydajność, wysoką dostępność, elastyczne skalowanie i dystrybucji globalnego. Mimo iż bazy danych NoSQL, deweloperzy mogą używać znane i zaawansowanych możliwości zapytań SQL na dane JSON. Wszystkie zasoby w usłudze DocumentDB są przechowywane jako dokumenty JSON. Zasoby są zarządzane jako *elementów*, które są dokumentami zawierający metadane, i *źródła*, które są kolekcjami elementów. Rysunek 8-2 przedstawiono relacje między różnymi zasobami usługi DocumentDB.


![Hierarchiczna relacja między zasobami w usłudze DocumentDB, bazy danych NoSQL JSON](./media/image8-2.png)

**Rysunek 8-2.** Organizacji zasobów usługi DocumentDB.

Język zapytań usługi DocumentDB jest proste, ale zaawansowanym interfejsem do wykonywania zapytań dokumentów JSON. Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywołania funkcji JavaScript.

**Odwołania — usługi DocumentDB**

-   Introduction\ usługi DocumentDB
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Inne opcje trwałości

W dodatku relacyjnych i opcje magazynu NoSQL aplikacje platformy ASP.NET Core mogą używać usługi Azure Storage do przechowywania różnych formatów danych i plików w sposób oparte na chmurze, skalowalnej. Usługa Azure Storage jest skalowalna na ogromną skalę, aby rozpocząć się niewielkich ilości danych i skali do przechowywania setki lub terabajtów, jeśli aplikacja wymaga przechowywania. Usługa Azure Storage obsługuje cztery rodzaje danych:

-   Magazyn obiektów blob niestrukturalnych tekst lub binarny magazynowania, również nazywany magazynem obiektów.

-   Magazyn tabel dla zestawów strukturalnych danych dostępny za pośrednictwem kluczy wiersza.

-   Magazyn kolejek niezawodnej na podstawie kolejki wiadomości.

-   Magazyn plików udostępnionych plików dostępu między maszynami wirtualnymi Azure i aplikacji lokalnych.

**Odwołania — usługa Azure Storage**

-   Introduction\ magazynu Azure
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Buforowanie

W aplikacji sieci web należy wykonać wszystkie żądania sieci web w możliwie jak najszybciej. Jest jednym ze sposobów osiągnięcia tego ograniczenia liczby wywołań zewnętrznego serwera należy wykonać w celu wykonania żądania. Buforowanie obejmuje przechowywanie kopii danych na serwerze (lub innego magazynu danych, czyli więcej łatwo proszeni niż źródła danych). Aplikacje sieci Web i szczególnie aplikacji z systemem innym niż SPA tradycyjnych sieci web, potrzebne do tworzenia cały interfejs użytkownika z każdym żądaniem. To często konieczne jest wprowadzenie wiele zapytań tej samej bazy danych wielokrotnie z żądania jednego użytkownika do następnego. W większości przypadków te dane zmiany rzadko, dlatego wyboru stale żądania z bazy danych. Platformy ASP.NET Core obsługuje buforowanie odpowiedzi do buforowania całe strony i buforowania danych, służącej do zapewnienia jeszcze bardziej precyzyjnej zachowanie buforowania.

Podczas implementowania buforowania, ważne jest należy wziąć pod uwagę separacji. Unikaj implementacji logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika. Zamiast tego Hermetyzowanie buforowanie własnych klas i zarządzać jego zachowanie przy użyciu konfiguracji. Następuje Open/zamknięty i zasad pojedynczego odpowiedzialność i ułatwić zarządzanie, jak używać buforowania w aplikacji jako ich przyrostu.

### <a name="aspnet-core-response-caching"></a>Buforowanie odpowiedzi platformy ASP.NET Core

Platformy ASP.NET Core obsługuje dwa poziomy buforowania odpowiedzi. Pierwszy poziom nie będzie buforować niczego na serwerze, ale dodaje nagłówki HTTP, które poinstruować klienci i serwery proxy do odpowiedzi z pamięci podręcznej. Ten sposób jest implementowany przez dodanie atrybutu ResponseCache do poszczególnych kontrolerów i akcji:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

Oprogramowanie pośredniczące buforowanie odpowiedzi będą automatycznie buforowane odpowiedzi na podstawie zestawu warunków, które można dostosować. Domyślnie tylko 200 odpowiedzi (OK) za pośrednictwem metody GET lub HEAD są buforowane. Ponadto żądania musi mieć odpowiedzi z Cache-Control: nagłówek publicznych i nie może zawierać nagłówki autoryzacji lub Set-Cookie. Zobacz [pełną listę buforowania warunki używane przez oprogramowanie pośredniczące buforowanie odpowiedzi](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Buforowanie danych

Zamiast (lub oprócz) buforowania odpowiedzi z sieci web pełną, można buforować wyniki poszczególnych danych zapytań. W tym celu można użyć w ramach buforowania pamięci na serwerze sieci web, lub [rozproszonej pamięci podręcznej](https://docs.microsoft.com/aspnet/core/performance/caching/distributed). W tej sekcji przedstawiono sposób wykonania w pamięci podręcznej pamięci.

Dodawanie obsługi pamięci (lub rozproszonych) buforowanie w ConfigureServices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Pamiętaj dodać pakiet Microsoft.Extensions.Caching.Memory NuGet również.

Po dodaniu usługi wszędzie tam, gdzie chcesz uzyskać dostęp do pamięci podręcznej możesz poprosić IMemoryCache za pomocą iniekcji zależności. W tym przykładzie CachedCatalogService jest przy użyciu wzorca projektowego serwera Proxy (lub Dekoratora), zapewniając alternatywną implementację ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie do) ta implementacja CatalogService.

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

Aby skonfigurować aplikację, aby używać pamięci podręcznej wersja usługi, ale nadal Zezwalaj usłudze można pobrać wystąpienia CatalogService musi się on w swoich konstruktorach, należy dodać następujące w ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Dzięki temu w miejscu wywołania bazy danych można pobrać danych katalogu zostanie zastosowane tylko raz na minutę, a nie na każde żądanie. W zależności od ruchu w witrynie może to mieć bardzo znaczący wpływ na liczbę zapytań do bazy danych i czas ładowania strony, strony głównej, który obecnie jest zależna od wszystkich trzech zapytań udostępniane przez tę usługę.

Problem, który pojawia się po zaimplementowaniu buforowanie jest *starych danych* — oznacza to, które uległy zmianie w źródle, ale wersja nieaktualny pozostaje w pamięci podręcznej. Prosty sposób, aby zminimalizować ten problem jest użyj małych czas trwania pamięci podręcznej, ponieważ zajęty aplikacji jest ograniczony dodatkową korzyścią rozszerzanie długości, które dane są buforowane. Rozważmy na przykład strona, która sprawia, że kwerenda pojedynczej bazy danych, a wymagany jest 10 razy na sekundę. Jeśli ta strona jest buforowana przez jedną minutę, spowoduje liczba zapytania bazy danych na minutę do usunięcia z 600 zmniejszenie 99.8% 1. Zamiast tego czas buforowania dokonane jedną godzinę, ogólne zmniejszenie wynosi 99.997%, ale teraz prawdopodobieństwo i potencjalne wiek starych danych zarówno zwiększa się znacznie.

Innym rozwiązaniem jest aktywne, po zaktualizowaniu danych, które zawierają, Usuń wpisy w pamięci podręcznej. Każdy wpis poszczególnych może zostać usunięty, jeśli znane jest kluczem:

```csharp
_cache.Remove(cacheKey);
```

Jeśli aplikacja udostępnia funkcje aktualizowania wpisów, które go przechowuje w pamięci podręcznej, należy usunąć odpowiednie wpisy w pamięci podręcznej w kodzie, który wykonuje aktualizacje. Czasami może być wiele różnych wpisów, które są zależne od określonego zestawu danych. W takim przypadku można go utworzyć zależności między wpisy w pamięci podręcznej, za pomocą CancellationChangeToken. Z CancellationChangeToken można jednocześnie wygaśnie wiele wpisów pamięci podręcznej przez token anulowania.

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)
