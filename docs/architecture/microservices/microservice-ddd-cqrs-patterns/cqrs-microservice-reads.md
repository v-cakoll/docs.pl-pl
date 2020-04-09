---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zrozumieć implementację strony zapytań CQRS na mikrousługi zamawiania w eShopOnContainers przy użyciu Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 49f42a5035bab38f800f3ec5ea24b01fde0d2964
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988755"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="b3c3a-103">Implementowanie odczytów/zapytań w mikrousługach CQRS</span><span class="sxs-lookup"><span data-stu-id="b3c3a-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="b3c3a-104">W przypadku odczytów/zapytań zamawianie mikrousługi z aplikacji referencyjnej eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszaru transakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="b3c3a-105">Dokonano tego przede wszystkim dlatego, że wymagania dotyczące zapytań i transakcji są drastycznie różne.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="b3c3a-106">Zapisuje wykonać transakcje, które muszą być zgodne z logiką domeny.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="b3c3a-107">Zapytania, z drugiej strony, są idempotentne i mogą być oddzielone od reguł domeny.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="b3c3a-108">Podejście jest proste, jak pokazano na rysunku 7-3.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="b3c3a-109">Interfejs interfejsu API jest implementowany przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takiej jak mikro obiekt owacyjna mapera (ORM) , taka jak Dapper, i zwracanie dynamicznych modeli viewmodele w zależności od potrzeb aplikacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Diagram przedstawiający kwerendy wysokiego poziomu w uproszczonym CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="b3c3a-111">**Rysunek 7-3**.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-111">**Figure 7-3**.</span></span> <span data-ttu-id="b3c3a-112">Najprostsze podejście do zapytań w mikrousługach CQRS</span><span class="sxs-lookup"><span data-stu-id="b3c3a-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="b3c3a-113">Najprostsze podejście po stronie zapytań w uproszczonym podejściu CQRS można zaimplementować, po prostu kwerendy bazy danych z Micro-ORM jak Dapper, zwracając dynamiczne Modele widoków.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by just querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="b3c3a-114">Definicje kwerendy kwerendy bazy danych i zwraca dynamiczny ViewModel zbudowany na bieżąco dla każdej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="b3c3a-115">Ponieważ zapytania są idempotentne, nie zmieni danych bez względu na to, ile razy uruchamiasz kwerendę.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="b3c3a-116">W związku z tym nie muszą być ograniczone przez dowolny wzorzec DDD używane w stronie transakcyjnej, takich jak agregaty i inne wzorce i dlatego kwerendy są oddzielone od obszaru transakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="b3c3a-117">Wystarczy zbadać bazy danych dla danych, które wymaga interfejsu użytkownika i zwraca dynamiczne ViewModel, który nie musi być statycznie zdefiniowane w dowolnym miejscu (bez klas dla ViewModels), z wyjątkiem instrukcji SQL siebie.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="b3c3a-118">Ponieważ jest to proste podejście, kod wymagany po stronie kwerend (takich jak kod przy użyciu micro ORM jak [Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w ramach tego samego projektu interfejsu API sieci Web.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)</span><span class="sxs-lookup"><span data-stu-id="b3c3a-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="b3c3a-119">Rysunek 7-4 pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="b3c3a-120">Zapytania są zdefiniowane w projekcie mikrousług **Ordering.API** w ramach rozwiązania eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Zrzut ekranu przedstawiający folder Kwerendy projektu Ordering.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="b3c3a-122">**Rysunek 7-4**.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-122">**Figure 7-4**.</span></span> <span data-ttu-id="b3c3a-123">Zapytania w mikrousługach zamawiania w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="b3c3a-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="b3c3a-124">Używanie modeli viewmodele specjalnie dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny</span><span class="sxs-lookup"><span data-stu-id="b3c3a-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="b3c3a-125">Ponieważ kwerendy są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może być specjalnie dla klientów, na podstawie danych zwróconych przez kwerendy.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="b3c3a-126">Te modele lub obiekty transferu danych (DTO) są nazywane Modelami widoków.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="b3c3a-127">Zwrócone dane (ViewModel) może być wynikiem łączenia danych z wielu jednostek lub tabel w bazie danych, lub nawet w wielu agregatów zdefiniowanych w modelu domeny dla obszaru transakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="b3c3a-128">W takim przypadku, ponieważ tworzysz kwerendy niezależne od modelu domeny, agreguje granice i ograniczenia są całkowicie ignorowane i możesz swobodnie wysyłać zapytania do dowolnej tabeli i kolumny, które mogą być potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="b3c3a-129">Takie podejście zapewnia dużą elastyczność i produktywność dla deweloperów tworzenia lub aktualizowania zapytań.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="b3c3a-130">ViewModels mogą być typy statyczne zdefiniowane w klasach.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="b3c3a-131">Lub mogą być tworzone dynamicznie na podstawie zapytań wykonywanych (jak jest zaimplementowana w mikrousługi zamawiania), który jest bardzo elastyczny dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="b3c3a-132">Użyj Dapper jako micro ORM do wykonywania zapytań</span><span class="sxs-lookup"><span data-stu-id="b3c3a-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="b3c3a-133">Można użyć dowolnego mikro ORM, Entity Framework Core, a nawet zwykły ADO.NET do wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="b3c3a-134">W przykładowej aplikacji Dapper został wybrany dla zamawiania mikrousługi w eShopOnContainers jako dobry przykład popularnego micro ORM.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="b3c3a-135">Można uruchomić zwykłych zapytań SQL z doskonałą wydajnością, ponieważ jest to bardzo lekka struktura.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="b3c3a-136">Za pomocą Dapper, można napisać zapytanie SQL, które można uzyskać dostęp i dołączyć do wielu tabel.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="b3c3a-137">Dapper jest projektem typu open source (oryginalnym stworzonym przez Sama Szafrana) i jest częścią bloków konstrukcyjnych używanych w [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="b3c3a-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="b3c3a-138">Aby korzystać z Dapper, wystarczy zainstalować go za pośrednictwem [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="b3c3a-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Zrzut ekranu przedstawiający pakiet Dapper w widoku pakietów NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="b3c3a-140">Należy również dodać using instrukcji, dzięki czemu kod ma dostęp do dapper metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="b3c3a-141">Korzystając z Dapper w kodzie, należy <xref:System.Data.SqlClient.SqlConnection> bezpośrednio użyć <xref:System.Data.SqlClient> klasy dostępne w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="b3c3a-142">Za pomocą QueryAsync metody i innych <xref:System.Data.SqlClient.SqlConnection> metod rozszerzenia, które rozszerzają klasy, można po prostu uruchomić kwerendy w sposób prosty i wydajny.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="b3c3a-143">Dynamiczne i statyczne modele widoków</span><span class="sxs-lookup"><span data-stu-id="b3c3a-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="b3c3a-144">Podczas zwracania ViewModels od strony serwera do aplikacji klienckich, można myśleć o tych ViewModels jako DTO (Obiekty transferu danych), które mogą być różne od wewnętrznych jednostek domeny modelu jednostki, ponieważ ViewModels przechowywania danych w sposób aplikacji klienckiej potrzeb.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="b3c3a-145">W związku z tym w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i redagować ViewModels dokładnie zgodnie z tym, jak aplikacja kliencka potrzebuje tych danych.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="b3c3a-146">Te ViewModels lub DTO mogą być zdefiniowane jawnie `OrderSummary` (jako klasy posiadacza danych), jak klasa wyświetlana w nowszym fragmentie kodu lub można po prostu zwrócić dynamiczne modele viewmodels lub dynamiczne DTO po prostu na podstawie atrybutów zwracanych przez zapytania, jako typ dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="b3c3a-147">ViewModel jako typ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="b3c3a-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="b3c3a-148">Jak pokazano w poniższym `ViewModel` kodzie, a może być bezpośrednio zwracany przez kwerendy, po prostu zwracając typ *dynamiczny,* który wewnętrznie jest oparty na atrybuty zwracane przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="b3c3a-149">Oznacza to, że podzbiór atrybutów do zwrotu opiera się na samej kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="b3c3a-150">W związku z tym po dodaniu nowej kolumny do kwerendy lub `ViewModel`sprzężenia, że dane są dynamicznie dodawane do zwracanego .</span><span class="sxs-lookup"><span data-stu-id="b3c3a-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="b3c3a-151">Ważnym punktem jest to, że przy użyciu typu dynamicznego, zwracana kolekcja danych jest dynamicznie montowane jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="b3c3a-152">**Plusy:** Takie podejście zmniejsza potrzebę modyfikowania statycznych viewmodel klas przy każdej aktualizacji zdanie SQL kwerendy, dzięki czemu to podejście projektu dość zwinny podczas kodowania, proste i szybkie ewoluować w odniesieniu do przyszłych zmian.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="b3c3a-153">**Wady:** W dłuższej perspektywie typy dynamiczne mogą negatywnie wpłynąć na przejrzystość i zgodność usługi z aplikacjami klienckimi.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="b3c3a-154">Ponadto oprogramowanie pośredniczące, takie jak Swashbuckle, nie może zapewnić tego samego poziomu dokumentacji zwróconych typów, jeśli używasz typów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="b3c3a-155">ViewModel jako wstępnie zdefiniowane klasy DTO</span><span class="sxs-lookup"><span data-stu-id="b3c3a-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="b3c3a-156">**Plusy:** Posiadanie statycznych wstępnie zdefiniowanych klas ViewModel, takich jak "kontrakty" oparte na jawnych klasach DTO, jest zdecydowanie lepsze dla publicznych interfejsów API, ale także dla mikrousług długoterminowych, nawet jeśli są one używane tylko przez tę samą aplikację.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-156">**Pros**: Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="b3c3a-157">Jeśli chcesz określić typy odpowiedzi dla Swagger, należy użyć jawnych klas DTO jako typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="b3c3a-158">W związku z tym wstępnie zdefiniowane klasy DTO umożliwiają oferowanie bogatszych informacji z Swagger.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="b3c3a-159">To poprawia dokumentację interfejsu API i zgodność podczas korzystania z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="b3c3a-160">**Minusy:** Jak wspomniano wcześniej, podczas aktualizowania kodu, wymaga kilku kroków, aby zaktualizować klasy DTO.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="b3c3a-161">*Porada na podstawie naszego doświadczenia:* W zapytaniach zaimplementowanych w mikrousługach zamawiania w eShopOnContainers, zaczęliśmy się rozwijać przy użyciu dynamicznych ViewModels, ponieważ było to bardzo proste i zwinne na wczesnych etapach rozwoju.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="b3c3a-162">Ale po ustabilizowaniu rozwoju, zdecydowaliśmy się refaktoryzować interfejsów API i używać statycznych lub wstępnie zdefiniowanych obiektów DTO dla ViewModels, ponieważ jest jaśniejsze dla konsumentów mikrousług, aby wiedzieć jawne typy DTO, używane jako "kontrakty".</span><span class="sxs-lookup"><span data-stu-id="b3c3a-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="b3c3a-163">W poniższym przykładzie można zobaczyć, jak kwerenda zwraca dane przy użyciu jawnej klasy DTO ViewModel: OrderSummary klasy.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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
            return await connection.QueryAsync<OrderSummary>(
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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="b3c3a-164">Opis typów odpowiedzi interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="b3c3a-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="b3c3a-165">Deweloperzy zużywający interfejsy API sieci web i mikrousług są najbardziej zaniepokojeni tym, co jest zwracane — w szczególności typy odpowiedzi i kody błędów (jeśli nie są standardowe).</span><span class="sxs-lookup"><span data-stu-id="b3c3a-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="b3c3a-166">Są one obsługiwane w komentarzach XML i adnotacjach danych.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="b3c3a-167">Bez odpowiedniej dokumentacji w interfejsie użytkownika Swagger konsument nie ma wiedzy o tym, jakie typy są zwracane lub jakie kody HTTP mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="b3c3a-168">Ten problem jest rozwiązany <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>przez dodanie , więc Swashbuckle może generować bogatsze informacje o modelu powrotu interfejsu API i wartości, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="b3c3a-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

<span data-ttu-id="b3c3a-169">Jednak `ProducesResponseType` atrybut nie może używać dynamicznych jako typu, ale `OrderSummary` wymaga użycia jawnych typów, takich jak ViewModel DTO, pokazany w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b3c3a-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="b3c3a-170">Jest to kolejny powód, dla którego jawne zwracane typy są lepsze niż typy dynamiczne, w dłuższej perspektywie.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="b3c3a-171">Korzystając z `ProducesResponseType` atrybutu, można również określić, jaki jest oczekiwany wynik w odniesieniu do możliwych błędów HTTP / kody, takie jak 200, 400, itp.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="b3c3a-172">Na poniższej ilustracji można zobaczyć, jak Swagger UI pokazuje informacje ResponseType.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Zrzut ekranu przedstawiający stronę interfejsu użytkownika swagger dla interfejsu API zamawiania.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="b3c3a-174">**Rysunek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-174">**Figure 7-5**.</span></span> <span data-ttu-id="b3c3a-175">Interfejs użytkownika swagger pokazujący typy odpowiedzi i możliwe kody stanu HTTP z interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="b3c3a-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="b3c3a-176">Możesz zobaczyć na obrazku powyżej kilka przykładowych wartości na podstawie viewmodel typów plus możliwe kody stanu HTTP, które mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="b3c3a-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b3c3a-177">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="b3c3a-177">Additional resources</span></span>

- <span data-ttu-id="b3c3a-178">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="b3c3a-178">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="b3c3a-179">**Julie Lerman. Punkty danych - Dapper, Entity Framework i Aplikacje hybrydowe (artykuł magazynu MSDN)**</span><span class="sxs-lookup"><span data-stu-id="b3c3a-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="b3c3a-180">**ASP.NET core Web API Strony pomocy przy użyciu Swagger**</span><span class="sxs-lookup"><span data-stu-id="b3c3a-180">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="b3c3a-181">[Poprzedni](eshoponcontainers-cqrs-ddd-microservice.md)
>[następny](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="b3c3a-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
