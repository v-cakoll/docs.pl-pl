---
title: Praca z danymi w aplikacji ASP.NET Core
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Praca z danymi w aplikacji platformy ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 914a10724c416f453d93f6efc16f9ad192798264
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827178"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Praca z danymi w aplikacji platformy ASP.NET Core

> "Dane cennego rzecz i będzie wystarczą na dłużej, niż samych systemów."
>
> Tim Berners-Lee

Dostęp do danych jest ważnym elementem niemal wszystkich aplikacji. Platforma ASP.NET Core obsługuje szereg opcji dostępu do danych, w tym platformy Entity Framework Core (i platformy Entity Framework 6 także) i można pracować z dowolnego środowiska .NET framework dostępu do danych. Wybór, z których dostępu do danych platformę, by używać zależy od potrzeb aplikacji. Abstrakcyjność te opcje w projektach ApplicationCore i interfejs użytkownika i enkapsulacji szczegółów implementacji w infrastrukturze, pomaga tworzyć oprogramowanie luźno powiązanych, sprawdzalnego działa zgodnie.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (dla relacyjnych baz danych)

Jeśli piszesz nowej aplikacji platformy ASP.NET Core, który wymaga do pracy z danymi relacyjnymi, platformy Entity Framework Core (EF Core) jest zalecany sposób dostępu do danych aplikacji. EF Core to maper obiektowo relacyjny (O/RM), który umożliwia deweloperom platformy .NET do utrwalania obiektów do i ze źródła danych. Eliminuje to potrzebę do większości kod dostępu do danych, których deweloperzy zazwyczaj konieczne zapisu. Np. ASP.NET Core programu EF Core ma został przepisany od podstaw w celu obsługi modułowej aplikacje dla wielu platform. Dodaj go do aplikacji jako pakiet NuGet, skonfiguruj go na uruchamianie i żądania za pomocą iniekcji zależności, wszędzie tam, gdzie ich potrzebujesz.

Aby użyć programu EF Core z bazą danych programu SQL Server, uruchom następujące polecenie interfejsu wiersza polecenia platformy dotnet:

polecenia DotNet Dodaj pakiet Microsoft.EntityFrameworkCore.SqlServer

Aby dodać obsługę dla źródła danych InMemory do testowania:

polecenia DotNet Dodaj pakiet Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>Kontekstu DbContext

Aby pracować z programem EF Core, potrzebujesz podklasą <xref:Microsoft.EntityFrameworkCore.DbContext>. Ta klasa posiada właściwości reprezentujące kolekcji obiektów, których Twoja aplikacja będzie działać z. Przykład eShopOnWeb obejmuje CatalogContext przy użyciu kolekcji elementów, marek i typy:

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

Twoje DbContext posiadanie Konstruktor, który akceptuje DbContextOptions oraz przekazania tego argumentu do konstruktora bazowego typu DbContext. Należy pamiętać, że jeśli masz tylko jeden kontekst DbContext w aplikacji, można przekazać wystąpienia DbContextOptions, ale jeśli masz więcej niż jeden należy użyć ogólnego DbContextOptions<T> typu, przekazując jako parametr ogólny typu DbContext.

### <a name="configuring-ef-core"></a>Konfigurowanie programu EF Core

W aplikacji ASP.NET Core zwykle skonfigurujesz programu EF Core w metodzie ConfigureServices. EF Core używa DbContextOptionsBuilder, która obsługuje kilka metod pomocnego rozszerzenia, aby usprawnić jego konfiguracji. Aby skonfigurować CatalogContext bazy danych programu SQL Server za pomocą parametrów połączenia, zdefiniowane w konfiguracji, należy dodać następujący kod do ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Aby użyć bazy danych w pamięci:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po zainstalowaniu programu EF Core, typem DbContext podrzędny utworzone i skonfigurowane w ConfigureServices, jesteś gotowy do użycia z programem EF Core. Wystąpienie tego typu DbContext w dowolnej usługi, którym jest on wymagany do żądania i rozpocząć pracę z utrwalonego jednostek za pomocą LINQ, tak jakby były one po prostu w kolekcji. EF Core działa tłumaczenia wyrażenia LINQ do zapytań SQL do przechowywania i pobierania danych.

Możesz zobaczyć zapytań programu EF Core jest wykonywany przez skonfigurowanie Rejestrator oraz zapewnienia jego poziom jest równa co najmniej informacji, jak pokazano w rysunek 8-1.

![](./media/image8-1.png)

Rysunek 8-1 rejestrowania programu EF Core zapytania do konsoli

### <a name="fetching-and-storing-data"></a>Trwa pobieranie i zapisywanie danych

Do pobierania danych z programem EF Core, dostęp do odpowiedniej właściwości i używać programu LINQ do filtrowania wyników. LINQ umożliwia również wykonywać projekcji, transformacji wyniku z jednego typu na inny. Poniższy przykład pobiera CatalogBrands, uporządkowane według nazwy, filtrowane według ich właściwość włączone i rzutowany na typ SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Jest ważne w powyższym przykładzie, aby dodać wywołanie do ToListAsync, aby można było przeprowadzić zapytanie natychmiastowo. W przeciwnym razie instrukcji przypisze element IQueryable<SelectListItem> do brandItems, który nie zostanie wykonany dopóki go wyliczenia. Istnieją zalety i wady do zwracania wyników IQueryable z metod. Umożliwia to zapytanie, które programu EF Core będzie konstruowania można dalej modyfikować, ale może również powodować błędy występujące tylko w czasie wykonywania, jeśli działania są dodawane do zapytania, które nie może tłumaczyć programu EF Core. Zazwyczaj bezpieczniej przekazać jakiekolwiek filtry do metody wykonywania dostępu do danych, a zwracany z powrotem kolekcji w pamięci (na przykład listy<T>) jako wynik.

EF Core śledzi zmiany w jednostkach, który pobiera się go z trwałości. Aby zapisać zmiany do śledzonych jednostki, po prostu Wywołaj metodę SaveChanges dla kontekstu DbContext, upewniając się, że jest to samo wystąpienie typu DbContext, który został użyty do pobrania jednostki. Dodawanie i usuwanie jednostek odbywa się bezpośrednio na odpowiedniej właściwości DbSet ponownie z wywołaniem funkcji SaveChanges można wykonać polecenia bazy danych. Poniższy przykład pokazuje, dodawanie, aktualizowanie i usuwanie jednostek trwałości.

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

EF Core obsługuje zarówno synchroniczne i asynchroniczne metody pobierania i zapisywania. W aplikacjach sieci web zaleca się używanie wzorca async/await z metodami asynchronicznymi, tak aby wątków serwera sieci web nie są blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.

### <a name="fetching-related-data"></a>Pobieranie powiązanych danych

Jeśli programu EF Core pobiera jednostek, wypełnienie wszystkich właściwości, które są przechowywane bezpośrednio z tej jednostki w bazie danych. Właściwości nawigacji, takie jak listy powiązanych jednostek nie są uzupełniane i może mieć ich ma wartość null. Dzięki temu programu EF Core nie: pobieranie większej ilości danych niż jest potrzebny, co jest szczególnie ważne dla aplikacji sieci web, które musi szybko przetwarzania żądań i zwracania odpowiedzi w sposób efektywny. Aby uwzględnić relacje z jednostki przy użyciu _wczesne ładowanie_, możesz określić właściwości, za pomocą metody rozszerzenia Include w zapytaniu, jak pokazano:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Może zawierać wiele relacji, a możesz również uwzględnić relacje podrzędne przy użyciu ThenInclude. EF Core wykona pojedynczego zapytania można pobrać Wynikowy zestaw jednostek. Alternatywnie może zawierać właściwości nawigacji dla właściwości nawigacji, przekazując "." -rozdzielonych ciąg `.Include()` metodę rozszerzenia, w następujący sposób:

```csharp
    .Include(“Items.Products”)
```

Oprócz enkapsulacji logikę filtrowania, Specyfikacja można określić kształt danych ma zostać zwrócone, łącznie z właściwości, które można wypełnić. Przykład eShopOnWeb obejmuje kilka specyfikacje, które pokazują, zawieranie wczesne ładowanie informacji w ramach specyfikacji. Aby zobaczyć, jak specyfikację jest używana jako część zapytania w tym miejscu:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

Innym rozwiązaniem do ładowania danych pokrewnych jest użycie _jawne ładowanie_. Jawne ładowanie umożliwia ładowanie dodatkowe dane do jednostki, które już zostały pobrane. Ponieważ wymaga to oddzielne żądania w bazie danych, nie jest zalecane dla aplikacji sieci web, które należy zminimalizować liczbę baz danych rund wprowadzone na żądanie.

_Powolne ładowanie_ to funkcja, która automatycznie ładuje powiązanych danych, ponieważ jest odwoływany przez aplikację. EF Core została dodana obsługa ładowania z opóźnieniem w wersji 2.1. Powolne ładowanie nie jest domyślnie włączona i wymaga zainstalowania `Microsoft.EntityFrameworkCore.Proxies`. Podobnie jak w przypadku jawne ładowanie powolne ładowanie powinien zazwyczaj można wyłączyć dla aplikacji sieci web, ponieważ spowoduje jej użycie w zapytaniach dodatkowa baza danych, które zostaną wprowadzone w ramach każdego żądania sieci web. Niestety koszty ponoszone przez powolne ładowanie często prowadzi niezauważona w czasie projektowania, gdy czas oczekiwania jest mały i często są małe, zestawy danych używane do testowania. Jednak w środowisku produkcyjnym z większej liczby użytkowników, większej ilości danych i więcej opóźnienia żądania dodatkowej bazy danych można często spowodować obniżenie wydajności dla aplikacji sieci web, które intensywnie korzystają z opóźnieniem ładowania.

[Należy unikać powolne ładowanie jednostek w aplikacjach sieci Web](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Zawieranie danych

EF Core obsługuje kilka funkcji, które umożliwiają modelu do hermetyzacji prawidłowo swojego stanu. Typowym problemem w modeli domeny jest eksponowanie właściwości nawigacji kolekcji jako typy list dostępny publicznie. Dzięki temu wszystkie współpracownika do manipulowania zawartość tych kolekcji typów, które może pominąć reguł biznesowych ważne związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie. Rozwiązaniem tego problemu, aby uwidocznić dostęp tylko do odczytu do powiązanej kolekcji i jawnie zapewnić metody definiowania sposobów, w których klientów można manipulować nimi, jak w poniższym przykładzie:

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

Należy pamiętać, że tego typu jednostki nie ujawnia publiczny `List` lub `ICollection` właściwości, ale zamiast tego udostępnia `IReadOnlyCollection` typ, który otacza bazowego typu listy. Gdy za pomocą ten wzorzec może wskazywać na platformy Entity Framework Core służące do pola pomocniczego w następujący sposób:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Innym sposobem, w którym można zwiększyć modelu domeny jest przy użyciu obiektów wartości dla typów, Brak tożsamości, które różnią się tylko przez ich właściwości. Używanie tych typów jako właściwości jednostki zabezpieczać logiki określonego obiektu wartości, gdzie należy i uniknąć zduplikowanych logika między wiele jednostek, które używają tego samego pojęcia. W programie Entity Framework Core można utrwalić obiekty wartości w tej samej tabeli jako ich właścicielem jednostki, konfigurując typ jako jednostki należące do firmy, w następujący sposób:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

W tym przykładzie `ShipToAddress` właściwość jest typu `Address`. `Address` jest obiekt wartości przy użyciu kilka właściwości, takich jak `Street` i `City`. EF Core mapuje `Order` obiektu do swojej tabeli z jedną kolumną na `Address` właściwości poprzedzania ich nazwa kolumny o nazwie właściwości. W tym przykładzie `Order` tabela będzie zawierać kolumny takie jak `ShipToAddress_Street` i `ShipToAddress_City`.

[EF Core 2.2 wprowadzono obsługę kolekcjami jednostek należące do firmy](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a>Odporne na błędy połączenia

Zasobów zewnętrznych, takich jak bazy danych SQL co pewien czas mogą być niedostępne. W przypadku tymczasowej niedostępności aplikacje mogą używać logikę ponawiania próby, aby uniknąć zgłaszania wyjątku. Ta technika jest często nazywany _elastyczność połączenia_. Można zaimplementować swoje [własnych ponawiania wykładniczego wycofywania](https://docs.microsoft.com/azure/architecture/patterns/retry) technika przez próby ponowienia z wykładniczo rosnącym czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób. Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępna przez krótki okres czasu, co spowoduje niepowodzenie niektórych żądań.

Dla bazy danych SQL Azure platformy Entity Framework Core już zawiera logikę ponawiania prób i odporności połączenia wewnętrznej bazy danych. Jednak należy włączyć strategii wykonywania programu Entity Framework, dla każdego połączenia DbContext, jeśli chcesz mieć odporne na błędy połączeń programu EF Core.

Na przykład następujący kod na poziomie połączenia platformy EF Core umożliwia odporne na błędy połączeń SQL, które są zwalniane, jeśli połączenie nie powiedzie się.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategii wykonywania i jawnego transakcji za pomocą BeginTransaction i wiele DbContexts

Po włączeniu ponownych prób w połączeniach programu EF Core każdej operacji, które możesz wykonać przy użyciu programu EF Core staje się własną wywołały operacji. Jeśli wystąpi błąd przejściowy, każde zapytanie i każde wywołanie funkcji SaveChanges zostanie ponowiona jako jednostka.

Jednak jeśli Twój kod inicjuje transakcji za pomocą BeginTransaction, definiujesz własną grupę działań, które muszą być traktowane jako jedna całość; wszystko wewnątrz transakcji musi zostać wycofana ponownie, jeśli wystąpi awaria. Jeśli użytkownik podejmie próbę wykonania transakcji, gdy za pomocą strategii wykonywania EF (zasady ponawiania) i obejmują SaveChanges kilka z wielu DbContexts w nim pojawi się wyjątek, jak pokazano poniżej.

System.InvalidOperationException: Strategia wykonywania skonfigurowany "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji zainicjowanej przez użytkownika. Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostka z możliwością ponowienia próby.

To rozwiązanie jest ręcznie wywołać strategii wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana. Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła delegata ponownie. Poniższy kod przedstawia sposób implementowania tego podejścia:

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

Jest pierwszym DbContext \_catalogContext, a druga DbContext mieści się w \_integrationEventLogService obiektu. Na koniec zatwierdzenia akcji będą wykonywane wielu DbContexts i za pomocą strategii wykonywania EF.

> ### <a name="references--entity-framework-core"></a>Odwołania — platformy Entity Framework Core
>
> - **Dokumentacji programu EF Core**  
>   <https://docs.microsoft.com/ef/>
> - **EF Core: Powiązane dane**  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Należy unikać powolne ładowanie jednostek w aplikacjach ASPNET**  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core lub micro ORM?

EF Core jest doskonałym wyborem do zarządzania trwałości i w większości przypadków hermetyzuje Szczegóły bazy danych z deweloperami aplikacji, nie jest jedyną dostępną. Innym sposobem typu open source jest [programem Dapper](https://github.com/StackExchange/Dapper), tak zwane ORM micro. Operacje micro-ORM to lekkie, mniej w pełni funkcjonalne narzędzie mapowania obiektów do struktur danych. W przypadku programem Dapper jego celów skupić się na wydajności, a nie w pełni enkapsulacji bazowego pyta o niego projekt używa do pobierania i aktualizowania danych. Ponieważ nie ona abstrakcyjna SQL od dewelopera, programem Dapper jest "uznane za bliższe sprzętu" i umożliwia deweloperom pisanie dokładnie operacja dostępu do zapytania, które mają być użyte dla danego danych.

EF Core ma dwie funkcje znaczące, zapewnia które oddzielić go z programem Dapper, ale również dodać do jej zmniejszenie wydajności. Pierwsza to tłumaczenie z wyrażenia LINQ do SQL. Te tłumaczenia są buforowane, ale mimo ma obciążenie w wykonywaniu ich po raz pierwszy. Drugim jest śledzenia zmian na jednostkach (dzięki czemu mogą być generowane instrukcjach update wydajne). To zachowanie można wyłączyć dla określonego zapytania za pomocą rozszerzenia AsNotTracking. EF Core generuje również zapytania SQL, które zwykle są bardzo wydajny i w każdym przypadku doskonale akceptowalne z punktu widzenia wydajności, ale jeśli potrzebujesz poprawnie kontrolę nad dokładne zapytanie do wykonania, możesz przekazać niestandardowe SQL (lub wykonaj procedurę składowaną) przy użyciu programu EF Podstawowe, zbyt. W tym przypadku przewyższa przekształcania programem Dapper nadal stosowane programu EF Core, ale tylko nieznacznie. Przedstawia Julie Lerman niektóre dane dotyczące wydajności w jej może artykuł w witrynie MSDN 2016 [programem Dapper, platformy Entity Framework oraz hybrydowych aplikacji](https://msdn.microsoft.com/magazine/mt703432.aspx). Dodatkowych testów porównawczych danych o wydajności dla różnych metod dostępu do danych można znaleźć na [lokacji z programem Dapper](https://github.com/StackExchange/Dapper).

Aby zobaczyć, jak składnia programem Dapper zmienia się z programem EF Core, należy wziąć pod uwagę te dwie wersje tej samej metody do pobierania listy elementów:

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

Jeśli potrzebujesz do tworzenia bardziej złożonych wykresów obiektów z programem Dapper, należy napisać samodzielnie skojarzone zapytania (w przeciwieństwie do dodawania dołączania, tak jak w programie EF Core). Jest to obsługiwane za pośrednictwem różnych składni, w tym funkcję o nazwie Multi mapowanie umożliwiające mapowanie poszczególne wiersze do wielu obiektów zamapowanego. Na przykład biorąc pod uwagę klasy wpis z właściwością właściciela typu użytkownika, następujące instrukcje SQL zwróci wszystkie niezbędne dane:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Każdego zwróconego wiersza zawiera dane użytkownika i Post. Ponieważ dane użytkownika musi być podłączona do danych Post za pomocą właściwości jego właściciela, jest używany następującą funkcję:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Listy pełnego kodu do zwrócenia zbiór wpisów z ich właściwości właściciela wypełniony danymi skojarzonego użytkownika mogą być następujące:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Ponieważ oferuje ona mniejszą hermetyzacji, programem Dapper wymaga deweloperów dowiedzieć się więcej o jak są przechowywane ich dane, jak skutecznie wykonuje zapytania i zapisać więcej kodu, aby go pobrać. Po zmianie modelu, a nie po prostu utworzenie nowej migracji (inna funkcja programu EF Core) i/lub aktualizowanie informacji o mapowaniu w jednym miejscu w DbContext każdego zapytania, które ma wpływ na musi zostać zaktualizowany. Te zapytania zostały bez gwarancji czasu kompilacji, więc one mogą przestać działać w czasie wykonywania w odpowiedzi na zmiany w modelu lub bazy danych, co utrudnia szybko wykrywać błędy. W zamian za tych kompromisów programem Dapper oferuje bardzo wydajne.

Dla większości aplikacji i większość części niemal wszystkich aplikacji programu EF Core zapewnia akceptowalny poziom wydajności. W związku z tym jego korzyści produktywność dla deweloperów prawdopodobnie przeważają swoje zmniejszenie wydajności. Dla zapytań, które mogą korzystać z pamięci podręcznej, rzeczywiste zapytanie może wykonać tylko niewielki odsetek czasu, dzięki czemu stosunkowo mały zapytania moot różnice wydajności.

## <a name="sql-or-nosql"></a>Bazy danych SQL lub NoSQL

Tradycyjnie relacyjnych baz danych, takich jak program SQL Server ma zdominowany trwałego magazynu danych w witrynie marketplace, ale nie są one dostępne jedynym rozwiązaniem. Bazy danych NoSQL, takie jak [bazy danych MongoDB](https://www.mongodb.com/what-is-mongodb) oferuje innego podejścia do przechowywania obiektów. Zamiast mapowanie obiektów na tabele oraz wiersze, innym rozwiązaniem jest serializacji wykresu cały obiekt i zapisz wynik. Zalety tego podejścia są co najmniej początkowo prostoty i wydajności. Bez obaw prostszym sposobem przechowywania pojedynczy obiekt Zserializowany za pomocą klucza, niż można rozłożyć obiektu do wielu tabel z relacjami i pobrać aktualizacji i wierszy, które uległy zmianie od ostatniego obiektu z bazy danych. Podobnie Pobieranie i deserializację pojedynczy obiekt z magazynu opartego na kluczach jest zwykle szybsze i prostsze niż złożonych sprzężeń lub wiele zapytań bazy danych wymagane do tworzenia w pełni tego samego obiektu z relacyjnej bazy danych. Brak blokady lub transakcji lub stałego schematu sprawia, że bazy danych NoSQL bardzo podatna na skalowanie na wiele maszyn, obsługa bardzo dużych zestawów danych.

Z drugiej strony bazy danych NoSQL (zazwyczaj są one nazywane) mają swoje wady. Relacyjne bazy danych użyj normalizacji, wymuszanie spójności i unikanie zduplikowanie danych. Zmniejsza całkowity rozmiar bazy danych i zapewnia, że aktualizacje do udostępnionych danych są dostępne bezpośrednio w bazie danych. W relacyjnej bazie danych tabeli adresów może odwołać się do kraju tabeli według identyfikatorów, taki sposób, że jeśli zmieniono nazwę kraju, rekordów adresów będą korzystać z aktualizacji bez muszą zostać zaktualizowane. Jednak w bazie danych NoSQL adres i jego skojarzone kraj może zostać Zserializowany jako część wiele obiektów przechowywanych. Aktualizacja Nazwa kraju wymagałoby wszystkie takie obiekty do zaktualizowania, a nie pojedynczego wiersza. Relacyjne bazy danych może również zagwarantować integralności relacyjnych przez wymuszenie zasad, takie jak klucze obce. Bazy danych NoSQL nie oferują zazwyczaj takie ograniczenia swoich danych.

Inny złożoności musi obsłużyć baz danych NoSQL jest przechowywania wersji. Po zmianie właściwości tego obiektu, nie można mogła zostać przeprowadzona poprzednich wersji, które były przechowywane. W związku z tym aby były zgodne ze schematem nowe należy zaktualizować wszystkich istniejących obiektów, które mają (poprzednia wersja) wersja po serializacji jest obiektu. Różni się to nie koncepcyjnie z relacyjnej bazy danych, w przypadku, gdy schemat zmienia się czasami wymagają skryptów aktualizacji lub mapowania aktualizacji. Jednak liczba wpisów, które muszą zostać zmodyfikowane odbywa się znacznie większa w ujęciu NoSQL, ponieważ ma więcej zduplikowanie danych.

Jest to możliwe w bazy danych NoSQL do przechowywania wielu wersji obiektów, coś stały schemat relacyjnych baz danych zwykle nie obsługują. Jednak w takiej sytuacji kod aplikacji należy uwzględnić istnienie poprzednie wersje obiekty, dodawanie dodatkowej złożoności.

Zazwyczaj nie wymuszają bazy danych NoSQL [ACID](https://en.wikipedia.org/wiki/ACID), co oznacza, że ich korzystnie wpływać na wydajność i skalowalność za pośrednictwem relacyjnych baz danych. Są one dobrze nadaje się do bardzo dużych zestawów danych i obiektów, które nie nadają się do magazynu w strukturach znormalizowanych tabel. Nie ma powodu i dlaczego pojedynczej aplikacji nie mogą korzystać zarówno relacyjnych baz danych NoSQL, przy użyciu każdego, gdzie najlepiej dostosowane.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB to w pełni zarządzana usługa bazy danych NoSQL, która oferuje magazyn danych bez schematu w chmurze. Baza danych DocumentDB jest stworzona z myślą szybkie przetwarzanie, przewidywalną wydajność, wysoką dostępność, elastyczne skalowanie i globalnej dystrybucji. Mimo iż bazę danych NoSQL, deweloperzy mogą używać szerokie i powszechnie znane możliwości zapytań SQL na dane JSON. Wszystkie zasoby w usłudze DocumentDB są przechowywane jako dokumenty JSON. Zasoby są zarządzane jako _elementów_, które są dokumenty zawierające metadane, oraz _źródła_, które są kolekcjami elementów. Rysunek 8-2 przedstawiono relacje między różnymi zasobami usługi DocumentDB.

![Hierarchiczna relacja między zasobami w usłudze DocumentDB, bazy danych NoSQL JSON](./media/image8-2.png)

**Rysunek 8-2.** Organizacji zasobów usługi DocumentDB.

Język zapytań usługi DocumentDB jest prostym, ale zaawansowanym interfejsem na wykonywanie zapytań względem dokumentów JSON. Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywołania funkcji JavaScript.

**Odwołania — baza danych DocumentDB**

- Wprowadzenie do usługi DocumentDB  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Inne opcje trwałości

Oprócz relacyjnych i opcje magazynu NoSQL aplikacje platformy ASP.NET Core można użyć usługi Azure Storage do przechowywania różnych formatów danych i plików w sposób oparte na chmurze, skalowalne. Usługa Azure Storage jest wysoce skalowalnej, więc możesz rozpocząć przechowywania niewielkich ilości danych i skalowanie w górę do przechowywania setki lub terabajtów, jeśli aplikacja wymaga go. Usługa Azure Storage obsługuje cztery rodzaje danych:

- Blob Storage służy do tekstu bez struktury lub magazyn binarny, nazywane również magazynu obiektów.

- Table Storage w przypadku zestawów strukturalnych danych dostępne za pośrednictwem kluczy wierszy.

- Queue Storage niezawodne kolejki komunikatów.

- Plik magazynu udostępnionego przy dostępie do plików między maszynami wirtualnymi platformy Azure i aplikacji lokalnych.

**Odwołania — usługa Azure Storage**

- Wprowadzenie do usługi Azure Storage  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Buforowanie

W aplikacjach sieci web należy wykonać wszystkie żądania sieci web w możliwie jak najszybciej. Jednym ze sposobów osiągnięcia tego jest ograniczyć liczbę wywołań zewnętrznego serwera należy wykonać w celu wykonania żądania. Buforowanie obejmuje przechowywanie kopii danych na serwerze (lub inny magazyn danych to znaczy więcej łatwo zapytań od źródła danych). Aplikacje sieci Web i szczególnie bez SPA tradycyjnej sieci web, konieczne zbudowanie cały interfejs użytkownika z każdym żądaniem. Obejmuje to często, dzięki czemu wiele z tego samego zapytania do bazy danych wielokrotnie z jednego użytkownika żądania do następnej. W większości przypadków te dane zmienia się rzadko, więc ma nieco powód, aby stale żądania z bazy danych. ASP.NET Core obsługuje buforowanie odpowiedzi do buforowania całe strony i buforowanie danych, który obsługuje bardziej szczegółowego zachowanie buforowania.

Podczas implementowania pamięci podręcznej, należy mieć na uwadze separacji zagadnień. Należy unikać implementacji logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika. Należy hermetyzować buforowania w jego własnej klasy i zarządzać jego zachowanie przy użyciu konfiguracji. Następuje otwarty/zamknięty i zasady pojedynczej odpowiedzialności i ułatwi zarządzanie, jak używać buforowania w aplikacji w miarę jej rozwoju.

### <a name="aspnet-core-response-caching"></a>Buforowanie odpowiedzi platformy ASP.NET Core

Platforma ASP.NET Core obsługuje dwa poziomy buforowanie odpowiedzi. Pierwszy poziom nie będzie buforować niczego na serwerze, ale dodaje nagłówki HTTP, które poinstruowanie klientów i serwerów proxy buforowanie odpowiedzi. Ten sposób jest implementowany przez dodanie atrybutu ResponseCache do poszczególnych kontrolerów i akcji:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

Poprzedni przykład, wynikiem będzie następujący nagłówek, które są dodawane do odpowiedzi poinstruowanie klientom Zbuforuj wynik do 60 sekund.

Cache-Control: public,max-age=60

Aby można było dodać buforowanie w pamięci po stronie serwera aplikacji, musi odwoływać się do pakietu Microsoft.AspNetCore.ResponseCaching NuGet, a następnie dodaj oprogramowanie pośredniczące buforowania odpowiedzi. To oprogramowanie pośredniczące jest skonfigurowany zarówno w ConfigureServices i Konfiguruj przy uruchamianiu:

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

Oprogramowanie pośredniczące buforowania odpowiedzi automatycznie będzie buforować odpowiedzi na podstawie zestawu warunków, które można dostosować. Domyślnie tylko 200 (OK) odpowiedzi na żądanie za pomocą metod GET lub główny są buforowane. Ponadto żądania muszą mieć odpowiedź z Cache-Control: nagłówek publicznych i nie może zawierać nagłówki autoryzacji lub Set-Cookie. Zobacz [pełną listę warunków pamięci podręcznej używane przez odpowiedzi, oprogramowanie pośredniczące buforowania](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Buforowanie danych

Zamiast (lub oprócz) buforowanie odpowiedzi z pełnej sieci web, można buforować wyniki zapytań danych. W tym celu można użyć w pamięć podręczna na serwerze sieci web, lub [rozproszonej pamięci podręcznej](/aspnet/core/performance/caching/distributed). W tej sekcji pokażemy, jak wdrożyć w pamięci podręcznej pamięci.

Dodano obsługę pamięci (lub rozproszonej) buforowania ConfigureServices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Pamiętaj dodać pakiet Microsoft.Extensions.Caching.Memory NuGet także.

Po dodaniu usługi wszędzie tam, gdzie chcesz uzyskać dostęp do pamięci podręcznej możesz poprosić IMemoryCache za pomocą iniekcji zależności. W tym przykładzie CachedCatalogService jest przy użyciu wzorca projektowego serwera Proxy (lub elementu Decorator), zapewniając alternatywnej implementacji ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie, aby) podstawowej implementacji CatalogService.

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

Aby skonfigurować aplikację do używania pamięci podręcznej wersji usługi, ale nadal umożliwić usłudze wystąpienia CatalogService potrzebuje w jego konstruktorze, należy dodać następujące w ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Dzięki temu w miejscu wywołania bazy danych, które można pobrać danych katalogu zostanie zastosowane tylko raz na minutę, a nie na każde żądanie. W zależności od ruchu sieciowego do lokacji może to mieć bardzo istotne znaczenie liczby zapytań do bazy danych i czas ładowania strony dla strony głównej, który obecnie zależy od wszystkich trzech zapytania udostępniane przez tę usługę.

Jest problem, który pojawia się, gdy buforowanie jest zaimplementowana _starych danych_ — oznacza to, że dane, które uległy zmianie w źródle, ale jest nieaktualna wersja pozostaje w pamięci podręcznej. Jest to prosty sposób rozwiązać ten problem do użycia małych czas trwania pamięci podręcznej, ponieważ zajęty aplikacji jest ograniczona dodatkową korzyścią rozszerzanie długości, które dane są buforowane. Rozważmy na przykład strona, która wykonuje zapytanie pojedynczej bazy danych, a żądania 10 razy na sekundę. Jeśli ta strona jest buforowana na jedną minutę, spowoduje wiele zapytań do bazy danych wprowadzone na minutę do usunięcia z 600 1, redukcji 99,8%. Jeśli zamiast tego czasu trwania pamięci podręcznej wprowadzono jedną godzinę, ogólne zmniejszenie będzie 99.997%, ale teraz prawdopodobieństwo i potencjalnego wiek starych danych są zarówno została znacznie zwiększona.

Innym rozwiązaniem jest aktywnie usunąć wpisy w pamięci podręcznej podczas aktualizacji danych, które zawierają. Może zostać usunięty wszelkie pojedynczy wpis, jeśli znane jest jego klucza:

```csharp
_cache.Remove(cacheKey);
```

Jeśli aplikacja ujawnia funkcje aktualizowania wpisów, które go zapisuje w pamięci podręcznej, możesz usunąć odpowiednie wpisy w pamięci podręcznej, w kodzie, który wykonuje aktualizacje. Czasami może występować wiele różnych wpisów, które są zależne od określonego zestawu danych. W takiej sytuacji może być przydatne do tworzenia zależności między wpisy w pamięci podręcznej, za pomocą CancellationChangeToken. Za pomocą CancellationChangeToken wiele wpisów pamięci podręcznej można unieważnić jednocześnie, przez token anulowania.

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

Buforowanie może znacznie zwiększyć wydajność stron sieci web, wielokrotnie żądającym takie same wartości z bazy danych. Pamiętaj zmierzyć wydajność dostępu i stronę przed zastosowaniem buforowania danych i są stosowane tylko wtedy buforowania tam, gdzie zobaczysz na potrzeby poprawy jakości obsługi. Buforowanie zużywanie zasobów pamięci serwera sieci web i zwiększa złożoność aplikacji, dlatego ważne jest, aby nie przedwcześnie Optymalizowanie przy użyciu tej metody.

>[!div class="step-by-step"]
>[Poprzednie](develop-asp-net-core-mvc-apps.md)
>[dalej](test-asp-net-core-mvc-apps.md)
