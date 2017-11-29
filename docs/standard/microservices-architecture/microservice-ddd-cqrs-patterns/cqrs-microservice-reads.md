---
title: "Implementowanie odczyty/kwerendy w mikrousługi CQRS"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odczyty/kwerendy w mikrousługi CQRS"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="c45be-104">Implementowanie odczyty/kwerendy w mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="c45be-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="c45be-105">Odczyty/zapytań porządkowania mikrousługi z aplikacji odwołanie eShopOnContainers implementuje zapytania niezależnie od DDD modelu i obszar transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c45be-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="c45be-106">Wykonano głównie, ponieważ znacząco różnią wymagań dla zapytań i transakcji.</span><span class="sxs-lookup"><span data-stu-id="c45be-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="c45be-107">Zapisy wykonania transakcji, które muszą być zgodne z logiką domeny.</span><span class="sxs-lookup"><span data-stu-id="c45be-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="c45be-108">Z drugiej strony, zapytania, są idempotentności i być rozdzielone od zasad domeny.</span><span class="sxs-lookup"><span data-stu-id="c45be-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="c45be-109">Podejście jest proste, jak pokazano na rysunku 9-3.</span><span class="sxs-lookup"><span data-stu-id="c45be-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="c45be-110">Interfejs API zaimplementowano przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury (na przykład micro ORM, takich jak Dapper) i zwracanie dynamiczne ViewModels w zależności od potrzeb aplikacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c45be-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="c45be-111">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="c45be-111">**Figure 9-3**.</span></span> <span data-ttu-id="c45be-112">Najprostsza metoda zapytań w mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="c45be-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="c45be-113">Jest to najprostsza metoda możliwe w dla zapytań.</span><span class="sxs-lookup"><span data-stu-id="c45be-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="c45be-114">Definicje kwerendy w bazie danych i zwracać dynamiczne ViewModel, oparty na bieżąco dla każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="c45be-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="c45be-115">Ponieważ zapytania są idempotentności, nie zmieni ich danych niezależnie od tego, ile razy wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="c45be-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="c45be-116">W związku z tym nie trzeba być ograniczone przez dowolnego wzorzec DDD używany po stronie transakcyjnych, takie jak wartości zagregowanych i innych wzorcach i dlatego zapytania są oddzielone od obszaru transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c45be-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="c45be-117">Po prostu zapytania do bazy danych, która wymaga interfejsu użytkownika i zwracać ViewModel dynamiczne, które muszą być statycznie zdefiniowany dowolnego miejsca (nie klasy dla ViewModels) z wyjątkiem w instrukcji SQL, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="c45be-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="c45be-118">Ponieważ jest to prosty podejście, kod wymagany dla strony zapytania (takich jak kodu za pomocą micro, takich jak ORM [Dapper](https://github.com/StackExchange/Dapper)) może być zaimplementowany [w tym samym projekcie interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="c45be-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="c45be-119">Na rysunku 9-4 przedstawiono to.</span><span class="sxs-lookup"><span data-stu-id="c45be-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="c45be-120">Zapytania są definiowane w **Ordering.API** mikrousługi projektu w ramach rozwiązania eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c45be-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="c45be-121">**Rysunek 9-4**.</span><span class="sxs-lookup"><span data-stu-id="c45be-121">**Figure 9-4**.</span></span> <span data-ttu-id="c45be-122">Zapytania w mikrousługi porządkowanie w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c45be-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="c45be-123">Przy użyciu ViewModels celowo dla aplikacji klienta, niezależnie od ograniczeń modelu domeny</span><span class="sxs-lookup"><span data-stu-id="c45be-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="c45be-124">Ponieważ zapytania są wykonywane do uzyskiwania danych wymaganych przez aplikacje klienckie, zwrócony typ można w szczególności wprowadzone dla klientów, na podstawie danych zwróconych przez zapytania.</span><span class="sxs-lookup"><span data-stu-id="c45be-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="c45be-125">Te modele lub obiekty Transfer danych (DTOs), są nazywane ViewModels.</span><span class="sxs-lookup"><span data-stu-id="c45be-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="c45be-126">Zwrócone dane (ViewModel) może być wynikiem sprzężenia danych z wielu obiektów lub tabele w bazie danych, lub nawet Agreguje wiele zdefiniowanych w modelu domeny dla transakcyjnego obszaru.</span><span class="sxs-lookup"><span data-stu-id="c45be-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="c45be-127">W takim przypadku ponieważ tworzenia kwerend niezależnie od modelu domeny, agregacje granic i ograniczenia całkowicie są ignorowane, a wolnych do badania żadnych tabel i kolumn, który może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="c45be-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="c45be-128">Ta metoda zapewnia dużą elastyczność i wydajność dla deweloperów, tworzenie lub aktualizowanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="c45be-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="c45be-129">ViewModels może być statyczne typy zdefiniowane w klasach.</span><span class="sxs-lookup"><span data-stu-id="c45be-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="c45be-130">Lub też można tworzyć dynamicznie na podstawie kwerend wykonywana (jak jest implementowane w porządkowania mikrousługi), który jest bardzo elastyczne dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="c45be-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="c45be-131">Przy użyciu Dapper jako micro ORM do wykonywania zapytań</span><span class="sxs-lookup"><span data-stu-id="c45be-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="c45be-132">Podczas wykonywania zapytań, można użyć dowolnego micro ORM, Entity Framework Core lub nawet zwykły ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c45be-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="c45be-133">W przykładowej aplikacji do porządkowania mikrousługi w eShopOnContainers jako przykład popularnych ORM micro wybrano Dapper.</span><span class="sxs-lookup"><span data-stu-id="c45be-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="c45be-134">Można go uruchomić zwykły kwerend SQL o bardzo dużej wydajności, ponieważ jest bardzo małe framework.</span><span class="sxs-lookup"><span data-stu-id="c45be-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="c45be-135">Dapper można napisać zapytanie SQL, które mogą uzyskać dostęp i dołączyć wiele tabel.</span><span class="sxs-lookup"><span data-stu-id="c45be-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="c45be-136">Dapper jest projekt typu open source (utworzony przez Sam szafran oryginału) i jest częścią bloki konstrukcyjne, używane w [przepełnienie stosu](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="c45be-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="c45be-137">Aby użyć Dapper, wystarczy zainstalować go za pomocą [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="c45be-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="c45be-138">Należy również dodać za pomocą instrukcji tak kod ma dostęp do metody Dapper rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c45be-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="c45be-139">Użycie Dapper w kodzie, możesz bezpośrednio użyć dostępne w przestrzeni nazw System.Data.SqlClient klasy SqlClient.</span><span class="sxs-lookup"><span data-stu-id="c45be-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="c45be-140">Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerza klasy SqlClient można po prostu uruchamianie zapytań w sposób prosty i wydajność.</span><span class="sxs-lookup"><span data-stu-id="c45be-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="c45be-141">ViewModels dynamiczną i statyczną</span><span class="sxs-lookup"><span data-stu-id="c45be-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="c45be-142">Jak pokazano w poniższym kodzie z porządkowania mikrousługi, większość ViewModels zwrócony przez zapytania są zaimplementowane jako *dynamiczne*.</span><span class="sxs-lookup"><span data-stu-id="c45be-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="c45be-143">Oznacza to, że podzbiór atrybutów, które mają być zwracane jest oparty na samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="c45be-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="c45be-144">Po dodaniu nowej kolumny do zapytania, lub Dołącz do tych danych jest dynamicznie dodawane do zwrócony ViewModel.</span><span class="sxs-lookup"><span data-stu-id="c45be-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="c45be-145">Takie podejście zmniejsza potrzebę modyfikowania zapytań w odpowiedzi na aktualizacje odpowiedni model danych, co ta podejście do projektowania, elastyczne i bardziej odporne na przyszłe zmiany.</span><span class="sxs-lookup"><span data-stu-id="c45be-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
  }
}
```

<span data-ttu-id="c45be-146">Istotne jest, czy przy użyciu typu dynamicznego, zwracane zbierania danych będzie można dynamicznie złożonego jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="c45be-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="c45be-147">Dla większości zapytań nie trzeba wstępnie DTO lub ViewModel klasy, co sprawia, że ich kodowania proste i produktywności.</span><span class="sxs-lookup"><span data-stu-id="c45be-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="c45be-148">Można jednak wstępnie ViewModels (na przykład wstępnie zdefiniowanych DTOs), jeśli chcesz mieć ViewModels z bardziej ograniczony w definicji jako umów.</span><span class="sxs-lookup"><span data-stu-id="c45be-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="c45be-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="c45be-149">Additional resources</span></span>

-   <span data-ttu-id="c45be-150">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="c45be-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="c45be-151">**Julie Lerman. Punkty danych - Dapper, Entity Framework i aplikacji hybrydowych (artykuł MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="c45be-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="c45be-152">*https://msdn.microsoft.com/en-us/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="c45be-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c45be-153">[Poprzednie] (eshoponcontainers-cqrs-ddd-microservice.md) [dalej] (ddd ukierunkowane microservice.md)</span><span class="sxs-lookup"><span data-stu-id="c45be-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
