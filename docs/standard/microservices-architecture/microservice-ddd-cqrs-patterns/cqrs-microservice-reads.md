---
title: "Implementowanie odczyty/kwerendy w mikrousługi CQRS"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odczyty/kwerendy w mikrousługi CQRS"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ca9bcefb317d2b3c7c225b773918ca4a2484cb8f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="552f8-104">Implementowanie odczyty/kwerendy w mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="552f8-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="552f8-105">Odczyty/zapytań porządkowania mikrousługi z aplikacji odwołanie eShopOnContainers implementuje zapytania niezależnie od DDD modelu i obszar transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="552f8-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="552f8-106">Wykonano głównie, ponieważ znacząco różnią wymagań dla zapytań i transakcji.</span><span class="sxs-lookup"><span data-stu-id="552f8-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="552f8-107">Zapisy wykonania transakcji, które muszą być zgodne z logiką domeny.</span><span class="sxs-lookup"><span data-stu-id="552f8-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="552f8-108">Z drugiej strony, zapytania, są idempotentności i być rozdzielone od zasad domeny.</span><span class="sxs-lookup"><span data-stu-id="552f8-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="552f8-109">Podejście jest proste, jak pokazano na rysunku 9-3.</span><span class="sxs-lookup"><span data-stu-id="552f8-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="552f8-110">Interfejs API zaimplementowano przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takich jak micro relacyjne mapowania ORM (Object) jak Dapper i zwracanie dynamiczne ViewModels w zależności od potrzeb aplikacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="552f8-110">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="552f8-111">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="552f8-111">**Figure 9-3**.</span></span> <span data-ttu-id="552f8-112">Najprostsza metoda zapytań w mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="552f8-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="552f8-113">Jest to najprostsza metoda możliwe w dla zapytań.</span><span class="sxs-lookup"><span data-stu-id="552f8-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="552f8-114">Definicje kwerendy w bazie danych i zwracać dynamiczne ViewModel, oparty na bieżąco dla każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="552f8-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="552f8-115">Ponieważ zapytania są idempotentności, zmienią danych niezależnie od tego, ile razy wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="552f8-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="552f8-116">W związku z tym nie trzeba być ograniczone przez dowolnego wzorzec DDD używany po stronie transakcyjnych, takie jak wartości zagregowanych i innych wzorcach i dlatego zapytania są oddzielone od obszaru transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="552f8-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="552f8-117">Po prostu zapytania do bazy danych, która wymaga interfejsu użytkownika i zwracać ViewModel dynamiczne, które muszą być statycznie zdefiniowany dowolnego miejsca (nie klasy dla ViewModels) z wyjątkiem w instrukcji SQL, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="552f8-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="552f8-118">Ponieważ jest to prosty podejście, kod wymagany dla strony zapytania (takich jak kodu za pomocą micro, takich jak ORM [Dapper](https://github.com/StackExchange/Dapper)) może być zaimplementowany [w tym samym projekcie interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="552f8-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="552f8-119">Na rysunku 9-4 przedstawiono to.</span><span class="sxs-lookup"><span data-stu-id="552f8-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="552f8-120">Zapytania są definiowane w **Ordering.API** mikrousługi projektu w ramach rozwiązania eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="552f8-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="552f8-121">**Rysunek 9-4**.</span><span class="sxs-lookup"><span data-stu-id="552f8-121">**Figure 9-4**.</span></span> <span data-ttu-id="552f8-122">Zapytania w mikrousługi porządkowanie w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="552f8-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="552f8-123">Przy użyciu ViewModels celowo dla aplikacji klienta, niezależnie od ograniczeń modelu domeny</span><span class="sxs-lookup"><span data-stu-id="552f8-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="552f8-124">Ponieważ zapytania są wykonywane do uzyskiwania danych wymaganych przez aplikacje klienckie, zwrócony typ można w szczególności wprowadzone dla klientów, na podstawie danych zwróconych przez zapytania.</span><span class="sxs-lookup"><span data-stu-id="552f8-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="552f8-125">Te modele lub obiekty Transfer danych (DTOs), są nazywane ViewModels.</span><span class="sxs-lookup"><span data-stu-id="552f8-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="552f8-126">Zwrócone dane (ViewModel) może być wynikiem sprzężenia danych z wielu obiektów lub tabele w bazie danych, lub nawet Agreguje wiele zdefiniowanych w modelu domeny dla transakcyjnego obszaru.</span><span class="sxs-lookup"><span data-stu-id="552f8-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="552f8-127">W takim przypadku ponieważ tworzenia kwerend niezależnie od modelu domeny, agregacje granic i ograniczenia całkowicie są ignorowane, a możesz go dowolnie zapytania żadnych tabel i kolumn, który może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="552f8-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="552f8-128">Ta metoda zapewnia dużą elastyczność i wydajność dla deweloperów, tworzenie lub aktualizowanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="552f8-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="552f8-129">ViewModels może być statyczne typy zdefiniowane w klasach.</span><span class="sxs-lookup"><span data-stu-id="552f8-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="552f8-130">Lub też można tworzyć dynamicznie na podstawie kwerend wykonywana (jak jest implementowane w porządkowania mikrousługi), który jest bardzo elastyczne dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="552f8-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="552f8-131">Przy użyciu Dapper jako micro ORM do wykonywania zapytań</span><span class="sxs-lookup"><span data-stu-id="552f8-131">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="552f8-132">Podczas wykonywania zapytań, można użyć dowolnego micro ORM, Entity Framework Core lub nawet zwykły ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="552f8-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="552f8-133">W przykładowej aplikacji Dapper został wybrany do porządkowania mikrousługi w eShopOnContainers jako przykład popularnych ORM micro.</span><span class="sxs-lookup"><span data-stu-id="552f8-133">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="552f8-134">Można go uruchomić zwykły kwerend SQL o bardzo dużej wydajności, ponieważ jest bardzo małe framework.</span><span class="sxs-lookup"><span data-stu-id="552f8-134">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="552f8-135">Dapper można napisać zapytanie SQL, które mogą uzyskać dostęp i dołączyć wiele tabel.</span><span class="sxs-lookup"><span data-stu-id="552f8-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="552f8-136">Dapper to projekt typu open source (utworzony przez Sam szafran oryginału) i jest częścią bloki konstrukcyjne, używane w [przepełnienie stosu](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="552f8-136">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="552f8-137">Aby użyć Dapper, wystarczy zainstalować go za pomocą [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="552f8-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="552f8-138">Należy również dodać za pomocą instrukcji tak kod ma dostęp do metody Dapper rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="552f8-138">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="552f8-139">W przypadku użycia Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> dostępne w klasie <xref:System.Data.SqlClient> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="552f8-139">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="552f8-140">Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasy, można po prostu wykonać zapytania w sposób prosty i wydajność.</span><span class="sxs-lookup"><span data-stu-id="552f8-140">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="552f8-141">Dynamiczne i ViewModels statyczne</span><span class="sxs-lookup"><span data-stu-id="552f8-141">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="552f8-142">W przypadku powrotu ViewModels z po stronie serwera do klienta aplikacji, należy zwrócić uwagę tych ViewModels jako DTOs, które mogą być różne do jednostek domeny wewnętrznej modelu jednostki, ponieważ wymaga aplikacji klienckiej sposobu wstrzymywania ViewModels danych.</span><span class="sxs-lookup"><span data-stu-id="552f8-142">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="552f8-143">W związku z tym w wielu przypadkach możesz agregować dane pochodzące z wielu domen, jednostek i tworzą ViewModels dokładnie według jak aplikacja, klient musi danych.</span><span class="sxs-lookup"><span data-stu-id="552f8-143">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="552f8-144">Te ViewModels lub DTOs można definiować jawnie (jako klasy symbol zastępczy danych) jak [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) klasy w późniejszym fragment kodu, lub po prostu może zwrócić ViewModels dynamicznych lub dynamiczne DTOs po prostu na podstawie atrybutów zwracane przez Twojego zapytania jako `dynamic` typu.</span><span class="sxs-lookup"><span data-stu-id="552f8-144">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="552f8-145">ViewModel jako typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="552f8-145">ViewModel as dynamic type</span></span>

<span data-ttu-id="552f8-146">Jak pokazano w poniższym kodzie, ViewModel może być bezpośrednio zwracany przez zapytania zwracając typu dynamicznego wewnętrznie na podstawie atrybutów zwróconych przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="552f8-146">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="552f8-147">Oznacza to, że podzbiór atrybutów, które mają być zwracane jest oparty na samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="552f8-147">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="552f8-148">W związku z tym po dodaniu nowej kolumny do zapytania, lub Dołącz do tych danych jest dynamicznie dodawane do zwrócony ViewModel.</span><span class="sxs-lookup"><span data-stu-id="552f8-148">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

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

<span data-ttu-id="552f8-149">Istotne jest, czy przy użyciu typu dynamicznego, zwracane zbierania danych są dynamicznie montowane jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="552f8-149">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="552f8-150">*Specjaliści:* takie podejście ogranicza potrzebę modyfikowanie klas statycznych ViewModel po zaktualizowaniu zdanie SQL kwerendy, co ta podejście do projektowania bardzo elastyczne podczas kodowania, proste i szybkie podlegać ewolucji w odniesieniu do przyszłych zmian.</span><span class="sxs-lookup"><span data-stu-id="552f8-150">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="552f8-151">*Cons:* w długim okresie, typy dynamiczne można mają negatywny wpływ na czytelność i mieć wpływ na zgodność usługi z aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="552f8-151">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="552f8-152">Ponadto oprogramowanie pośredniczące oprogramowanie, takie jak Swagger nie może dostarczyć poziomu dokumentacji na typy zwracane Jeśli za pomocą zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="552f8-152">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="552f8-153">ViewModel jako wstępnie zdefiniowanych klas DTO</span><span class="sxs-lookup"><span data-stu-id="552f8-153">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="552f8-154">*Specjaliści:* o wstępnie zdefiniowanych ViewModel klasy statyczne, takie jak "kontraktów" oparte na jawne klasy DTO, zdecydowanie lepiej jest dla publicznych interfejsów API, ale także na mikrousług długoterminowej, nawet wtedy, gdy są one używane tylko w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="552f8-154">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="552f8-155">Jeśli chcesz określić typy odpowiedzi dla struktury swagger, musisz użyć jawnego klasy DTO jako typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="552f8-155">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="552f8-156">W związku z tym wstępnie zdefiniowanych klas DTO umożliwiają oferują bogatszy informacji z programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="552f8-156">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="552f8-157">Zwiększająca dokumentacji interfejsu API i zgodności podczas używania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="552f8-157">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="552f8-158">*Cons:* jak wspomniano wcześniej, jeśli zaktualizowanie kodu, zajmuje kilka więcej kroki, aby zaktualizować klasy DTO.</span><span class="sxs-lookup"><span data-stu-id="552f8-158">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="552f8-159">*Porada opartej na naszym doświadczeniu:* w zapytaniach wdrożone na mikrousługi porządkowanie w eShopOnContainers, firma Microsoft Rozpoczęto tworzenie za pomocą dynamicznej ViewModels jak bardzo proste i elastyczne na wczesnym etapie programowania.</span><span class="sxs-lookup"><span data-stu-id="552f8-159">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="552f8-160">Jednak po rozwoju został stabilizowany, wybraliśmy Refaktoryzuj interfejsów API i używać DTOs statyczne lub wstępnie zdefiniowane dla ViewModels, ponieważ jest on jaśniejszy dla konsumentów mikrousługi należy wiedzieć jawnie DTO typów, używany jako "kontrakty".</span><span class="sxs-lookup"><span data-stu-id="552f8-160">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="552f8-161">W poniższym przykładzie widać, jak zapytanie zwraca dane za pomocą jawnej klasy ViewModel DTO: klasa OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="552f8-161">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            var result = await connection.QueryAsync<dynamic>(
                  @"SELECT o.[Id] as ordernumber, 
                  o.[OrderDate] as [date],os.[Name] as [status], 
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid 
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    } 
}
```

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="552f8-162">Zawierająca opis odpowiedzi typów interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="552f8-162">Describing response types of Web APIs</span></span>

<span data-ttu-id="552f8-163">Deweloperom korzystanie z interfejsów API sieci web i mikrousług są najbardziej związane z wartością zwróconą — w szczególności typy odpowiedzi i kody błędów (o ile nie standard).</span><span class="sxs-lookup"><span data-stu-id="552f8-163">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="552f8-164">Te są obsługiwane w adnotacjach komentarzy i danych XML.</span><span class="sxs-lookup"><span data-stu-id="552f8-164">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="552f8-165">Bez prawidłowego dokumentacji w Interfejsie użytkownika programu Swagger, użytkownik nie ma wiedzy zwracanych typów lub jakie HTTP może być zwracany kodów.</span><span class="sxs-lookup"><span data-stu-id="552f8-165">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="552f8-166">Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc Swagger mogą generować bardziej rozbudowane informacje o modelu zwracany interfejsu API i wartości, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="552f8-166">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
       //Additional code...
       [Route("")]
       [HttpGet]
       [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
                             (int)HttpStatusCode.OK)]
       public async Task<IActionResult> GetOrders()
       {
           var orderTask = _orderQueries.GetOrdersAsync();
           var orders = await orderTask;
           return Ok(orders);
        }
    }
}
```

<span data-ttu-id="552f8-167">Jednak `ProducesResponseType` atrybutu nie można używać dynamicznej, zgodnie z typem, ponieważ wymaga tak samo, jak korzystać z typów jawnych, `OrderSummary` DTO ViewModel, pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="552f8-167">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="552f8-168">Jest to kolejny powód, dlaczego jawne zwracane typy są lepszym rozwiązaniem niż typów dynamicznych w perspektywie długoterminowej.</span><span class="sxs-lookup"><span data-stu-id="552f8-168">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="552f8-169">Korzystając z `ProducesResponseType` atrybutu, można również określić, co to jest oczekiwany wynik w zakresie możliwości HTTP/kody błędów, takich jak 200,400, itp.</span><span class="sxs-lookup"><span data-stu-id="552f8-169">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="552f8-170">Na poniższej ilustracji widać, jak przedstawiono informacje o wartość ResponseType przez interfejs użytkownika programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="552f8-170">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="552f8-171">**Rysunek 9-5**.</span><span class="sxs-lookup"><span data-stu-id="552f8-171">**Figure 9-5**.</span></span> <span data-ttu-id="552f8-172">Wyświetlanie typów odpowiedzi i możliwe kody stanu HTTP składnika Web API interfejs użytkownika struktury swagger</span><span class="sxs-lookup"><span data-stu-id="552f8-172">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="552f8-173">Widać na ilustracji powyżej niektóre przykładowe wartości oparte na typy ViewModel plus możliwe kody stanu HTTP, które mogą być zwrócone.</span><span class="sxs-lookup"><span data-stu-id="552f8-173">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="552f8-174">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="552f8-174">Additional resources</span></span>

-   <span data-ttu-id="552f8-175">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="552f8-175">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="552f8-176">**Julie Lerman. Punkty danych - Dapper, Entity Framework i aplikacji hybrydowych (artykuł MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="552f8-176">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="552f8-177">*https://msdn.microsoft.com/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="552f8-177">*https://msdn.microsoft.com/magazine/mt703432.aspx*</span></span>

-   <span data-ttu-id="552f8-178">**Strony pomocy dla interfejsu Web API platformy ASP.NET Core korzystające z programu Swagger**</span><span class="sxs-lookup"><span data-stu-id="552f8-178">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    <span data-ttu-id="552f8-179">*https://docs.microsoft.com/ASPNET/Core/Tutorials/Web-API-Help-Pages-Using-swagger?Tabs=Visual-Studio*</span><span class="sxs-lookup"><span data-stu-id="552f8-179">*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="552f8-180">[Poprzednie] (eshoponcontainers-cqrs-ddd-microservice.md) [dalej] (ddd ukierunkowane microservice.md)</span><span class="sxs-lookup"><span data-stu-id="552f8-180">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
