---
title: Praca z danymi w aplikacjach ASP.NET Core
description: Architekt nowoczesnych aplikacji sieci Web z ASP.NET Core i Azure | Praca z danymi w aplikacjach ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: b706332b28aec669a841f510046aa7b185be1373
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987845"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Praca z danymi w ASP.NET podstawowych aplikacjach

> "Dane są cenną rzeczą i będą trwać dłużej niż same systemy."
>
> Tim Berners

Dostęp do danych jest ważną częścią niemal każdej aplikacji. ASP.NET Core obsługuje wiele opcji dostępu do danych, w tym Entity Framework Core (i Entity Framework 6, jak również) i może pracować z dowolnej platformy dostępu do danych .NET. Wybór struktury dostępu do danych do użycia zależy od potrzeb aplikacji. Abstrakcja tych wyborów z ApplicationCore i projektów interfejsu użytkownika i hermetyzacji szczegóły implementacji w infrastrukturze, pomaga produkować luźno sprzężone, testowalne oprogramowanie.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (dla relacyjnych baz danych)

Jeśli piszesz nową aplikację ASP.NET Core, która musi pracować z danymi relacyjnymi, a następnie Entity Framework Core (EF Core) jest zalecanym sposobem dla aplikacji, aby uzyskać dostęp do swoich danych. EF Core jest maperem obiekto-relacyjne (O/RM), który umożliwia deweloperom platformy .NET utrwalanie obiektów do i ze źródła danych. Eliminuje to potrzebę większości deweloperów kodu dostępu do danych zazwyczaj trzeba napisać. Podobnie jak ASP.NET Core, EF Core został przepisany od podstaw do obsługi modułowych aplikacji wieloplatformowych. Dodać go do aplikacji jako pakiet NuGet, skonfigurować go w starcie i zażądać go za pomocą iniekcji zależności, gdziekolwiek jest to potrzebne.

Aby użyć ef core z bazą danych programu SQL Server, uruchom następujące polecenie dotnet CLI:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Aby dodać obsługę źródła danych InMemory do testowania:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a>Kontekst DbContext

Do pracy z EF Core potrzebna <xref:Microsoft.EntityFrameworkCore.DbContext>jest podklasa . Ta klasa zawiera właściwości reprezentujące kolekcje jednostek, z którymi aplikacja będzie współpracować. Przykład eShopOnWeb zawiera CatalogContext z kolekcjami dla towarów, marek i typów:

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

Twój DbContext musi mieć konstruktora, który akceptuje DbContextOptions i przekazać ten argument do konstruktora dbcontext bazy. Jeśli masz tylko jeden DbContext w aplikacji, można przekazać wystąpienie DbContextOptions, ale jeśli masz więcej niż jeden,\<należy użyć ogólnego DbContextOptions T> typu, przekazując w DbContext typu jako parametr ogólny.

### <a name="configuring-ef-core"></a>Konfigurowanie ef core

W aplikacji ASP.NET Core zazwyczaj skonfigurujesz EF Core w metodzie ConfigureServices. EF Core używa DbContextOptionsBuilder, który obsługuje kilka metod rozszerzenia pomocne, aby usprawnić jego konfigurację. Aby skonfigurować CatalogContext do używania bazy danych programu SQL Server z ciągiem połączenia zdefiniowanym w programie Configuration, należy dodać następujący kod do configureservices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Aby użyć bazy danych w pamięci:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po zainstalowaniu EF Core, utworzeniu typu podrzędnego DbContext i skonfigurowaniu go w ConfigureServices, można przystąpić do użycia EF Core. Można zażądać wystąpienia typu DbContext w dowolnej usłudze, która jej potrzebuje, i rozpocząć pracę z utrwalonych jednostek przy użyciu LINQ tak, jakby były one po prostu w kolekcji. EF Core wykonuje pracę tłumaczenia wyrażeń LINQ do zapytań SQL do przechowywania i pobierania danych.

Można zobaczyć kwerendy EF Core jest wykonywany przez skonfigurowanie rejestratora i zapewnienie jego poziom jest ustawiony na co najmniej informacje, jak pokazano na rysunku 8-1.

![Rejestrowanie zapytań EF Core do konsoli](./media/image8-1.png)

**Rysunek 8-1**. Rejestrowanie zapytań EF Core do konsoli

### <a name="fetching-and-storing-data"></a>Pobieranie i przechowywanie danych

Aby pobrać dane z EF Core, można uzyskać dostęp do odpowiedniej właściwości i użyć LINQ do filtrowania wyniku. Można również użyć LINQ do wykonywania projekcji, przekształcając wynik z jednego typu do innego. Poniższy przykład można pobrać CatalogBrands, uporządkowane według nazwy, filtrowane przez ich Enabled właściwości i rzutowane na SelectListItem typu:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

W powyższym przykładzie należy dodać wywołanie do ToListAsync w celu natychmiastowego wykonania kwerendy. W przeciwnym razie instrukcja przypisze\<IQueryable SelectListItem> do brandItems, które nie zostaną wykonane, dopóki nie zostanie wyliczony. Istnieją plusy i minusy do powrotu IQueryable wyniki z metod. Umożliwia kwerendy EF Core będzie konstruować do dalszej modyfikacji, ale może również spowodować błędy, które występują tylko w czasie wykonywania, jeśli operacje są dodawane do kwerendy, że EF Core nie może przetłumaczyć. Ogólnie bezpieczniejsze jest przekazywanie filtrów do metody wykonywania dostępu do danych i powrót kolekcji\<w pamięci (na przykład lista T>) w wyniku.

EF Core śledzi zmiany na jednostkach pobiera z trwałości. Aby zapisać zmiany w śledzone jednostki, wystarczy wywołać SaveChanges metody na DbContext, upewniając się, że jest to samo wystąpienie DbContext, który został użyty do pobrania jednostki. Dodawanie i usuwanie jednostek odbywa się bezpośrednio na odpowiedniej właściwości DbSet, ponownie z wywołaniem SaveChanges do wykonania poleceń bazy danych. W poniższym przykładzie pokazano dodawanie, aktualizowanie i usuwanie jednostek z trwałości.

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

EF Core obsługuje zarówno synchroniczne i asynchroniczne metody pobierania i zapisywania. W aplikacjach sieci web zaleca się użycie wzorca asynchronii/await z metodami asynchronizującymi, aby wątki serwera sieci web nie były blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.

### <a name="fetching-related-data"></a>Pobieranie powiązanych danych

Gdy EF Core pobiera jednostki, wypełnia wszystkie właściwości, które są przechowywane bezpośrednio z tej jednostki w bazie danych. Właściwości nawigacji, takie jak listy powiązanych jednostek, nie są wypełniane i mogą mieć ich wartość ustawioną na wartość null. Gwarantuje to, że EF Core nie pobiera więcej danych niż jest to potrzebne, co jest szczególnie ważne dla aplikacji sieci web, które muszą szybko przetwarzać żądania i zwracać odpowiedzi w skuteczny sposób. Aby uwzględnić relacje z encją przy użyciu _ładowania z użyciem opcji ,należy_określić właściwość przy użyciu metody Dołączania rozszerzenia w kwerendzie, jak pokazano na rysunku:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Można dołączyć wiele relacji, a także podzespołowania za pomocą ThenInclude. EF Core wykona pojedynczą kwerendę, aby pobrać wynikowy zestaw jednostek. Alternatywnie można uwzględnić właściwości nawigacji właściwości nawigacji, przekazując '.' -oddzielony ciąg `.Include()` do metody rozszerzenia, jak tak:

```csharp
    .Include("Items.Products")
```

Oprócz hermetyzacji logiki filtrowania, specyfikacja można określić kształt danych, które mają być zwracane, w tym właściwości, które mają być wypełniane. Przykład eShopOnWeb zawiera kilka specyfikacji, które pokazują hermetyzację chętnych ładowania informacji w specyfikacji. Możesz zobaczyć, jak specyfikacja jest używana jako część kwerendy tutaj:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

Inną opcją ładowania powiązanych danych jest użycie _jawnego ładowania_. Jawne ładowanie umożliwia załadowanie dodatkowych danych do jednostki, która została już pobrana. Ponieważ wiąże się to z osobnym żądaniem do bazy danych, nie jest zalecane dla aplikacji sieci web, co powinno zminimalizować liczbę rund bazy danych wykonanych na żądanie.

_Ładowanie z opóźnieniem_ jest funkcją, która automatycznie ładuje powiązane dane, do których odwołuje się aplikacja. EF Core dodał wsparcie dla powolnego ładowania w wersji 2.1. Ładowanie z opóźnieniem nie jest domyślnie `Microsoft.EntityFrameworkCore.Proxies`włączone i wymaga zainstalowania pliku . Podobnie jak w przypadku jawnego ładowania, ładowanie z opóźnieniem powinno być zazwyczaj wyłączone dla aplikacji sieci web, ponieważ jego użycie spowoduje dodatkowe zapytania bazy danych są dokonywane w ramach każdego żądania sieci web. Niestety obciążenie poniesione przez opóźnienie ładowania często pozostaje niezauważone w czasie programowania, gdy opóźnienie jest małe i często zestawy danych używane do testowania są małe. Jednak w produkcji, z większą liczą użytkowników, więcej danych i więcej opóźnień, dodatkowe żądania bazy danych często może spowodować niską wydajność dla aplikacji sieci web, które intensywnie używać ładowania z opóźnieniem.

[Unikaj jednostek ładowania z opóźnieniem w aplikacjach sieci Web](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Hermetyzacja danych

EF Core obsługuje kilka funkcji, które umożliwiają modelu poprawnie hermetyzować jego stan. Typowym problemem w modelach domeny jest to, że uwidaczniają właściwości nawigacji kolekcji jako publicznie dostępne typy list. Dzięki temu każdy współpracownik manipulować zawartością tych typów kolekcji, które mogą pominąć ważne reguły biznesowe związane z kolekcji, ewentualnie pozostawiając obiekt w nieprawidłowym stanie. Rozwiązaniem tego problemu jest udostępnić dostęp tylko do odczytu do powiązanych kolekcji i jawnie zapewnić metody definiujące sposoby, w których klienci mogą manipulować nimi, jak w tym przykładzie:

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

Ten typ jednostki nie `List` udostępnia `ICollection` publicznej lub właściwości, `IReadOnlyCollection` ale zamiast tego udostępnia typ, który otacza podstawowy typ listy. Korzystając z tego wzorca, można wskazać entity framework core, aby użyć pola zapasowego w taki sposób:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Innym sposobem, w którym można poprawić model domeny jest za pomocą obiektów wartości dla typów, które nie mają tożsamości i są wyróżniane tylko przez ich właściwości. Za pomocą takich typów, jak właściwości jednostek może pomóc zachować logiki specyficzne dla obiektu wartości, gdzie należy i można uniknąć zduplikowanej logiki między wieloma jednostkami, które używają tej samej koncepcji. W entity framework core można utrwalać obiekty wartości w tej samej tabeli co ich jednostki będące właścicielem, konfigurując typ jako jednostkę należącą do sieci, tak jak:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

W tym przykładzie `ShipToAddress` właściwość `Address`jest typu . `Address`jest obiektem wartości o kilku `Street` `City`właściwościach, takich jak i . EF Core `Order` mapuje obiekt do swojej `Address` tabeli z jedną kolumną na właściwość, prefiksując każdą nazwę kolumny o nazwie właściwości. W tym przykładzie tabela `Order` będzie `ShipToAddress_Street` zawierać `ShipToAddress_City`kolumny, takie jak i . W razie potrzeby można również przechowywać posiadane typy w oddzielnych tabelach.

Dowiedz się więcej o [pomocy technicznej jednostki należącej do firmy w ef core](/ef/core/modeling/owned-entities).

### <a name="resilient-connections"></a>Elastyczne połączenia

Zasoby zewnętrzne, takie jak bazy danych SQL, mogą czasami być niedostępne. W przypadku tymczasowej niedostępności aplikacje mogą używać logiki ponawiania, aby uniknąć wywoływania wyjątku. Technika ta jest powszechnie określana jako _odporność połączenia_. Można zaimplementować [własne próby ponawiania z wykładniczej](https://docs.microsoft.com/azure/architecture/patterns/retry) techniki wycofywania, próbując ponowić próbę z wykładniczo zwiększając czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób. Ta technika obejmuje fakt, że zasoby w chmurze mogą sporadycznie być niedostępne przez krótki okres czasu, co powoduje niepowodzenie niektórych żądań.

W przypadku usługi Azure SQL DB entity framework core już zapewnia odporność połączenia wewnętrznej bazy danych i logiki ponawiania próby. Ale należy włączyć strategię wykonywania entity framework dla każdego połączenia DbContext, jeśli chcesz mieć odporne połączenia EF Core.

Na przykład następujący kod na poziomie połączenia EF Core umożliwia odporne połączenia SQL, które są ponowione, jeśli połączenie nie powiedzie się.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie wykonywania i jawne transakcje przy użyciu BeginTransaction i wielu DbContexts

Gdy próby są włączone w połączeniach EF Core, każda operacja, którą wykonujesz przy użyciu EF Core staje się własną operacją ponawianą. Każde zapytanie i każde wywołanie SaveChanges zostaną ponowione jako jednostka, jeśli wystąpi błąd przejściowy.

Jednak jeśli kod inicjuje transakcję przy użyciu BeginTransaction, definiujesz własną grupę operacji, które muszą być traktowane jako jednostka; wszystko wewnątrz transakcji musi zostać wycofane, jeśli wystąpi błąd. Zostanie wyświetlony wyjątek, jak następujące, jeśli spróbujesz wykonać tę transakcję podczas korzystania ze strategii wykonywania EF (zasady ponawiania próby) i dołączyć kilka SaveChanges z wielu DbContexts w nim.

System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Użyj strategii wykonywania zwróconej przez "DbContext.Database.CreateExecutionStrategy()", aby wykonać wszystkie operacje w transakcji jako jednostkę ponawianą próbę.

Rozwiązaniem jest ręczne wywołanie strategii wykonywania EF z delegata reprezentującego wszystko, co musi zostać wykonane. Jeśli wystąpi błąd przejściowy, strategia wykonywania ponownie wywoła delegata. Poniższy kod pokazuje, jak zaimplementować to podejście:

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

Pierwszy DbContext jest \_catalogContext i drugi DbContext \_znajduje się w integrationEventLogService obiektu. Na koniec commit akcji zostanie wykonana wiele DbContexts i przy użyciu strategii realizacji EF.

> ### <a name="references--entity-framework-core"></a>Referencje — core struktury jednostki
>
> - **Ef Core Dokumenty**
>   <https://docs.microsoft.com/ef/>
> - **Ef Core: Powiązane dane**
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Unikaj jednostek ładowania z opóźnieniem w aplikacjach ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core lub mikro-ORM?

Ef Core jest doskonałym wyborem do zarządzania trwałością i w przeważającej części hermetyzuje szczegóły bazy danych od deweloperów aplikacji, nie jest to jedyny wybór. Inną popularną alternatywą open-source jest [Dapper](https://github.com/StackExchange/Dapper), tzw micro-ORM. Micro-ORM to lekkie, mniej w pełni funkcjonalne narzędzie do mapowania obiektów do struktur danych. W przypadku Dapper jego cele projektowe koncentrują się na wydajności, a nie w pełni hermetyzując podstawowe zapytania, których używa do pobierania i aktualizowania danych. Ponieważ nie jest abstrakcyjny SQL od dewelopera, Dapper jest "bliżej metalu" i pozwala deweloperom napisać dokładne zapytania, które mają być używane dla danej operacji dostępu do danych.

EF Core ma dwie istotne funkcje, które zapewnia, które oddzielają go od Dapper, ale także dodać do jego wydajności narzutu. Pierwszym z nich jest tłumaczenie z wyrażeń LINQ do SQL. Te tłumaczenia są buforowane, ale mimo to istnieje obciążenie w wykonywaniu ich po raz pierwszy. Drugim jest śledzenie zmian w jednostkach (tak, aby można było wygenerować efektywne instrukcje aktualizacji). To zachowanie można wyłączyć dla określonych zapytań przy użyciu rozszerzenia AsNotTracking. EF Core generuje również zapytania SQL, które zwykle są bardzo wydajne i w każdym razie całkowicie dopuszczalne z punktu widzenia wydajności, ale jeśli potrzebujesz precyzyjnej kontroli nad dokładną kwerendą do wykonania, można przekazać w niestandardowym języku SQL (lub wykonać procedurę składowaną) przy użyciu EF Core, zbyt. W tym przypadku Dapper nadal przewyższa EF Core, ale tylko nieznacznie. Julie Lerman przedstawia pewne dane dotyczące wydajności w swoim artykule MSDN z maja 2016 [r. Dapper, Entity Framework i Hybrid Apps](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps). Dodatkowe dane porównawcze wydajności dla różnych metod dostępu do danych można znaleźć na [stronie Dapper](https://github.com/StackExchange/Dapper).

Aby zobaczyć, jak składnia dapper różni się od EF Core, należy wziąć pod uwagę te dwie wersje tej samej metody pobierania listy elementów:

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

Jeśli chcesz zbudować bardziej złożone wykresy obiektów z Dapper, należy napisać skojarzone zapytania samodzielnie (w przeciwieństwie do dodawania Include jak w EF Core). Jest to obsługiwane przez różne składni, w tym funkcję o nazwie Mapowanie wielokrotne, która umożliwia mapowanie poszczególnych wierszy na wiele mapowanych obiektów. Na przykład biorąc pod uwagę klasę Post z właściwością Właściciel typu Użytkownik, następujący SQL zwróci wszystkie niezbędne dane:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Każdy zwrócony wiersz zawiera dane użytkownika i postu. Ponieważ dane Użytkownika powinny być dołączone do danych Post za pośrednictwem jego własności Owner, stosuje się następującą funkcję:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Pełna lista kodów do zwrócenia kolekcji wpisów z ich Owner właściwości wypełnione skojarzonych danych użytkownika będzie:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Ponieważ oferuje mniej hermetyzacji Dapper wymaga deweloperzy wiedzieć więcej o tym, jak ich dane są przechowywane, jak skutecznie zbadać go i napisać więcej kodu, aby go pobrać. Gdy model się zmieni, zamiast po prostu utworzyć nową migrację (inną funkcję EF Core) i/lub zaktualizować informacje mapowania w jednym miejscu w DbContext, każda kwerenda, która ma wpływ, musi zostać zaktualizowana. Te zapytania nie mają żadnych gwarancji czasu kompilacji, więc mogą one przerwy w czasie wykonywania w odpowiedzi na zmiany w modelu lub bazy danych, co błędy trudniejsze do wykrycia szybko. W zamian za te kompromisy, Dapper oferuje niezwykle szybką wydajność.

W przypadku większości aplikacji i większości części prawie wszystkich aplikacji EF Core oferuje akceptowalną wydajność. W związku z tym jego korzyści wydajności dewelopera mogą przeważać nad jego wydajnością. W przypadku kwerend, które mogą korzystać z buforowania, rzeczywiste zapytanie może być wykonywane tylko niewielki procent czasu, dzięki czemu stosunkowo małe różnice wydajności kwerendy dyskusyjne.

## <a name="sql-or-nosql"></a>SQL lub NoSQL

Tradycyjnie relacyjne bazy danych, takie jak SQL Server, zdominowały rynek trwałego przechowywania danych, ale nie są jedynym dostępnym rozwiązaniem. Bazy danych NoSQL, takie jak [MongoDB,](https://www.mongodb.com/what-is-mongodb) oferują inne podejście do przechowywania obiektów. Zamiast mapowania obiektów do tabel i wierszy, inną opcją jest serializowanie całego wykresu obiektu i przechowywanie wyniku. Zalety tego podejścia, przynajmniej początkowo, to prostota i wydajność. Łatwiej jest przechowywać pojedynczy serializowany obiekt z kluczem niż rozkładać obiekt na wiele tabel z relacjami i aktualizacjami i wierszami, które mogły ulec zmianie od czasu ostatniego pobrania obiektu z bazy danych. Podobnie pobieranie i deserializacja pojedynczego obiektu z magazynu opartego na kluczach jest zazwyczaj znacznie szybsze i łatwiejsze niż sprzężenia złożone lub wiele zapytań bazy danych wymaganych do pełnego skomponowania tego samego obiektu z relacyjnej bazy danych. Brak blokad lub transakcji lub schematu stałego również sprawia, że bazy danych NoSQL podatne na skalowanie na wielu komputerach, obsługujących bardzo dużych zestawów danych.

Z drugiej strony bazy danych NoSQL (jak są one zwykle nazywane) mają swoje wady. Relacyjne bazy danych używają normalizacji, aby wymusić spójność i uniknąć powielania danych. Zmniejsza to całkowity rozmiar bazy danych i zapewnia, że aktualizacje udostępnionych danych są dostępne natychmiast w całej bazie danych. W relacyjnej bazie danych tabela adresowa może odwoływać się do tabeli Kraj według identyfikatora, tak aby w przypadku zmiany nazwy kraju/regionu rekordy adresów korzystały z aktualizacji bez konieczności aktualizowania. Jednak w bazie danych NoSQL adres i skojarzony z nim kraj mogą być serializowane jako część wielu przechowywanych obiektów. Aktualizacja nazwy kraju/regionu wymagałaby aktualizacji wszystkich takich obiektów, a nie pojedynczego wiersza. Relacyjne bazy danych mogą również zapewnić integralność relacyjnej, wymuszając reguły, takie jak klucze obce. Bazy danych NoSQL zazwyczaj nie oferują takich ograniczeń na ich danych.

Inną złożonością, z którą muszą radzić sobie bazy danych NoSQL, jest przechowywanie wersji. Po zmianie właściwości obiektu, może nie być w stanie być deserialized z poprzednich wersji, które były przechowywane. W związku z tym wszystkie istniejące obiekty, które mają serializowane (poprzednia) wersja obiektu muszą zostać zaktualizowane, aby były zgodne z jego nowym schematem. Nie różni się to koncepcyjnie od relacyjnej bazy danych, w której zmiany schematu czasami wymagają skryptów aktualizacji lub aktualizacji mapowania. Jednak liczba wpisów, które muszą być modyfikowane jest często znacznie większa w podejściu NoSQL, ponieważ istnieje więcej powielania danych.

Jest to możliwe w bazach danych NoSQL do przechowywania wielu wersji obiektów, coś stałe schemat relacyjnych baz danych zazwyczaj nie obsługują. Jednak w tym przypadku kod aplikacji będzie musiał uwzględnić istnienie poprzednich wersji obiektów, dodając dodatkową złożoność.

Bazy danych NoSQL zazwyczaj nie wymuszają [ACID](https://en.wikipedia.org/wiki/ACID), co oznacza, że mają zarówno wydajność, jak i skalowalność korzyści w stosunku do relacyjnych baz danych. Doskonale nadają się do bardzo dużych zestawów danych i obiektów, które nie są dobrze przystosowane do przechowywania w znormalizowanych strukturach tabel. Nie ma powodu, dla którego pojedyncza aplikacja nie może korzystać z relacyjnych i nosql baz danych, przy użyciu każdego, gdzie jest to najlepiej nadaje.

## <a name="azure-cosmos-db"></a>Azure Cosmos DB

Usługa Azure Cosmos DB to w pełni zarządzana usługa bazy danych NoSQL, która oferuje magazyn danych bez użycia schematu w chmurze. Usługa Azure Cosmos DB została stworzona z myślą o szybkiej i przewidywalnej wydajności, wysokiej dostępności, elastycznym skalowaniu i dystrybucji globalnej. Pomimo bazy danych NoSQL, deweloperzy mogą korzystać z bogatych i znanych funkcji zapytań SQL na danych JSON. Wszystkie zasoby w usłudze Azure Cosmos DB są przechowywane jako dokumenty JSON. Zasoby są zarządzane jako _elementy_, które są dokumentami zawierającymi metadane i _źródła danych_, które są kolekcjami elementów. Rysunek 8-2 przedstawia relację między różnymi zasobami usługi Azure Cosmos DB.

![Hierarchiczna relacja między zasobami w usłudze Azure Cosmos DB, bazie danych JSON NoSQL](./media/image8-2.png)

**Rysunek 8-2.** Organizacja zasobów usługi Azure Cosmos DB.

Język zapytań usługi Azure Cosmos DB to prosty, ale zaawansowany interfejs do wykonywania zapytań o dokumenty JSON. Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywoływania funkcji języka JavaScript.

**Odwołania — usługa Azure Cosmos DB**

- Wprowadzenie do usługi Azure Cosmos DB<https://docs.microsoft.com/azure/cosmos-db/introduction>

## <a name="other-persistence-options"></a>Inne opcje trwałości

Oprócz relacyjnych i nosql opcje magazynu, ASP.NET aplikacje Core można używać usługi Azure Storage do przechowywania różnych formatów danych i plików w chmurze, skalowalny sposób. Usługa Azure Storage jest masowo skalowalna, dzięki czemu można rozpocząć przechowywanie niewielkich ilości danych i skalować do przechowywania setek lub terabajtów, jeśli aplikacja tego wymaga. Usługa Azure Storage obsługuje cztery rodzaje danych:

- Magazyn obiektów blob dla nieustrukturyzowanego tekstu lub magazynu binarnego, nazywany również magazynem obiektów.

- Magazyn tabel dla zestawów danych strukturalnych, dostępny za pomocą kluczy wierszy.

- Magazyn kolejek dla niezawodnych wiadomości opartych na kolejkach.

- Magazyn plików dla udostępnionego dostępu do plików między maszynami wirtualnymi platformy Azure i aplikacjami lokalnymi.

**Odwołania — usługa Azure Storage**

- Wprowadzenie do usługi Azure Storage<https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Buforowanie

W aplikacjach sieci web każde żądanie sieci web należy wykonać w jak najkrótszym czasie. Jednym ze sposobów osiągnięcia tego celu jest ograniczenie liczby wywołań zewnętrznych, które serwer musi wykonać, aby ukończyć żądanie. Buforowanie polega na przechowywaniu kopii danych na serwerze (lub innym magazynie danych, który jest łatwiej wyszukiwany niż źródło danych). Aplikacje sieci Web, a zwłaszcza nie-SPA tradycyjnych aplikacji sieci web, trzeba zbudować cały interfejs użytkownika przy każdym żądaniu. Często wiąże się to z wykonywaniem wielu tych samych zapytań bazy danych wielokrotnie z jednego żądania użytkownika do następnego. W większości przypadków te dane zmieniają się rzadko, więc nie ma powodu, aby stale żądać go z bazy danych. ASP.NET Core obsługuje buforowanie odpowiedzi, buforowanie całych stron i buforowanie danych, które obsługuje bardziej szczegółowe zachowanie buforowania.

Podczas wdrażania buforowania, ważne jest, aby pamiętać o oddzieleniu problemów. Należy unikać implementowania logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika. Zamiast tego hermetyzować buforowania w własnych klasach i używać konfiguracji do zarządzania jego zachowanie. Jest to zgodne z zasadami Otwarte/Zamknięte i Pojedyncza Odpowiedzialność i ułatwi zarządzanie sposób korzystania z buforowania w aplikacji, jak rośnie.

### <a name="aspnet-core-response-caching"></a>ASP.NET Buforowanie odpowiedzi podstawowych

ASP.NET Core obsługuje dwa poziomy buforowania odpowiedzi. Pierwszy poziom nie buforuje niczego na serwerze, ale dodaje nagłówki HTTP, które instruują klientów i serwery proxy do buforowania odpowiedzi. Jest to implementowane przez dodanie responsecache atrybut do poszczególnych kontrolerów lub akcji:

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

W poprzednim przykładzie spowoduje, że następujący nagłówek zostanie dodany do odpowiedzi, instruując klientów do buforowania wyniku przez maksymalnie 60 sekund.

Kontrola pamięci podręcznej: publiczna, max-age=60

Aby dodać buforowanie po stronie serwera w pamięci do aplikacji, należy odwołać się do pakietu Microsoft.AspNetCore.ResponseCaching NuGet, a następnie dodać oprogramowanie pośredniczące buforowania odpowiedzi. To oprogramowanie pośredniczące jest skonfigurowane zarówno w obszarze ConfigureServices, jak i Configure in Startup:

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

Oprogramowanie pośredniczące buforowania odpowiedzi automatycznie buforuje odpowiedzi na podstawie zestawu warunków, które można dostosować. Domyślnie tylko 200 (OK) odpowiedzi wymagane za pośrednictwem metody GET lub HEAD są buforowane. Ponadto żądania muszą mieć odpowiedź z cache-control: nagłówek publiczny i nie może zawierać nagłówków autoryzacji lub set-cookie. Zobacz [pełną listę warunków buforowania używanych przez oprogramowanie pośredniczące buforowania odpowiedzi](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Buforowanie danych

Zamiast (lub dodatkowo) buforowania pełnych odpowiedzi sieci web, można buforować wyniki poszczególnych zapytań danych. W tym celu można użyć w buforowaniu pamięci na serwerze sieci web lub użyć [rozproszonej pamięci podręcznej](/aspnet/core/performance/caching/distributed). W tej sekcji pokazano, jak zaimplementować w buforowaniu pamięci.

Dodano obsługę buforowania pamięci (lub rozproszonego) w configureservices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Należy również dodać pakiet Microsoft.Extensions.Caching.Memory NuGet.

Po dodaniu usługi, żądanie IMemoryCache za pośrednictwem iniekcji zależności, gdziekolwiek trzeba uzyskać dostęp do pamięci podręcznej. W tym przykładzie CachedCatalogService używa wzorca projektu proxy (lub Dekorator), zapewniając alternatywną implementację ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie) podstawowej implementacji CatalogService.

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

Aby skonfigurować aplikację do korzystania z buforowanej wersji usługi, ale nadal zezwalaj usłudze na uzyskanie wystąpienia CatalogService, której potrzebuje w konstruktorze, należy dodać następujące w configureservices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Z tym w miejscu bazy danych wywołuje pobieranie danych katalogu będą dokonywane tylko raz na minutę, a nie na każde żądanie. W zależności od ruchu do witryny może to mieć znaczący wpływ na liczbę zapytań do bazy danych i średni czas ładowania strony dla strony głównej, która obecnie zależy od wszystkich trzech zapytań udostępniane przez tę usługę.

Problem, który pojawia się podczas buforowania jest zaimplementowane jest _przestarzałe dane_ — oznacza to, że dane, które uległy zmianie u źródła, ale wersja nieaktualna pozostaje w pamięci podręcznej. Prostym sposobem złagodzenia tego problemu jest użycie małych czasów trwania pamięci podręcznej, ponieważ dla zajętej aplikacji istnieje ograniczona dodatkowa korzyść dla rozszerzenia długości danych jest buforowana. Rozważmy na przykład stronę, która tworzy kwerendę pojedynczej bazy danych i jest wymagana 10 razy na sekundę. Jeśli ta strona jest buforowana przez jedną minutę, spowoduje to spadek liczby zapytań bazy danych wykonanych na minutę z 600 do 1, co oznacza zmniejszenie o 99,8%. Jeśli zamiast tego czas trwania pamięci podręcznej zostały wykonane jedną godzinę, ogólne zmniejszenie będzie 99.997%, ale teraz prawdopodobieństwo i potencjalny wiek starych danych są zarówno znacznie wzrosła.

Innym podejściem jest proaktywne usuwanie wpisów pamięci podręcznej, gdy dane, które zawierają są aktualizowane. Każdy pojedynczy wpis można usunąć, jeśli jego klucz jest znany:

```csharp
_cache.Remove(cacheKey);
```

Jeśli aplikacja udostępnia funkcje aktualizowania wpisów, które buforuje, można usunąć odpowiednie wpisy pamięci podręcznej w kodzie, który wykonuje aktualizacje. Czasami może istnieć wiele różnych wpisów, które zależą od określonego zestawu danych. W takim przypadku może być przydatne do tworzenia zależności między wpisami pamięci podręcznej, przy użyciu CancellationChangeToken. Z CancellationChangeToken, można wygasnąć wiele wpisów pamięci podręcznej na raz, anulując token.

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

Buforowanie może znacznie poprawić wydajność stron sieci web, które wielokrotnie żądają tych samych wartości z bazy danych. Przed zastosowaniem buforowania należy zmierzyć dostęp do danych i wydajność strony, a także zastosować buforowanie tylko wtedy, gdy istnieje potrzeba poprawy. Buforowanie zużywa zasoby pamięci serwera sieci web i zwiększa złożoność aplikacji, dlatego ważne jest, aby nie przedwcześnie optymalizować przy użyciu tej techniki.

>[!div class="step-by-step"]
>[Poprzedni](develop-asp-net-core-mvc-apps.md)
>[następny](test-asp-net-core-mvc-apps.md)
