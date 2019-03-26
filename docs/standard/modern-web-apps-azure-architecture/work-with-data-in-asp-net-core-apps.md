---
title: Praca z danymi w aplikacji ASP.NET Core
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Praca z danymi w aplikacji platformy ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 23c0995c512a07c41b3e2dbe8bc7528723379efa
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463738"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="8693f-103">Praca z danymi w aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8693f-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="8693f-104">"Dane cennego rzecz i będzie wystarczą na dłużej, niż samych systemów."</span><span class="sxs-lookup"><span data-stu-id="8693f-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="8693f-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="8693f-105">Tim Berners-Lee</span></span>

<span data-ttu-id="8693f-106">Dostęp do danych jest ważnym elementem niemal wszystkich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8693f-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="8693f-107">Platforma ASP.NET Core obsługuje szereg opcji dostępu do danych, w tym platformy Entity Framework Core (i platformy Entity Framework 6 także) i można pracować z dowolnego środowiska .NET framework dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="8693f-108">Wybór, z których dostępu do danych platformę, by używać zależy od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8693f-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="8693f-109">Abstrakcyjność te opcje w projektach ApplicationCore i interfejs użytkownika i enkapsulacji szczegółów implementacji w infrastrukturze, pomaga tworzyć oprogramowanie luźno powiązanych, sprawdzalnego działa zgodnie.</span><span class="sxs-lookup"><span data-stu-id="8693f-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="8693f-110">Entity Framework Core (dla relacyjnych baz danych)</span><span class="sxs-lookup"><span data-stu-id="8693f-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="8693f-111">Jeśli piszesz nowej aplikacji platformy ASP.NET Core, który wymaga do pracy z danymi relacyjnymi, platformy Entity Framework Core (EF Core) jest zalecany sposób dostępu do danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8693f-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="8693f-112">EF Core to maper obiektowo relacyjny (O/RM), który umożliwia deweloperom platformy .NET do utrwalania obiektów do i ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="8693f-113">Eliminuje to potrzebę do większości kod dostępu do danych, których deweloperzy zazwyczaj konieczne zapisu.</span><span class="sxs-lookup"><span data-stu-id="8693f-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="8693f-114">Np. ASP.NET Core programu EF Core ma został przepisany od podstaw w celu obsługi modułowej aplikacje dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="8693f-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="8693f-115">Dodaj go do aplikacji jako pakiet NuGet, skonfiguruj go na uruchamianie i żądania za pomocą iniekcji zależności, wszędzie tam, gdzie ich potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="8693f-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="8693f-116">Aby użyć programu EF Core z bazą danych programu SQL Server, uruchom następujące polecenie interfejsu wiersza polecenia platformy dotnet:</span><span class="sxs-lookup"><span data-stu-id="8693f-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="8693f-117">polecenia DotNet Dodaj pakiet Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="8693f-117">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="8693f-118">Aby dodać obsługę dla źródła danych InMemory do testowania:</span><span class="sxs-lookup"><span data-stu-id="8693f-118">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="8693f-119">polecenia DotNet Dodaj pakiet Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="8693f-119">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="8693f-120">Kontekstu DbContext</span><span class="sxs-lookup"><span data-stu-id="8693f-120">The DbContext</span></span>

<span data-ttu-id="8693f-121">Aby pracować z programem EF Core, potrzebujesz podklasą <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="8693f-121">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="8693f-122">Ta klasa posiada właściwości reprezentujące kolekcji obiektów, których Twoja aplikacja będzie działać z.</span><span class="sxs-lookup"><span data-stu-id="8693f-122">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="8693f-123">Przykład eShopOnWeb obejmuje CatalogContext przy użyciu kolekcji elementów, marek i typy:</span><span class="sxs-lookup"><span data-stu-id="8693f-123">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="8693f-124">Twoje DbContext posiadanie Konstruktor, który akceptuje DbContextOptions oraz przekazania tego argumentu do konstruktora bazowego typu DbContext.</span><span class="sxs-lookup"><span data-stu-id="8693f-124">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="8693f-125">Należy pamiętać, że jeśli masz tylko jeden kontekst DbContext w aplikacji, można przekazać wystąpienia DbContextOptions, ale jeśli masz więcej niż jeden należy użyć ogólnego DbContextOptions\<T > typu, przekazując jako parametr ogólny typu DbContext.</span><span class="sxs-lookup"><span data-stu-id="8693f-125">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="8693f-126">Konfigurowanie programu EF Core</span><span class="sxs-lookup"><span data-stu-id="8693f-126">Configuring EF Core</span></span>

<span data-ttu-id="8693f-127">W aplikacji ASP.NET Core zwykle skonfigurujesz programu EF Core w metodzie ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="8693f-127">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="8693f-128">EF Core używa DbContextOptionsBuilder, która obsługuje kilka metod pomocnego rozszerzenia, aby usprawnić jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8693f-128">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="8693f-129">Aby skonfigurować CatalogContext bazy danych programu SQL Server za pomocą parametrów połączenia, zdefiniowane w konfiguracji, należy dodać następujący kod do ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="8693f-129">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="8693f-130">Aby użyć bazy danych w pamięci:</span><span class="sxs-lookup"><span data-stu-id="8693f-130">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="8693f-131">Po zainstalowaniu programu EF Core, typem DbContext podrzędny utworzone i skonfigurowane w ConfigureServices, jesteś gotowy do użycia z programem EF Core.</span><span class="sxs-lookup"><span data-stu-id="8693f-131">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="8693f-132">Wystąpienie tego typu DbContext w dowolnej usługi, którym jest on wymagany do żądania i rozpocząć pracę z utrwalonego jednostek za pomocą LINQ, tak jakby były one po prostu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8693f-132">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="8693f-133">EF Core działa tłumaczenia wyrażenia LINQ do zapytań SQL do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-133">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="8693f-134">Możesz zobaczyć zapytań programu EF Core jest wykonywany przez skonfigurowanie Rejestrator oraz zapewnienia jego poziom jest równa co najmniej informacji, jak pokazano w rysunek 8-1.</span><span class="sxs-lookup"><span data-stu-id="8693f-134">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="8693f-135">Rysunek 8-1 rejestrowania programu EF Core zapytania do konsoli</span><span class="sxs-lookup"><span data-stu-id="8693f-135">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="8693f-136">Trwa pobieranie i zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="8693f-136">Fetching and storing Data</span></span>

<span data-ttu-id="8693f-137">Do pobierania danych z programem EF Core, dostęp do odpowiedniej właściwości i używać programu LINQ do filtrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="8693f-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="8693f-138">LINQ umożliwia również wykonywać projekcji, transformacji wyniku z jednego typu na inny.</span><span class="sxs-lookup"><span data-stu-id="8693f-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="8693f-139">Poniższy przykład pobiera CatalogBrands, uporządkowane według nazwy, filtrowane według ich właściwość włączone i rzutowany na typ SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="8693f-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="8693f-140">Jest ważne w powyższym przykładzie, aby dodać wywołanie do ToListAsync, aby można było przeprowadzić zapytanie natychmiastowo.</span><span class="sxs-lookup"><span data-stu-id="8693f-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="8693f-141">W przeciwnym razie instrukcji przypisze element IQueryable\<SelectListItem > do brandItems, który nie zostanie wykonany dopóki go wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8693f-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="8693f-142">Istnieją zalety i wady do zwracania wyników IQueryable z metod.</span><span class="sxs-lookup"><span data-stu-id="8693f-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="8693f-143">Umożliwia to zapytanie, które programu EF Core będzie konstruowania można dalej modyfikować, ale może również powodować błędy występujące tylko w czasie wykonywania, jeśli działania są dodawane do zapytania, które nie może tłumaczyć programu EF Core.</span><span class="sxs-lookup"><span data-stu-id="8693f-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="8693f-144">Zazwyczaj bezpieczniej przekazać jakiekolwiek filtry do metody wykonywania dostępu do danych, a zwracany z powrotem kolekcji w pamięci (na przykład listy\<T >) w wyniku.</span><span class="sxs-lookup"><span data-stu-id="8693f-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="8693f-145">EF Core śledzi zmiany w jednostkach, który pobiera się go z trwałości.</span><span class="sxs-lookup"><span data-stu-id="8693f-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="8693f-146">Aby zapisać zmiany do śledzonych jednostki, po prostu Wywołaj metodę SaveChanges dla kontekstu DbContext, upewniając się, że jest to samo wystąpienie typu DbContext, który został użyty do pobrania jednostki.</span><span class="sxs-lookup"><span data-stu-id="8693f-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="8693f-147">Dodawanie i usuwanie jednostek odbywa się bezpośrednio na odpowiedniej właściwości DbSet ponownie z wywołaniem funkcji SaveChanges można wykonać polecenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="8693f-148">Poniższy przykład pokazuje, dodawanie, aktualizowanie i usuwanie jednostek trwałości.</span><span class="sxs-lookup"><span data-stu-id="8693f-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="8693f-149">EF Core obsługuje zarówno synchroniczne i asynchroniczne metody pobierania i zapisywania.</span><span class="sxs-lookup"><span data-stu-id="8693f-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="8693f-150">W aplikacjach sieci web zaleca się używanie wzorca async/await z metodami asynchronicznymi, tak aby wątków serwera sieci web nie są blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="8693f-151">Pobieranie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="8693f-151">Fetching related data</span></span>

<span data-ttu-id="8693f-152">Jeśli programu EF Core pobiera jednostek, wypełnienie wszystkich właściwości, które są przechowywane bezpośrednio z tej jednostki w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="8693f-153">Właściwości nawigacji, takie jak listy powiązanych jednostek nie są uzupełniane i może mieć ich ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="8693f-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="8693f-154">Dzięki temu programu EF Core nie: pobieranie większej ilości danych niż jest potrzebny, co jest szczególnie ważne dla aplikacji sieci web, które musi szybko przetwarzania żądań i zwracania odpowiedzi w sposób efektywny.</span><span class="sxs-lookup"><span data-stu-id="8693f-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="8693f-155">Aby uwzględnić relacje z jednostki przy użyciu _wczesne ładowanie_, możesz określić właściwości, za pomocą metody rozszerzenia Include w zapytaniu, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="8693f-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="8693f-156">Może zawierać wiele relacji, a możesz również uwzględnić relacje podrzędne przy użyciu ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="8693f-156">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="8693f-157">EF Core wykona pojedynczego zapytania można pobrać Wynikowy zestaw jednostek.</span><span class="sxs-lookup"><span data-stu-id="8693f-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="8693f-158">Alternatywnie może zawierać właściwości nawigacji dla właściwości nawigacji, przekazując "." -rozdzielonych ciąg `.Include()` metodę rozszerzenia, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8693f-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include(“Items.Products”)
```

<span data-ttu-id="8693f-159">Oprócz enkapsulacji logikę filtrowania, Specyfikacja można określić kształt danych ma zostać zwrócone, łącznie z właściwości, które można wypełnić.</span><span class="sxs-lookup"><span data-stu-id="8693f-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="8693f-160">Przykład eShopOnWeb obejmuje kilka specyfikacje, które pokazują, zawieranie wczesne ładowanie informacji w ramach specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="8693f-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="8693f-161">Aby zobaczyć, jak specyfikację jest używana jako część zapytania w tym miejscu:</span><span class="sxs-lookup"><span data-stu-id="8693f-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="8693f-162">Innym rozwiązaniem do ładowania danych pokrewnych jest użycie _jawne ładowanie_.</span><span class="sxs-lookup"><span data-stu-id="8693f-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="8693f-163">Jawne ładowanie umożliwia ładowanie dodatkowe dane do jednostki, które już zostały pobrane.</span><span class="sxs-lookup"><span data-stu-id="8693f-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="8693f-164">Ponieważ wymaga to oddzielne żądania w bazie danych, nie jest zalecane dla aplikacji sieci web, które należy zminimalizować liczbę baz danych rund wprowadzone na żądanie.</span><span class="sxs-lookup"><span data-stu-id="8693f-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="8693f-165">_Powolne ładowanie_ to funkcja, która automatycznie ładuje powiązanych danych, ponieważ jest odwoływany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8693f-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="8693f-166">EF Core została dodana obsługa ładowania z opóźnieniem w wersji 2.1.</span><span class="sxs-lookup"><span data-stu-id="8693f-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="8693f-167">Powolne ładowanie nie jest domyślnie włączona i wymaga zainstalowania `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="8693f-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="8693f-168">Podobnie jak w przypadku jawne ładowanie powolne ładowanie powinien zazwyczaj można wyłączyć dla aplikacji sieci web, ponieważ spowoduje jej użycie w zapytaniach dodatkowa baza danych, które zostaną wprowadzone w ramach każdego żądania sieci web.</span><span class="sxs-lookup"><span data-stu-id="8693f-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="8693f-169">Niestety koszty ponoszone przez powolne ładowanie często prowadzi niezauważona w czasie projektowania, gdy czas oczekiwania jest mały i często są małe, zestawy danych używane do testowania.</span><span class="sxs-lookup"><span data-stu-id="8693f-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="8693f-170">Jednak w środowisku produkcyjnym z większej liczby użytkowników, większej ilości danych i więcej opóźnienia żądania dodatkowej bazy danych można często spowodować obniżenie wydajności dla aplikacji sieci web, które intensywnie korzystają z opóźnieniem ładowania.</span><span class="sxs-lookup"><span data-stu-id="8693f-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="8693f-171">Należy unikać powolne ładowanie jednostek w aplikacjach sieci Web</span><span class="sxs-lookup"><span data-stu-id="8693f-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="8693f-172">Zawieranie danych</span><span class="sxs-lookup"><span data-stu-id="8693f-172">Encapsulating data</span></span>

<span data-ttu-id="8693f-173">EF Core obsługuje kilka funkcji, które umożliwiają modelu do hermetyzacji prawidłowo swojego stanu.</span><span class="sxs-lookup"><span data-stu-id="8693f-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="8693f-174">Typowym problemem w modeli domeny jest eksponowanie właściwości nawigacji kolekcji jako typy list dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="8693f-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="8693f-175">Dzięki temu wszystkie współpracownika do manipulowania zawartość tych kolekcji typów, które może pominąć reguł biznesowych ważne związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="8693f-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="8693f-176">Rozwiązaniem tego problemu, aby uwidocznić dostęp tylko do odczytu do powiązanej kolekcji i jawnie zapewnić metody definiowania sposobów, w których klientów można manipulować nimi, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8693f-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

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

<span data-ttu-id="8693f-177">Należy pamiętać, że tego typu jednostki nie ujawnia publiczny `List` lub `ICollection` właściwości, ale zamiast tego udostępnia `IReadOnlyCollection` typ, który otacza bazowego typu listy.</span><span class="sxs-lookup"><span data-stu-id="8693f-177">Note that this entity type doesn’t expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="8693f-178">Gdy za pomocą ten wzorzec może wskazywać na platformy Entity Framework Core służące do pola pomocniczego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8693f-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="8693f-179">Innym sposobem, w którym można zwiększyć modelu domeny jest przy użyciu obiektów wartości dla typów, Brak tożsamości, które różnią się tylko przez ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="8693f-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="8693f-180">Używanie tych typów jako właściwości jednostki zabezpieczać logiki określonego obiektu wartości, gdzie należy i uniknąć zduplikowanych logika między wiele jednostek, które używają tego samego pojęcia.</span><span class="sxs-lookup"><span data-stu-id="8693f-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="8693f-181">W programie Entity Framework Core można utrwalić obiekty wartości w tej samej tabeli jako ich właścicielem jednostki, konfigurując typ jako jednostki należące do firmy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8693f-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="8693f-182">W tym przykładzie `ShipToAddress` właściwość jest typu `Address`.</span><span class="sxs-lookup"><span data-stu-id="8693f-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="8693f-183">`Address` jest obiekt wartości przy użyciu kilka właściwości, takich jak `Street` i `City`.</span><span class="sxs-lookup"><span data-stu-id="8693f-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="8693f-184">EF Core mapuje `Order` obiektu do swojej tabeli z jedną kolumną na `Address` właściwości poprzedzania ich nazwa kolumny o nazwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="8693f-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="8693f-185">W tym przykładzie `Order` tabela będzie zawierać kolumny takie jak `ShipToAddress_Street` i `ShipToAddress_City`.</span><span class="sxs-lookup"><span data-stu-id="8693f-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span>

[<span data-ttu-id="8693f-186">EF Core 2.2 wprowadzono obsługę kolekcjami jednostek należące do firmy</span><span class="sxs-lookup"><span data-stu-id="8693f-186">EF Core 2.2 introduces support for collections of owned entities</span></span>](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a><span data-ttu-id="8693f-187">Odporne na błędy połączenia</span><span class="sxs-lookup"><span data-stu-id="8693f-187">Resilient connections</span></span>

<span data-ttu-id="8693f-188">Zasobów zewnętrznych, takich jak bazy danych SQL co pewien czas mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8693f-188">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="8693f-189">W przypadku tymczasowej niedostępności aplikacje mogą używać logikę ponawiania próby, aby uniknąć zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8693f-189">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="8693f-190">Ta technika jest często nazywany _elastyczność połączenia_.</span><span class="sxs-lookup"><span data-stu-id="8693f-190">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="8693f-191">Można zaimplementować swoje [własnych ponawiania wykładniczego wycofywania](https://docs.microsoft.com/azure/architecture/patterns/retry) technika przez próby ponowienia z wykładniczo rosnącym czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="8693f-191">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="8693f-192">Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępna przez krótki okres czasu, co spowoduje niepowodzenie niektórych żądań.</span><span class="sxs-lookup"><span data-stu-id="8693f-192">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="8693f-193">Dla bazy danych SQL Azure platformy Entity Framework Core już zawiera logikę ponawiania prób i odporności połączenia wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-193">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="8693f-194">Jednak należy włączyć strategii wykonywania programu Entity Framework, dla każdego połączenia DbContext, jeśli chcesz mieć odporne na błędy połączeń programu EF Core.</span><span class="sxs-lookup"><span data-stu-id="8693f-194">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="8693f-195">Na przykład następujący kod na poziomie połączenia platformy EF Core umożliwia odporne na błędy połączeń SQL, które są zwalniane, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="8693f-195">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="8693f-196">Strategii wykonywania i jawnego transakcji za pomocą BeginTransaction i wiele DbContexts</span><span class="sxs-lookup"><span data-stu-id="8693f-196">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="8693f-197">Po włączeniu ponownych prób w połączeniach programu EF Core każdej operacji, które możesz wykonać przy użyciu programu EF Core staje się własną wywołały operacji.</span><span class="sxs-lookup"><span data-stu-id="8693f-197">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="8693f-198">Jeśli wystąpi błąd przejściowy, każde zapytanie i każde wywołanie funkcji SaveChanges zostanie ponowiona jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="8693f-198">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="8693f-199">Jednak jeśli Twój kod inicjuje transakcji za pomocą BeginTransaction, definiujesz własną grupę działań, które muszą być traktowane jako jedna całość; wszystko wewnątrz transakcji musi zostać wycofana ponownie, jeśli wystąpi awaria.</span><span class="sxs-lookup"><span data-stu-id="8693f-199">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="8693f-200">Jeśli użytkownik podejmie próbę wykonania transakcji, gdy za pomocą strategii wykonywania EF (zasady ponawiania) i obejmują SaveChanges kilka z wielu DbContexts w nim pojawi się wyjątek, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="8693f-200">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="8693f-201">System.InvalidOperationException: Strategia wykonywania skonfigurowany "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji zainicjowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8693f-201">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="8693f-202">Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostka z możliwością ponowienia próby.</span><span class="sxs-lookup"><span data-stu-id="8693f-202">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="8693f-203">To rozwiązanie jest ręcznie wywołać strategii wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="8693f-203">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="8693f-204">Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła delegata ponownie.</span><span class="sxs-lookup"><span data-stu-id="8693f-204">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="8693f-205">Poniższy kod przedstawia sposób implementowania tego podejścia:</span><span class="sxs-lookup"><span data-stu-id="8693f-205">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="8693f-206">Jest pierwszym DbContext \_catalogContext, a druga DbContext mieści się w \_integrationEventLogService obiektu.</span><span class="sxs-lookup"><span data-stu-id="8693f-206">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="8693f-207">Na koniec zatwierdzenia akcji będą wykonywane wielu DbContexts i za pomocą strategii wykonywania EF.</span><span class="sxs-lookup"><span data-stu-id="8693f-207">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="8693f-208">Odwołania — platformy Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="8693f-208">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="8693f-209">**Dokumentacji programu EF Core**</span><span class="sxs-lookup"><span data-stu-id="8693f-209">**EF Core Docs**</span></span>  
>   <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="8693f-210">**EF Core: Powiązane dane**</span><span class="sxs-lookup"><span data-stu-id="8693f-210">**EF Core: Related Data**</span></span>  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="8693f-211">**Należy unikać powolne ładowanie jednostek w aplikacjach ASPNET**</span><span class="sxs-lookup"><span data-stu-id="8693f-211">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="8693f-212">EF Core lub micro ORM?</span><span class="sxs-lookup"><span data-stu-id="8693f-212">EF Core or micro-ORM?</span></span>

<span data-ttu-id="8693f-213">EF Core jest doskonałym wyborem do zarządzania trwałości i w większości przypadków hermetyzuje Szczegóły bazy danych z deweloperami aplikacji, nie jest jedyną dostępną.</span><span class="sxs-lookup"><span data-stu-id="8693f-213">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="8693f-214">Innym sposobem typu open source jest [programem Dapper](https://github.com/StackExchange/Dapper), tak zwane ORM micro.</span><span class="sxs-lookup"><span data-stu-id="8693f-214">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="8693f-215">Operacje micro-ORM to lekkie, mniej w pełni funkcjonalne narzędzie mapowania obiektów do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-215">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="8693f-216">W przypadku programem Dapper jego celów skupić się na wydajności, a nie w pełni enkapsulacji bazowego pyta o niego projekt używa do pobierania i aktualizowania danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-216">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="8693f-217">Ponieważ nie ona abstrakcyjna SQL od dewelopera, programem Dapper jest "uznane za bliższe sprzętu" i umożliwia deweloperom pisanie dokładnie operacja dostępu do zapytania, które mają być użyte dla danego danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-217">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="8693f-218">EF Core ma dwie funkcje znaczące, zapewnia które oddzielić go z programem Dapper, ale również dodać do jej zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="8693f-218">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="8693f-219">Pierwsza to tłumaczenie z wyrażenia LINQ do SQL.</span><span class="sxs-lookup"><span data-stu-id="8693f-219">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="8693f-220">Te tłumaczenia są buforowane, ale mimo ma obciążenie w wykonywaniu ich po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8693f-220">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="8693f-221">Drugim jest śledzenia zmian na jednostkach (dzięki czemu mogą być generowane instrukcjach update wydajne).</span><span class="sxs-lookup"><span data-stu-id="8693f-221">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="8693f-222">To zachowanie można wyłączyć dla określonego zapytania za pomocą rozszerzenia AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="8693f-222">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="8693f-223">EF Core generuje również zapytania SQL, które zwykle są bardzo wydajny i w każdym przypadku doskonale akceptowalne z punktu widzenia wydajności, ale jeśli potrzebujesz poprawnie kontrolę nad dokładne zapytanie do wykonania, możesz przekazać niestandardowe SQL (lub wykonaj procedurę składowaną) przy użyciu programu EF Podstawowe, zbyt.</span><span class="sxs-lookup"><span data-stu-id="8693f-223">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="8693f-224">W tym przypadku przewyższa przekształcania programem Dapper nadal stosowane programu EF Core, ale tylko nieznacznie.</span><span class="sxs-lookup"><span data-stu-id="8693f-224">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="8693f-225">Przedstawia Julie Lerman niektóre dane dotyczące wydajności w jej może artykuł w witrynie MSDN 2016 [programem Dapper, platformy Entity Framework oraz hybrydowych aplikacji](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="8693f-225">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="8693f-226">Dodatkowych testów porównawczych danych o wydajności dla różnych metod dostępu do danych można znaleźć na [lokacji z programem Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="8693f-226">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="8693f-227">Aby zobaczyć, jak składnia programem Dapper zmienia się z programem EF Core, należy wziąć pod uwagę te dwie wersje tej samej metody do pobierania listy elementów:</span><span class="sxs-lookup"><span data-stu-id="8693f-227">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="8693f-228">Jeśli potrzebujesz do tworzenia bardziej złożonych wykresów obiektów z programem Dapper, należy napisać samodzielnie skojarzone zapytania (w przeciwieństwie do dodawania dołączania, tak jak w programie EF Core).</span><span class="sxs-lookup"><span data-stu-id="8693f-228">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="8693f-229">Jest to obsługiwane za pośrednictwem różnych składni, w tym funkcję o nazwie Multi mapowanie umożliwiające mapowanie poszczególne wiersze do wielu obiektów zamapowanego.</span><span class="sxs-lookup"><span data-stu-id="8693f-229">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="8693f-230">Na przykład biorąc pod uwagę klasy wpis z właściwością właściciela typu użytkownika, następujące instrukcje SQL zwróci wszystkie niezbędne dane:</span><span class="sxs-lookup"><span data-stu-id="8693f-230">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="8693f-231">Każdego zwróconego wiersza zawiera dane użytkownika i Post.</span><span class="sxs-lookup"><span data-stu-id="8693f-231">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="8693f-232">Ponieważ dane użytkownika musi być podłączona do danych Post za pomocą właściwości jego właściciela, jest używany następującą funkcję:</span><span class="sxs-lookup"><span data-stu-id="8693f-232">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="8693f-233">Listy pełnego kodu do zwrócenia zbiór wpisów z ich właściwości właściciela wypełniony danymi skojarzonego użytkownika mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="8693f-233">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="8693f-234">Ponieważ oferuje ona mniejszą hermetyzacji, programem Dapper wymaga deweloperów dowiedzieć się więcej o jak są przechowywane ich dane, jak skutecznie wykonuje zapytania i zapisać więcej kodu, aby go pobrać.</span><span class="sxs-lookup"><span data-stu-id="8693f-234">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="8693f-235">Po zmianie modelu, a nie po prostu utworzenie nowej migracji (inna funkcja programu EF Core) i/lub aktualizowanie informacji o mapowaniu w jednym miejscu w DbContext każdego zapytania, które ma wpływ na musi zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="8693f-235">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="8693f-236">Te zapytania zostały bez gwarancji czasu kompilacji, więc one mogą przestać działać w czasie wykonywania w odpowiedzi na zmiany w modelu lub bazy danych, co utrudnia szybko wykrywać błędy.</span><span class="sxs-lookup"><span data-stu-id="8693f-236">These queries have no compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="8693f-237">W zamian za tych kompromisów programem Dapper oferuje bardzo wydajne.</span><span class="sxs-lookup"><span data-stu-id="8693f-237">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="8693f-238">Dla większości aplikacji i większość części niemal wszystkich aplikacji programu EF Core zapewnia akceptowalny poziom wydajności.</span><span class="sxs-lookup"><span data-stu-id="8693f-238">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="8693f-239">W związku z tym jego korzyści produktywność dla deweloperów prawdopodobnie przeważają swoje zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="8693f-239">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="8693f-240">Dla zapytań, które mogą korzystać z pamięci podręcznej, rzeczywiste zapytanie może wykonać tylko niewielki odsetek czasu, dzięki czemu stosunkowo mały zapytania moot różnice wydajności.</span><span class="sxs-lookup"><span data-stu-id="8693f-240">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="8693f-241">Bazy danych SQL lub NoSQL</span><span class="sxs-lookup"><span data-stu-id="8693f-241">SQL or NoSQL</span></span>

<span data-ttu-id="8693f-242">Tradycyjnie relacyjnych baz danych, takich jak program SQL Server ma zdominowany trwałego magazynu danych w witrynie marketplace, ale nie są one dostępne jedynym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="8693f-242">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="8693f-243">Bazy danych NoSQL, takie jak [bazy danych MongoDB](https://www.mongodb.com/what-is-mongodb) oferuje innego podejścia do przechowywania obiektów.</span><span class="sxs-lookup"><span data-stu-id="8693f-243">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="8693f-244">Zamiast mapowanie obiektów na tabele oraz wiersze, innym rozwiązaniem jest serializacji wykresu cały obiekt i zapisz wynik.</span><span class="sxs-lookup"><span data-stu-id="8693f-244">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="8693f-245">Zalety tego podejścia są co najmniej początkowo prostoty i wydajności.</span><span class="sxs-lookup"><span data-stu-id="8693f-245">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="8693f-246">Bez obaw prostszym sposobem przechowywania pojedynczy obiekt Zserializowany za pomocą klucza, niż można rozłożyć obiektu do wielu tabel z relacjami i pobrać aktualizacji i wierszy, które uległy zmianie od ostatniego obiektu z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-246">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="8693f-247">Podobnie Pobieranie i deserializację pojedynczy obiekt z magazynu opartego na kluczach jest zwykle szybsze i prostsze niż złożonych sprzężeń lub wiele zapytań bazy danych wymagane do tworzenia w pełni tego samego obiektu z relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-247">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="8693f-248">Brak blokady lub transakcji lub stałego schematu sprawia, że bazy danych NoSQL bardzo podatna na skalowanie na wiele maszyn, obsługa bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-248">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="8693f-249">Z drugiej strony bazy danych NoSQL (zazwyczaj są one nazywane) mają swoje wady.</span><span class="sxs-lookup"><span data-stu-id="8693f-249">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="8693f-250">Relacyjne bazy danych użyj normalizacji, wymuszanie spójności i unikanie zduplikowanie danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-250">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="8693f-251">Zmniejsza całkowity rozmiar bazy danych i zapewnia, że aktualizacje do udostępnionych danych są dostępne bezpośrednio w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-251">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="8693f-252">W relacyjnej bazie danych tabeli adresów może odwołać się do kraju tabeli według identyfikatorów, taki sposób, że jeśli zmieniono nazwę kraju, rekordów adresów będą korzystać z aktualizacji bez muszą zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="8693f-252">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="8693f-253">Jednak w bazie danych NoSQL adres i jego skojarzone kraj może zostać Zserializowany jako część wiele obiektów przechowywanych.</span><span class="sxs-lookup"><span data-stu-id="8693f-253">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="8693f-254">Aktualizacja Nazwa kraju wymagałoby wszystkie takie obiekty do zaktualizowania, a nie pojedynczego wiersza.</span><span class="sxs-lookup"><span data-stu-id="8693f-254">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="8693f-255">Relacyjne bazy danych może również zagwarantować integralności relacyjnych przez wymuszenie zasad, takie jak klucze obce.</span><span class="sxs-lookup"><span data-stu-id="8693f-255">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="8693f-256">Bazy danych NoSQL nie oferują zazwyczaj takie ograniczenia swoich danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-256">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="8693f-257">Inny złożoności musi obsłużyć baz danych NoSQL jest przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="8693f-257">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="8693f-258">Po zmianie właściwości tego obiektu, nie można mogła zostać przeprowadzona poprzednich wersji, które były przechowywane.</span><span class="sxs-lookup"><span data-stu-id="8693f-258">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="8693f-259">W związku z tym aby były zgodne ze schematem nowe należy zaktualizować wszystkich istniejących obiektów, które mają (poprzednia wersja) wersja po serializacji jest obiektu.</span><span class="sxs-lookup"><span data-stu-id="8693f-259">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="8693f-260">Różni się to nie koncepcyjnie z relacyjnej bazy danych, w przypadku, gdy schemat zmienia się czasami wymagają skryptów aktualizacji lub mapowania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8693f-260">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="8693f-261">Jednak liczba wpisów, które muszą zostać zmodyfikowane odbywa się znacznie większa w ujęciu NoSQL, ponieważ ma więcej zduplikowanie danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-261">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="8693f-262">Jest to możliwe w bazy danych NoSQL do przechowywania wielu wersji obiektów, coś stały schemat relacyjnych baz danych zwykle nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="8693f-262">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="8693f-263">Jednak w takiej sytuacji kod aplikacji należy uwzględnić istnienie poprzednie wersje obiekty, dodawanie dodatkowej złożoności.</span><span class="sxs-lookup"><span data-stu-id="8693f-263">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="8693f-264">Zazwyczaj nie wymuszają bazy danych NoSQL [ACID](https://en.wikipedia.org/wiki/ACID), co oznacza, że ich korzystnie wpływać na wydajność i skalowalność za pośrednictwem relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-264">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="8693f-265">Są one dobrze nadaje się do bardzo dużych zestawów danych i obiektów, które nie nadają się do magazynu w strukturach znormalizowanych tabel.</span><span class="sxs-lookup"><span data-stu-id="8693f-265">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="8693f-266">Nie ma powodu i dlaczego pojedynczej aplikacji nie mogą korzystać zarówno relacyjnych baz danych NoSQL, przy użyciu każdego, gdzie najlepiej dostosowane.</span><span class="sxs-lookup"><span data-stu-id="8693f-266">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="8693f-267">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="8693f-267">Azure DocumentDB</span></span>

<span data-ttu-id="8693f-268">Azure DocumentDB to w pełni zarządzana usługa bazy danych NoSQL, która oferuje magazyn danych bez schematu w chmurze.</span><span class="sxs-lookup"><span data-stu-id="8693f-268">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="8693f-269">Baza danych DocumentDB jest stworzona z myślą szybkie przetwarzanie, przewidywalną wydajność, wysoką dostępność, elastyczne skalowanie i globalnej dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="8693f-269">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="8693f-270">Mimo iż bazę danych NoSQL, deweloperzy mogą używać szerokie i powszechnie znane możliwości zapytań SQL na dane JSON.</span><span class="sxs-lookup"><span data-stu-id="8693f-270">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="8693f-271">Wszystkie zasoby w usłudze DocumentDB są przechowywane jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="8693f-271">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="8693f-272">Zasoby są zarządzane jako _elementów_, które są dokumenty zawierające metadane, oraz _źródła_, które są kolekcjami elementów.</span><span class="sxs-lookup"><span data-stu-id="8693f-272">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="8693f-273">Rysunek 8-2 przedstawiono relacje między różnymi zasobami usługi DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="8693f-273">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>

![Hierarchiczna relacja między zasobami w usłudze DocumentDB, bazy danych NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="8693f-275">**Rysunek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="8693f-275">**Figure 8-2.**</span></span> <span data-ttu-id="8693f-276">Organizacji zasobów usługi DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="8693f-276">DocumentDB resource organization.</span></span>

<span data-ttu-id="8693f-277">Język zapytań usługi DocumentDB jest prostym, ale zaawansowanym interfejsem na wykonywanie zapytań względem dokumentów JSON.</span><span class="sxs-lookup"><span data-stu-id="8693f-277">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="8693f-278">Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywołania funkcji JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8693f-278">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="8693f-279">**Odwołania — baza danych DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="8693f-279">**References – DocumentDB**</span></span>

- <span data-ttu-id="8693f-280">Wprowadzenie do usługi DocumentDB</span><span class="sxs-lookup"><span data-stu-id="8693f-280">DocumentDB Introduction</span></span>  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="8693f-281">Inne opcje trwałości</span><span class="sxs-lookup"><span data-stu-id="8693f-281">Other persistence options</span></span>

<span data-ttu-id="8693f-282">Oprócz relacyjnych i opcje magazynu NoSQL aplikacje platformy ASP.NET Core można użyć usługi Azure Storage do przechowywania różnych formatów danych i plików w sposób oparte na chmurze, skalowalne.</span><span class="sxs-lookup"><span data-stu-id="8693f-282">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="8693f-283">Usługa Azure Storage jest wysoce skalowalnej, więc możesz rozpocząć przechowywania niewielkich ilości danych i skalowanie w górę do przechowywania setki lub terabajtów, jeśli aplikacja wymaga go.</span><span class="sxs-lookup"><span data-stu-id="8693f-283">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="8693f-284">Usługa Azure Storage obsługuje cztery rodzaje danych:</span><span class="sxs-lookup"><span data-stu-id="8693f-284">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="8693f-285">Blob Storage służy do tekstu bez struktury lub magazyn binarny, nazywane również magazynu obiektów.</span><span class="sxs-lookup"><span data-stu-id="8693f-285">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="8693f-286">Table Storage w przypadku zestawów strukturalnych danych dostępne za pośrednictwem kluczy wierszy.</span><span class="sxs-lookup"><span data-stu-id="8693f-286">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="8693f-287">Queue Storage niezawodne kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8693f-287">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="8693f-288">Plik magazynu udostępnionego przy dostępie do plików między maszynami wirtualnymi platformy Azure i aplikacji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8693f-288">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="8693f-289">**Odwołania — usługa Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="8693f-289">**References – Azure Storage**</span></span>

- <span data-ttu-id="8693f-290">Wprowadzenie do usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8693f-290">Azure Storage Introduction</span></span>  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="8693f-291">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="8693f-291">Caching</span></span>

<span data-ttu-id="8693f-292">W aplikacjach sieci web należy wykonać wszystkie żądania sieci web w możliwie jak najszybciej.</span><span class="sxs-lookup"><span data-stu-id="8693f-292">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="8693f-293">Jednym ze sposobów osiągnięcia tego jest ograniczyć liczbę wywołań zewnętrznego serwera należy wykonać w celu wykonania żądania.</span><span class="sxs-lookup"><span data-stu-id="8693f-293">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="8693f-294">Buforowanie obejmuje przechowywanie kopii danych na serwerze (lub inny magazyn danych to znaczy więcej łatwo zapytań od źródła danych).</span><span class="sxs-lookup"><span data-stu-id="8693f-294">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="8693f-295">Aplikacje sieci Web i szczególnie bez SPA tradycyjnej sieci web, konieczne zbudowanie cały interfejs użytkownika z każdym żądaniem.</span><span class="sxs-lookup"><span data-stu-id="8693f-295">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="8693f-296">Obejmuje to często, dzięki czemu wiele z tego samego zapytania do bazy danych wielokrotnie z jednego użytkownika żądania do następnej.</span><span class="sxs-lookup"><span data-stu-id="8693f-296">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="8693f-297">W większości przypadków te dane zmienia się rzadko, więc ma nieco powód, aby stale żądania z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-297">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="8693f-298">ASP.NET Core obsługuje buforowanie odpowiedzi do buforowania całe strony i buforowanie danych, który obsługuje bardziej szczegółowego zachowanie buforowania.</span><span class="sxs-lookup"><span data-stu-id="8693f-298">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="8693f-299">Podczas implementowania pamięci podręcznej, należy mieć na uwadze separacji zagadnień.</span><span class="sxs-lookup"><span data-stu-id="8693f-299">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="8693f-300">Należy unikać implementacji logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8693f-300">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="8693f-301">Należy hermetyzować buforowania w jego własnej klasy i zarządzać jego zachowanie przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8693f-301">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="8693f-302">Następuje otwarty/zamknięty i zasady pojedynczej odpowiedzialności i ułatwi zarządzanie, jak używać buforowania w aplikacji w miarę jej rozwoju.</span><span class="sxs-lookup"><span data-stu-id="8693f-302">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="8693f-303">Buforowanie odpowiedzi platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8693f-303">ASP.NET Core response caching</span></span>

<span data-ttu-id="8693f-304">Platforma ASP.NET Core obsługuje dwa poziomy buforowanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8693f-304">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="8693f-305">Pierwszy poziom nie będzie buforować niczego na serwerze, ale dodaje nagłówki HTTP, które poinstruowanie klientów i serwerów proxy buforowanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8693f-305">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="8693f-306">Ten sposób jest implementowany przez dodanie atrybutu ResponseCache do poszczególnych kontrolerów i akcji:</span><span class="sxs-lookup"><span data-stu-id="8693f-306">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="8693f-307">Poprzedni przykład, wynikiem będzie następujący nagłówek, które są dodawane do odpowiedzi poinstruowanie klientom Zbuforuj wynik do 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="8693f-307">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="8693f-308">Cache-Control: public,max-age=60</span><span class="sxs-lookup"><span data-stu-id="8693f-308">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="8693f-309">Aby można było dodać buforowanie w pamięci po stronie serwera aplikacji, musi odwoływać się do pakietu Microsoft.AspNetCore.ResponseCaching NuGet, a następnie dodaj oprogramowanie pośredniczące buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8693f-309">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="8693f-310">To oprogramowanie pośredniczące jest skonfigurowany zarówno w ConfigureServices i Konfiguruj przy uruchamianiu:</span><span class="sxs-lookup"><span data-stu-id="8693f-310">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="8693f-311">Oprogramowanie pośredniczące buforowania odpowiedzi automatycznie będzie buforować odpowiedzi na podstawie zestawu warunków, które można dostosować.</span><span class="sxs-lookup"><span data-stu-id="8693f-311">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="8693f-312">Domyślnie tylko 200 (OK) odpowiedzi na żądanie za pomocą metod GET lub główny są buforowane.</span><span class="sxs-lookup"><span data-stu-id="8693f-312">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="8693f-313">Ponadto żądania muszą mieć odpowiedź z Cache-Control: nagłówek publicznych i nie może zawierać nagłówki autoryzacji lub Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="8693f-313">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="8693f-314">Zobacz [pełną listę warunków pamięci podręcznej używane przez odpowiedzi, oprogramowanie pośredniczące buforowania](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="8693f-314">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="8693f-315">Buforowanie danych</span><span class="sxs-lookup"><span data-stu-id="8693f-315">Data caching</span></span>

<span data-ttu-id="8693f-316">Zamiast (lub oprócz) buforowanie odpowiedzi z pełnej sieci web, można buforować wyniki zapytań danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-316">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="8693f-317">W tym celu można użyć w pamięć podręczna na serwerze sieci web, lub [rozproszonej pamięci podręcznej](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="8693f-317">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="8693f-318">W tej sekcji pokażemy, jak wdrożyć w pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="8693f-318">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="8693f-319">Dodano obsługę pamięci (lub rozproszonej) buforowania ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="8693f-319">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="8693f-320">Pamiętaj dodać pakiet Microsoft.Extensions.Caching.Memory NuGet także.</span><span class="sxs-lookup"><span data-stu-id="8693f-320">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="8693f-321">Po dodaniu usługi wszędzie tam, gdzie chcesz uzyskać dostęp do pamięci podręcznej możesz poprosić IMemoryCache za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="8693f-321">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="8693f-322">W tym przykładzie CachedCatalogService jest przy użyciu wzorca projektowego serwera Proxy (lub elementu Decorator), zapewniając alternatywnej implementacji ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie, aby) podstawowej implementacji CatalogService.</span><span class="sxs-lookup"><span data-stu-id="8693f-322">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="8693f-323">Aby skonfigurować aplikację do używania pamięci podręcznej wersji usługi, ale nadal umożliwić usłudze wystąpienia CatalogService potrzebuje w jego konstruktorze, należy dodać następujące w ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="8693f-323">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="8693f-324">Dzięki temu w miejscu wywołania bazy danych, które można pobrać danych katalogu zostanie zastosowane tylko raz na minutę, a nie na każde żądanie.</span><span class="sxs-lookup"><span data-stu-id="8693f-324">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="8693f-325">W zależności od ruchu sieciowego do lokacji może to mieć bardzo istotne znaczenie liczby zapytań do bazy danych i czas ładowania strony dla strony głównej, który obecnie zależy od wszystkich trzech zapytania udostępniane przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8693f-325">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="8693f-326">Jest problem, który pojawia się, gdy buforowanie jest zaimplementowana _starych danych_ — oznacza to, że dane, które uległy zmianie w źródle, ale jest nieaktualna wersja pozostaje w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8693f-326">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="8693f-327">Jest to prosty sposób rozwiązać ten problem do użycia małych czas trwania pamięci podręcznej, ponieważ zajęty aplikacji jest ograniczona dodatkową korzyścią rozszerzanie długości, które dane są buforowane.</span><span class="sxs-lookup"><span data-stu-id="8693f-327">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="8693f-328">Rozważmy na przykład strona, która wykonuje zapytanie pojedynczej bazy danych, a żądania 10 razy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="8693f-328">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="8693f-329">Jeśli ta strona jest buforowana na jedną minutę, spowoduje wiele zapytań do bazy danych wprowadzone na minutę do usunięcia z 600 1, redukcji 99,8%.</span><span class="sxs-lookup"><span data-stu-id="8693f-329">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="8693f-330">Jeśli zamiast tego czasu trwania pamięci podręcznej wprowadzono jedną godzinę, ogólne zmniejszenie będzie 99.997%, ale teraz prawdopodobieństwo i potencjalnego wiek starych danych są zarówno została znacznie zwiększona.</span><span class="sxs-lookup"><span data-stu-id="8693f-330">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="8693f-331">Innym rozwiązaniem jest aktywnie usunąć wpisy w pamięci podręcznej podczas aktualizacji danych, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="8693f-331">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="8693f-332">Może zostać usunięty wszelkie pojedynczy wpis, jeśli znane jest jego klucza:</span><span class="sxs-lookup"><span data-stu-id="8693f-332">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="8693f-333">Jeśli aplikacja ujawnia funkcje aktualizowania wpisów, które go zapisuje w pamięci podręcznej, możesz usunąć odpowiednie wpisy w pamięci podręcznej, w kodzie, który wykonuje aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="8693f-333">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="8693f-334">Czasami może występować wiele różnych wpisów, które są zależne od określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-334">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="8693f-335">W takiej sytuacji może być przydatne do tworzenia zależności między wpisy w pamięci podręcznej, za pomocą CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="8693f-335">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="8693f-336">Za pomocą CancellationChangeToken wiele wpisów pamięci podręcznej można unieważnić jednocześnie, przez token anulowania.</span><span class="sxs-lookup"><span data-stu-id="8693f-336">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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

<span data-ttu-id="8693f-337">Buforowanie może znacznie zwiększyć wydajność stron sieci web, wielokrotnie żądającym takie same wartości z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8693f-337">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="8693f-338">Pamiętaj zmierzyć wydajność dostępu i stronę przed zastosowaniem buforowania danych i są stosowane tylko wtedy buforowania tam, gdzie zobaczysz na potrzeby poprawy jakości obsługi.</span><span class="sxs-lookup"><span data-stu-id="8693f-338">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="8693f-339">Buforowanie zużywanie zasobów pamięci serwera sieci web i zwiększa złożoność aplikacji, dlatego ważne jest, aby nie przedwcześnie Optymalizowanie przy użyciu tej metody.</span><span class="sxs-lookup"><span data-stu-id="8693f-339">Caching consumes web server memory resources and increases the complexity of the application, so it’s important you don’t prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8693f-340">[Poprzednie](develop-asp-net-core-mvc-apps.md)
>[dalej](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="8693f-340">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
