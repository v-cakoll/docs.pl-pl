---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, wykonania zapytania boku CQRS na szeregowania mikrousługi w ramach aplikacji eShopOnContainers przy użyciu programem Dapper.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: a77a92d12e3b60ebb67bab557a4e5ec1dd2f882f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126449"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="06822-103">Implementowanie odczytów i zapytań w mikrousłudze CQRS</span><span class="sxs-lookup"><span data-stu-id="06822-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="06822-104">Dla odczytów i zapytań szeregowania mikrousług z aplikacji referencyjnej w ramach aplikacji eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszar transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="06822-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="06822-105">Stało się przede wszystkim, ponieważ żądania dla zapytania i transakcje są znacząco różne.</span><span class="sxs-lookup"><span data-stu-id="06822-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="06822-106">Zapisy wykonywania transakcji, które muszą być zgodne z logiką domeny.</span><span class="sxs-lookup"><span data-stu-id="06822-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="06822-107">Zapytania, z drugiej strony, są idempotentne i być rozdzielone od zasad domeny.</span><span class="sxs-lookup"><span data-stu-id="06822-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="06822-108">Podejście to proste, jak pokazano w rysunek 7-3.</span><span class="sxs-lookup"><span data-stu-id="06822-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="06822-109">Interfejs API jest implementowany przez kontrolerów internetowych interfejsów API przy użyciu dowolnej infrastruktury, takich jak micro relacyjnego mapowania ORM (Object) np. programem Dapper i zwracanie modele dynamicznych widoków w zależności od potrzeb aplikacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="06822-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Najprostsza metoda stronie zapytań w uproszczone podejście CQRS może być implementowany przez tylko zapytanie do bazy danych za pomocą Micro-ORM np. programem Dapper, zwracając modele dynamicznych widoków.](./media/image3.png)

<span data-ttu-id="06822-111">**Rysunek 7-3**.</span><span class="sxs-lookup"><span data-stu-id="06822-111">**Figure 7-3**.</span></span> <span data-ttu-id="06822-112">Najprostszą metodą dla zapytań w mikrousłudze CQRS</span><span class="sxs-lookup"><span data-stu-id="06822-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="06822-113">Jest to najprostsza metoda możliwe dla zapytań.</span><span class="sxs-lookup"><span data-stu-id="06822-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="06822-114">Definicje zapytania w bazie danych i zwracają ViewModel dynamiczne, oparta na bieżąco dla każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="06822-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="06822-115">Ponieważ zapytania są idempotentne, nie zmienią danych niezależnie od tego, ile razy można uruchomić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="06822-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="06822-116">W związku z tym nie trzeba być ograniczana przez wszelkie wzorzec DDD używane w transakcji po stronie, takich jak zagregowanych danych i inne wzorce i dlatego zapytania są oddzielone od obszaru transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="06822-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="06822-117">Po prostu danych, która wymaga interfejsu użytkownika w bazie danych i zwracać ViewModel dynamicznych, które nie muszą zostać statycznie zdefiniowanych dowolnego miejsca (nie klasy dla modele widoków) z wyjątkiem w instrukcji SQL, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="06822-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="06822-118">Ponieważ jest to proste podejście, kod wymagany po stronie zapytania (np. kodu za pomocą micro, takich jak ORM [programem Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w obrębie tego samego projektu interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="06822-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="06822-119">7 — pokazano na rysunku 4 to.</span><span class="sxs-lookup"><span data-stu-id="06822-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="06822-120">Zapytania są definiowane w **Ordering.API** mikrousług projektu w ramach rozwiązania w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="06822-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Widok Eksploratora rozwiązania, projektu Ordering.API, przedstawiający aplikację > folderu zapytania.](./media/image4.png)

<span data-ttu-id="06822-122">**Rysunek 7-4**.</span><span class="sxs-lookup"><span data-stu-id="06822-122">**Figure 7-4**.</span></span> <span data-ttu-id="06822-123">Zapytania w mikrousługach porządkowanie w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="06822-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="06822-124">Użyj modele widoków celowo dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny</span><span class="sxs-lookup"><span data-stu-id="06822-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="06822-125">Ponieważ zapytania są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może specjalnie się dla klientów, w oparciu o dane zwrócone przez zapytania.</span><span class="sxs-lookup"><span data-stu-id="06822-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="06822-126">Te modele lub obiektów transferu danych (dto), są nazywane modele widoków.</span><span class="sxs-lookup"><span data-stu-id="06822-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="06822-127">Zwrócone dane (ViewModel) może być wynikiem łączenie danych z wielu obiektów lub tabel w bazie danych lub nawet przez wiele agregacje zdefiniowane w modelu domeny dla obszaru transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="06822-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="06822-128">W tym przypadku ponieważ tworzysz zapytania niezależnie od modelu domeny, agregacje granice i ograniczenia całkowicie są ignorowane i możesz zbadać żadnych tabel i kolumn, który może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="06822-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="06822-129">To podejście zapewnia dużą elastyczność i produktywność dla deweloperów, tworzenie lub aktualizowanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="06822-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="06822-130">Modele widoków mogą być statyczne typy zdefiniowane w klasach.</span><span class="sxs-lookup"><span data-stu-id="06822-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="06822-131">Lub można opracować dynamicznie w oparciu zapytania wykonywane (ponieważ jest zaimplementowana w mikrousługach szeregowania), który jest bardzo agile dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="06822-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="06822-132">Pełnić do wykonywania zapytań wczesnych ORM programem Dapper</span><span class="sxs-lookup"><span data-stu-id="06822-132">Use Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="06822-133">Można użyć dowolnego wczesnych ORM, platformy Entity Framework Core lub nawet zwykły ADO.NET podczas wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="06822-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="06822-134">W przykładowej aplikacji programem Dapper został wybrany do szeregowania mikrousługi w ramach aplikacji eShopOnContainers jako dobrym przykładem popularnych ORM micro.</span><span class="sxs-lookup"><span data-stu-id="06822-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="06822-135">Zwykły zapytania SQL może działać o bardzo dużej wydajności, ponieważ jest on bardzo małe framework.</span><span class="sxs-lookup"><span data-stu-id="06822-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="06822-136">Korzystając z programem Dapper, można napisać zapytanie SQL, które mogą uzyskać dostęp i Dołącz do wielu tabel.</span><span class="sxs-lookup"><span data-stu-id="06822-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="06822-137">Programem Dapper to projekt typu open source (oryginalnie utworzone przez Sam szafran) i jest częścią bloki konstrukcyjne, używane w [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="06822-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="06822-138">Aby korzystać z programem Dapper, wystarczy zainstalować go za pośrednictwem [pakietu NuGet z programem Dapper](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="06822-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Programem Dapper pakiet jako wyświetlane w widoku pakiety zarządzania NuGet w programie VS.](./media/image4.1.png)

<span data-ttu-id="06822-140">Należy także dodać przy użyciu instrukcji, dzięki czemu kod ma dostęp do metod rozszerzenia programem Dapper.</span><span class="sxs-lookup"><span data-stu-id="06822-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="06822-141">Korzystając z programem Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> dostępna w klasie <xref:System.Data.SqlClient> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06822-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="06822-142">Za pomocą metody QueryAsync i innych metod rozszerzających, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasy, można po prostu uruchomić zapytania w sposób prosty i wydajny.</span><span class="sxs-lookup"><span data-stu-id="06822-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="06822-143">Dynamiczne i modele widoków statyczne</span><span class="sxs-lookup"><span data-stu-id="06822-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="06822-144">Przy powrocie modele widoków po stronie serwera do aplikacji klienckich, można to porównać te modele widoków jako dto (obiektów transferu danych), które mogą być różnych jednostek domeny wewnętrznej modelu jednostki, ponieważ modele widoków przechowywania danych sposób aplikację kliencką wymagania związane z.</span><span class="sxs-lookup"><span data-stu-id="06822-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="06822-145">W związku z tym w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i narzędzia compose modele widoków dokładnie według jak aplikacja kliencka potrzebuje tych danych.</span><span class="sxs-lookup"><span data-stu-id="06822-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="06822-146">Te modele widoków lub dto może być jawnie zdefiniowane w (jako klasy symbol zastępczy danych) takich jak `OrderSummary` klasy wyświetlane w późniejszym fragment kodu, lub po prostu może zwrócić modele dynamicznych widoków lub dynamicznej dto, po prostu na podstawie atrybutów zwracane przez Twojego zapytania jako dynamiczny Typ.</span><span class="sxs-lookup"><span data-stu-id="06822-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="06822-147">ViewModel jako typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="06822-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="06822-148">Jak pokazano w poniższym kodzie `ViewModel` może bezpośrednio zostać zwrócony przez zapytania, zwracając tylko *dynamiczne* typ, który wewnętrznie opiera się na atrybutach zwróconych przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="06822-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="06822-149">Oznacza to, że podzbiór atrybutów, które mają zostać zwrócone opiera się na samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="06822-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="06822-150">W związku z tym, jeśli dodasz nową kolumnę do zapytania lub łączenia tych danych jest dynamicznie dodawane do zwracanego `ViewModel`.</span><span class="sxs-lookup"><span data-stu-id="06822-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="06822-151">Istotną kwestią jest to, że za pomocą dynamicznego typu zwracanego zbierania danych jest dynamicznie składany jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="06822-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="06822-152">**Zalety:** To podejście ogranicza potrzebę zmodyfikować statycznych klas ViewModel po zaktualizowaniu zdania SQL kwerendy, dość agile, podczas kodowania, prosty i szybki rozwój rozumieniu przyszłe zmiany, dzięki czemu takie podejście do projektowania.</span><span class="sxs-lookup"><span data-stu-id="06822-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="06822-153">**Wady:** W dłuższej perspektywie typów dynamicznych może niekorzystnie wpłynąć na przejrzystości i zgodności usługi przy użyciu aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="06822-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="06822-154">Ponadto oprogramowania oprogramowania pośredniczącego, takiego jak pakiet Swashbuckle nie może dostarczyć taki sam poziom dokumentacji na typy zwracane, jeśli przy użyciu typów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="06822-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="06822-155">ViewModel jako wstępnie zdefiniowany obiekt DTO klasy</span><span class="sxs-lookup"><span data-stu-id="06822-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="06822-156">**Specjaliści**: Wstępnie zdefiniowane ViewModel klas statycznych, takich jak "Umowy" oparte na jawne klas DTO, jest zdecydowanie lepszym miejscem dla publicznych interfejsów API, ale także na mikrousługi w długim okresie, nawet jeśli są używane tylko przez samą aplikację.</span><span class="sxs-lookup"><span data-stu-id="06822-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="06822-157">Jeśli chcesz określić typy odpowiedzi dla struktury Swagger, należy użyć jawnej klasy DTO jako typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="06822-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="06822-158">W związku z tym wstępnie zdefiniowanych klas DTO umożliwiają oferowanie bogatsze informacje z programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="06822-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="06822-159">Dokumentacja interfejsu API i zgodności, poprawiający podczas korzystania z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="06822-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="06822-160">**Cons**: Jak wspomniano wcześniej, podczas aktualizowania kodu, może potrwać kilka więcej kroki, aby zaktualizować obiekt DTO klasy.</span><span class="sxs-lookup"><span data-stu-id="06822-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="06822-161">*Porada oparte na naszych doświadczeniach*: W zapytaniach wdrożone na mikrousługach porządkowanie w ramach aplikacji eShopOnContainers Rozpoczęliśmy tworzenia za pomocą dynamicznego modele widoków, jak bardzo proste i zwinne na wczesnym etapie projektowania.</span><span class="sxs-lookup"><span data-stu-id="06822-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="06822-162">Jednak po rozwoju była charakteryzują się rozległymi, wybraliśmy Refaktoryzuj interfejsów API i używanie dto statyczne lub wstępnie zdefiniowane modele widoków, ponieważ jest bardziej zrozumiały dla konsumentów mikrousług wiedzieć jawnych typów DTO, używane jako "Umowy".</span><span class="sxs-lookup"><span data-stu-id="06822-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="06822-163">W poniższym przykładzie można zobaczyć, jak zapytanie zwraca dane za pomocą jawnego klasy ViewModel DTO: klasa OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="06822-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="06822-164">Opis typów odpowiedzi interfejsów API sieci Web</span><span class="sxs-lookup"><span data-stu-id="06822-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="06822-165">Deweloperom korzystanie z internetowych interfejsów API i mikrousług są najbardziej interesujących co to jest zwracany — w szczególności typy odpowiedzi i kody błędów usługi (Jeśli to nie standard).</span><span class="sxs-lookup"><span data-stu-id="06822-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="06822-166">Są one obsługiwane w adnotacjach komentarze i dane XML.</span><span class="sxs-lookup"><span data-stu-id="06822-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="06822-167">Bez prawidłowego dokumentacji w Interfejsie użytkownika programu Swagger, użytkownik nie ma wiedzy zwracane są typy lub HTTP, które mogą być zwracane kodów.</span><span class="sxs-lookup"><span data-stu-id="06822-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="06822-168">Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc pakiet Swashbuckle może generować bogatsze informacje o modelu zwracany interfejsu API i wartości, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="06822-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="06822-169">Jednak `ProducesResponseType` atrybutu nie można użyć dynamicznego, zgodnie z typem, ale wymaga przeprowadzenia używać jawnych typów, takie jak `OrderSummary` ViewModel DTO, pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="06822-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="06822-170">Jest to kolejny powód, dlaczego jawne typy zwracane są lepsze niż typy dynamiczne w perspektywie długoterminowej.</span><span class="sxs-lookup"><span data-stu-id="06822-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="06822-171">Korzystając z `ProducesResponseType` atrybut, można również określić, jak co to jest oczekiwany wynik w zakresie możliwe błędy HTTP/kodów, 200, 400, itp.</span><span class="sxs-lookup"><span data-stu-id="06822-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="06822-172">Na poniższej ilustracji widać, jak interfejs użytkownika struktury Swagger z informacjami wartość ResponseType.</span><span class="sxs-lookup"><span data-stu-id="06822-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Widok przeglądarki strony interfejs użytkownika struktury Swagger dla interfejsu API kolejności.](./media/image5.png)

<span data-ttu-id="06822-174">**Rysunek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="06822-174">**Figure 7-5**.</span></span> <span data-ttu-id="06822-175">Wyświetlanie typów odpowiedzi i możliwe kody stanu HTTP z internetowego interfejsu API interfejs użytkownika struktury swagger</span><span class="sxs-lookup"><span data-stu-id="06822-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="06822-176">Widać na ilustracji powyżej niektóre przykładowe wartości, na podstawie typów ViewModel oraz możliwe kody stanu HTTP, które mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="06822-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="06822-177">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="06822-177">Additional resources</span></span>

- <span data-ttu-id="06822-178">**Programem dapper** \\</span><span class="sxs-lookup"><span data-stu-id="06822-178">**Dapper** \\</span></span>
  [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

- <span data-ttu-id="06822-179">**Julie Lerman. Punkty danych — programem Dapper, platformy Entity Framework oraz hybrydowych aplikacji (artykuł MSDN mag)** \\</span><span class="sxs-lookup"><span data-stu-id="06822-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)** \\</span></span>
  [*https://msdn.microsoft.com/magazine/mt703432.aspx*](https://msdn.microsoft.com/magazine/mt703432.aspx)

- <span data-ttu-id="06822-180">**ASP.NET Core stron sieci Web interfejsu API pomocy korzystające z programu Swagger** \\</span><span class="sxs-lookup"><span data-stu-id="06822-180">**ASP.NET Core Web API Help Pages using Swagger** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio)

>[!div class="step-by-step"]
><span data-ttu-id="06822-181">[Poprzednie](eshoponcontainers-cqrs-ddd-microservice.md)
>[dalej](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="06822-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>