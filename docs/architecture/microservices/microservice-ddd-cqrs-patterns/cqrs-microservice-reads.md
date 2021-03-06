---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z implementacją zapytania CQRS na mikrousłudze porządkowania w eShopOnContainers przy użyciu Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 71db95e6fc17475693183be9c6854884cd331ce1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614412"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementowanie operacji odczytu/zapytań w CQRS mikrousługi

W przypadku operacji odczytu/zapytań, mikrousługa porządkowania z aplikacji referencyjnej eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszaru transakcyjnego. Zostało to zrobione przede wszystkim dlatego, że wymagania dotyczące zapytań i transakcji są znacząco inne. Zapisuje transakcje wykonania, które muszą być zgodne z logiką domeny. Zapytania, z drugiej strony, są idempotentne i mogą być segregowane z reguł domeny.

Podejście jest proste, jak pokazano na rysunku 7-3. Interfejs API jest implementowany przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takiej jak relacyjne mapowanie mikroobiektu (ORM), takie jak Dapper, i zwracanie dynamicznego modele widoków w zależności od potrzeb aplikacji interfejsu użytkownika.

![Diagram przedstawiający zapytania wysokiego poziomu — po stronie uproszczonej CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Rysunek 7-3**. Najprostszym podejściem do wykonywania zapytań w mikrousłudze CQRS

Najprostszym podejściem dla zapytań w uproszczone podejście CQRS można zaimplementować, wykonując zapytania do bazy danych za pomocą mikroorm, takiego jak Dapper, zwracając dynamiczny modele widoków. Definicje zapytania zapytania do bazy danych i zwracają dynamiczny ViewModel zbudowany na bieżąco dla każdego zapytania. Ponieważ zapytania są idempotentne, nie zmieniają danych niezależnie od tego, ile razy zostało uruchomione zapytanie. W związku z tym nie trzeba ograniczać się przez żaden wzorzec DDD używany w stronie transakcyjnej, taki jak agregacje i inne wzorce, a także to, dlaczego zapytania są oddzielone od obszaru transakcyjnego. Kwerenda bazy danych wymaga danych, które są wymagane przez interfejs użytkownika i zwracają dynamiczny ViewModel, który nie musi być statycznie zdefiniowany w dowolnym miejscu (brak klas dla modele widoków), z wyjątkiem samych instrukcji SQL.

Ponieważ takie podejście jest proste, kod wymagany dla strony zapytania (na przykład kod korzystający z mikroorm like [Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w ramach tego samego projektu interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Przedstawiono to na rysunku 7-4. Zapytania są definiowane w projekcie **porządkowania. API** mikrousług w ramach rozwiązania eShopOnContainers.

![Zrzut ekranu przedstawiający folder zapytania projektu porządkowania. API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Rysunek 7-4**. Zapytania w mikrousłudze porządkowania w eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Używaj modele widoków określonych dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny

Ponieważ zapytania są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może być przeznaczony dla klientów na podstawie danych zwróconych przez zapytania. Te modele lub Transfer danych obiekty (DTO) są nazywane modele widoków.

Zwrócone dane (ViewModel) mogą wynikać z dołączania danych z wielu jednostek lub tabel w bazie danych, a nawet wielu agregacji zdefiniowanych w modelu domeny dla obszaru transakcyjnego. W tym przypadku, ponieważ tworzysz zapytania niezależnie od modelu domeny, granice zagregowane i ograniczenia są ignorowane i można wysyłać zapytania do dowolnej tabeli i kolumny, które mogą być potrzebne. Takie podejście zapewnia dużą elastyczność i produktywność dla deweloperów tworzących lub aktualizujących zapytania.

Modele widoków mogą być typami statycznymi zdefiniowanymi w klasach. Lub mogą być tworzone dynamicznie na podstawie zapytań wykonanych (zgodnie z implementacją mikrousługi porządkowania), które są bardzo elastyczne dla deweloperów.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Używanie Dapper jako mikroorm do wykonywania zapytań

Do wykonywania zapytań można użyć dowolnego mikroorm, Entity Framework Core lub nawet zwykłego ADO.NET. W przykładowej aplikacji Dapper został wybrany dla mikrousługi porządkowania w eShopOnContainers jako dobry przykład popularnego mikroorm. Może uruchamiać zwykłe zapytania SQL o doskonałej wydajności, ponieważ jest to platforma uproszczona. Za pomocą Dapper można napisać zapytanie SQL, które może uzyskać dostęp do wielu tabel i dołączyć do nich.

Dapper to projekt typu "open source" (oryginalny utworzony przez sam Saffron) i jest częścią bloków konstrukcyjnych używanych w [Stack Overflow](https://stackoverflow.com/). Aby korzystać z Dapper, wystarczy zainstalować go za pomocą [pakietu NuGet Dapper](https://www.nuget.org/packages/Dapper), jak pokazano na poniższym rysunku:

![Zrzut ekranu przedstawiający pakiet Dapper w widoku pakiety NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Należy również dodać `using` dyrektywę, aby kod miał dostęp do metod rozszerzenia Dapper.

Gdy używasz Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> klasy dostępnej w <xref:System.Data.SqlClient> przestrzeni nazw. Za pomocą metody QueryAsync i innych metod rozszerzających, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasę, można uruchamiać zapytania w sposób prosty i wydajny.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamiczny a statyczny modele widoków

Po powrocie modele widoków z serwera do aplikacji klienckich można myśleć o tych modele widoków jako DTO (Transfer danych obiektów), które mogą być różne dla wewnętrznych jednostek domeny modelu jednostki, ponieważ modele widoków przechowuje dane w sposób potrzeb aplikacji klienta. Z tego względu w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i precyzyjnie redagować modele widoków według sposobu, w jaki aplikacja kliencka wymaga tych danych.

Te modele widoków lub DTO mogą być zdefiniowane jawnie (jako klasy posiadaczy danych), takie jak `OrderSummary` Klasa pokazana w późniejszym fragmencie kodu. Lub można po prostu zwrócić dynamiczny modele widoków lub dynamiczny DTO na podstawie atrybutów zwracanych przez zapytania jako typ dynamiczny.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako typ dynamiczny

Jak pokazano w poniższym kodzie, `ViewModel` można zwrócić bezpośrednio przez zapytania, zwracając typ *dynamiczny* , który wewnętrznie jest oparty na atrybutach zwracanych przez zapytanie. Oznacza to, że podzbiór atrybutów do zwrócenia jest oparty na zapytaniu. W związku z tym, jeśli dodasz nową kolumnę do zapytania lub sprzężenia, dane te są dynamicznie dodawane do zwracanego `ViewModel` .

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

Ważnym punktem jest to, że za pomocą typu dynamicznego, zwrócona kolekcja danych jest dynamicznie zmontowany jako ViewModel.

**Specjaliści:** Takie podejście zmniejsza konieczność modyfikacji statycznych klas ViewModel za każdym razem, gdy aktualizujesz zdanie SQL zapytania, dzięki czemu ten podejście projektowe jest elastyczne podczas kodowania, bezpośrednie i szybkiej ewolucji w odniesieniu do przyszłych zmian.

**Wady:** W długim okresie typy dynamiczne mogą mieć negatywny wpływ na przejrzystość i zgodność usługi z aplikacjami klienckimi. Ponadto oprogramowanie pośredniczące, takie jak Swashbuckle, nie może zapewnić tego samego poziomu dokumentacji dla zwracanych typów, jeśli są używane typy dynamiczne.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako wstępnie zdefiniowane klasy DTO

**Specjaliści**: posiadanie statycznych, wstępnie zdefiniowanych klas ViewModel, takich jak "kontrakty", opartych na jawnych klasach DTO, jest w pełni lepszym rozwiązaniem dla publicznych interfejsów API, ale również dla mikrousług, nawet jeśli są one używane tylko przez tę samą aplikację.

Jeśli chcesz określić typy odpowiedzi dla struktury Swagger, musisz użyć jawnych klas DTO jako typu zwracanego. W związku z tym wstępnie zdefiniowane klasy DTO umożliwiają oferowanie bardziej szczegółowych informacji z struktury Swagger. Poprawia to dokumentację interfejsu API i zgodność przy korzystaniu z interfejsu API.

**Wady**: jak wspomniano wcześniej, podczas aktualizowania kodu należy wykonać kilka kroków, aby zaktualizować klasy DTO.

*Porada oparta na naszym doświadczeniu*: w zapytaniach zaimplementowanych w mikrousłudze porządkowania w programie eShopOnContainers rozpoczynamy Programowanie przy użyciu dynamicznych modele widoków, ponieważ było to proste i elastyczne na wczesnych etapach tworzenia. Jednak po ustabilizowaniu rozwoju wybieramy do refaktoryzacji interfejsy API i używają statycznego lub wstępnie zdefiniowanego DTO dla modele widoków, ponieważ jest to wyraźniejsze dla konsumentów mikrousług, aby znać jawne typy DTO, używane jako "kontrakty".

W poniższym przykładzie można zobaczyć, jak zapytanie zwraca dane przy użyciu jawnej klasy ViewModel DTO: klasy OrderSummary.

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

#### <a name="describe-response-types-of-web-apis"></a>Opisywanie typów odpowiedzi interfejsów API sieci Web

Deweloperzy korzystający z interfejsów API sieci Web i mikrousług są najbardziej zainteresowani tym, co jest zwracane — w szczególności typy odpowiedzi i kody błędów (jeśli nie są standardem). Typy odpowiedzi są obsługiwane w komentarzach XML i adnotacjach danych.

Bez odpowiedniej dokumentacji w interfejsie użytkownika programu Swagger klient nie ma wiedzy na temat typów zwracanych lub kodów HTTP, które mogą być zwracane. Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> , więc Swashbuckle może generować bogatsze informacje o modelu i wartościach zwracanych przez interfejs API, jak pokazano w poniższym kodzie:

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

Jednak `ProducesResponseType` atrybut nie może używać elementu dynamicznego jako typu, ale wymaga użycia jawnych typów, takich jak `OrderSummary` ViewModel DTO, pokazany w poniższym przykładzie:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Jest to kolejny powód, dla którego jawne zwracane typy są lepsze niż typy dynamiczne w długim okresie. Przy użyciu `ProducesResponseType` atrybutu można także określić oczekiwany wynik w odniesieniu do możliwych błędów/kodów http, takich jak 200, 400 itd.

Na poniższej ilustracji widać, jak interfejs użytkownika struktury Swagger wyświetla informacje o odpowiedzi.

![Zrzut ekranu przedstawiający stronę interfejsu użytkownika programu Swagger dla interfejsu API porządkowania.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Rysunek 7-5**. Interfejs użytkownika struktury Swagger pokazujący typy odpowiedzi i możliwe kody stanu HTTP z internetowego interfejsu API

Obraz pokazuje kilka przykładowych wartości na podstawie typów ViewModel i możliwych kodów stanu HTTP, które mogą być zwracane.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Punkty danych — Dapper, Entity Framework i aplikacje hybrydowe (artykuł z magazynu MSDN)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **ASP.NET Core stronach pomocy interfejsu API sieci Web przy użyciu programu Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Poprzedni](eshoponcontainers-cqrs-ddd-microservice.md) 
> [Dalej](ddd-oriented-microservice.md)
