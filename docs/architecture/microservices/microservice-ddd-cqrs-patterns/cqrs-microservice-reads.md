---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z implementacją zapytania CQRS na mikrousłudze porządkowania w eShopOnContainers przy użyciu Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: f791546e2fc00e276ab55302802a5534465ace58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295990"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="e76ca-103">Implementowanie operacji odczytu/zapytań w CQRS mikrousługi</span><span class="sxs-lookup"><span data-stu-id="e76ca-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="e76ca-104">W przypadku operacji odczytu/zapytań, mikrousługa porządkowania z aplikacji referencyjnej eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszaru transakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="e76ca-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="e76ca-105">Zostało to zrobione przede wszystkim dlatego, że wymagania dotyczące zapytań i transakcji są znacząco inne.</span><span class="sxs-lookup"><span data-stu-id="e76ca-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="e76ca-106">Zapisuje transakcje wykonania, które muszą być zgodne z logiką domeny.</span><span class="sxs-lookup"><span data-stu-id="e76ca-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="e76ca-107">Zapytania, z drugiej strony, są idempotentne i mogą być segregowane z reguł domeny.</span><span class="sxs-lookup"><span data-stu-id="e76ca-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="e76ca-108">Podejście jest proste, jak pokazano na rysunku 7-3.</span><span class="sxs-lookup"><span data-stu-id="e76ca-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="e76ca-109">Interfejs API jest implementowany przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takiej jak relacyjne mapowanie mikroobiektu (ORM), takie jak Dapper, i zwracanie dynamicznego modele widoków w zależności od potrzeb aplikacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e76ca-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Najprostszym podejściem do wykonywania zapytań w uproszczonym podejściu CQRS może być implementacja przez samo wykonanie zapytania dotyczącego bazy danych przy użyciu mikroorm, na przykład Dapper, zwrócenie dynamicznego modele widoków.](./media/image3.png)

<span data-ttu-id="e76ca-111">**Rysunek 7-3**.</span><span class="sxs-lookup"><span data-stu-id="e76ca-111">**Figure 7-3**.</span></span> <span data-ttu-id="e76ca-112">Najprostszym podejściem do wykonywania zapytań w mikrousłudze CQRS</span><span class="sxs-lookup"><span data-stu-id="e76ca-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="e76ca-113">Jest to najprostsza możliwa Metoda dla zapytań.</span><span class="sxs-lookup"><span data-stu-id="e76ca-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="e76ca-114">Definicje zapytania zapytania do bazy danych i zwracają dynamiczny ViewModel zbudowany na bieżąco dla każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e76ca-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="e76ca-115">Ponieważ zapytania są idempotentne, nie zmieniają danych niezależnie od tego, ile razy zostało uruchomione zapytanie.</span><span class="sxs-lookup"><span data-stu-id="e76ca-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="e76ca-116">W związku z tym nie trzeba ograniczać się przez żaden wzorzec DDD używany w stronie transakcyjnej, taki jak agregacje i inne wzorce, a także to, dlaczego zapytania są oddzielone od obszaru transakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="e76ca-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="e76ca-117">Po prostu wysyłasz zapytanie do bazy danych o dane wymagane przez interfejs użytkownika i zwracają dynamiczny ViewModel, który nie musi być statycznie zdefiniowany w dowolnym miejscu (brak klas dla modele widoków), z wyjątkiem samych instrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="e76ca-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="e76ca-118">Ponieważ jest to proste podejście, kod wymagany dla strony zapytania (na przykład kod korzystający z mikroorm like [Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w ramach tego samego projektu interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="e76ca-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="e76ca-119">Przedstawiono to na rysunku 7-4.</span><span class="sxs-lookup"><span data-stu-id="e76ca-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="e76ca-120">Zapytania są definiowane w projekcie **porządkowania. API** mikrousług w ramach rozwiązania eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e76ca-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Widok Eksplorator rozwiązań projektu porządkowania. API, pokazujący folder > zapytań aplikacji.](./media/image4.png)

<span data-ttu-id="e76ca-122">**Rysunek 7-4**.</span><span class="sxs-lookup"><span data-stu-id="e76ca-122">**Figure 7-4**.</span></span> <span data-ttu-id="e76ca-123">Zapytania w mikrousłudze porządkowania w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="e76ca-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="e76ca-124">Używaj modele widoków określonych dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny</span><span class="sxs-lookup"><span data-stu-id="e76ca-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="e76ca-125">Ponieważ zapytania są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może być przeznaczony dla klientów na podstawie danych zwróconych przez zapytania.</span><span class="sxs-lookup"><span data-stu-id="e76ca-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="e76ca-126">Te modele lub Transfer danych obiekty (DTO) są nazywane modele widoków.</span><span class="sxs-lookup"><span data-stu-id="e76ca-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="e76ca-127">Zwrócone dane (ViewModel) mogą wynikać z dołączania danych z wielu jednostek lub tabel w bazie danych, a nawet wielu agregacji zdefiniowanych w modelu domeny dla obszaru transakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="e76ca-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="e76ca-128">W tym przypadku, ponieważ tworzysz zapytania niezależnie od modelu domeny, zagregowane granice i ograniczenia są całkowicie ignorowane i można wysyłać zapytania do dowolnej tabeli i kolumny, które mogą być potrzebne.</span><span class="sxs-lookup"><span data-stu-id="e76ca-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="e76ca-129">Takie podejście zapewnia dużą elastyczność i produktywność dla deweloperów tworzących lub aktualizujących zapytania.</span><span class="sxs-lookup"><span data-stu-id="e76ca-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="e76ca-130">Modele widoków mogą być typami statycznymi zdefiniowanymi w klasach.</span><span class="sxs-lookup"><span data-stu-id="e76ca-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="e76ca-131">Lub mogą być tworzone dynamicznie na podstawie zapytań wykonanych (zgodnie z implementacją mikrousługi porządkowania), które są bardzo elastyczne dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="e76ca-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="e76ca-132">Używanie Dapper jako mikroorm do wykonywania zapytań</span><span class="sxs-lookup"><span data-stu-id="e76ca-132">Use Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="e76ca-133">Do wykonywania zapytań można użyć dowolnego mikroorm, Entity Framework Core lub nawet zwykłego ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e76ca-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="e76ca-134">W przykładowej aplikacji Dapper został wybrany dla mikrousługi porządkowania w eShopOnContainers jako dobry przykład popularnego mikroorm.</span><span class="sxs-lookup"><span data-stu-id="e76ca-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="e76ca-135">Może uruchamiać zwykłe zapytania SQL o doskonałej wydajności, ponieważ jest to bardzo lekka struktura.</span><span class="sxs-lookup"><span data-stu-id="e76ca-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="e76ca-136">Za pomocą Dapper można napisać zapytanie SQL, które może uzyskać dostęp do wielu tabel i dołączyć do nich.</span><span class="sxs-lookup"><span data-stu-id="e76ca-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="e76ca-137">Dapper to projekt typu "open source" (oryginalny utworzony przez sam Saffron) i jest częścią bloków konstrukcyjnych używanych w [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="e76ca-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="e76ca-138">Aby korzystać z Dapper, wystarczy zainstalować go za pomocą [pakietu NuGet Dapper](https://www.nuget.org/packages/Dapper), jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="e76ca-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Pakiet Dapper wyświetlany w widoku Zarządzanie pakietami NuGet w programie VS.](./media/image4.1.png)

<span data-ttu-id="e76ca-140">Należy również dodać instrukcję using, aby kod miał dostęp do metod rozszerzenia Dapper.</span><span class="sxs-lookup"><span data-stu-id="e76ca-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="e76ca-141">Gdy używasz Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> klasy dostępnej <xref:System.Data.SqlClient> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e76ca-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="e76ca-142">Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasę, można po prostu uruchamiać zapytania w sposób prosty i wydajny.</span><span class="sxs-lookup"><span data-stu-id="e76ca-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="e76ca-143">Dynamiczny a statyczny modele widoków</span><span class="sxs-lookup"><span data-stu-id="e76ca-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="e76ca-144">Po powrocie modele widoków z serwera do aplikacji klienckich można myśleć o tych modele widoków jako DTO (Transfer danych obiektów), które mogą być różne dla wewnętrznych jednostek domeny modelu jednostki, ponieważ modele widoków przechowuje dane w sposób, w jaki aplikacja kliencka konieczne.</span><span class="sxs-lookup"><span data-stu-id="e76ca-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="e76ca-145">Z tego względu w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i precyzyjnie redagować modele widoków według sposobu, w jaki aplikacja kliencka wymaga tych danych.</span><span class="sxs-lookup"><span data-stu-id="e76ca-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="e76ca-146">Te modele widoków lub DTO można jawnie zdefiniować (jako klasy posiadaczy danych), takie `OrderSummary` jak Klasa pokazana w późniejszym fragmencie kodu, lub po prostu zwrócić dynamiczną modele widoków lub dynamiczną DTO na podstawie atrybutów zwracanych przez zapytania jako dynamiczne Wprowadź.</span><span class="sxs-lookup"><span data-stu-id="e76ca-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="e76ca-147">ViewModel jako typ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="e76ca-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="e76ca-148">Jak pokazano w poniższym kodzie, `ViewModel` można zwrócić bezpośrednio przez zapytania, zwracając typ *dynamiczny* , który wewnętrznie jest oparty na atrybutach zwracanych przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="e76ca-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="e76ca-149">Oznacza to, że podzbiór atrybutów do zwrócenia jest oparty na zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="e76ca-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="e76ca-150">W związku z tym, jeśli dodasz nową kolumnę do zapytania lub sprzężenia, dane te są dynamicznie dodawane do `ViewModel`zwracanego.</span><span class="sxs-lookup"><span data-stu-id="e76ca-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="e76ca-151">Ważnym punktem jest to, że za pomocą typu dynamicznego, zwrócona kolekcja danych jest dynamicznie zmontowany jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="e76ca-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="e76ca-152">**Formaty** Takie podejście zmniejsza konieczność modyfikacji statycznych klas ViewModel za każdym razem, gdy aktualizujesz zdanie SQL zapytania, dzięki czemu ten projekt podejścia jest dość Agile podczas kodowania, bezpośrednie i szybkiej ewolucji w odniesieniu do przyszłych zmian.</span><span class="sxs-lookup"><span data-stu-id="e76ca-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="e76ca-153">**Wada** W długim okresie typy dynamiczne mogą mieć negatywny wpływ na przejrzystość i zgodność usługi z aplikacjami klienckimi.</span><span class="sxs-lookup"><span data-stu-id="e76ca-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="e76ca-154">Ponadto oprogramowanie pośredniczące, takie jak Swashbuckle, nie może zapewnić tego samego poziomu dokumentacji dla zwracanych typów, jeśli są używane typy dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="e76ca-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="e76ca-155">ViewModel jako wstępnie zdefiniowane klasy DTO</span><span class="sxs-lookup"><span data-stu-id="e76ca-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="e76ca-156">**Specjaliści**: Posiadanie statycznych wstępnie zdefiniowanych klas ViewModel, na przykład "umów" opartych na jawnych klasach DTO, jest w znacznym zakresie lepszym rozwiązaniem dla publicznych interfejsów API, ale także dla mikrousług długoterminowych, nawet jeśli są one używane tylko przez tę samą aplikację.</span><span class="sxs-lookup"><span data-stu-id="e76ca-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="e76ca-157">Jeśli chcesz określić typy odpowiedzi dla struktury Swagger, musisz użyć jawnych klas DTO jako typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="e76ca-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="e76ca-158">W związku z tym wstępnie zdefiniowane klasy DTO umożliwiają oferowanie bardziej szczegółowych informacji z struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="e76ca-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="e76ca-159">Poprawia to dokumentację interfejsu API i zgodność przy korzystaniu z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="e76ca-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="e76ca-160">**Wady**: Jak wspomniano wcześniej, podczas aktualizowania kodu potrzebne są kilka kroków pozwalające zaktualizować klasy DTO.</span><span class="sxs-lookup"><span data-stu-id="e76ca-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="e76ca-161">*Porada oparta na naszym doświadczeniu*: W zapytaniach zaimplementowanych w mikrousłudze porządkowania w programie eShopOnContainers rozpoczynamy Programowanie przy użyciu dynamicznego modele widoków, ponieważ było bardzo proste i elastyczne na wczesnych etapach tworzenia oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="e76ca-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="e76ca-162">Jednak po ustabilizowaniu rozwoju wybieramy do refaktoryzacji interfejsy API i używają statycznego lub wstępnie zdefiniowanego DTO dla modele widoków, ponieważ jest to wyraźniejsze dla konsumentów mikrousług, aby znać jawne typy DTO, używane jako "kontrakty".</span><span class="sxs-lookup"><span data-stu-id="e76ca-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="e76ca-163">W poniższym przykładzie można zobaczyć, jak zapytanie zwraca dane przy użyciu jawnej klasy ViewModel DTO: klasy OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="e76ca-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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
            var result = await connection.QueryAsync<OrderSummary>(
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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="e76ca-164">Opisywanie typów odpowiedzi interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="e76ca-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="e76ca-165">Deweloperzy korzystający z interfejsów API sieci Web i mikrousług są najbardziej zainteresowani tym, co jest zwracane — w szczególności typy odpowiedzi i kody błędów (jeśli nie są standardem).</span><span class="sxs-lookup"><span data-stu-id="e76ca-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="e76ca-166">Są one obsługiwane w komentarzach XML i adnotacjach danych.</span><span class="sxs-lookup"><span data-stu-id="e76ca-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="e76ca-167">Bez odpowiedniej dokumentacji w interfejsie użytkownika programu Swagger klient nie ma wiedzy na temat typów zwracanych lub kodów HTTP, które mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="e76ca-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="e76ca-168">Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc Swashbuckle może generować bogatsze informacje o modelu i wartościach zwracanych przez interfejs API, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e76ca-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="e76ca-169">Jednak atrybut nie może używać elementu dynamicznego jako typu, ale wymaga użycia jawnych typów, `OrderSummary` takich jak ViewModel DTO, pokazany w poniższym przykładzie: `ProducesResponseType`</span><span class="sxs-lookup"><span data-stu-id="e76ca-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="e76ca-170">Jest to kolejny powód, dla którego jawne zwracane typy są lepsze niż typy dynamiczne w długim okresie.</span><span class="sxs-lookup"><span data-stu-id="e76ca-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="e76ca-171">Przy użyciu `ProducesResponseType` atrybutu można także określić oczekiwany wynik w odniesieniu do możliwych błędów/kodów http, takich jak 200, 400 itd.</span><span class="sxs-lookup"><span data-stu-id="e76ca-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="e76ca-172">Na poniższej ilustracji widać, jak interfejs użytkownika struktury Swagger wyświetla informacje o odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e76ca-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Widok przeglądarki na stronie interfejsu użytkownika struktury Swagger dla interfejsu API porządkowania.](./media/image5.png)

<span data-ttu-id="e76ca-174">**Rysunek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="e76ca-174">**Figure 7-5**.</span></span> <span data-ttu-id="e76ca-175">Interfejs użytkownika struktury Swagger pokazujący typy odpowiedzi i możliwe kody stanu HTTP z internetowego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="e76ca-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="e76ca-176">Na obrazie można zobaczyć więcej przykładowych wartości na podstawie typów ViewModel oraz możliwych kodów stanu HTTP, które mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="e76ca-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e76ca-177">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e76ca-177">Additional resources</span></span>

- <span data-ttu-id="e76ca-178">**Dapper** </span><span class="sxs-lookup"><span data-stu-id="e76ca-178">**Dapper** </span></span>\
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="e76ca-179">**Julie Lerman. Punkty danych — Dapper, Entity Framework i aplikacje hybrydowe (MSDN mag. article)**  </span><span class="sxs-lookup"><span data-stu-id="e76ca-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)** </span></span>\
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- <span data-ttu-id="e76ca-180">**ASP.NET Core stronach pomocy interfejsu API sieci Web przy użyciu programu Swagger** </span><span class="sxs-lookup"><span data-stu-id="e76ca-180">**ASP.NET Core Web API Help Pages using Swagger** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="e76ca-181">[Poprzedni](eshoponcontainers-cqrs-ddd-microservice.md)Następny
>[](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="e76ca-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
