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
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Implementowanie odczyty/kwerendy w mikrousługi CQRS

Odczyty/zapytań porządkowania mikrousługi z aplikacji odwołanie eShopOnContainers implementuje zapytania niezależnie od DDD modelu i obszar transakcyjnych. Wykonano głównie, ponieważ znacząco różnią wymagań dla zapytań i transakcji. Zapisy wykonania transakcji, które muszą być zgodne z logiką domeny. Z drugiej strony, zapytania, są idempotentności i być rozdzielone od zasad domeny.

Podejście jest proste, jak pokazano na rysunku 9-3. Interfejs API zaimplementowano przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takich jak micro relacyjne mapowania ORM (Object) jak Dapper i zwracanie dynamiczne ViewModels w zależności od potrzeb aplikacji interfejsu użytkownika.

![](./media/image3.png)

**Rysunek 9-3**. Najprostsza metoda zapytań w mikrousługi CQRS

Jest to najprostsza metoda możliwe w dla zapytań. Definicje kwerendy w bazie danych i zwracać dynamiczne ViewModel, oparty na bieżąco dla każdego zapytania. Ponieważ zapytania są idempotentności, zmienią danych niezależnie od tego, ile razy wykonywania zapytania. W związku z tym nie trzeba być ograniczone przez dowolnego wzorzec DDD używany po stronie transakcyjnych, takie jak wartości zagregowanych i innych wzorcach i dlatego zapytania są oddzielone od obszaru transakcyjnych. Po prostu zapytania do bazy danych, która wymaga interfejsu użytkownika i zwracać ViewModel dynamiczne, które muszą być statycznie zdefiniowany dowolnego miejsca (nie klasy dla ViewModels) z wyjątkiem w instrukcji SQL, samodzielnie.

Ponieważ jest to prosty podejście, kod wymagany dla strony zapytania (takich jak kodu za pomocą micro, takich jak ORM [Dapper](https://github.com/StackExchange/Dapper)) może być zaimplementowany [w tym samym projekcie interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Na rysunku 9-4 przedstawiono to. Zapytania są definiowane w **Ordering.API** mikrousługi projektu w ramach rozwiązania eShopOnContainers.

![](./media/image4.png)

**Rysunek 9-4**. Zapytania w mikrousługi porządkowanie w eShopOnContainers

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Przy użyciu ViewModels celowo dla aplikacji klienta, niezależnie od ograniczeń modelu domeny

Ponieważ zapytania są wykonywane do uzyskiwania danych wymaganych przez aplikacje klienckie, zwrócony typ można w szczególności wprowadzone dla klientów, na podstawie danych zwróconych przez zapytania. Te modele lub obiekty Transfer danych (DTOs), są nazywane ViewModels.

Zwrócone dane (ViewModel) może być wynikiem sprzężenia danych z wielu obiektów lub tabele w bazie danych, lub nawet Agreguje wiele zdefiniowanych w modelu domeny dla transakcyjnego obszaru. W takim przypadku ponieważ tworzenia kwerend niezależnie od modelu domeny, agregacje granic i ograniczenia całkowicie są ignorowane, a możesz go dowolnie zapytania żadnych tabel i kolumn, który może być konieczne. Ta metoda zapewnia dużą elastyczność i wydajność dla deweloperów, tworzenie lub aktualizowanie zapytań.

ViewModels może być statyczne typy zdefiniowane w klasach. Lub też można tworzyć dynamicznie na podstawie kwerend wykonywana (jak jest implementowane w porządkowania mikrousługi), który jest bardzo elastyczne dla deweloperów.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Przy użyciu Dapper jako micro ORM do wykonywania zapytań

Podczas wykonywania zapytań, można użyć dowolnego micro ORM, Entity Framework Core lub nawet zwykły ADO.NET. W przykładowej aplikacji Dapper został wybrany do porządkowania mikrousługi w eShopOnContainers jako przykład popularnych ORM micro. Można go uruchomić zwykły kwerend SQL o bardzo dużej wydajności, ponieważ jest bardzo małe framework. Dapper można napisać zapytanie SQL, które mogą uzyskać dostęp i dołączyć wiele tabel.

Dapper to projekt typu open source (utworzony przez Sam szafran oryginału) i jest częścią bloki konstrukcyjne, używane w [przepełnienie stosu](https://stackoverflow.com/). Aby użyć Dapper, wystarczy zainstalować go za pomocą [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji:

![](./media/image4.1.png)

Należy również dodać za pomocą instrukcji tak kod ma dostęp do metody Dapper rozszerzenia.

W przypadku użycia Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> dostępne w klasie <xref:System.Data.SqlClient> przestrzeni nazw. Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasy, można po prostu wykonać zapytania w sposób prosty i wydajność.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamiczne i ViewModels statyczne

W przypadku powrotu ViewModels z po stronie serwera do klienta aplikacji, należy zwrócić uwagę tych ViewModels jako DTOs, które mogą być różne do jednostek domeny wewnętrznej modelu jednostki, ponieważ wymaga aplikacji klienckiej sposobu wstrzymywania ViewModels danych. W związku z tym w wielu przypadkach możesz agregować dane pochodzące z wielu domen, jednostek i tworzą ViewModels dokładnie według jak aplikacja, klient musi danych.

Te ViewModels lub DTOs można definiować jawnie (jako klasy symbol zastępczy danych) jak [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) klasy w późniejszym fragment kodu, lub po prostu może zwrócić ViewModels dynamicznych lub dynamiczne DTOs po prostu na podstawie atrybutów zwracane przez Twojego zapytania jako `dynamic` typu.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako typu dynamicznego

Jak pokazano w poniższym kodzie, ViewModel może być bezpośrednio zwracany przez zapytania zwracając typu dynamicznego wewnętrznie na podstawie atrybutów zwróconych przez kwerendę. Oznacza to, że podzbiór atrybutów, które mają być zwracane jest oparty na samą kwerendę. W związku z tym po dodaniu nowej kolumny do zapytania, lub Dołącz do tych danych jest dynamicznie dodawane do zwrócony ViewModel.

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

Istotne jest, czy przy użyciu typu dynamicznego, zwracane zbierania danych są dynamicznie montowane jako ViewModel.

*Specjaliści:* takie podejście ogranicza potrzebę modyfikowanie klas statycznych ViewModel po zaktualizowaniu zdanie SQL kwerendy, co ta podejście do projektowania bardzo elastyczne podczas kodowania, proste i szybkie podlegać ewolucji w odniesieniu do przyszłych zmian.

*Cons:* w długim okresie, typy dynamiczne można mają negatywny wpływ na czytelność i mieć wpływ na zgodność usługi z aplikacji klienta. Ponadto oprogramowanie pośredniczące oprogramowanie, takie jak Swagger nie może dostarczyć poziomu dokumentacji na typy zwracane Jeśli za pomocą zestawów dynamicznych.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako wstępnie zdefiniowanych klas DTO

*Specjaliści:* o wstępnie zdefiniowanych ViewModel klasy statyczne, takie jak "kontraktów" oparte na jawne klasy DTO, zdecydowanie lepiej jest dla publicznych interfejsów API, ale także na mikrousług długoterminowej, nawet wtedy, gdy są one używane tylko w tej samej aplikacji.

Jeśli chcesz określić typy odpowiedzi dla struktury swagger, musisz użyć jawnego klasy DTO jako typ zwracany. W związku z tym wstępnie zdefiniowanych klas DTO umożliwiają oferują bogatszy informacji z programu Swagger. Zwiększająca dokumentacji interfejsu API i zgodności podczas używania interfejsu API.

*Cons:* jak wspomniano wcześniej, jeśli zaktualizowanie kodu, zajmuje kilka więcej kroki, aby zaktualizować klasy DTO.

*Porada opartej na naszym doświadczeniu:* w zapytaniach wdrożone na mikrousługi porządkowanie w eShopOnContainers, firma Microsoft Rozpoczęto tworzenie za pomocą dynamicznej ViewModels jak bardzo proste i elastyczne na wczesnym etapie programowania. Jednak po rozwoju został stabilizowany, wybraliśmy Refaktoryzuj interfejsów API i używać DTOs statyczne lub wstępnie zdefiniowane dla ViewModels, ponieważ jest on jaśniejszy dla konsumentów mikrousługi należy wiedzieć jawnie DTO typów, używany jako "kontrakty".

W poniższym przykładzie widać, jak zapytanie zwraca dane za pomocą jawnej klasy ViewModel DTO: klasa OrderSummary.

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

#### <a name="describing-response-types-of-web-apis"></a>Zawierająca opis odpowiedzi typów interfejsów API sieci Web

Deweloperom korzystanie z interfejsów API sieci web i mikrousług są najbardziej związane z wartością zwróconą — w szczególności typy odpowiedzi i kody błędów (o ile nie standard). Te są obsługiwane w adnotacjach komentarzy i danych XML.

Bez prawidłowego dokumentacji w Interfejsie użytkownika programu Swagger, użytkownik nie ma wiedzy zwracanych typów lub jakie HTTP może być zwracany kodów. Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc Swagger mogą generować bardziej rozbudowane informacje o modelu zwracany interfejsu API i wartości, jak pokazano w poniższym kodzie:

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

Jednak `ProducesResponseType` atrybutu nie można używać dynamicznej, zgodnie z typem, ponieważ wymaga tak samo, jak korzystać z typów jawnych, `OrderSummary` DTO ViewModel, pokazano w poniższym przykładzie:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Jest to kolejny powód, dlaczego jawne zwracane typy są lepszym rozwiązaniem niż typów dynamicznych w perspektywie długoterminowej.
Korzystając z `ProducesResponseType` atrybutu, można również określić, co to jest oczekiwany wynik w zakresie możliwości HTTP/kody błędów, takich jak 200,400, itp.

Na poniższej ilustracji widać, jak przedstawiono informacje o wartość ResponseType przez interfejs użytkownika programu Swagger.

![](./media/image5.png)

**Rysunek 9-5**. Wyświetlanie typów odpowiedzi i możliwe kody stanu HTTP składnika Web API interfejs użytkownika struktury swagger

Widać na ilustracji powyżej niektóre przykładowe wartości oparte na typy ViewModel plus możliwe kody stanu HTTP, które mogą być zwrócone.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Punkty danych - Dapper, Entity Framework i aplikacji hybrydowych (artykuł MSDN Mag.)**

    *https://msdn.microsoft.com/Magazine/mt703432.aspx*

-   **Strony pomocy dla interfejsu Web API platformy ASP.NET Core korzystające z programu Swagger**

    *https://docs.microsoft.com/ASPNET/Core/Tutorials/Web-API-Help-Pages-Using-swagger?Tabs=Visual-Studio*

>[!div class="step-by-step"]
[Poprzednie] (eshoponcontainers-cqrs-ddd-microservice.md) [dalej] (ddd ukierunkowane microservice.md)
