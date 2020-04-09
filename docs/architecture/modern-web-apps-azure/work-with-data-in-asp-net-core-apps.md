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
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="8e233-103">Praca z danymi w ASP.NET podstawowych aplikacjach</span><span class="sxs-lookup"><span data-stu-id="8e233-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="8e233-104">"Dane są cenną rzeczą i będą trwać dłużej niż same systemy."</span><span class="sxs-lookup"><span data-stu-id="8e233-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="8e233-105">Tim Berners</span><span class="sxs-lookup"><span data-stu-id="8e233-105">Tim Berners-Lee</span></span>

<span data-ttu-id="8e233-106">Dostęp do danych jest ważną częścią niemal każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e233-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="8e233-107">ASP.NET Core obsługuje wiele opcji dostępu do danych, w tym Entity Framework Core (i Entity Framework 6, jak również) i może pracować z dowolnej platformy dostępu do danych .NET.</span><span class="sxs-lookup"><span data-stu-id="8e233-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="8e233-108">Wybór struktury dostępu do danych do użycia zależy od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e233-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="8e233-109">Abstrakcja tych wyborów z ApplicationCore i projektów interfejsu użytkownika i hermetyzacji szczegóły implementacji w infrastrukturze, pomaga produkować luźno sprzężone, testowalne oprogramowanie.</span><span class="sxs-lookup"><span data-stu-id="8e233-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="8e233-110">Entity Framework Core (dla relacyjnych baz danych)</span><span class="sxs-lookup"><span data-stu-id="8e233-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="8e233-111">Jeśli piszesz nową aplikację ASP.NET Core, która musi pracować z danymi relacyjnymi, a następnie Entity Framework Core (EF Core) jest zalecanym sposobem dla aplikacji, aby uzyskać dostęp do swoich danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="8e233-112">EF Core jest maperem obiekto-relacyjne (O/RM), który umożliwia deweloperom platformy .NET utrwalanie obiektów do i ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="8e233-113">Eliminuje to potrzebę większości deweloperów kodu dostępu do danych zazwyczaj trzeba napisać.</span><span class="sxs-lookup"><span data-stu-id="8e233-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="8e233-114">Podobnie jak ASP.NET Core, EF Core został przepisany od podstaw do obsługi modułowych aplikacji wieloplatformowych.</span><span class="sxs-lookup"><span data-stu-id="8e233-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="8e233-115">Dodać go do aplikacji jako pakiet NuGet, skonfigurować go w starcie i zażądać go za pomocą iniekcji zależności, gdziekolwiek jest to potrzebne.</span><span class="sxs-lookup"><span data-stu-id="8e233-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="8e233-116">Aby użyć ef core z bazą danych programu SQL Server, uruchom następujące polecenie dotnet CLI:</span><span class="sxs-lookup"><span data-stu-id="8e233-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="8e233-117">Aby dodać obsługę źródła danych InMemory do testowania:</span><span class="sxs-lookup"><span data-stu-id="8e233-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="8e233-118">Kontekst DbContext</span><span class="sxs-lookup"><span data-stu-id="8e233-118">The DbContext</span></span>

<span data-ttu-id="8e233-119">Do pracy z EF Core potrzebna <xref:Microsoft.EntityFrameworkCore.DbContext>jest podklasa .</span><span class="sxs-lookup"><span data-stu-id="8e233-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="8e233-120">Ta klasa zawiera właściwości reprezentujące kolekcje jednostek, z którymi aplikacja będzie współpracować.</span><span class="sxs-lookup"><span data-stu-id="8e233-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="8e233-121">Przykład eShopOnWeb zawiera CatalogContext z kolekcjami dla towarów, marek i typów:</span><span class="sxs-lookup"><span data-stu-id="8e233-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="8e233-122">Twój DbContext musi mieć konstruktora, który akceptuje DbContextOptions i przekazać ten argument do konstruktora dbcontext bazy.</span><span class="sxs-lookup"><span data-stu-id="8e233-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="8e233-123">Jeśli masz tylko jeden DbContext w aplikacji, można przekazać wystąpienie DbContextOptions, ale jeśli masz więcej niż jeden,\<należy użyć ogólnego DbContextOptions T> typu, przekazując w DbContext typu jako parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="8e233-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="8e233-124">Konfigurowanie ef core</span><span class="sxs-lookup"><span data-stu-id="8e233-124">Configuring EF Core</span></span>

<span data-ttu-id="8e233-125">W aplikacji ASP.NET Core zazwyczaj skonfigurujesz EF Core w metodzie ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="8e233-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="8e233-126">EF Core używa DbContextOptionsBuilder, który obsługuje kilka metod rozszerzenia pomocne, aby usprawnić jego konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8e233-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="8e233-127">Aby skonfigurować CatalogContext do używania bazy danych programu SQL Server z ciągiem połączenia zdefiniowanym w programie Configuration, należy dodać następujący kod do configureservices:</span><span class="sxs-lookup"><span data-stu-id="8e233-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="8e233-128">Aby użyć bazy danych w pamięci:</span><span class="sxs-lookup"><span data-stu-id="8e233-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="8e233-129">Po zainstalowaniu EF Core, utworzeniu typu podrzędnego DbContext i skonfigurowaniu go w ConfigureServices, można przystąpić do użycia EF Core.</span><span class="sxs-lookup"><span data-stu-id="8e233-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="8e233-130">Można zażądać wystąpienia typu DbContext w dowolnej usłudze, która jej potrzebuje, i rozpocząć pracę z utrwalonych jednostek przy użyciu LINQ tak, jakby były one po prostu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8e233-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="8e233-131">EF Core wykonuje pracę tłumaczenia wyrażeń LINQ do zapytań SQL do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="8e233-132">Można zobaczyć kwerendy EF Core jest wykonywany przez skonfigurowanie rejestratora i zapewnienie jego poziom jest ustawiony na co najmniej informacje, jak pokazano na rysunku 8-1.</span><span class="sxs-lookup"><span data-stu-id="8e233-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![Rejestrowanie zapytań EF Core do konsoli](./media/image8-1.png)

<span data-ttu-id="8e233-134">**Rysunek 8-1**.</span><span class="sxs-lookup"><span data-stu-id="8e233-134">**Figure 8-1**.</span></span> <span data-ttu-id="8e233-135">Rejestrowanie zapytań EF Core do konsoli</span><span class="sxs-lookup"><span data-stu-id="8e233-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="8e233-136">Pobieranie i przechowywanie danych</span><span class="sxs-lookup"><span data-stu-id="8e233-136">Fetching and storing Data</span></span>

<span data-ttu-id="8e233-137">Aby pobrać dane z EF Core, można uzyskać dostęp do odpowiedniej właściwości i użyć LINQ do filtrowania wyniku.</span><span class="sxs-lookup"><span data-stu-id="8e233-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="8e233-138">Można również użyć LINQ do wykonywania projekcji, przekształcając wynik z jednego typu do innego.</span><span class="sxs-lookup"><span data-stu-id="8e233-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="8e233-139">Poniższy przykład można pobrać CatalogBrands, uporządkowane według nazwy, filtrowane przez ich Enabled właściwości i rzutowane na SelectListItem typu:</span><span class="sxs-lookup"><span data-stu-id="8e233-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="8e233-140">W powyższym przykładzie należy dodać wywołanie do ToListAsync w celu natychmiastowego wykonania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="8e233-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="8e233-141">W przeciwnym razie instrukcja przypisze\<IQueryable SelectListItem> do brandItems, które nie zostaną wykonane, dopóki nie zostanie wyliczony.</span><span class="sxs-lookup"><span data-stu-id="8e233-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="8e233-142">Istnieją plusy i minusy do powrotu IQueryable wyniki z metod.</span><span class="sxs-lookup"><span data-stu-id="8e233-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="8e233-143">Umożliwia kwerendy EF Core będzie konstruować do dalszej modyfikacji, ale może również spowodować błędy, które występują tylko w czasie wykonywania, jeśli operacje są dodawane do kwerendy, że EF Core nie może przetłumaczyć.</span><span class="sxs-lookup"><span data-stu-id="8e233-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="8e233-144">Ogólnie bezpieczniejsze jest przekazywanie filtrów do metody wykonywania dostępu do danych i powrót kolekcji\<w pamięci (na przykład lista T>) w wyniku.</span><span class="sxs-lookup"><span data-stu-id="8e233-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="8e233-145">EF Core śledzi zmiany na jednostkach pobiera z trwałości.</span><span class="sxs-lookup"><span data-stu-id="8e233-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="8e233-146">Aby zapisać zmiany w śledzone jednostki, wystarczy wywołać SaveChanges metody na DbContext, upewniając się, że jest to samo wystąpienie DbContext, który został użyty do pobrania jednostki.</span><span class="sxs-lookup"><span data-stu-id="8e233-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="8e233-147">Dodawanie i usuwanie jednostek odbywa się bezpośrednio na odpowiedniej właściwości DbSet, ponownie z wywołaniem SaveChanges do wykonania poleceń bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="8e233-148">W poniższym przykładzie pokazano dodawanie, aktualizowanie i usuwanie jednostek z trwałości.</span><span class="sxs-lookup"><span data-stu-id="8e233-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="8e233-149">EF Core obsługuje zarówno synchroniczne i asynchroniczne metody pobierania i zapisywania.</span><span class="sxs-lookup"><span data-stu-id="8e233-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="8e233-150">W aplikacjach sieci web zaleca się użycie wzorca asynchronii/await z metodami asynchronizującymi, aby wątki serwera sieci web nie były blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="8e233-151">Pobieranie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="8e233-151">Fetching related data</span></span>

<span data-ttu-id="8e233-152">Gdy EF Core pobiera jednostki, wypełnia wszystkie właściwości, które są przechowywane bezpośrednio z tej jednostki w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="8e233-153">Właściwości nawigacji, takie jak listy powiązanych jednostek, nie są wypełniane i mogą mieć ich wartość ustawioną na wartość null.</span><span class="sxs-lookup"><span data-stu-id="8e233-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="8e233-154">Gwarantuje to, że EF Core nie pobiera więcej danych niż jest to potrzebne, co jest szczególnie ważne dla aplikacji sieci web, które muszą szybko przetwarzać żądania i zwracać odpowiedzi w skuteczny sposób.</span><span class="sxs-lookup"><span data-stu-id="8e233-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="8e233-155">Aby uwzględnić relacje z encją przy użyciu _ładowania z użyciem opcji ,należy_określić właściwość przy użyciu metody Dołączania rozszerzenia w kwerendzie, jak pokazano na rysunku:</span><span class="sxs-lookup"><span data-stu-id="8e233-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="8e233-156">Można dołączyć wiele relacji, a także podzespołowania za pomocą ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="8e233-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="8e233-157">EF Core wykona pojedynczą kwerendę, aby pobrać wynikowy zestaw jednostek.</span><span class="sxs-lookup"><span data-stu-id="8e233-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="8e233-158">Alternatywnie można uwzględnić właściwości nawigacji właściwości nawigacji, przekazując '.' -oddzielony ciąg `.Include()` do metody rozszerzenia, jak tak:</span><span class="sxs-lookup"><span data-stu-id="8e233-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="8e233-159">Oprócz hermetyzacji logiki filtrowania, specyfikacja można określić kształt danych, które mają być zwracane, w tym właściwości, które mają być wypełniane.</span><span class="sxs-lookup"><span data-stu-id="8e233-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="8e233-160">Przykład eShopOnWeb zawiera kilka specyfikacji, które pokazują hermetyzację chętnych ładowania informacji w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="8e233-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="8e233-161">Możesz zobaczyć, jak specyfikacja jest używana jako część kwerendy tutaj:</span><span class="sxs-lookup"><span data-stu-id="8e233-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="8e233-162">Inną opcją ładowania powiązanych danych jest użycie _jawnego ładowania_.</span><span class="sxs-lookup"><span data-stu-id="8e233-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="8e233-163">Jawne ładowanie umożliwia załadowanie dodatkowych danych do jednostki, która została już pobrana.</span><span class="sxs-lookup"><span data-stu-id="8e233-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="8e233-164">Ponieważ wiąże się to z osobnym żądaniem do bazy danych, nie jest zalecane dla aplikacji sieci web, co powinno zminimalizować liczbę rund bazy danych wykonanych na żądanie.</span><span class="sxs-lookup"><span data-stu-id="8e233-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="8e233-165">_Ładowanie z opóźnieniem_ jest funkcją, która automatycznie ładuje powiązane dane, do których odwołuje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8e233-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="8e233-166">EF Core dodał wsparcie dla powolnego ładowania w wersji 2.1.</span><span class="sxs-lookup"><span data-stu-id="8e233-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="8e233-167">Ładowanie z opóźnieniem nie jest domyślnie `Microsoft.EntityFrameworkCore.Proxies`włączone i wymaga zainstalowania pliku .</span><span class="sxs-lookup"><span data-stu-id="8e233-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="8e233-168">Podobnie jak w przypadku jawnego ładowania, ładowanie z opóźnieniem powinno być zazwyczaj wyłączone dla aplikacji sieci web, ponieważ jego użycie spowoduje dodatkowe zapytania bazy danych są dokonywane w ramach każdego żądania sieci web.</span><span class="sxs-lookup"><span data-stu-id="8e233-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="8e233-169">Niestety obciążenie poniesione przez opóźnienie ładowania często pozostaje niezauważone w czasie programowania, gdy opóźnienie jest małe i często zestawy danych używane do testowania są małe.</span><span class="sxs-lookup"><span data-stu-id="8e233-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="8e233-170">Jednak w produkcji, z większą liczą użytkowników, więcej danych i więcej opóźnień, dodatkowe żądania bazy danych często może spowodować niską wydajność dla aplikacji sieci web, które intensywnie używać ładowania z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="8e233-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="8e233-171">Unikaj jednostek ładowania z opóźnieniem w aplikacjach sieci Web</span><span class="sxs-lookup"><span data-stu-id="8e233-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="8e233-172">Hermetyzacja danych</span><span class="sxs-lookup"><span data-stu-id="8e233-172">Encapsulating data</span></span>

<span data-ttu-id="8e233-173">EF Core obsługuje kilka funkcji, które umożliwiają modelu poprawnie hermetyzować jego stan.</span><span class="sxs-lookup"><span data-stu-id="8e233-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="8e233-174">Typowym problemem w modelach domeny jest to, że uwidaczniają właściwości nawigacji kolekcji jako publicznie dostępne typy list.</span><span class="sxs-lookup"><span data-stu-id="8e233-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="8e233-175">Dzięki temu każdy współpracownik manipulować zawartością tych typów kolekcji, które mogą pominąć ważne reguły biznesowe związane z kolekcji, ewentualnie pozostawiając obiekt w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="8e233-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="8e233-176">Rozwiązaniem tego problemu jest udostępnić dostęp tylko do odczytu do powiązanych kolekcji i jawnie zapewnić metody definiujące sposoby, w których klienci mogą manipulować nimi, jak w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8e233-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

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

<span data-ttu-id="8e233-177">Ten typ jednostki nie `List` udostępnia `ICollection` publicznej lub właściwości, `IReadOnlyCollection` ale zamiast tego udostępnia typ, który otacza podstawowy typ listy.</span><span class="sxs-lookup"><span data-stu-id="8e233-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="8e233-178">Korzystając z tego wzorca, można wskazać entity framework core, aby użyć pola zapasowego w taki sposób:</span><span class="sxs-lookup"><span data-stu-id="8e233-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="8e233-179">Innym sposobem, w którym można poprawić model domeny jest za pomocą obiektów wartości dla typów, które nie mają tożsamości i są wyróżniane tylko przez ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="8e233-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="8e233-180">Za pomocą takich typów, jak właściwości jednostek może pomóc zachować logiki specyficzne dla obiektu wartości, gdzie należy i można uniknąć zduplikowanej logiki między wieloma jednostkami, które używają tej samej koncepcji.</span><span class="sxs-lookup"><span data-stu-id="8e233-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="8e233-181">W entity framework core można utrwalać obiekty wartości w tej samej tabeli co ich jednostki będące właścicielem, konfigurując typ jako jednostkę należącą do sieci, tak jak:</span><span class="sxs-lookup"><span data-stu-id="8e233-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="8e233-182">W tym przykładzie `ShipToAddress` właściwość `Address`jest typu .</span><span class="sxs-lookup"><span data-stu-id="8e233-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="8e233-183">`Address`jest obiektem wartości o kilku `Street` `City`właściwościach, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="8e233-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="8e233-184">EF Core `Order` mapuje obiekt do swojej `Address` tabeli z jedną kolumną na właściwość, prefiksując każdą nazwę kolumny o nazwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="8e233-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="8e233-185">W tym przykładzie tabela `Order` będzie `ShipToAddress_Street` zawierać `ShipToAddress_City`kolumny, takie jak i .</span><span class="sxs-lookup"><span data-stu-id="8e233-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="8e233-186">W razie potrzeby można również przechowywać posiadane typy w oddzielnych tabelach.</span><span class="sxs-lookup"><span data-stu-id="8e233-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="8e233-187">Dowiedz się więcej o [pomocy technicznej jednostki należącej do firmy w ef core](/ef/core/modeling/owned-entities).</span><span class="sxs-lookup"><span data-stu-id="8e233-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="8e233-188">Elastyczne połączenia</span><span class="sxs-lookup"><span data-stu-id="8e233-188">Resilient connections</span></span>

<span data-ttu-id="8e233-189">Zasoby zewnętrzne, takie jak bazy danych SQL, mogą czasami być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8e233-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="8e233-190">W przypadku tymczasowej niedostępności aplikacje mogą używać logiki ponawiania, aby uniknąć wywoływania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8e233-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="8e233-191">Technika ta jest powszechnie określana jako _odporność połączenia_.</span><span class="sxs-lookup"><span data-stu-id="8e233-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="8e233-192">Można zaimplementować [własne próby ponawiania z wykładniczej](https://docs.microsoft.com/azure/architecture/patterns/retry) techniki wycofywania, próbując ponowić próbę z wykładniczo zwiększając czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="8e233-192">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="8e233-193">Ta technika obejmuje fakt, że zasoby w chmurze mogą sporadycznie być niedostępne przez krótki okres czasu, co powoduje niepowodzenie niektórych żądań.</span><span class="sxs-lookup"><span data-stu-id="8e233-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="8e233-194">W przypadku usługi Azure SQL DB entity framework core już zapewnia odporność połączenia wewnętrznej bazy danych i logiki ponawiania próby.</span><span class="sxs-lookup"><span data-stu-id="8e233-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="8e233-195">Ale należy włączyć strategię wykonywania entity framework dla każdego połączenia DbContext, jeśli chcesz mieć odporne połączenia EF Core.</span><span class="sxs-lookup"><span data-stu-id="8e233-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="8e233-196">Na przykład następujący kod na poziomie połączenia EF Core umożliwia odporne połączenia SQL, które są ponowione, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="8e233-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="8e233-197">Strategie wykonywania i jawne transakcje przy użyciu BeginTransaction i wielu DbContexts</span><span class="sxs-lookup"><span data-stu-id="8e233-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="8e233-198">Gdy próby są włączone w połączeniach EF Core, każda operacja, którą wykonujesz przy użyciu EF Core staje się własną operacją ponawianą.</span><span class="sxs-lookup"><span data-stu-id="8e233-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="8e233-199">Każde zapytanie i każde wywołanie SaveChanges zostaną ponowione jako jednostka, jeśli wystąpi błąd przejściowy.</span><span class="sxs-lookup"><span data-stu-id="8e233-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="8e233-200">Jednak jeśli kod inicjuje transakcję przy użyciu BeginTransaction, definiujesz własną grupę operacji, które muszą być traktowane jako jednostka; wszystko wewnątrz transakcji musi zostać wycofane, jeśli wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="8e233-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="8e233-201">Zostanie wyświetlony wyjątek, jak następujące, jeśli spróbujesz wykonać tę transakcję podczas korzystania ze strategii wykonywania EF (zasady ponawiania próby) i dołączyć kilka SaveChanges z wielu DbContexts w nim.</span><span class="sxs-lookup"><span data-stu-id="8e233-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="8e233-202">System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8e233-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="8e233-203">Użyj strategii wykonywania zwróconej przez "DbContext.Database.CreateExecutionStrategy()", aby wykonać wszystkie operacje w transakcji jako jednostkę ponawianą próbę.</span><span class="sxs-lookup"><span data-stu-id="8e233-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="8e233-204">Rozwiązaniem jest ręczne wywołanie strategii wykonywania EF z delegata reprezentującego wszystko, co musi zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="8e233-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="8e233-205">Jeśli wystąpi błąd przejściowy, strategia wykonywania ponownie wywoła delegata.</span><span class="sxs-lookup"><span data-stu-id="8e233-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="8e233-206">Poniższy kod pokazuje, jak zaimplementować to podejście:</span><span class="sxs-lookup"><span data-stu-id="8e233-206">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="8e233-207">Pierwszy DbContext jest \_catalogContext i drugi DbContext \_znajduje się w integrationEventLogService obiektu.</span><span class="sxs-lookup"><span data-stu-id="8e233-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="8e233-208">Na koniec commit akcji zostanie wykonana wiele DbContexts i przy użyciu strategii realizacji EF.</span><span class="sxs-lookup"><span data-stu-id="8e233-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="8e233-209">Referencje — core struktury jednostki</span><span class="sxs-lookup"><span data-stu-id="8e233-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="8e233-210">**Ef Core Dokumenty**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="8e233-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="8e233-211">**Ef Core: Powiązane dane**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="8e233-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="8e233-212">**Unikaj jednostek ładowania z opóźnieniem w aplikacjach ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="8e233-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="8e233-213">EF Core lub mikro-ORM?</span><span class="sxs-lookup"><span data-stu-id="8e233-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="8e233-214">Ef Core jest doskonałym wyborem do zarządzania trwałością i w przeważającej części hermetyzuje szczegóły bazy danych od deweloperów aplikacji, nie jest to jedyny wybór.</span><span class="sxs-lookup"><span data-stu-id="8e233-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="8e233-215">Inną popularną alternatywą open-source jest [Dapper](https://github.com/StackExchange/Dapper), tzw micro-ORM.</span><span class="sxs-lookup"><span data-stu-id="8e233-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="8e233-216">Micro-ORM to lekkie, mniej w pełni funkcjonalne narzędzie do mapowania obiektów do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="8e233-217">W przypadku Dapper jego cele projektowe koncentrują się na wydajności, a nie w pełni hermetyzując podstawowe zapytania, których używa do pobierania i aktualizowania danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="8e233-218">Ponieważ nie jest abstrakcyjny SQL od dewelopera, Dapper jest "bliżej metalu" i pozwala deweloperom napisać dokładne zapytania, które mają być używane dla danej operacji dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="8e233-219">EF Core ma dwie istotne funkcje, które zapewnia, które oddzielają go od Dapper, ale także dodać do jego wydajności narzutu.</span><span class="sxs-lookup"><span data-stu-id="8e233-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="8e233-220">Pierwszym z nich jest tłumaczenie z wyrażeń LINQ do SQL.</span><span class="sxs-lookup"><span data-stu-id="8e233-220">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="8e233-221">Te tłumaczenia są buforowane, ale mimo to istnieje obciążenie w wykonywaniu ich po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8e233-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="8e233-222">Drugim jest śledzenie zmian w jednostkach (tak, aby można było wygenerować efektywne instrukcje aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="8e233-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="8e233-223">To zachowanie można wyłączyć dla określonych zapytań przy użyciu rozszerzenia AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="8e233-223">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="8e233-224">EF Core generuje również zapytania SQL, które zwykle są bardzo wydajne i w każdym razie całkowicie dopuszczalne z punktu widzenia wydajności, ale jeśli potrzebujesz precyzyjnej kontroli nad dokładną kwerendą do wykonania, można przekazać w niestandardowym języku SQL (lub wykonać procedurę składowaną) przy użyciu EF Core, zbyt.</span><span class="sxs-lookup"><span data-stu-id="8e233-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="8e233-225">W tym przypadku Dapper nadal przewyższa EF Core, ale tylko nieznacznie.</span><span class="sxs-lookup"><span data-stu-id="8e233-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="8e233-226">Julie Lerman przedstawia pewne dane dotyczące wydajności w swoim artykule MSDN z maja 2016 [r. Dapper, Entity Framework i Hybrid Apps](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span><span class="sxs-lookup"><span data-stu-id="8e233-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="8e233-227">Dodatkowe dane porównawcze wydajności dla różnych metod dostępu do danych można znaleźć na [stronie Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="8e233-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="8e233-228">Aby zobaczyć, jak składnia dapper różni się od EF Core, należy wziąć pod uwagę te dwie wersje tej samej metody pobierania listy elementów:</span><span class="sxs-lookup"><span data-stu-id="8e233-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="8e233-229">Jeśli chcesz zbudować bardziej złożone wykresy obiektów z Dapper, należy napisać skojarzone zapytania samodzielnie (w przeciwieństwie do dodawania Include jak w EF Core).</span><span class="sxs-lookup"><span data-stu-id="8e233-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="8e233-230">Jest to obsługiwane przez różne składni, w tym funkcję o nazwie Mapowanie wielokrotne, która umożliwia mapowanie poszczególnych wierszy na wiele mapowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e233-230">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="8e233-231">Na przykład biorąc pod uwagę klasę Post z właściwością Właściciel typu Użytkownik, następujący SQL zwróci wszystkie niezbędne dane:</span><span class="sxs-lookup"><span data-stu-id="8e233-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="8e233-232">Każdy zwrócony wiersz zawiera dane użytkownika i postu.</span><span class="sxs-lookup"><span data-stu-id="8e233-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="8e233-233">Ponieważ dane Użytkownika powinny być dołączone do danych Post za pośrednictwem jego własności Owner, stosuje się następującą funkcję:</span><span class="sxs-lookup"><span data-stu-id="8e233-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="8e233-234">Pełna lista kodów do zwrócenia kolekcji wpisów z ich Owner właściwości wypełnione skojarzonych danych użytkownika będzie:</span><span class="sxs-lookup"><span data-stu-id="8e233-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="8e233-235">Ponieważ oferuje mniej hermetyzacji Dapper wymaga deweloperzy wiedzieć więcej o tym, jak ich dane są przechowywane, jak skutecznie zbadać go i napisać więcej kodu, aby go pobrać.</span><span class="sxs-lookup"><span data-stu-id="8e233-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="8e233-236">Gdy model się zmieni, zamiast po prostu utworzyć nową migrację (inną funkcję EF Core) i/lub zaktualizować informacje mapowania w jednym miejscu w DbContext, każda kwerenda, która ma wpływ, musi zostać zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="8e233-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="8e233-237">Te zapytania nie mają żadnych gwarancji czasu kompilacji, więc mogą one przerwy w czasie wykonywania w odpowiedzi na zmiany w modelu lub bazy danych, co błędy trudniejsze do wykrycia szybko.</span><span class="sxs-lookup"><span data-stu-id="8e233-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="8e233-238">W zamian za te kompromisy, Dapper oferuje niezwykle szybką wydajność.</span><span class="sxs-lookup"><span data-stu-id="8e233-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="8e233-239">W przypadku większości aplikacji i większości części prawie wszystkich aplikacji EF Core oferuje akceptowalną wydajność.</span><span class="sxs-lookup"><span data-stu-id="8e233-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="8e233-240">W związku z tym jego korzyści wydajności dewelopera mogą przeważać nad jego wydajnością.</span><span class="sxs-lookup"><span data-stu-id="8e233-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="8e233-241">W przypadku kwerend, które mogą korzystać z buforowania, rzeczywiste zapytanie może być wykonywane tylko niewielki procent czasu, dzięki czemu stosunkowo małe różnice wydajności kwerendy dyskusyjne.</span><span class="sxs-lookup"><span data-stu-id="8e233-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="8e233-242">SQL lub NoSQL</span><span class="sxs-lookup"><span data-stu-id="8e233-242">SQL or NoSQL</span></span>

<span data-ttu-id="8e233-243">Tradycyjnie relacyjne bazy danych, takie jak SQL Server, zdominowały rynek trwałego przechowywania danych, ale nie są jedynym dostępnym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="8e233-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="8e233-244">Bazy danych NoSQL, takie jak [MongoDB,](https://www.mongodb.com/what-is-mongodb) oferują inne podejście do przechowywania obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e233-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="8e233-245">Zamiast mapowania obiektów do tabel i wierszy, inną opcją jest serializowanie całego wykresu obiektu i przechowywanie wyniku.</span><span class="sxs-lookup"><span data-stu-id="8e233-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="8e233-246">Zalety tego podejścia, przynajmniej początkowo, to prostota i wydajność.</span><span class="sxs-lookup"><span data-stu-id="8e233-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="8e233-247">Łatwiej jest przechowywać pojedynczy serializowany obiekt z kluczem niż rozkładać obiekt na wiele tabel z relacjami i aktualizacjami i wierszami, które mogły ulec zmianie od czasu ostatniego pobrania obiektu z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="8e233-248">Podobnie pobieranie i deserializacja pojedynczego obiektu z magazynu opartego na kluczach jest zazwyczaj znacznie szybsze i łatwiejsze niż sprzężenia złożone lub wiele zapytań bazy danych wymaganych do pełnego skomponowania tego samego obiektu z relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="8e233-249">Brak blokad lub transakcji lub schematu stałego również sprawia, że bazy danych NoSQL podatne na skalowanie na wielu komputerach, obsługujących bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="8e233-250">Z drugiej strony bazy danych NoSQL (jak są one zwykle nazywane) mają swoje wady.</span><span class="sxs-lookup"><span data-stu-id="8e233-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="8e233-251">Relacyjne bazy danych używają normalizacji, aby wymusić spójność i uniknąć powielania danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="8e233-252">Zmniejsza to całkowity rozmiar bazy danych i zapewnia, że aktualizacje udostępnionych danych są dostępne natychmiast w całej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-252">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="8e233-253">W relacyjnej bazie danych tabela adresowa może odwoływać się do tabeli Kraj według identyfikatora, tak aby w przypadku zmiany nazwy kraju/regionu rekordy adresów korzystały z aktualizacji bez konieczności aktualizowania.</span><span class="sxs-lookup"><span data-stu-id="8e233-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="8e233-254">Jednak w bazie danych NoSQL adres i skojarzony z nim kraj mogą być serializowane jako część wielu przechowywanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e233-254">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="8e233-255">Aktualizacja nazwy kraju/regionu wymagałaby aktualizacji wszystkich takich obiektów, a nie pojedynczego wiersza.</span><span class="sxs-lookup"><span data-stu-id="8e233-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="8e233-256">Relacyjne bazy danych mogą również zapewnić integralność relacyjnej, wymuszając reguły, takie jak klucze obce.</span><span class="sxs-lookup"><span data-stu-id="8e233-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="8e233-257">Bazy danych NoSQL zazwyczaj nie oferują takich ograniczeń na ich danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="8e233-258">Inną złożonością, z którą muszą radzić sobie bazy danych NoSQL, jest przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="8e233-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="8e233-259">Po zmianie właściwości obiektu, może nie być w stanie być deserialized z poprzednich wersji, które były przechowywane.</span><span class="sxs-lookup"><span data-stu-id="8e233-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="8e233-260">W związku z tym wszystkie istniejące obiekty, które mają serializowane (poprzednia) wersja obiektu muszą zostać zaktualizowane, aby były zgodne z jego nowym schematem.</span><span class="sxs-lookup"><span data-stu-id="8e233-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="8e233-261">Nie różni się to koncepcyjnie od relacyjnej bazy danych, w której zmiany schematu czasami wymagają skryptów aktualizacji lub aktualizacji mapowania.</span><span class="sxs-lookup"><span data-stu-id="8e233-261">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="8e233-262">Jednak liczba wpisów, które muszą być modyfikowane jest często znacznie większa w podejściu NoSQL, ponieważ istnieje więcej powielania danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="8e233-263">Jest to możliwe w bazach danych NoSQL do przechowywania wielu wersji obiektów, coś stałe schemat relacyjnych baz danych zazwyczaj nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="8e233-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="8e233-264">Jednak w tym przypadku kod aplikacji będzie musiał uwzględnić istnienie poprzednich wersji obiektów, dodając dodatkową złożoność.</span><span class="sxs-lookup"><span data-stu-id="8e233-264">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="8e233-265">Bazy danych NoSQL zazwyczaj nie wymuszają [ACID](https://en.wikipedia.org/wiki/ACID), co oznacza, że mają zarówno wydajność, jak i skalowalność korzyści w stosunku do relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="8e233-266">Doskonale nadają się do bardzo dużych zestawów danych i obiektów, które nie są dobrze przystosowane do przechowywania w znormalizowanych strukturach tabel.</span><span class="sxs-lookup"><span data-stu-id="8e233-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="8e233-267">Nie ma powodu, dla którego pojedyncza aplikacja nie może korzystać z relacyjnych i nosql baz danych, przy użyciu każdego, gdzie jest to najlepiej nadaje.</span><span class="sxs-lookup"><span data-stu-id="8e233-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="8e233-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="8e233-268">Azure Cosmos DB</span></span>

<span data-ttu-id="8e233-269">Usługa Azure Cosmos DB to w pełni zarządzana usługa bazy danych NoSQL, która oferuje magazyn danych bez użycia schematu w chmurze.</span><span class="sxs-lookup"><span data-stu-id="8e233-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="8e233-270">Usługa Azure Cosmos DB została stworzona z myślą o szybkiej i przewidywalnej wydajności, wysokiej dostępności, elastycznym skalowaniu i dystrybucji globalnej.</span><span class="sxs-lookup"><span data-stu-id="8e233-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="8e233-271">Pomimo bazy danych NoSQL, deweloperzy mogą korzystać z bogatych i znanych funkcji zapytań SQL na danych JSON.</span><span class="sxs-lookup"><span data-stu-id="8e233-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="8e233-272">Wszystkie zasoby w usłudze Azure Cosmos DB są przechowywane jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="8e233-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="8e233-273">Zasoby są zarządzane jako _elementy_, które są dokumentami zawierającymi metadane i _źródła danych_, które są kolekcjami elementów.</span><span class="sxs-lookup"><span data-stu-id="8e233-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="8e233-274">Rysunek 8-2 przedstawia relację między różnymi zasobami usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="8e233-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![Hierarchiczna relacja między zasobami w usłudze Azure Cosmos DB, bazie danych JSON NoSQL](./media/image8-2.png)

<span data-ttu-id="8e233-276">**Rysunek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="8e233-276">**Figure 8-2.**</span></span> <span data-ttu-id="8e233-277">Organizacja zasobów usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="8e233-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="8e233-278">Język zapytań usługi Azure Cosmos DB to prosty, ale zaawansowany interfejs do wykonywania zapytań o dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="8e233-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="8e233-279">Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywoływania funkcji języka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8e233-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="8e233-280">**Odwołania — usługa Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="8e233-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="8e233-281">Wprowadzenie do usługi Azure Cosmos DB<https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="8e233-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="8e233-282">Inne opcje trwałości</span><span class="sxs-lookup"><span data-stu-id="8e233-282">Other persistence options</span></span>

<span data-ttu-id="8e233-283">Oprócz relacyjnych i nosql opcje magazynu, ASP.NET aplikacje Core można używać usługi Azure Storage do przechowywania różnych formatów danych i plików w chmurze, skalowalny sposób.</span><span class="sxs-lookup"><span data-stu-id="8e233-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="8e233-284">Usługa Azure Storage jest masowo skalowalna, dzięki czemu można rozpocząć przechowywanie niewielkich ilości danych i skalować do przechowywania setek lub terabajtów, jeśli aplikacja tego wymaga.</span><span class="sxs-lookup"><span data-stu-id="8e233-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="8e233-285">Usługa Azure Storage obsługuje cztery rodzaje danych:</span><span class="sxs-lookup"><span data-stu-id="8e233-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="8e233-286">Magazyn obiektów blob dla nieustrukturyzowanego tekstu lub magazynu binarnego, nazywany również magazynem obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e233-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="8e233-287">Magazyn tabel dla zestawów danych strukturalnych, dostępny za pomocą kluczy wierszy.</span><span class="sxs-lookup"><span data-stu-id="8e233-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="8e233-288">Magazyn kolejek dla niezawodnych wiadomości opartych na kolejkach.</span><span class="sxs-lookup"><span data-stu-id="8e233-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="8e233-289">Magazyn plików dla udostępnionego dostępu do plików między maszynami wirtualnymi platformy Azure i aplikacjami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="8e233-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="8e233-290">**Odwołania — usługa Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="8e233-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="8e233-291">Wprowadzenie do usługi Azure Storage<https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="8e233-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="8e233-292">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="8e233-292">Caching</span></span>

<span data-ttu-id="8e233-293">W aplikacjach sieci web każde żądanie sieci web należy wykonać w jak najkrótszym czasie.</span><span class="sxs-lookup"><span data-stu-id="8e233-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="8e233-294">Jednym ze sposobów osiągnięcia tego celu jest ograniczenie liczby wywołań zewnętrznych, które serwer musi wykonać, aby ukończyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="8e233-294">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="8e233-295">Buforowanie polega na przechowywaniu kopii danych na serwerze (lub innym magazynie danych, który jest łatwiej wyszukiwany niż źródło danych).</span><span class="sxs-lookup"><span data-stu-id="8e233-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="8e233-296">Aplikacje sieci Web, a zwłaszcza nie-SPA tradycyjnych aplikacji sieci web, trzeba zbudować cały interfejs użytkownika przy każdym żądaniu.</span><span class="sxs-lookup"><span data-stu-id="8e233-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="8e233-297">Często wiąże się to z wykonywaniem wielu tych samych zapytań bazy danych wielokrotnie z jednego żądania użytkownika do następnego.</span><span class="sxs-lookup"><span data-stu-id="8e233-297">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="8e233-298">W większości przypadków te dane zmieniają się rzadko, więc nie ma powodu, aby stale żądać go z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="8e233-299">ASP.NET Core obsługuje buforowanie odpowiedzi, buforowanie całych stron i buforowanie danych, które obsługuje bardziej szczegółowe zachowanie buforowania.</span><span class="sxs-lookup"><span data-stu-id="8e233-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="8e233-300">Podczas wdrażania buforowania, ważne jest, aby pamiętać o oddzieleniu problemów.</span><span class="sxs-lookup"><span data-stu-id="8e233-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="8e233-301">Należy unikać implementowania logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8e233-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="8e233-302">Zamiast tego hermetyzować buforowania w własnych klasach i używać konfiguracji do zarządzania jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8e233-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="8e233-303">Jest to zgodne z zasadami Otwarte/Zamknięte i Pojedyncza Odpowiedzialność i ułatwi zarządzanie sposób korzystania z buforowania w aplikacji, jak rośnie.</span><span class="sxs-lookup"><span data-stu-id="8e233-303">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="8e233-304">ASP.NET Buforowanie odpowiedzi podstawowych</span><span class="sxs-lookup"><span data-stu-id="8e233-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="8e233-305">ASP.NET Core obsługuje dwa poziomy buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8e233-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="8e233-306">Pierwszy poziom nie buforuje niczego na serwerze, ale dodaje nagłówki HTTP, które instruują klientów i serwery proxy do buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8e233-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="8e233-307">Jest to implementowane przez dodanie responsecache atrybut do poszczególnych kontrolerów lub akcji:</span><span class="sxs-lookup"><span data-stu-id="8e233-307">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="8e233-308">W poprzednim przykładzie spowoduje, że następujący nagłówek zostanie dodany do odpowiedzi, instruując klientów do buforowania wyniku przez maksymalnie 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="8e233-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="8e233-309">Kontrola pamięci podręcznej: publiczna, max-age=60</span><span class="sxs-lookup"><span data-stu-id="8e233-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="8e233-310">Aby dodać buforowanie po stronie serwera w pamięci do aplikacji, należy odwołać się do pakietu Microsoft.AspNetCore.ResponseCaching NuGet, a następnie dodać oprogramowanie pośredniczące buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8e233-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="8e233-311">To oprogramowanie pośredniczące jest skonfigurowane zarówno w obszarze ConfigureServices, jak i Configure in Startup:</span><span class="sxs-lookup"><span data-stu-id="8e233-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="8e233-312">Oprogramowanie pośredniczące buforowania odpowiedzi automatycznie buforuje odpowiedzi na podstawie zestawu warunków, które można dostosować.</span><span class="sxs-lookup"><span data-stu-id="8e233-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="8e233-313">Domyślnie tylko 200 (OK) odpowiedzi wymagane za pośrednictwem metody GET lub HEAD są buforowane.</span><span class="sxs-lookup"><span data-stu-id="8e233-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="8e233-314">Ponadto żądania muszą mieć odpowiedź z cache-control: nagłówek publiczny i nie może zawierać nagłówków autoryzacji lub set-cookie.</span><span class="sxs-lookup"><span data-stu-id="8e233-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="8e233-315">Zobacz [pełną listę warunków buforowania używanych przez oprogramowanie pośredniczące buforowania odpowiedzi](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="8e233-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="8e233-316">Buforowanie danych</span><span class="sxs-lookup"><span data-stu-id="8e233-316">Data caching</span></span>

<span data-ttu-id="8e233-317">Zamiast (lub dodatkowo) buforowania pełnych odpowiedzi sieci web, można buforować wyniki poszczególnych zapytań danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="8e233-318">W tym celu można użyć w buforowaniu pamięci na serwerze sieci web lub użyć [rozproszonej pamięci podręcznej](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="8e233-318">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="8e233-319">W tej sekcji pokazano, jak zaimplementować w buforowaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="8e233-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="8e233-320">Dodano obsługę buforowania pamięci (lub rozproszonego) w configureservices:</span><span class="sxs-lookup"><span data-stu-id="8e233-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="8e233-321">Należy również dodać pakiet Microsoft.Extensions.Caching.Memory NuGet.</span><span class="sxs-lookup"><span data-stu-id="8e233-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="8e233-322">Po dodaniu usługi, żądanie IMemoryCache za pośrednictwem iniekcji zależności, gdziekolwiek trzeba uzyskać dostęp do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e233-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="8e233-323">W tym przykładzie CachedCatalogService używa wzorca projektu proxy (lub Dekorator), zapewniając alternatywną implementację ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie) podstawowej implementacji CatalogService.</span><span class="sxs-lookup"><span data-stu-id="8e233-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="8e233-324">Aby skonfigurować aplikację do korzystania z buforowanej wersji usługi, ale nadal zezwalaj usłudze na uzyskanie wystąpienia CatalogService, której potrzebuje w konstruktorze, należy dodać następujące w configureservices:</span><span class="sxs-lookup"><span data-stu-id="8e233-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="8e233-325">Z tym w miejscu bazy danych wywołuje pobieranie danych katalogu będą dokonywane tylko raz na minutę, a nie na każde żądanie.</span><span class="sxs-lookup"><span data-stu-id="8e233-325">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="8e233-326">W zależności od ruchu do witryny może to mieć znaczący wpływ na liczbę zapytań do bazy danych i średni czas ładowania strony dla strony głównej, która obecnie zależy od wszystkich trzech zapytań udostępniane przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8e233-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="8e233-327">Problem, który pojawia się podczas buforowania jest zaimplementowane jest _przestarzałe dane_ — oznacza to, że dane, które uległy zmianie u źródła, ale wersja nieaktualna pozostaje w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e233-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="8e233-328">Prostym sposobem złagodzenia tego problemu jest użycie małych czasów trwania pamięci podręcznej, ponieważ dla zajętej aplikacji istnieje ograniczona dodatkowa korzyść dla rozszerzenia długości danych jest buforowana.</span><span class="sxs-lookup"><span data-stu-id="8e233-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="8e233-329">Rozważmy na przykład stronę, która tworzy kwerendę pojedynczej bazy danych i jest wymagana 10 razy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="8e233-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="8e233-330">Jeśli ta strona jest buforowana przez jedną minutę, spowoduje to spadek liczby zapytań bazy danych wykonanych na minutę z 600 do 1, co oznacza zmniejszenie o 99,8%.</span><span class="sxs-lookup"><span data-stu-id="8e233-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="8e233-331">Jeśli zamiast tego czas trwania pamięci podręcznej zostały wykonane jedną godzinę, ogólne zmniejszenie będzie 99.997%, ale teraz prawdopodobieństwo i potencjalny wiek starych danych są zarówno znacznie wzrosła.</span><span class="sxs-lookup"><span data-stu-id="8e233-331">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="8e233-332">Innym podejściem jest proaktywne usuwanie wpisów pamięci podręcznej, gdy dane, które zawierają są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="8e233-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="8e233-333">Każdy pojedynczy wpis można usunąć, jeśli jego klucz jest znany:</span><span class="sxs-lookup"><span data-stu-id="8e233-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="8e233-334">Jeśli aplikacja udostępnia funkcje aktualizowania wpisów, które buforuje, można usunąć odpowiednie wpisy pamięci podręcznej w kodzie, który wykonuje aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="8e233-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="8e233-335">Czasami może istnieć wiele różnych wpisów, które zależą od określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="8e233-336">W takim przypadku może być przydatne do tworzenia zależności między wpisami pamięci podręcznej, przy użyciu CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="8e233-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="8e233-337">Z CancellationChangeToken, można wygasnąć wiele wpisów pamięci podręcznej na raz, anulując token.</span><span class="sxs-lookup"><span data-stu-id="8e233-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

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

<span data-ttu-id="8e233-338">Buforowanie może znacznie poprawić wydajność stron sieci web, które wielokrotnie żądają tych samych wartości z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8e233-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="8e233-339">Przed zastosowaniem buforowania należy zmierzyć dostęp do danych i wydajność strony, a także zastosować buforowanie tylko wtedy, gdy istnieje potrzeba poprawy.</span><span class="sxs-lookup"><span data-stu-id="8e233-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="8e233-340">Buforowanie zużywa zasoby pamięci serwera sieci web i zwiększa złożoność aplikacji, dlatego ważne jest, aby nie przedwcześnie optymalizować przy użyciu tej techniki.</span><span class="sxs-lookup"><span data-stu-id="8e233-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8e233-341">[Poprzedni](develop-asp-net-core-mvc-apps.md)
>[następny](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="8e233-341">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
