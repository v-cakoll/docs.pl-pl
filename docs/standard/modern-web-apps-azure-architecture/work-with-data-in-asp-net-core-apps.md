---
title: Praca z danymi w aplikacjach Core ASP.NET
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Praca z danymi w asp
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 89df46c8e04e1826c84058e5d2a92d089eb96098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592525"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="a50b2-103">Praca z danymi w aplikacjach platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a50b2-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="a50b2-104">"Danych należy cenny i trwa dłużej niż samych systemów".</span><span class="sxs-lookup"><span data-stu-id="a50b2-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="a50b2-105">Timowi Berners Lewandowski</span><span class="sxs-lookup"><span data-stu-id="a50b2-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="a50b2-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="a50b2-106">Summary</span></span>

<span data-ttu-id="a50b2-107">Dostęp do danych jest ważnym elementem prawie każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="a50b2-108">Platformy ASP.NET Core obsługuje wiele różnych opcji dostępu do danych, w tym Entity Framework Core (a także Entity Framework 6) i pracować z dowolnego .NET framework dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="a50b2-109">Wybór danych dostęp framework do użycia zależy od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="a50b2-110">Abstrakcyjność te wybory w projektach ApplicationCore i interfejsu użytkownika i hermetyzuje szczegóły implementacji w infrastrukturze, pomaga utworzyć luźno powiązanych, testować oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a50b2-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="a50b2-111">Entity Framework Core (w przypadku relacyjnych baz danych)</span><span class="sxs-lookup"><span data-stu-id="a50b2-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="a50b2-112">Jeśli piszesz nowej aplikacji platformy ASP.NET Core, który wymaga do pracy z danych relacyjnych Entity Framework Core (EF rdzeń) jest zalecany sposób dostępu do danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="a50b2-113">Podstawowe EF jest obiektów relacyjnych mapowania (O/RM), który umożliwia deweloperom platformy .NET utrwalania obiektów do i z źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="a50b2-114">Eliminuje potrzebę większość kodu dostępu do danych, deweloperzy zazwyczaj musi zapisać.</span><span class="sxs-lookup"><span data-stu-id="a50b2-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="a50b2-115">Podobnie jak platformy ASP.NET Core EF Core została ponownie napisana od podstaw Obsługa modularnej aplikacji dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="a50b2-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="a50b2-116">Dodaj go do aplikacji jako pakietu NuGet, ją skonfigurować w uruchamiania i żądania za pomocą iniekcji zależności wszędzie tam, gdzie będzie potrzebny.</span><span class="sxs-lookup"><span data-stu-id="a50b2-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="a50b2-117">Aby używać EF Core z bazy danych programu SQL Server, uruchom następujące polecenie dotnet w interfejsu wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="a50b2-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="a50b2-118">Pakiet Microsoft.EntityFrameworkCore.SqlServer dodać DotNet</span><span class="sxs-lookup"><span data-stu-id="a50b2-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="a50b2-119">Aby dodać obsługę InMemory źródła danych, do testowania:</span><span class="sxs-lookup"><span data-stu-id="a50b2-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="a50b2-120">Pakiet Microsoft.EntityFrameworkCore.InMemory dodać DotNet</span><span class="sxs-lookup"><span data-stu-id="a50b2-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="a50b2-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="a50b2-121">The DbContext</span></span>

<span data-ttu-id="a50b2-122">Aby pracować z EF Core, konieczne jest podklasą klasy DbContext.</span><span class="sxs-lookup"><span data-stu-id="a50b2-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="a50b2-123">Ta klasa zawiera reprezentujący kolekcje jednostek, który aplikacja będzie działać z właściwości.</span><span class="sxs-lookup"><span data-stu-id="a50b2-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="a50b2-124">Przykładowe eShopOnWeb obejmuje CatalogContext z kolekcji elementów, marek i typy:</span><span class="sxs-lookup"><span data-stu-id="a50b2-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="a50b2-125">Twoje DbContext musi mieć konstruktora akceptującego DbContextOptions i przekazać ten argument do konstruktora podstawowego typu DbContext.</span><span class="sxs-lookup"><span data-stu-id="a50b2-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="a50b2-126">Należy pamiętać, że jeśli masz tylko jedną DbContext w aplikacji, można przekazać wystąpienia DbContextOptions, ale jeśli masz więcej niż jeden należy użyć ogólnego DbContextOptions<T> typu, przekazując danego typu DbContext jako parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="a50b2-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="a50b2-127">Konfigurowanie EF Core</span><span class="sxs-lookup"><span data-stu-id="a50b2-127">Configuring EF Core</span></span>

<span data-ttu-id="a50b2-128">W aplikacji platformy ASP.NET Core zwykle skonfigurujesz EF Core w metodę ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="a50b2-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="a50b2-129">Podstawowe EF używa DbContextOptionsBuilder, która obsługuje kilka metod rozszerzenia przydatne uprościć konfigurację.</span><span class="sxs-lookup"><span data-stu-id="a50b2-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="a50b2-130">Aby skonfigurować CatalogContext do korzystania z bazy danych programu SQL Server z użyciem parametrów połączenia określonych w konfiguracji, czy Dodaj następujący kod do ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="a50b2-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="a50b2-131">Korzystanie z bazy danych w pamięci:</span><span class="sxs-lookup"><span data-stu-id="a50b2-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="a50b2-132">Po zainstalowaniu Core EF, typ podrzędny typu DbContext utworzone i skonfigurowane w ConfigureServices, można przystąpić do użycia EF Core.</span><span class="sxs-lookup"><span data-stu-id="a50b2-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="a50b2-133">Wystąpienie typu DbContext, w dowolnej usługi, który musi on zażądać i rozpocząć pracę z utrwalonego za pomocą LINQ, tak jakby były to po prostu w kolekcji jednostek.</span><span class="sxs-lookup"><span data-stu-id="a50b2-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="a50b2-134">Podstawowe EF działa tłumaczenia wyrażenia LINQ do zapytania SQL do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="a50b2-135">Widać zapytania EF Core jest wykonywany, konfigurując Rejestrator i zapewnienia jego poziom jest ustawiony na co najmniej informacje, jak pokazano w rysunek 8-1.</span><span class="sxs-lookup"><span data-stu-id="a50b2-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="a50b2-136">Rysunek 8-1 rejestrowanie podstawowych EF zapytania do konsoli</span><span class="sxs-lookup"><span data-stu-id="a50b2-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="a50b2-137">Trwa pobieranie i zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="a50b2-137">Fetching and Storing Data</span></span>

<span data-ttu-id="a50b2-138">Pobieranie danych z EF Core, dostęp do odpowiedniej właściwości i użyj rozszerzenia LINQ, aby przefiltrować wynik.</span><span class="sxs-lookup"><span data-stu-id="a50b2-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="a50b2-139">Umożliwia także LINQ do wykonywania projekcji, przekształcanie wyników z jednego typu na inny.</span><span class="sxs-lookup"><span data-stu-id="a50b2-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="a50b2-140">Poniższy przykład czy pobrać CatalogBrands, uporządkowanych według nazwy, filtrowane według ich właściwości Enabled i rzutowany na typ SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="a50b2-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="a50b2-141">Jest ważne w powyższym przykładzie, aby dodać wywołanie ToListAsync Aby natychmiast wykonać zapytanie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="a50b2-142">W przeciwnym razie instrukcji przypisze IQueryable<SelectListItem> do brandItems, które nie zostaną wykonane do czasu jej wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a50b2-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="a50b2-143">Brak zalet i wad do zwracania wyników IQueryable z metod.</span><span class="sxs-lookup"><span data-stu-id="a50b2-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="a50b2-144">Dzięki temu zapytania, które utworzy EF Core dalsze można zmodyfikować, ale może również spowodować błędy występujące tylko w czasie wykonywania, jeśli działania są dodawane do zapytania, które nie może dokonywać translacji EF Core.</span><span class="sxs-lookup"><span data-stu-id="a50b2-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="a50b2-145">Zazwyczaj bezpieczniej do przekazania wszystkie filtry do metody wykonywania dostępu do danych, a następnie powrót z powrotem kolekcji w pamięci (na przykład<T>) w wyniku.</span><span class="sxs-lookup"><span data-stu-id="a50b2-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="a50b2-146">Podstawowe EF śledzi zmiany na jednostek, który pobiera go z magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="a50b2-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="a50b2-147">Można zapisać zmian śledzonych jednostki, po prostu Wywołaj metodę SaveChanges dla kontekstu DbContext, upewniając się, że jest to samo wystąpienie typu DbContext, które zostało użyte do pobierania jednostki.</span><span class="sxs-lookup"><span data-stu-id="a50b2-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="a50b2-148">Dodawanie i usuwanie jednostek jest bezpośrednio na odpowiedniej właściwości DbSet ponownie w wyniku wywołania metody SaveChanges można wykonać polecenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="a50b2-149">W poniższym przykładzie pokazano, dodawanie, aktualizowanie i usuwanie jednostek z magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="a50b2-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="a50b2-150">Jądro EF obsługuje zarówno synchroniczne i metod asynchronicznych pobieranie i zapisywanie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="a50b2-151">W aplikacji sieci web zaleca się wzorca async/await za pomocą metody asynchroniczne, dzięki czemu wątków serwera sieci web nie są blokowane podczas oczekiwania na zakończenie operacji dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="a50b2-152">Pobieranie danych pokrewne</span><span class="sxs-lookup"><span data-stu-id="a50b2-152">Fetching Related Data</span></span>

<span data-ttu-id="a50b2-153">Gdy EF Core pobiera jednostki, wypełnienie wszystkich właściwości, które są przechowywane bezpośrednio z tego obiektu w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="a50b2-154">Właściwości nawigacji, takie jak listy z powiązanych jednostek nie są wypełnione i może być ich ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a50b2-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="a50b2-155">Dzięki temu EF Core nie pobieranie więcej danych niż jest potrzebny, który jest szczególnie ważne w przypadku aplikacji sieci web, które musi szybko przetwarzają żądania i zwracać odpowiedzi wydajne.</span><span class="sxs-lookup"><span data-stu-id="a50b2-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="a50b2-156">Aby uwzględnić relacje z jednostki przy użyciu *wczesny ładowania*, określ właściwość przy użyciu metody rozszerzenia Include w zapytaniu, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="a50b2-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="a50b2-157">Może zawierać wiele relacji i mogą również obejmować relacje podrzędne za pomocą ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="a50b2-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="a50b2-158">Podstawowe EF wykona pojedynczego zapytania można pobrać Wynikowy zestaw jednostek.</span><span class="sxs-lookup"><span data-stu-id="a50b2-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="a50b2-159">Inną opcją w przypadku ładowania danych pokrewnych jest użycie *jawnego ładowania*.</span><span class="sxs-lookup"><span data-stu-id="a50b2-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="a50b2-160">Jawne ładowania umożliwia ładowanie dodatkowe dane do jednostki, który już został pobrany.</span><span class="sxs-lookup"><span data-stu-id="a50b2-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="a50b2-161">Ponieważ ten proces obejmuje oddzielne żądanie do bazy danych, nie jest zalecane dla aplikacji sieci web, które należy zminimalizować liczbę baz danych rund wprowadzone na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="a50b2-162">*Powolne ładowanie* jest funkcją, która automatycznie ładuje powiązanych danych, ponieważ jest odwoływany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a50b2-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="a50b2-163">Nie jest aktualnie Nieobsługiwany przez podstawowe EF, ale jako z jawnego ładowania powinien zwykle zostać wyłączony dla aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="a50b2-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="a50b2-164">Elastyczne połączenia</span><span class="sxs-lookup"><span data-stu-id="a50b2-164">Resilient Connections</span></span>

<span data-ttu-id="a50b2-165">Zasobów zewnętrznych, takich jak bazy danych SQL co pewien czas mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="a50b2-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="a50b2-166">W wypadku tymczasowej niedostępności aplikacje mogą używać logika ponowień, aby uniknąć, który wywołał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a50b2-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="a50b2-167">Ta metoda jest często określana jako *elastyczności połączenia*.</span><span class="sxs-lookup"><span data-stu-id="a50b2-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="a50b2-168">Można zaimplementować Twojej [własnych ponownie za pomocą wykładniczego wycofywania](https://docs.microsoft.com/azure/architecture/patterns/retry) technika, próbując rety z rośnie wykładniczo czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a50b2-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="a50b2-169">Ta metoda obejmuje fakt, że zasobów w chmurze mogą sporadycznie być niedostępne w krótkich okresach czasu, co spowoduje niepowodzenie niektórych żądań.</span><span class="sxs-lookup"><span data-stu-id="a50b2-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="a50b2-170">Dla bazy danych SQL Azure programu Entity Framework Core zawiera już logiki odporności i ponów próbę połączenia wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="a50b2-171">Jednak musisz włączyć strategia wykonywania programu Entity Framework dla każdego połączenia DbContext, jeśli mają odporność połączeń EF Core.</span><span class="sxs-lookup"><span data-stu-id="a50b2-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="a50b2-172">Na przykład następujący kod na poziomie połączenia EF Core umożliwia elastyczne połączeń z serwerem SQL, które są zwalniane, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="a50b2-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="a50b2-173">Strategie wykonywania i jawnych transakcji przy użyciu BeginTransaction i wielu DbContexts</span><span class="sxs-lookup"><span data-stu-id="a50b2-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="a50b2-174">Po włączeniu ponownych prób w połączeniach EF Core każdej operacji wykonywanych przy użyciu EF Core staje się działania można spróbować ponownie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="a50b2-175">Jeśli wystąpi błąd przejściowy, każdego zapytania i każde wywołanie metody SaveChanges zostanie ponowiona jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="a50b2-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="a50b2-176">Jednak jeśli kod inicjuje transakcji za pomocą BeginTransaction, definiowania grupy działań, które muszą być traktowane jako jednostka — wszystkie elementy wewnątrz transakcji została wycofana, jeśli wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="a50b2-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="a50b2-177">Jeśli próba wykonania tej transakcji, używając strategii wykonywania EF (zasady ponawiania) i obejmują SaveChanges kilka z wielu DbContexts w nim, zostanie wyświetlony następujący wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a50b2-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="a50b2-178">System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a50b2-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="a50b2-179">Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostki można spróbować ponownie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="a50b2-180">Rozwiązanie to ręczne wywoływanie strategia wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="a50b2-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="a50b2-181">Jeśli wystąpi błąd przejściowy, strategia wykonywania zostaną wywołane delegat ponownie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="a50b2-182">Poniższy kod przedstawia sposób wykonania tego podejścia:</span><span class="sxs-lookup"><span data-stu-id="a50b2-182">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="a50b2-183">Jest first DbContext \_catalogContext, a drugi DbContext znajduje się w \_integrationEventLogService obiektu.</span><span class="sxs-lookup"><span data-stu-id="a50b2-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="a50b2-184">Na koniec zatwierdzenia akcji, będzie można wykonać wiele DbContexts i używanie strategii wykonywania EF.</span><span class="sxs-lookup"><span data-stu-id="a50b2-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="a50b2-185">Odwołania — Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a50b2-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="a50b2-186">**Dokumentacja Core EF**</span><span class="sxs-lookup"><span data-stu-id="a50b2-186">**EF Core Docs**</span></span>  
> <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="a50b2-187">**EF rdzeni: Dane dotyczące**</span><span class="sxs-lookup"><span data-stu-id="a50b2-187">**EF Core: Related Data**</span></span>  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="a50b2-188">**Unikaj ładowania opóźnionego jednostek w aplikacjach ASPNET**</span><span class="sxs-lookup"><span data-stu-id="a50b2-188">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="a50b2-189">Podstawowych funkcji EF lub micro ORM?</span><span class="sxs-lookup"><span data-stu-id="a50b2-189">EF Core or micro-ORM?</span></span>

<span data-ttu-id="a50b2-190">Podstawowe EF jest doskonałym wyborem do zarządzania trwałości i w większości przypadków hermetyzuje Szczegóły bazy danych z deweloperzy aplikacji, nie jest to tylko możliwe.</span><span class="sxs-lookup"><span data-stu-id="a50b2-190">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="a50b2-191">Popularne typu open source alternatywą jest [Dapper](https://github.com/StackExchange/Dapper), tak zwane ORM micro.</span><span class="sxs-lookup"><span data-stu-id="a50b2-191">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="a50b2-192">Micro-ORM to lekkie, mniej kompletne narzędzie do mapowania obiektów struktur danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-192">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="a50b2-193">W przypadku Dapper jego celów skupić się na wydajność, a nie w pełni hermetyzując odpowiadającego jej zapytania projekt używa do pobierania i aktualizowania danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-193">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="a50b2-194">Ponieważ go nie jako abstract SQL od dewelopera, Dapper "zbliżonej do systemu operacyjnego" i umożliwia deweloperom pisanie dokładnie operacja dostępu do zapytań, które mają być użyte dla podanych danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-194">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="a50b2-195">Podstawowe EF ma dwie funkcje znaczących zapewnia które oddzieli go od Dapper, ale również dodać do jego zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="a50b2-195">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="a50b2-196">Pierwsza to tłumaczenia z wyrażenia LINQ do SQL.</span><span class="sxs-lookup"><span data-stu-id="a50b2-196">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="a50b2-197">Te tłumaczenia są buforowane, ale mimo tego istnieje narzut przy wykonywaniu ich po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a50b2-197">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="a50b2-198">Drugim jest śledzenia zmian jednostek (dzięki czemu można wygenerować instrukcji update wydajne).</span><span class="sxs-lookup"><span data-stu-id="a50b2-198">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="a50b2-199">To zachowanie można wyłączyć dla określonego zapytania za pomocą rozszerzenia AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="a50b2-199">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="a50b2-200">Podstawowe EF generuje również zapytania SQL, które są zazwyczaj bardzo wydajny i w każdym przypadku doskonale akceptowalne z punktu widzenia wydajności, ale jeśli konieczne drobne kontrolę nad dokładne zapytanie do wykonania, można przekazać niestandardowe SQL (lub procedurę składowaną) przy użyciu EF Podstawowe, zbyt.</span><span class="sxs-lookup"><span data-stu-id="a50b2-200">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="a50b2-201">W takim przypadku nadal Dapper outperforms EF Core, ale tylko nieznacznie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-201">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="a50b2-202">Przedstawia Julie Lerman niektóre dane dotyczące wydajności w jej może artykuł w witrynie MSDN 2016 [Dapper, Entity Framework oraz aplikacje hybrydowe](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="a50b2-202">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="a50b2-203">Dodatkowych testów porównawczych danych o wydajności dla różnych metod dostępu do danych można znaleźć w [Dapper lokacji](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="a50b2-203">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="a50b2-204">Aby zobaczyć, jak składnia Dapper różni się od wartości podstawowej EF, należy wziąć pod uwagę następujące dwie wersje tej samej metody do pobierania listy elementów:</span><span class="sxs-lookup"><span data-stu-id="a50b2-204">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="a50b2-205">Potrzebne do utworzenia bardziej złożonych wykresów obiektów z Dapper, należy napisać samodzielnie skojarzonych kwerend (w przeciwieństwie do dodawania dołączania, jak w programie EF Core).</span><span class="sxs-lookup"><span data-stu-id="a50b2-205">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="a50b2-206">Jest to obsługiwane za pomocą różnych składni, włączając funkcję Multi mapowania umożliwiające mapowania poszczególnych wierszy na wiele obiektów mapowane.</span><span class="sxs-lookup"><span data-stu-id="a50b2-206">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="a50b2-207">Przykładowo podana klasy Post z właściwością właściciela typu użytkownika, następujące instrukcje SQL zwróci wszystkich niezbędnych danych:</span><span class="sxs-lookup"><span data-stu-id="a50b2-207">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="a50b2-208">Każdego zwróconego wiersza zawiera dane użytkownika i Post.</span><span class="sxs-lookup"><span data-stu-id="a50b2-208">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="a50b2-209">Ponieważ dane użytkownika powinien być dołączony do danych Post za pomocą właściwości jego właściciel, jest używana następująca funkcja:</span><span class="sxs-lookup"><span data-stu-id="a50b2-209">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="a50b2-210">Listy pełnego kodu mają być zwracane zbiór wpisów z ich właściwości Owner wypełniony danymi skojarzonego użytkownika mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="a50b2-210">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="a50b2-211">Ponieważ zapewnia hermetyzację mniej Dapper wymaga deweloperzy dowiedzieć się więcej o jak są przechowywane ich dane, jak skutecznie wysyłać zapytania i zapisać więcej kod, aby go pobrać.</span><span class="sxs-lookup"><span data-stu-id="a50b2-211">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="a50b2-212">Po zmianie modelu, a nie po prostu tworzenie nowych migracji (inna funkcja EF Core) i/lub aktualizowanie informacji o mapowaniu w jednym miejscu DbContext, należy zaktualizować każdego zapytania, które jest w pełni funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a50b2-212">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="a50b2-213">Te zapytania ma nie gwarancje czas kompilacji, w związku z ich mogą być dzielone w czasie wykonywania w odpowiedzi na zmiany do modelu lub bazy danych, co utrudnia szybko wykrywać błędy.</span><span class="sxs-lookup"><span data-stu-id="a50b2-213">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="a50b2-214">W zamian za te kompromisy Dapper oferuje bardzo duża wydajność.</span><span class="sxs-lookup"><span data-stu-id="a50b2-214">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="a50b2-215">Dla większości aplikacji, a większość części prawie wszystkie aplikacje EF Core oferuje akceptowalną wydajność.</span><span class="sxs-lookup"><span data-stu-id="a50b2-215">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="a50b2-216">W związku z tym korzyści produktywności deweloperów prawdopodobnie przeważają jego zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="a50b2-216">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="a50b2-217">Dla zapytania, które mogą korzystać z pamięci podręcznej, rzeczywiste zapytanie może można wykonywać tylko niewielki procent czasu, wprowadzenie niewielkich zapytania moot różnic w wydajności.</span><span class="sxs-lookup"><span data-stu-id="a50b2-217">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="a50b2-218">Bazy danych SQL lub NoSQL</span><span class="sxs-lookup"><span data-stu-id="a50b2-218">SQL or NoSQL</span></span>

<span data-ttu-id="a50b2-219">Tradycyjnie relacyjnych baz danych, takich jak SQL Server ma zdominowany witryny marketplace w celu przechowywania danych, ale nie są dostępne rozwiązania tylko.</span><span class="sxs-lookup"><span data-stu-id="a50b2-219">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="a50b2-220">Bazy danych NoSQL, takich jak [MongoDB](https://www.mongodb.com/what-is-mongodb) oferują różne podejścia do przechowywania obiektów.</span><span class="sxs-lookup"><span data-stu-id="a50b2-220">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="a50b2-221">Zamiast obiektów mapowania tabel oraz wiersze, inną opcją jest serializować wykres całego obiektu, a następnie zapisz wynik.</span><span class="sxs-lookup"><span data-stu-id="a50b2-221">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="a50b2-222">Zalety tego podejścia są co najmniej początkowo prostoty i wydajności.</span><span class="sxs-lookup"><span data-stu-id="a50b2-222">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="a50b2-223">Jest oczywiście łatwiejsze do przechowywania pojedynczego serializacji obiektu z kluczem niż aby Rozłóż obiekt na wiele tabel z relacjami i aktualizacji oraz wiersze, które zostały zmienione od ostatniego obiektu pobrany z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-223">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="a50b2-224">Podobnie Pobieranie i deserializację pojedynczego obiektu z magazynu opartego na kluczach jest zwykle szybsze i prostsze niż złożonych sprzężeń lub wiele zapytań bazy danych, wymagane pełni utworzenie tego samego obiektu z relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-224">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="a50b2-225">Brak blokad lub transakcji lub stałego schematu powoduje bazy danych NoSQL bardzo nadającymi się do skalowania obejmującego wiele maszyn, obsługa bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-225">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="a50b2-226">Z drugiej strony bazy danych NoSQL (zwykle są one nazywane) mają swoje wady.</span><span class="sxs-lookup"><span data-stu-id="a50b2-226">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="a50b2-227">Relacyjnych baz danych użyj normalizacji, aby wymusić spójność i uniknąć duplikowania danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-227">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="a50b2-228">Zmniejsza całkowity rozmiar bazy danych i zapewnia, że aktualizacje do udostępnionych danych są dostępne natychmiast w całej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-228">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="a50b2-229">Relacyjnej bazy danych tabeli adresów może odwołać się do kraju tabeli przez identyfikator, taki sposób, że jeśli zmieniono nazwę kraju, rekordów adresów będą korzystać z aktualizacji bez sobą konieczności aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-229">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="a50b2-230">Jednak w bazie danych NoSQL adres i skojarzone kraj może można serializować wiele obiektów przechowywanych w ramach.</span><span class="sxs-lookup"><span data-stu-id="a50b2-230">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="a50b2-231">Aktualizacja nazwy kraju wymagają wszystkie takie obiekty zaktualizowane, zamiast pojedynczy wiersz.</span><span class="sxs-lookup"><span data-stu-id="a50b2-231">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="a50b2-232">Relacyjnych baz danych można również zapewnienia integralności relacyjne wymuszania reguł, takich jak klucze obce.</span><span class="sxs-lookup"><span data-stu-id="a50b2-232">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="a50b2-233">Bazy danych NoSQL nie oferują zwykle takie ograniczenia dotyczące ich danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-233">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="a50b2-234">Inny złożoności musi uwzględniać bazy danych NoSQL jest przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-234">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="a50b2-235">Po zmianie właściwości obiektów, nie można możliwość wykonania deserializacji do poprzednich wersji, które były przechowywane.</span><span class="sxs-lookup"><span data-stu-id="a50b2-235">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="a50b2-236">W związku z tym aby był zgodny ze schematem nowe należy zaktualizować wszystkich istniejących obiektów serializowanych wersję (poprzedni) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a50b2-236">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="a50b2-237">To nie jest koncepcyjnie różnych z relacyjnej bazy danych, w przypadku, gdy zmiany schematu czasami wymagają skryptów aktualizacji lub mapowania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-237">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="a50b2-238">Jednak liczbę wpisów, które muszą zostać zmodyfikowane często jest znacznie większa w ujęciu NoSQL, ponieważ istnieje więcej zduplikowanie danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-238">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="a50b2-239">Jest to możliwe w bazach danych NoSQL, aby przechowywać wiele wersji obiektów, zwykle nie obsługują coś stałego schematu relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-239">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="a50b2-240">Jednak w takim przypadku kod aplikacji należy konta istnienie poprzednie wersje obiektów oraz dodawanie dodatkowej złożoności.</span><span class="sxs-lookup"><span data-stu-id="a50b2-240">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="a50b2-241">Zwykle nie Wymuszaj bazy danych NoSQL [kwasu](https://en.wikipedia.org/wiki/ACID), co oznacza, że mają one korzyści skalowalność i wydajność za pośrednictwem relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-241">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="a50b2-242">Są one odpowiednie do bardzo dużych zestawów danych i obiektów, które nie są odpowiednie do magazynu w strukturach znormalizowane tabeli.</span><span class="sxs-lookup"><span data-stu-id="a50b2-242">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="a50b2-243">To nie ma powodu Dlaczego pojedynczej aplikacji nie może korzystać z obu relacyjnych i bazy danych NoSQL, przy użyciu których najlepiej nadaje się.</span><span class="sxs-lookup"><span data-stu-id="a50b2-243">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="a50b2-244">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="a50b2-244">Azure DocumentDB</span></span>

<span data-ttu-id="a50b2-245">Azure DocumentDB to w pełni zarządzana usługa bazy danych NoSQL, oferująca magazynu oparte na chmurze dane bez schematu.</span><span class="sxs-lookup"><span data-stu-id="a50b2-245">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="a50b2-246">Usługa DocumentDB jest skompilowany dla szybkie przetwarzanie, przewidywalną wydajność, wysoką dostępność, elastyczne skalowanie i dystrybucji globalnego.</span><span class="sxs-lookup"><span data-stu-id="a50b2-246">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="a50b2-247">Mimo iż bazy danych NoSQL, deweloperzy mogą używać znane i zaawansowanych możliwości zapytań SQL na dane JSON.</span><span class="sxs-lookup"><span data-stu-id="a50b2-247">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="a50b2-248">Wszystkie zasoby w usłudze DocumentDB są przechowywane jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="a50b2-248">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="a50b2-249">Zasoby są zarządzane jako *elementów*, które są dokumentami zawierający metadane, i *źródła*, które są kolekcjami elementów.</span><span class="sxs-lookup"><span data-stu-id="a50b2-249">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="a50b2-250">Rysunek 8-2 przedstawiono relacje między różnymi zasobami usługi DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="a50b2-250">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![Hierarchiczna relacja między zasobami w usłudze DocumentDB, bazy danych NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="a50b2-252">**Rysunek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="a50b2-252">**Figure 8-2.**</span></span> <span data-ttu-id="a50b2-253">Organizacji zasobów usługi DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="a50b2-253">DocumentDB resource organization.</span></span>

<span data-ttu-id="a50b2-254">Język zapytań usługi DocumentDB jest proste, ale zaawansowanym interfejsem do wykonywania zapytań dokumentów JSON.</span><span class="sxs-lookup"><span data-stu-id="a50b2-254">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="a50b2-255">Język obsługuje podzbiór gramatyki ANSI SQL i dodaje głęboką integrację obiektów, tablic, konstrukcji obiektów i wywołania funkcji JavaScript.</span><span class="sxs-lookup"><span data-stu-id="a50b2-255">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="a50b2-256">**Odwołania — usługi DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="a50b2-256">**References – DocumentDB**</span></span>

-   <span data-ttu-id="a50b2-257">Introduction\ usługi DocumentDB</span><span class="sxs-lookup"><span data-stu-id="a50b2-257">DocumentDB Introduction\\</span></span>
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="a50b2-258">Inne opcje trwałości</span><span class="sxs-lookup"><span data-stu-id="a50b2-258">Other Persistence Options</span></span>

<span data-ttu-id="a50b2-259">W dodatku relacyjnych i opcje magazynu NoSQL aplikacje platformy ASP.NET Core mogą używać usługi Azure Storage do przechowywania różnych formatów danych i plików w sposób oparte na chmurze, skalowalnej.</span><span class="sxs-lookup"><span data-stu-id="a50b2-259">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="a50b2-260">Usługa Azure Storage jest skalowalna na ogromną skalę, aby rozpocząć się niewielkich ilości danych i skali do przechowywania setki lub terabajtów, jeśli aplikacja wymaga przechowywania.</span><span class="sxs-lookup"><span data-stu-id="a50b2-260">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="a50b2-261">Usługa Azure Storage obsługuje cztery rodzaje danych:</span><span class="sxs-lookup"><span data-stu-id="a50b2-261">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="a50b2-262">Magazyn obiektów blob niestrukturalnych tekst lub binarny magazynowania, również nazywany magazynem obiektów.</span><span class="sxs-lookup"><span data-stu-id="a50b2-262">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="a50b2-263">Magazyn tabel dla zestawów strukturalnych danych dostępny za pośrednictwem kluczy wiersza.</span><span class="sxs-lookup"><span data-stu-id="a50b2-263">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="a50b2-264">Magazyn kolejek niezawodnej na podstawie kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a50b2-264">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="a50b2-265">Magazyn plików udostępnionych plików dostępu między maszynami wirtualnymi Azure i aplikacji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-265">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="a50b2-266">**Odwołania — usługa Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="a50b2-266">**References – Azure Storage**</span></span>

-   <span data-ttu-id="a50b2-267">Introduction\ magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="a50b2-267">Azure Storage Introduction\\</span></span>
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="a50b2-268">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="a50b2-268">Caching</span></span>

<span data-ttu-id="a50b2-269">W aplikacji sieci web należy wykonać wszystkie żądania sieci web w możliwie jak najszybciej.</span><span class="sxs-lookup"><span data-stu-id="a50b2-269">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="a50b2-270">Jest jednym ze sposobów osiągnięcia tego ograniczenia liczby wywołań zewnętrznego serwera należy wykonać w celu wykonania żądania.</span><span class="sxs-lookup"><span data-stu-id="a50b2-270">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="a50b2-271">Buforowanie obejmuje przechowywanie kopii danych na serwerze (lub innego magazynu danych, czyli więcej łatwo proszeni niż źródła danych).</span><span class="sxs-lookup"><span data-stu-id="a50b2-271">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="a50b2-272">Aplikacje sieci Web i szczególnie aplikacji z systemem innym niż SPA tradycyjnych sieci web, potrzebne do tworzenia cały interfejs użytkownika z każdym żądaniem.</span><span class="sxs-lookup"><span data-stu-id="a50b2-272">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="a50b2-273">To często konieczne jest wprowadzenie wiele zapytań tej samej bazy danych wielokrotnie z żądania jednego użytkownika do następnego.</span><span class="sxs-lookup"><span data-stu-id="a50b2-273">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="a50b2-274">W większości przypadków te dane zmiany rzadko, dlatego wyboru stale żądania z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-274">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="a50b2-275">Platformy ASP.NET Core obsługuje buforowanie odpowiedzi do buforowania całe strony i buforowania danych, służącej do zapewnienia jeszcze bardziej precyzyjnej zachowanie buforowania.</span><span class="sxs-lookup"><span data-stu-id="a50b2-275">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="a50b2-276">Podczas implementowania buforowania, ważne jest należy wziąć pod uwagę separacji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-276">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="a50b2-277">Unikaj implementacji logiki buforowania w logice dostępu do danych lub w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a50b2-277">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="a50b2-278">Zamiast tego Hermetyzowanie buforowanie własnych klas i zarządzać jego zachowanie przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a50b2-278">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="a50b2-279">Następuje Open/zamknięty i zasad pojedynczego odpowiedzialność i ułatwić zarządzanie, jak używać buforowania w aplikacji jako ich przyrostu.</span><span class="sxs-lookup"><span data-stu-id="a50b2-279">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="a50b2-280">Buforowanie odpowiedzi platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a50b2-280">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="a50b2-281">Platformy ASP.NET Core obsługuje dwa poziomy buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a50b2-281">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="a50b2-282">Pierwszy poziom nie będzie buforować niczego na serwerze, ale dodaje nagłówki HTTP, które poinstruować klienci i serwery proxy do odpowiedzi z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a50b2-282">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="a50b2-283">Ten sposób jest implementowany przez dodanie atrybutu ResponseCache do poszczególnych kontrolerów i akcji:</span><span class="sxs-lookup"><span data-stu-id="a50b2-283">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

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

<span data-ttu-id="a50b2-284">Oprogramowanie pośredniczące buforowanie odpowiedzi będą automatycznie buforowane odpowiedzi na podstawie zestawu warunków, które można dostosować.</span><span class="sxs-lookup"><span data-stu-id="a50b2-284">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="a50b2-285">Domyślnie tylko 200 odpowiedzi (OK) za pośrednictwem metody GET lub HEAD są buforowane.</span><span class="sxs-lookup"><span data-stu-id="a50b2-285">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="a50b2-286">Ponadto żądania musi mieć odpowiedzi z Cache-Control: nagłówek publicznych i nie może zawierać nagłówki autoryzacji lub Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-286">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="a50b2-287">Zobacz [pełną listę buforowania warunki używane przez oprogramowanie pośredniczące buforowanie odpowiedzi](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="a50b2-287">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="a50b2-288">Buforowanie danych</span><span class="sxs-lookup"><span data-stu-id="a50b2-288">Data Caching</span></span>

<span data-ttu-id="a50b2-289">Zamiast (lub oprócz) buforowania odpowiedzi z sieci web pełną, można buforować wyniki poszczególnych danych zapytań.</span><span class="sxs-lookup"><span data-stu-id="a50b2-289">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="a50b2-290">W tym celu można użyć w ramach buforowania pamięci na serwerze sieci web, lub [rozproszonej pamięci podręcznej](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="a50b2-290">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="a50b2-291">W tej sekcji przedstawiono sposób wykonania w pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="a50b2-291">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="a50b2-292">Dodawanie obsługi pamięci (lub rozproszonych) buforowanie w ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="a50b2-292">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="a50b2-293">Pamiętaj dodać pakiet Microsoft.Extensions.Caching.Memory NuGet również.</span><span class="sxs-lookup"><span data-stu-id="a50b2-293">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="a50b2-294">Po dodaniu usługi wszędzie tam, gdzie chcesz uzyskać dostęp do pamięci podręcznej możesz poprosić IMemoryCache za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="a50b2-294">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="a50b2-295">W tym przykładzie CachedCatalogService jest przy użyciu wzorca projektowego serwera Proxy (lub Dekoratora), zapewniając alternatywną implementację ICatalogService, która kontroluje dostęp do (lub dodaje zachowanie do) ta implementacja CatalogService.</span><span class="sxs-lookup"><span data-stu-id="a50b2-295">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="a50b2-296">Aby skonfigurować aplikację, aby używać pamięci podręcznej wersja usługi, ale nadal Zezwalaj usłudze można pobrać wystąpienia CatalogService musi się on w swoich konstruktorach, należy dodać następujące w ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="a50b2-296">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="a50b2-297">Dzięki temu w miejscu wywołania bazy danych można pobrać danych katalogu zostanie zastosowane tylko raz na minutę, a nie na każde żądanie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-297">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="a50b2-298">W zależności od ruchu w witrynie może to mieć bardzo znaczący wpływ na liczbę zapytań do bazy danych i czas ładowania strony, strony głównej, który obecnie jest zależna od wszystkich trzech zapytań udostępniane przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="a50b2-298">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="a50b2-299">Problem, który pojawia się po zaimplementowaniu buforowanie jest *starych danych* — oznacza to, które uległy zmianie w źródle, ale wersja nieaktualny pozostaje w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a50b2-299">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="a50b2-300">Prosty sposób, aby zminimalizować ten problem jest użyj małych czas trwania pamięci podręcznej, ponieważ zajęty aplikacji jest ograniczony dodatkową korzyścią rozszerzanie długości, które dane są buforowane.</span><span class="sxs-lookup"><span data-stu-id="a50b2-300">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="a50b2-301">Rozważmy na przykład strona, która sprawia, że kwerenda pojedynczej bazy danych, a wymagany jest 10 razy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="a50b2-301">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="a50b2-302">Jeśli ta strona jest buforowana przez jedną minutę, spowoduje liczba zapytania bazy danych na minutę do usunięcia z 600 zmniejszenie 99.8% 1.</span><span class="sxs-lookup"><span data-stu-id="a50b2-302">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="a50b2-303">Zamiast tego czas buforowania dokonane jedną godzinę, ogólne zmniejszenie wynosi 99.997%, ale teraz prawdopodobieństwo i potencjalne wiek starych danych zarówno zwiększa się znacznie.</span><span class="sxs-lookup"><span data-stu-id="a50b2-303">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="a50b2-304">Innym rozwiązaniem jest aktywne, po zaktualizowaniu danych, które zawierają, Usuń wpisy w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a50b2-304">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="a50b2-305">Każdy wpis poszczególnych może zostać usunięty, jeśli znane jest kluczem:</span><span class="sxs-lookup"><span data-stu-id="a50b2-305">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="a50b2-306">Jeśli aplikacja udostępnia funkcje aktualizowania wpisów, które go przechowuje w pamięci podręcznej, należy usunąć odpowiednie wpisy w pamięci podręcznej w kodzie, który wykonuje aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="a50b2-306">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="a50b2-307">Czasami może być wiele różnych wpisów, które są zależne od określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a50b2-307">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="a50b2-308">W takim przypadku można go utworzyć zależności między wpisy w pamięci podręcznej, za pomocą CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="a50b2-308">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="a50b2-309">Z CancellationChangeToken można jednocześnie wygaśnie wiele wpisów pamięci podręcznej przez token anulowania.</span><span class="sxs-lookup"><span data-stu-id="a50b2-309">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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
<span data-ttu-id="a50b2-310">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a50b2-310">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
