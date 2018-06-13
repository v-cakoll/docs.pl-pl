---
title: Implementowanie odczyty/kwerendy w mikrousługi CQRS
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odczyty/kwerendy w mikrousługi CQRS
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.openlocfilehash: 8eca01acc2308097d1684be8bdb0f07edd86832f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579109"
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="c9550-103">Implementowanie odczyty/kwerendy w mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="c9550-103">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="c9550-104">Odczyty/zapytań porządkowania mikrousługi z aplikacji odwołanie eShopOnContainers implementuje zapytania niezależnie od DDD modelu i obszar transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c9550-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="c9550-105">Wykonano głównie, ponieważ znacząco różnią wymagań dla zapytań i transakcji.</span><span class="sxs-lookup"><span data-stu-id="c9550-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="c9550-106">Zapisy wykonania transakcji, które muszą być zgodne z logiką domeny.</span><span class="sxs-lookup"><span data-stu-id="c9550-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="c9550-107">Z drugiej strony, zapytania, są idempotentności i być rozdzielone od zasad domeny.</span><span class="sxs-lookup"><span data-stu-id="c9550-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="c9550-108">Podejście jest proste, jak pokazano na rysunku 9-3.</span><span class="sxs-lookup"><span data-stu-id="c9550-108">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="c9550-109">Interfejs API zaimplementowano przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takich jak micro relacyjne mapowania ORM (Object) jak Dapper i zwracanie dynamiczne ViewModels w zależności od potrzeb aplikacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9550-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="c9550-110">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="c9550-110">**Figure 9-3**.</span></span> <span data-ttu-id="c9550-111">Najprostsza metoda zapytań w mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="c9550-111">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="c9550-112">Jest to najprostsza metoda możliwe w dla zapytań.</span><span class="sxs-lookup"><span data-stu-id="c9550-112">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="c9550-113">Definicje kwerendy w bazie danych i zwracać dynamiczne ViewModel, oparty na bieżąco dla każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="c9550-113">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="c9550-114">Ponieważ zapytania są idempotentności, zmienią danych niezależnie od tego, ile razy wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="c9550-114">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="c9550-115">W związku z tym nie trzeba być ograniczone przez dowolnego wzorzec DDD używany po stronie transakcyjnych, takie jak wartości zagregowanych i innych wzorcach i dlatego zapytania są oddzielone od obszaru transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c9550-115">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="c9550-116">Po prostu zapytania do bazy danych, która wymaga interfejsu użytkownika i zwracać ViewModel dynamiczne, które muszą być statycznie zdefiniowany dowolnego miejsca (nie klasy dla ViewModels) z wyjątkiem w instrukcji SQL, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="c9550-116">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="c9550-117">Ponieważ jest to prosty podejście, kod wymagany dla strony zapytania (takich jak kodu za pomocą micro, takich jak ORM [Dapper](https://github.com/StackExchange/Dapper)) może być zaimplementowany [w tym samym projekcie interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="c9550-117">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="c9550-118">Na rysunku 9-4 przedstawiono to.</span><span class="sxs-lookup"><span data-stu-id="c9550-118">Figure 9-4 shows this.</span></span> <span data-ttu-id="c9550-119">Zapytania są definiowane w **Ordering.API** mikrousługi projektu w ramach rozwiązania eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c9550-119">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="c9550-120">**Rysunek 9-4**.</span><span class="sxs-lookup"><span data-stu-id="c9550-120">**Figure 9-4**.</span></span> <span data-ttu-id="c9550-121">Zapytania w mikrousługi porządkowanie w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c9550-121">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="c9550-122">Przy użyciu ViewModels celowo dla aplikacji klienta, niezależnie od ograniczeń modelu domeny</span><span class="sxs-lookup"><span data-stu-id="c9550-122">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="c9550-123">Ponieważ zapytania są wykonywane do uzyskiwania danych wymaganych przez aplikacje klienckie, zwrócony typ można w szczególności wprowadzone dla klientów, na podstawie danych zwróconych przez zapytania.</span><span class="sxs-lookup"><span data-stu-id="c9550-123">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="c9550-124">Te modele lub obiekty Transfer danych (DTOs), są nazywane ViewModels.</span><span class="sxs-lookup"><span data-stu-id="c9550-124">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="c9550-125">Zwrócone dane (ViewModel) może być wynikiem sprzężenia danych z wielu obiektów lub tabele w bazie danych, lub nawet Agreguje wiele zdefiniowanych w modelu domeny dla transakcyjnego obszaru.</span><span class="sxs-lookup"><span data-stu-id="c9550-125">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="c9550-126">W takim przypadku ponieważ tworzenia kwerend niezależnie od modelu domeny, agregacje granic i ograniczenia całkowicie są ignorowane, a możesz go dowolnie zapytania żadnych tabel i kolumn, który może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="c9550-126">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="c9550-127">Ta metoda zapewnia dużą elastyczność i wydajność dla deweloperów, tworzenie lub aktualizowanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="c9550-127">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="c9550-128">ViewModels może być statyczne typy zdefiniowane w klasach.</span><span class="sxs-lookup"><span data-stu-id="c9550-128">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="c9550-129">Lub też można tworzyć dynamicznie na podstawie kwerend wykonywana (jak jest implementowane w porządkowania mikrousługi), który jest bardzo elastyczne dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="c9550-129">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="c9550-130">Przy użyciu Dapper jako micro ORM do wykonywania zapytań</span><span class="sxs-lookup"><span data-stu-id="c9550-130">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="c9550-131">Podczas wykonywania zapytań, można użyć dowolnego micro ORM, Entity Framework Core lub nawet zwykły ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c9550-131">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="c9550-132">W przykładowej aplikacji Dapper został wybrany do porządkowania mikrousługi w eShopOnContainers jako przykład popularnych ORM micro.</span><span class="sxs-lookup"><span data-stu-id="c9550-132">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="c9550-133">Można go uruchomić zwykły kwerend SQL o bardzo dużej wydajności, ponieważ jest bardzo małe framework.</span><span class="sxs-lookup"><span data-stu-id="c9550-133">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="c9550-134">Dapper można napisać zapytanie SQL, które mogą uzyskać dostęp i dołączyć wiele tabel.</span><span class="sxs-lookup"><span data-stu-id="c9550-134">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="c9550-135">Dapper to projekt typu open source (utworzony przez Sam szafran oryginału) i jest częścią bloki konstrukcyjne, używane w [przepełnienie stosu](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="c9550-135">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="c9550-136">Aby użyć Dapper, wystarczy zainstalować go za pomocą [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="c9550-136">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="c9550-137">Należy również dodać za pomocą instrukcji tak kod ma dostęp do metody Dapper rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c9550-137">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="c9550-138">W przypadku użycia Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> dostępne w klasie <xref:System.Data.SqlClient> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9550-138">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="c9550-139">Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasy, można po prostu wykonać zapytania w sposób prosty i wydajność.</span><span class="sxs-lookup"><span data-stu-id="c9550-139">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="c9550-140">Dynamiczne i ViewModels statyczne</span><span class="sxs-lookup"><span data-stu-id="c9550-140">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="c9550-141">W przypadku powrotu ViewModels z po stronie serwera do klienta aplikacji, należy zwrócić uwagę tych ViewModels jako DTOs, które mogą być różne do jednostek domeny wewnętrznej modelu jednostki, ponieważ wymaga aplikacji klienckiej sposobu wstrzymywania ViewModels danych.</span><span class="sxs-lookup"><span data-stu-id="c9550-141">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="c9550-142">W związku z tym w wielu przypadkach możesz agregować dane pochodzące z wielu domen, jednostek i tworzą ViewModels dokładnie według jak aplikacja, klient musi danych.</span><span class="sxs-lookup"><span data-stu-id="c9550-142">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="c9550-143">Te ViewModels lub DTOs można definiować jawnie (jako klasy symbol zastępczy danych) jak [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) klasy w późniejszym fragment kodu, lub po prostu może zwrócić ViewModels dynamicznych lub dynamiczne DTOs po prostu na podstawie atrybutów zwracane przez Twojego zapytania jako `dynamic` typu.</span><span class="sxs-lookup"><span data-stu-id="c9550-143">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="c9550-144">ViewModel jako typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="c9550-144">ViewModel as dynamic type</span></span>

<span data-ttu-id="c9550-145">Jak pokazano w poniższym kodzie, ViewModel może być bezpośrednio zwracany przez zapytania zwracając typu dynamicznego wewnętrznie na podstawie atrybutów zwróconych przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="c9550-145">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="c9550-146">Oznacza to, że podzbiór atrybutów, które mają być zwracane jest oparty na samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="c9550-146">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="c9550-147">W związku z tym po dodaniu nowej kolumny do zapytania, lub Dołącz do tych danych jest dynamicznie dodawane do zwrócony ViewModel.</span><span class="sxs-lookup"><span data-stu-id="c9550-147">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

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

<span data-ttu-id="c9550-148">Istotne jest, czy przy użyciu typu dynamicznego, zwracane zbierania danych są dynamicznie montowane jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="c9550-148">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="c9550-149">*Specjaliści:* takie podejście ogranicza potrzebę modyfikowanie klas statycznych ViewModel po zaktualizowaniu zdanie SQL kwerendy, co ta podejście do projektowania bardzo elastyczne podczas kodowania, proste i szybkie podlegać ewolucji w odniesieniu do przyszłych zmian.</span><span class="sxs-lookup"><span data-stu-id="c9550-149">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="c9550-150">*Cons:* w długim okresie, typy dynamiczne można mają negatywny wpływ na czytelność i mieć wpływ na zgodność usługi z aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="c9550-150">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="c9550-151">Ponadto oprogramowanie pośredniczące oprogramowanie, takie jak Swagger nie może dostarczyć poziomu dokumentacji na typy zwracane Jeśli za pomocą zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="c9550-151">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="c9550-152">ViewModel jako wstępnie zdefiniowanych klas DTO</span><span class="sxs-lookup"><span data-stu-id="c9550-152">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="c9550-153">*Specjaliści:* o wstępnie zdefiniowanych ViewModel klasy statyczne, takie jak "kontraktów" oparte na jawne klasy DTO, zdecydowanie lepiej jest dla publicznych interfejsów API, ale także na mikrousług długoterminowej, nawet wtedy, gdy są one używane tylko w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9550-153">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="c9550-154">Jeśli chcesz określić typy odpowiedzi dla struktury swagger, musisz użyć jawnego klasy DTO jako typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="c9550-154">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="c9550-155">W związku z tym wstępnie zdefiniowanych klas DTO umożliwiają oferują bogatszy informacji z programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="c9550-155">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="c9550-156">Zwiększająca dokumentacji interfejsu API i zgodności podczas używania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="c9550-156">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="c9550-157">*Cons:* jak wspomniano wcześniej, jeśli zaktualizowanie kodu, zajmuje kilka więcej kroki, aby zaktualizować klasy DTO.</span><span class="sxs-lookup"><span data-stu-id="c9550-157">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="c9550-158">*Porada opartej na naszym doświadczeniu:* w zapytaniach wdrożone na mikrousługi porządkowanie w eShopOnContainers, firma Microsoft Rozpoczęto tworzenie za pomocą dynamicznej ViewModels jak bardzo proste i elastyczne na wczesnym etapie programowania.</span><span class="sxs-lookup"><span data-stu-id="c9550-158">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="c9550-159">Jednak po rozwoju został stabilizowany, wybraliśmy Refaktoryzuj interfejsów API i używać DTOs statyczne lub wstępnie zdefiniowane dla ViewModels, ponieważ jest on jaśniejszy dla konsumentów mikrousługi należy wiedzieć jawnie DTO typów, używany jako "kontrakty".</span><span class="sxs-lookup"><span data-stu-id="c9550-159">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="c9550-160">W poniższym przykładzie widać, jak zapytanie zwraca dane za pomocą jawnej klasy ViewModel DTO: klasa OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="c9550-160">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="c9550-161">Zawierająca opis odpowiedzi typów interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="c9550-161">Describing response types of Web APIs</span></span>

<span data-ttu-id="c9550-162">Deweloperom korzystanie z interfejsów API sieci web i mikrousług są najbardziej związane z wartością zwróconą — w szczególności typy odpowiedzi i kody błędów (o ile nie standard).</span><span class="sxs-lookup"><span data-stu-id="c9550-162">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="c9550-163">Te są obsługiwane w adnotacjach komentarzy i danych XML.</span><span class="sxs-lookup"><span data-stu-id="c9550-163">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="c9550-164">Bez prawidłowego dokumentacji w Interfejsie użytkownika programu Swagger, użytkownik nie ma wiedzy zwracanych typów lub jakie HTTP może być zwracany kodów.</span><span class="sxs-lookup"><span data-stu-id="c9550-164">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="c9550-165">Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc Swagger mogą generować bardziej rozbudowane informacje o modelu zwracany interfejsu API i wartości, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c9550-165">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="c9550-166">Jednak `ProducesResponseType` atrybutu nie można używać dynamicznej, zgodnie z typem, ponieważ wymaga tak samo, jak korzystać z typów jawnych, `OrderSummary` DTO ViewModel, pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c9550-166">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="c9550-167">Jest to kolejny powód, dlaczego jawne zwracane typy są lepszym rozwiązaniem niż typów dynamicznych w perspektywie długoterminowej.</span><span class="sxs-lookup"><span data-stu-id="c9550-167">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="c9550-168">Korzystając z `ProducesResponseType` atrybutu, można również określić, co to jest oczekiwany wynik w zakresie możliwości HTTP/kody błędów, takich jak 200,400, itp.</span><span class="sxs-lookup"><span data-stu-id="c9550-168">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="c9550-169">Na poniższej ilustracji widać, jak przedstawiono informacje o wartość ResponseType przez interfejs użytkownika programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="c9550-169">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="c9550-170">**Rysunek 9-5**.</span><span class="sxs-lookup"><span data-stu-id="c9550-170">**Figure 9-5**.</span></span> <span data-ttu-id="c9550-171">Wyświetlanie typów odpowiedzi i możliwe kody stanu HTTP składnika Web API interfejs użytkownika struktury swagger</span><span class="sxs-lookup"><span data-stu-id="c9550-171">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="c9550-172">Widać na ilustracji powyżej niektóre przykładowe wartości oparte na typy ViewModel plus możliwe kody stanu HTTP, które mogą być zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c9550-172">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c9550-173">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="c9550-173">Additional resources</span></span>

-   <span data-ttu-id="c9550-174">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="c9550-174">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="c9550-175">**Julie Lerman. Punkty danych - Dapper, Entity Framework i aplikacji hybrydowych (artykuł MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="c9550-175">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    *https://msdn.microsoft.com/magazine/mt703432.aspx*

-   <span data-ttu-id="c9550-176">**Strony pomocy dla interfejsu Web API platformy ASP.NET Core korzystające z programu Swagger**</span><span class="sxs-lookup"><span data-stu-id="c9550-176">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    *https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*

>[!div class="step-by-step"]
<span data-ttu-id="c9550-177">[Poprzednie] (eshoponcontainers-cqrs-ddd-microservice.md) [dalej] (ddd ukierunkowane microservice.md)</span><span class="sxs-lookup"><span data-stu-id="c9550-177">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
