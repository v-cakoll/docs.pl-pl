---
title: Praca z danymi w ASP.NET podstawowych aplikacji
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Praca z danymi w aplikacjach ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 5a38ca94b6df676858e7cb058272e450aaf1572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241042"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Praca z danymi w ASP.NET podstawowych aplikacji

> "Dane są cenną rzeczą i będą trwać dłużej niż same systemy."
>
> Tim Berners

Dostęp do danych jest ważną częścią prawie każdej aplikacji. ASP.NET Core obsługuje wiele opcji dostępu do danych, w tym entity framework core (i entity framework 6, jak również) i może pracować z dowolnej platformy dostępu do danych .NET. Wybór, które ramy dostępu do danych do wykorzystania zależy od potrzeb aplikacji. Abstrakcja tych wyborów z applicationcore i ui projektów i hermetyzowania szczegóły implementacji w infrastrukturze, pomaga produkować luźno sprzęgo, oprogramowanie do testowania.

## <a name="entity-framework-core-for-relational-databases"></a>Rdzeń frameworku jednostek (dla relacyjnych baz danych)

Jeśli piszesz nową aplikację ASP.NET Core, która musi pracować z danymi relacyjnymi, a następnie Entity Framework Core (EF Core) jest zalecanym sposobem dostępu aplikacji do jej danych. EF Core jest obiekt-relacyjne mapowanie (O/RM), który umożliwia deweloperom platformy .NET utrwalić obiekty do i ze źródła danych. Eliminuje potrzebę większości kodów dostępu do danych, które deweloperzy zazwyczaj muszą napisać. Podobnie jak ASP.NET Core, EF Core został przepisany od podstaw, aby obsługiwać modułowe aplikacje wieloplatformowe. Dodać go do aplikacji jako pakiet NuGet, skonfigurować go w startupie i zażądać go za pomocą iniekcji zależności, gdziekolwiek jest to potrzebne.

Aby użyć EF Core z bazą danych programu SQL Server, uruchom następujące polecenie interfejsu wiersza polecenia dotnet:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Aby dodać obsługę źródła danych InMemory, do testowania:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a>Kontekst dbcontext

Aby pracować z EF Core, potrzebna <xref:Microsoft.EntityFrameworkCore.DbContext>jest podklasa . Ta klasa przechowuje właściwości reprezentujące kolekcje jednostek, z którą będzie współpracować aplikacja. Przykład eShopOnWeb zawiera CatalogContext z kolekcjami dla towarów, marek i typów:

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

DbContext musi mieć konstruktora, który akceptuje DbContextOptions i przekazać ten argument do podstawowego konstruktora DbContext. Jeśli masz tylko jeden DbContext w aplikacji, można przekazać wystąpienie DbContextOptions, ale jeśli masz więcej\<niż jeden należy użyć ogólnego DbContextOptions T> typu, przekazując w dbcontext typu jako parametr ogólny.

### <a name="configuring-ef-core"></a>Konfigurowanie rdzenia EF

W aplikacji ASP.NET Core zazwyczaj konfigurujesz EF Core w metodzie ConfigureServices. EF Core używa DbContextOptionsBuilder, który obsługuje kilka przydatnych metod rozszerzenia w celu usprawnienia jego konfiguracji. Aby skonfigurować catalogcontext do używania bazy danych programu SQL Server z parametrypołączenia zdefiniowane w konfiguracji, należy dodać następujący kod do ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Aby użyć bazy danych w pamięci:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po zainstalowaniu EF Core, utworzeniu typu podrzędnego DbContext i skonfigurowaniu go w Usłudze ConfigureServices, można przystąpić do użycia EF Core. Można zażądać wystąpienia typu DbContext w dowolnej usłudze, która go potrzebuje, i rozpocząć pracę z utrwaonym jednostek przy użyciu LINQ tak, jakby były one po prostu w kolekcji. EF Core wykonuje pracę tłumaczenia wyrażeń LINQ na zapytania SQL do przechowywania i pobierania danych.

Można zobaczyć zapytania EF Core jest wykonywana przez skonfigurowanie rejestratora i zapewnienie jego poziom jest ustawiony na co najmniej informacje, jak pokazano na rysunku 8-1.

![Rejestrowanie zapytań EF Core do konsoli](./media/image8-1.png)

**Rysunek 8-1**. Rejestrowanie zapytań EF Core do konsoli

### <a name="fetching-and-storing-data"></a>Pobieranie i przechowywanie danych

Aby pobrać dane z EF Core, można uzyskać dostęp do odpowiedniej właściwości i użyć LINQ do filtrowania wyniku. Można również użyć LINQ do wykonywania projekcji, przekształcając wynik z jednego typu do drugiego. W poniższym przykładzie można pobrać CatalogBrands, uporządkowane według nazwy, filtrowane według ich Enabled właściwości i rzutowane na SelectListItem typu:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

W powyższym przykładzie ważne jest dodanie wywołania toListAsync w celu natychmiastowego wykonania kwerendy. W przeciwnym razie instrukcja przypisze\<iQueryable SelectListItem> do brandItems, które nie będą wykonywane, dopóki nie zostanie wyliczona. Istnieją plusy i minusy do zwracania iQueryable wyniki z metod. Umożliwia kwerendy EF Core skonstruować do dalszej modyfikacji, ale może również spowodować błędy, które występują tylko w czasie wykonywania, jeśli operacje są dodawane do kwerendy, które EF Core nie może tłumaczyć. Zazwyczaj bezpieczniej jest przekazać wszystkie filtry do metody wykonywania dostępu do danych i przywrócić\<kolekcję w pamięci (na przykład Lista T>) w wyniku.

EF Core śledzi zmiany na jednostkach pobiera z trwałości. Aby zapisać zmiany w śledzonej jednostce, należy wywołać SaveChanges metody na DbContext, upewniając się, że jest to samo Wystąpienie DbContext, który został użyty do pobrania jednostki. Dodawanie i usuwanie jednostek odbywa się bezpośrednio na odpowiedniej właściwości DbSet, ponownie z wywołaniem SaveChanges do wykonywania poleceń bazy danych. W poniższym przykładzie przedstawiono dodawanie, aktualizowanie i usuwanie jednostek z trwałości.

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

EF Core obsługuje zarówno synchroniczne, jak i asynchroniczne metody pobierania i zapisywania. W aplikacjach sieci web zaleca się użycie wzorca asynchronicznego/await z metodami asynchronicznego, aby wątki serwera sieci web nie były blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.

### <a name="fetching-related-data"></a>Pobieranie powiązanych danych

Gdy EF Core pobiera jednostki, wypełnia wszystkie właściwości, które są przechowywane bezpośrednio z tej jednostki w bazie danych. Właściwości nawigacji, takie jak listy powiązanych jednostek, nie są wypełniane i mogą mieć wartość ustawioną na null. Dzięki temu EF Core nie pobiera więcej danych niż jest to potrzebne, co jest szczególnie ważne dla aplikacji sieci web, które muszą szybko przetwarzać żądania i zwracać odpowiedzi w efektywny sposób. Aby uwzględnić relacje z jednostką przy użyciu _wydłużenia,_ należy określić właściwość przy użyciu metody dołączania rozszerzenia w kwerendzie, jak pokazano:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Można dołączyć wiele relacji i można również dołączyć podrelacje za pomocą ThenInclude. EF Core wykona pojedynczą kwerendę, aby pobrać wynikowy zestaw jednostek. Alternatywnie można dołączyć właściwości nawigacji właściwości nawigacji, przekazując ".' -oddzielony ciąg `.Include()` do metody rozszerzenia, tak jak:

```csharp
    .Include(“Items.Products”)
```

Oprócz hermetyzacji logiki filtrowania specyfikacja może określić kształt danych, które mają być zwracane, w tym właściwości do wypełnienia. Przykład eShopOnWeb zawiera kilka specyfikacji, które pokazują hermetyzujące chętnie ładowania informacji w specyfikacji. Możesz zobaczyć, jak specyfikacja jest używana jako część kwerendy tutaj:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

Inną opcją ładowania powiązanych danych jest użycie _jawnego ładowania_. Jawne ładowanie umożliwia załadowanie dodatkowych danych do jednostki, która została już pobrana. Ponieważ wiąże się to z oddzielnym żądaniem do bazy danych, nie jest zalecane dla aplikacji sieci web, które powinny zminimalizować liczbę rund bazy danych wykonanych na żądanie.

_Powolne ładowanie_ jest funkcją, która automatycznie ładuje powiązane dane, do których odwołuje się aplikacja. EF Core dodał obsługę leniwego ładowania w wersji 2.1. Powolne ładowanie nie jest domyślnie włączone `Microsoft.EntityFrameworkCore.Proxies`i wymaga zainstalowania pliku . Podobnie jak w przypadku jawnego ładowania, powolne ładowanie zazwyczaj powinny być wyłączone dla aplikacji sieci web, ponieważ jego użycie spowoduje dodatkowe zapytania bazy danych są dokonywane w ramach każdego żądania sieci web. Niestety obciążenie wynikające z leniwego ładowania często pozostaje niezauważone w czasie rozwoju, gdy opóźnienie jest małe i często zestawy danych używane do testowania są małe. Jednak w środowisku produkcyjnym, z większą liczbą użytkowników, większą liczbą danych i większym opóźnieniem, żądania dodatkowej bazy danych często mogą powodować słabą wydajność aplikacji sieci web, które w dużym czasie korzystają z ładowania z opóźnieniem.

[Unikaj leniwego ładowania jednostek w aplikacjach sieci Web](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Hermetyzowanie danych

EF Core obsługuje kilka funkcji, które umożliwiają modelowi prawidłowe hermetyzowanie jego stanu. Typowym problemem w modelach domeny jest to, że uwidaczniają właściwości nawigacji kolekcji jako publicznie dostępne typy list. Dzięki temu każdy współpracownik do manipulowania zawartością tych typów kolekcji, które mogą ominąć ważne reguły biznesowe związane z kolekcji, ewentualnie pozostawiając obiekt w nieprawidłowym stanie. Rozwiązaniem tego problemu jest udostępnienie dostępu tylko do odczytu do powiązanych kolekcji i jawnie podać metody definiujące sposoby, w których klienci mogą nimi manipulować, jak w tym przykładzie:

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

Ten typ jednostki nie uwidacznia publicznego `List` lub `ICollection` właściwości, ale zamiast tego udostępnia `IReadOnlyCollection` typ, który otacza typ listy źródłowej. Korzystając z tego wzorca, można wskazać do entity framework core do korzystania z pola podstawowego, takie jak:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Innym sposobem, w jaki można poprawić model domeny jest za pomocą obiektów wartości dla typów, które nie mają tożsamości i są rozróżniane tylko przez ich właściwości. Przy użyciu takich typów, jak właściwości jednostek może pomóc zachować logiki specyficzne dla obiektu wartości, do którego należy i można uniknąć zduplikowanej logiki między wieloma jednostkami, które używają tej samej koncepcji. W centrum struktury jednostki można utrwalić obiekty wartości w tej samej tabeli co ich jednostka będące ich właścicielem, konfigurując typ jako jednostkę należącą do obiektu, tak jak:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

W tym przykładzie `ShipToAddress` właściwość jest `Address`typu . `Address`jest obiektem wartości o kilku `Street` `City`właściwościach, takich jak i . EF Core `Order` mapuje obiekt do jego `Address` tabeli z jedną kolumną na właściwość, poprzedzając każdą nazwę kolumny z nazwą właściwości. W tym przykładzie `Order` tabela będzie zawierać `ShipToAddress_Street` `ShipToAddress_City`kolumny, takie jak i . Istnieje również możliwość przechowywania posiadanych typów w oddzielnych tabelach, w razie potrzeby.

Dowiedz się więcej o [obsłudze jednostek należących do firmy EF Core](/ef/core/modeling/owned-entities).

### <a name="resilient-connections"></a>Odporne połączenia

Zasoby zewnętrzne, takie jak bazy danych SQL, mogą być czasami niedostępne. W przypadku tymczasowej niedostępności aplikacje można użyć logiki ponawiania próby, aby uniknąć zgłaszania wyjątku. Ta technika jest powszechnie określana jako _odporność połączenia_. Można zaimplementować [własną próbę ponawiania za pomocą wykładniczej techniki wycofywania,](https://docs.microsoft.com/azure/architecture/patterns/retry) próbując ponowić próbę przy wykładniczo zwiększającym czas oczekiwania, dopóki nie zostanie osiągnięta maksymalna liczba ponownych prób. Ta technika obejmuje fakt, że zasoby w chmurze mogą być sporadycznie niedostępne przez krótki okres czasu, co powoduje niepowodzenie niektórych żądań.

W przypadku usługi Azure SQL DB, entity Framework Core już zapewnia odporność połączenia wewnętrznej bazy danych i logikę ponawiania próby. Należy jednak włączyć strategię wykonywania struktury jednostek dla każdego połączenia DbContext, jeśli chcesz mieć odporne połączenia EF Core.

Na przykład następujący kod na poziomie połączenia EF Core umożliwia odporne połączenia SQL, które są ponowione w przypadku niepowodzenia połączenia.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie realizacji i jawne transakcje przy użyciu BeginTransaction i wielu DbContexts

Po włączeniu ponownych prób w połączeniach EF Core każda operacja wykonywana przy użyciu EF Core staje się własną operacją ponawiania prób. Każde zapytanie i każde wywołanie SaveChanges zostanie ponowione jako jednostka, jeśli wystąpi błąd przejściowy.

Jednak jeśli kod inicjuje transakcję przy użyciu BeginTransaction, definiujesz własną grupę operacji, które muszą być traktowane jako jednostka; wszystko wewnątrz transakcji musi zostać wycofana w przypadku wystąpienia awarii. Zobaczysz wyjątek, jak poniższe, jeśli spróbujesz wykonać tę transakcję podczas korzystania ze strategii wykonania EF (zasady ponawiania próby) i należy dołączyć kilka SaveChanges z wielu DbContexts w nim.

System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Użyj strategii wykonywania zwracanej przez "DbContext.Database.CreateExecutionStrategy()", aby wykonać wszystkie operacje w transakcji jako jednostkę podlegającą ponawianiu próby.

Rozwiązaniem jest ręczne wywołanie strategii wykonywania EF z delegata reprezentujących wszystko, co musi zostać wykonane. Jeśli wystąpi błąd przejściowy, strategia wykonywania ponownie wywoła delegata. Poniższy kod pokazuje, jak zaimplementować to podejście:

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

Pierwszy DbContext jest \_catalogContext i drugi DbContext \_jest w integracyjneEventLogService obiektu. Na koniec commit akcja będzie wykonywana wiele DbContexts i przy użyciu strategii wykonywania EF.

> ### <a name="references--entity-framework-core"></a>Odwołania — rdzeń frameworkencji
>
> - **Dokumenty podstawowe EF**
>   <https://docs.microsoft.com/ef/>
> - **EF Core: Powiązane dane**
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Unikaj leniwego ładowania jednostek w aplikacjach ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core lub micro-ORM?

Ef Core jest doskonałym wyborem do zarządzania trwałością, a w większości hermetyzuje szczegóły bazy danych od deweloperów aplikacji, nie jest to jedyny wybór. Inną popularną alternatywą open-source jest [Dapper](https://github.com/StackExchange/Dapper), tak zwany mikro-ORM. Mikro-ORM to lekkie, mniej w pełni funkcjonalne narzędzie do mapowania obiektów na struktury danych. W przypadku Dapper, jego cele projektowe koncentrują się na wydajności, a nie w pełni hermetyzując podstawowe zapytania, których używa do pobierania i aktualizowania danych. Ponieważ nie jest abstrakcyjny SQL od dewelopera, Dapper jest "bliżej metalu" i pozwala deweloperom napisać dokładne zapytania, które chcą użyć dla danej operacji dostępu do danych.

EF Core ma dwie istotne funkcje, które udostępniają, które oddzielają go od Dapper, ale także dodają do jego narzutów wydajności. Pierwszym z nich jest tłumaczenie z wyrażeń LINQ do SQL. Te tłumaczenia są buforowane, ale mimo to istnieje obciążenie w wykonywaniu ich po raz pierwszy. Drugi to śledzenie zmian w jednostkach (dzięki czemu można wygenerować instrukcje efektywnej aktualizacji). To zachowanie można wyłączyć dla określonych zapytań przy użyciu AsNotTracking rozszerzenia. EF Core generuje również zapytania SQL, które zwykle są bardzo wydajne i w każdym przypadku całkowicie akceptowalne z punktu widzenia wydajności, ale jeśli potrzebujesz dokładnej kontroli nad dokładną kwerendą do wykonania, można przekazać w niestandardowych SQL (lub wykonać procedurę składowaną) przy użyciu EF Rdzeń też. W tym przypadku Dapper nadal przewyższa EF Core, ale tylko nieznacznie. Julie Lerman prezentuje pewne dane dotyczące wydajności w swoim artykule MSDN z maja 2016 [r. Dapper, Entity Framework i Aplikacje hybrydowe](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps). Dodatkowe dane testowe wydajności dla różnych metod dostępu do danych można znaleźć [na stronie Dapper](https://github.com/StackExchange/Dapper).

Aby zobaczyć, jak składnia programu Dapper różni się od rdzenia EF, należy wziąć pod uwagę te dwie wersje tej samej metody pobierania listy elementów:

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

Jeśli chcesz utworzyć bardziej złożone wykresy obiektów z Dapper, należy napisać skojarzone zapytania samodzielnie (w przeciwieństwie do dodawania Include jak w EF Core). Jest to obsługiwane przez różne składnie, w tym funkcję o nazwie Mapowanie wielu, która umożliwia mapowanie poszczególnych wierszy na wiele mapowanych obiektów. Na przykład biorąc pod uwagę klasy Post z właściwością Właściciel typu Użytkownik, następujący SQL zwróci wszystkie niezbędne dane:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Każdy zwrócony wiersz zawiera zarówno dane użytkownika, jak i opublikuj. Ponieważ dane Użytkownika powinny być dołączone do danych Post za pośrednictwem jego właściciela właściwości, stosuje się następującą funkcję:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Pełna lista kodu, aby zwrócić kolekcję wpisów z ich owner właściwości wypełnione skojarzonych danych użytkownika będzie:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Ponieważ oferuje mniej hermetyzacji, Dapper wymaga deweloperzy wiedzą więcej o tym, jak ich dane są przechowywane, jak zapytanie go wydajnie i napisać więcej kodu, aby go pobrać. Po zmianie modelu, zamiast po prostu tworzenie nowej migracji (inna funkcja EF Core) i/lub aktualizowanie informacji mapowania w jednym miejscu w DbContext, każda kwerenda, której dotyczy problem, musi zostać zaktualizowana. Te kwerendy nie mają gwarancji czasu kompilacji, więc mogą zostać przerwane w czasie wykonywania w odpowiedzi na zmiany modelu lub bazy danych, co utrudnia szybkie wykrycie błędów. W zamian za te kompromisy, Dapper oferuje niezwykle szybką wydajność.

W przypadku większości aplikacji i większości części prawie wszystkich aplikacji EF Core oferuje akceptowalną wydajność. W związku z tym jego korzyści wydajności dewelopera mogą przeważyć jego obciążenie wydajności. W przypadku kwerend, które mogą korzystać z buforowania, rzeczywiste zapytanie może być wykonywane tylko niewielki procent czasu, dzięki czemu stosunkowo niewielkie różnice w wydajności zapytań dyskusyjne.

## <a name="sql-or-nosql"></a>SQL lub NoSQL

Tradycyjnie relacyjne bazy danych, takie jak SQL Server, zdominowały rynek trwałego przechowywania danych, ale nie są jedynym dostępnym rozwiązaniem. Bazy danych NoSQL, takie jak [MongoDB,](https://www.mongodb.com/what-is-mongodb) oferują inne podejście do przechowywania obiektów. Zamiast mapowania obiektów do tabel i wierszy, inną opcją jest serializacja całego wykresu obiektu i przechowywanie wyniku. Korzyści z tego podejścia, przynajmniej początkowo, to prostota i wydajność. Łatwiej jest przechowywać pojedynczy obiekt serializowany z kluczem niż rozłożyć obiekt na wiele tabel z relacjami i aktualizacjami i wierszami, które mogły ulec zmianie od czasu ostatniego pobrania obiektu z bazy danych. Podobnie pobieranie i deserializowanie pojedynczego obiektu z magazynu opartego na kluczach jest zazwyczaj znacznie szybsze i łatwiejsze niż złożone sprzężenia lub wiele zapytań bazy danych wymaganych do pełnego skomponowania tego samego obiektu z relacyjnej bazy danych. Brak blokad lub transakcji lub stały schemat sprawia, że bazy danych NoSQL są podatne na skalowanie na wielu komputerach, obsługując bardzo duże zestawy danych.

Z drugiej strony bazy danych NoSQL (jak są one zwykle nazywane) mają swoje wady. Relatoryswe bazy danych używają normalizacji do wymuszania spójności i unikania powielania danych. Zmniejsza to całkowity rozmiar bazy danych i zapewnia, że aktualizacje udostępnionych danych są dostępne natychmiast w całej bazie danych. W relacyjnej bazie danych tabela Adres może odwoływać się do tabeli Country według identyfikatora, tak że jeśli nazwa kraju/regionu zostanie zmieniona, rekordy adresów będą korzystać z aktualizacji bez konieczności aktualizowania. Jednak w bazie danych NoSQL adres i skojarzony z nim kraj może być serializowany jako część wielu przechowywanych obiektów. Aktualizacja nazwy kraju/regionu wymagałaby aktualizacji wszystkich takich obiektów, a nie pojedynczego wiersza. Relacyjne bazy danych można również zapewnić integralność relacyjnej przez wymuszanie reguł, takich jak klucze obce. Bazy danych NoSQL zazwyczaj nie oferują takich ograniczeń dotyczących ich danych.

Inną złożonością bazy danych NoSQL musi radzić sobie z jest przechowywanie wersji. Po zmianie właściwości obiektu może nie być możliwe deserializacji z poprzednich wersji, które były przechowywane. W związku z tym wszystkie istniejące obiekty, które mają serializowane (poprzednia) wersja obiektu musi zostać zaktualizowana, aby były zgodne z jego nowym schematem. Nie różni się to koncepcyjnie od relacyjnej bazy danych, gdzie zmiany schematu czasami wymagają aktualizacji skryptów lub aktualizacji mapowania. Jednak liczba wpisów, które muszą zostać zmodyfikowane, jest często znacznie większa w podejściu NoSQL, ponieważ istnieje więcej duplikacji danych.

Jest możliwe w bazach danych NoSQL do przechowywania wielu wersji obiektów, coś stałe schematu relacyjnych baz danych zazwyczaj nie obsługują. Jednak w tym przypadku kod aplikacji będzie musiał uwzględnić istnienie poprzednich wersji obiektów, dodając dodatkową złożoność.

Bazy danych NoSQL zazwyczaj nie wymuszają [ACID](https://en.wikipedia.org/wiki/ACID), co oznacza, że mają zarówno wydajność, jak i skalowalność korzyści w stosunku do relacyjnych baz danych. Są one dobrze dostosowane do bardzo dużych zestawów danych i obiektów, które nie są dobrze przystosowane do przechowywania w znormalizowanych strukturach tabel. Nie ma powodu, dla którego pojedyncza aplikacja nie może korzystać z relacyjnych i nosql baz danych, przy użyciu każdego, gdzie jest to najlepiej nadaje.

## <a name="azure-cosmos-db"></a>Azure Cosmos DB

Usługa Azure Cosmos DB to w pełni zarządzana usługa bazy danych NoSQL, która oferuje magazyn danych bez schematu w chmurze. Usługa Azure Cosmos DB została stworzona z myślą o szybkiej i przewidywalnej wydajności, wysokiej dostępności, elastycznym skalowaniu i dystrybucji globalnej. Pomimo tego, że jest to baza danych NoSQL, deweloperzy mogą korzystać z rozbudowanych i znanych funkcji zapytań SQL na danych JSON. Wszystkie zasoby w usłudze Azure Cosmos DB są przechowywane jako dokumenty JSON. Zasoby są zarządzane jako _elementy_, które są dokumentami zawierającymi metadane i _źródłami danych_, które są kolekcjami towarów. Rysunek 8-2 przedstawia relację między różnymi zasobami usługi Azure Cosmos DB.

![Hierarchiczna relacja między zasobami w usłudze Azure Cosmos DB — baza danych JSON NoSQL](./media/image8-2.png)

**Rysunek 8-2.** Organizacja zasobów usługi Azure Cosmos DB.

Język zapytań usługi Azure Cosmos DB to prosty, ale zaawansowany interfejs do wykonywania zapytań dotyczących dokumentów JSON. Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywoływania funkcji języka JavaScript.

**Odwołania — usługa Azure Cosmos DB**

- Wprowadzenie usługi Azure Cosmos DB<https://docs.microsoft.com/azure/cosmos-db/introduction>

## <a name="other-persistence-options"></a>Inne opcje trwałości

Oprócz opcji magazynowych relacyjnych i NoSQL ASP.NET aplikacje podstawowe mogą używać usługi Azure Storage do przechowywania różnych formatów danych i plików w sposób skalowalny w chmurze. Usługa Azure Storage jest znacznie skalowalna, dzięki czemu można rozpocząć przechowywanie niewielkich ilości danych i skalować do przechowywania setek lub terabajtów, jeśli aplikacja tego wymaga. Usługa Azure Storage obsługuje cztery rodzaje danych:

- Magazyn obiektów Blob dla nieustrukturyzowanego tekstu lub magazynu binarnego, nazywany również magazynem obiektów.

- Magazyn tabel dla uporządkowanych zestawów danych, dostępny za pomocą kluczy wierszy.

- Magazyn kolejek dla niezawodnej obsługi wiadomości opartych na kolejkach.

- Magazyn plików dla udostępnionego dostępu do plików między maszynami wirtualnymi platformy Azure i aplikacjami lokalnymi.

**Odwołania — usługa Azure Storage**

- Wprowadzenie usługi Azure Storage<https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Buforowanie

W aplikacjach sieci web każde żądanie sieci web powinno zostać wypełnione w jak najkrótszym czasie. Jednym ze sposobów osiągnięcia tego celu jest ograniczenie liczby wywołań zewnętrznych, które serwer musi wykonać, aby ukończyć żądanie. Buforowanie polega na przechowywaniu kopii danych na serwerze (lub innym magazynie danych, który jest łatwiej wyszukiwany niż źródło danych). Aplikacje sieci Web, a zwłaszcza tradycyjne aplikacje sieci Web innych niż SPA, muszą tworzyć cały interfejs użytkownika przy każdym żądaniu. Często wiąże się to z tworzeniem wielu zapytań tej samej bazy danych wielokrotnie z jednego żądania użytkownika do następnego. W większości przypadków te dane zmieniają się rzadko, więc nie ma powodu, aby stale żądać ich z bazy danych. ASP.NET Core obsługuje buforowanie odpowiedzi, buforowanie całych stron i buforowanie danych, które obsługuje bardziej szczegółowe zachowanie buforowania.

Podczas implementowania buforowania, ważne jest, aby pamiętać o separacji problemów. Należy unikać implementowania logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika. Zamiast tego hermetyzować buforowania w swoich własnych klas i używać konfiguracji do zarządzania jego zachowanie. Wynika to z zasad open/closed i pojedynczej odpowiedzialności i ułatwi zarządzanie sposób używania buforowania w aplikacji w miarę jej wzrostu.

### <a name="aspnet-core-response-caching"></a>buforowanie odpowiedzi ASP.NET core

ASP.NET Core obsługuje dwa poziomy buforowania odpowiedzi. Pierwszy poziom nie buforuje niczego na serwerze, ale dodaje nagłówki HTTP, które instruują klientów i serwery proxy do buforowania odpowiedzi. Jest to realizowane przez dodanie ResponseCache atrybut do poszczególnych kontrolerów lub akcji:

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

Poprzedni przykład spowoduje następujące nagłówek jest dodawany do odpowiedzi, instruując klientów do buforowania wynik przez maksymalnie 60 sekund.

Kontrola pamięci podręcznej: publiczna, max-age=60

Aby dodać buforowanie pamięci po stronie serwera do aplikacji, należy odwołać się do pakietu Microsoft.AspNetCore.ResponseCaching NuGet, a następnie dodać narzędzie pośredniczące buforowanie odpowiedzi. To oprogramowanie pośredniczą jest skonfigurowane zarówno w skonfigurowaniu usług, jak i konfiguracji podczas uruchamiania:

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

Zagęszczenie buforowania odpowiedzi automatycznie buforuje odpowiedzi na podstawie zestawu warunków, które można dostosować. Domyślnie tylko 200 (OK) odpowiedzi wymagane za pośrednictwem get lub head metody są buforowane. Ponadto żądania muszą mieć odpowiedź z cache-control: nagłówek publiczny i nie może zawierać nagłówki autoryzacji lub set-cookie. Zobacz [pełną listę warunków buforowania używanych przez zagęszanie buforowania odpowiedzi](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Buforowanie danych

Zamiast (lub oprócz) buforowania pełnych odpowiedzi sieci web, można buforować wyniki poszczególnych zapytań dotyczących danych. W tym celu można użyć w buforowaniu pamięci na serwerze sieci web lub użyć [rozproszonej pamięci podręcznej](/aspnet/core/performance/caching/distributed). W tej sekcji zademonstruje, jak zaimplementować w pamięci podręcznej.

W usługach ConfigureServices można dodać obsługę buforowania pamięci (lub dystrybucji):

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Pamiętaj, aby dodać pakiet Microsoft.Extensions.Caching.Memory NuGet, jak również.

Po dodaniu usługi, żądasz IMemoryCache za pomocą iniekcji zależności wszędzie tam, gdzie trzeba uzyskać dostęp do pamięci podręcznej. W tym przykładzie CachedCatalogService używa wzorca projektu serwera proxy (lub dekoratora), zapewniając alternatywną implementację ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie) podstawowej implementacji CatalogService.

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
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
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
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

Aby skonfigurować aplikację do używania buforowanej wersji usługi, ale nadal zezwalaj usłudze na uzyskanie wystąpienia CatalogService, którego potrzebuje w swoim konstruktorze, należy dodać następujące elementy w usłudze ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Z tym w miejscu wywołania bazy danych, aby pobrać dane katalogu będą dokonywane tylko raz na minutę, a nie na każde żądanie. W zależności od ruchu do witryny może to mieć znaczący wpływ na liczbę zapytań do bazy danych i średni czas ładowania strony dla strony głównej, która obecnie zależy od wszystkich trzech zapytań uwidacznianych przez tę usługę.

Problem, który pojawia się podczas buforowania jest implementowany jest _stare dane_ — oznacza to, że dane, które uległy zmianie u źródła, ale nieaktualna wersja pozostaje w pamięci podręcznej. Prosty sposób, aby złagodzić ten problem jest użycie małych czasów trwania pamięci podręcznej, ponieważ dla aplikacji zajęty jest ograniczona dodatkowa korzyść do rozszerzenia danych długości jest buforowany. Rozważmy na przykład stronę, która tworzy kwerendę pojedynczej bazy danych i jest wymagana 10 razy na sekundę. Jeśli ta strona jest buforowana przez jedną minutę, spowoduje to spadek liczby zapytań bazy danych na minutę z 600 do 1, co oznacza skrócenie o 99,8%. Jeśli zamiast tego czas trwania pamięci podręcznej zostały wykonane jedną godzinę, ogólne zmniejszenie będzie 99.997%, ale teraz prawdopodobieństwo i potencjalny wiek starych danych są zarówno znacznie wzrosła.

Innym podejściem jest proaktywne usuwanie wpisów pamięci podręcznej po zaktualizowaniu zawartych w nie danych. Każdy pojedynczy wpis można usunąć, jeśli jego klucz jest znany:

```csharp
_cache.Remove(cacheKey);
```

Jeśli aplikacja udostępnia funkcje aktualizacji wpisów, które buforuje, można usunąć odpowiednie wpisy pamięci podręcznej w kodzie, który wykonuje aktualizacje. Czasami może istnieć wiele różnych wpisów, które zależą od określonego zestawu danych. W takim przypadku może być przydatne do tworzenia zależności między wpisami pamięci podręcznej przy użyciu CancellationChangeToken. Z CancellationChangeToken, można wygasnąć wiele wpisów pamięci podręcznej na raz, anulując token.

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

Buforowanie może znacznie zwiększyć wydajność stron internetowych, które wielokrotnie żądają tych samych wartości z bazy danych. Pamiętaj, aby zmierzyć dostęp do danych i wydajność strony przed zastosowaniem buforowania i zastosować buforowanie tylko wtedy, gdy widzisz potrzebę poprawy. Buforowanie zużywa zasoby pamięci serwera sieci web i zwiększa złożoność aplikacji, dlatego ważne jest, aby nie przedwcześnie zoptymalizować przy użyciu tej techniki.

>[!div class="step-by-step"]
>[Poprzedni](develop-asp-net-core-mvc-apps.md)
>[następny](test-asp-net-core-mvc-apps.md)
