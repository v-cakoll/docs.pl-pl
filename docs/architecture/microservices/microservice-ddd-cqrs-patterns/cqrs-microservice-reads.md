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
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementowanie odczytów/zapytań w mikrousługach CQRS

W przypadku odczytów/zapytań zamawianie mikrousługi z aplikacji referencyjnej eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszaru transakcyjnego. Dokonano tego przede wszystkim dlatego, że wymagania dotyczące zapytań i transakcji są drastycznie różne. Zapisuje wykonać transakcje, które muszą być zgodne z logiką domeny. Zapytania, z drugiej strony, są idempotentne i mogą być oddzielone od reguł domeny.

Podejście jest proste, jak pokazano na rysunku 7-3. Interfejs interfejsu API jest implementowany przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takiej jak mikro obiekt owacyjna mapera (ORM) , taka jak Dapper, i zwracanie dynamicznych modeli viewmodele w zależności od potrzeb aplikacji interfejsu użytkownika.

![Diagram przedstawiający kwerendy wysokiego poziomu w uproszczonym CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Rysunek 7-3**. Najprostsze podejście do zapytań w mikrousługach CQRS

Najprostsze podejście po stronie zapytań w uproszczonym podejściu CQRS można zaimplementować, po prostu kwerendy bazy danych z Micro-ORM jak Dapper, zwracając dynamiczne Modele widoków. Definicje kwerendy kwerendy bazy danych i zwraca dynamiczny ViewModel zbudowany na bieżąco dla każdej kwerendy. Ponieważ zapytania są idempotentne, nie zmieni danych bez względu na to, ile razy uruchamiasz kwerendę. W związku z tym nie muszą być ograniczone przez dowolny wzorzec DDD używane w stronie transakcyjnej, takich jak agregaty i inne wzorce i dlatego kwerendy są oddzielone od obszaru transakcyjnego. Wystarczy zbadać bazy danych dla danych, które wymaga interfejsu użytkownika i zwraca dynamiczne ViewModel, który nie musi być statycznie zdefiniowane w dowolnym miejscu (bez klas dla ViewModels), z wyjątkiem instrukcji SQL siebie.

Ponieważ jest to proste podejście, kod wymagany po stronie kwerend (takich jak kod przy użyciu micro ORM jak [Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w ramach tego samego projektu interfejsu API sieci Web.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs) Rysunek 7-4 pokazuje to. Zapytania są zdefiniowane w projekcie mikrousług **Ordering.API** w ramach rozwiązania eShopOnContainers.

![Zrzut ekranu przedstawiający folder Kwerendy projektu Ordering.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Rysunek 7-4**. Zapytania w mikrousługach zamawiania w eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Używanie modeli viewmodele specjalnie dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny

Ponieważ kwerendy są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może być specjalnie dla klientów, na podstawie danych zwróconych przez kwerendy. Te modele lub obiekty transferu danych (DTO) są nazywane Modelami widoków.

Zwrócone dane (ViewModel) może być wynikiem łączenia danych z wielu jednostek lub tabel w bazie danych, lub nawet w wielu agregatów zdefiniowanych w modelu domeny dla obszaru transakcyjnego. W takim przypadku, ponieważ tworzysz kwerendy niezależne od modelu domeny, agreguje granice i ograniczenia są całkowicie ignorowane i możesz swobodnie wysyłać zapytania do dowolnej tabeli i kolumny, które mogą być potrzebne. Takie podejście zapewnia dużą elastyczność i produktywność dla deweloperów tworzenia lub aktualizowania zapytań.

ViewModels mogą być typy statyczne zdefiniowane w klasach. Lub mogą być tworzone dynamicznie na podstawie zapytań wykonywanych (jak jest zaimplementowana w mikrousługi zamawiania), który jest bardzo elastyczny dla deweloperów.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Użyj Dapper jako micro ORM do wykonywania zapytań

Można użyć dowolnego mikro ORM, Entity Framework Core, a nawet zwykły ADO.NET do wykonywania zapytań. W przykładowej aplikacji Dapper został wybrany dla zamawiania mikrousługi w eShopOnContainers jako dobry przykład popularnego micro ORM. Można uruchomić zwykłych zapytań SQL z doskonałą wydajnością, ponieważ jest to bardzo lekka struktura. Za pomocą Dapper, można napisać zapytanie SQL, które można uzyskać dostęp i dołączyć do wielu tabel.

Dapper jest projektem typu open source (oryginalnym stworzonym przez Sama Szafrana) i jest częścią bloków konstrukcyjnych używanych w [Stack Overflow](https://stackoverflow.com/). Aby korzystać z Dapper, wystarczy zainstalować go za pośrednictwem [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższym rysunku:

![Zrzut ekranu przedstawiający pakiet Dapper w widoku pakietów NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Należy również dodać using instrukcji, dzięki czemu kod ma dostęp do dapper metody rozszerzenia.

Korzystając z Dapper w kodzie, należy <xref:System.Data.SqlClient.SqlConnection> bezpośrednio użyć <xref:System.Data.SqlClient> klasy dostępne w obszarze nazw. Za pomocą QueryAsync metody i innych <xref:System.Data.SqlClient.SqlConnection> metod rozszerzenia, które rozszerzają klasy, można po prostu uruchomić kwerendy w sposób prosty i wydajny.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamiczne i statyczne modele widoków

Podczas zwracania ViewModels od strony serwera do aplikacji klienckich, można myśleć o tych ViewModels jako DTO (Obiekty transferu danych), które mogą być różne od wewnętrznych jednostek domeny modelu jednostki, ponieważ ViewModels przechowywania danych w sposób aplikacji klienckiej potrzeb. W związku z tym w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i redagować ViewModels dokładnie zgodnie z tym, jak aplikacja kliencka potrzebuje tych danych.

Te ViewModels lub DTO mogą być zdefiniowane jawnie `OrderSummary` (jako klasy posiadacza danych), jak klasa wyświetlana w nowszym fragmentie kodu lub można po prostu zwrócić dynamiczne modele viewmodels lub dynamiczne DTO po prostu na podstawie atrybutów zwracanych przez zapytania, jako typ dynamiczny.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako typ dynamiczny

Jak pokazano w poniższym `ViewModel` kodzie, a może być bezpośrednio zwracany przez kwerendy, po prostu zwracając typ *dynamiczny,* który wewnętrznie jest oparty na atrybuty zwracane przez kwerendę. Oznacza to, że podzbiór atrybutów do zwrotu opiera się na samej kwerendzie. W związku z tym po dodaniu nowej kolumny do kwerendy lub `ViewModel`sprzężenia, że dane są dynamicznie dodawane do zwracanego .

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

Ważnym punktem jest to, że przy użyciu typu dynamicznego, zwracana kolekcja danych jest dynamicznie montowane jako ViewModel.

**Plusy:** Takie podejście zmniejsza potrzebę modyfikowania statycznych viewmodel klas przy każdej aktualizacji zdanie SQL kwerendy, dzięki czemu to podejście projektu dość zwinny podczas kodowania, proste i szybkie ewoluować w odniesieniu do przyszłych zmian.

**Wady:** W dłuższej perspektywie typy dynamiczne mogą negatywnie wpłynąć na przejrzystość i zgodność usługi z aplikacjami klienckimi. Ponadto oprogramowanie pośredniczące, takie jak Swashbuckle, nie może zapewnić tego samego poziomu dokumentacji zwróconych typów, jeśli używasz typów dynamicznych.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako wstępnie zdefiniowane klasy DTO

**Plusy:** Posiadanie statycznych wstępnie zdefiniowanych klas ViewModel, takich jak "kontrakty" oparte na jawnych klasach DTO, jest zdecydowanie lepsze dla publicznych interfejsów API, ale także dla mikrousług długoterminowych, nawet jeśli są one używane tylko przez tę samą aplikację.

Jeśli chcesz określić typy odpowiedzi dla Swagger, należy użyć jawnych klas DTO jako typu zwracanego. W związku z tym wstępnie zdefiniowane klasy DTO umożliwiają oferowanie bogatszych informacji z Swagger. To poprawia dokumentację interfejsu API i zgodność podczas korzystania z interfejsu API.

**Minusy:** Jak wspomniano wcześniej, podczas aktualizowania kodu, wymaga kilku kroków, aby zaktualizować klasy DTO.

*Porada na podstawie naszego doświadczenia:* W zapytaniach zaimplementowanych w mikrousługach zamawiania w eShopOnContainers, zaczęliśmy się rozwijać przy użyciu dynamicznych ViewModels, ponieważ było to bardzo proste i zwinne na wczesnych etapach rozwoju. Ale po ustabilizowaniu rozwoju, zdecydowaliśmy się refaktoryzować interfejsów API i używać statycznych lub wstępnie zdefiniowanych obiektów DTO dla ViewModels, ponieważ jest jaśniejsze dla konsumentów mikrousług, aby wiedzieć jawne typy DTO, używane jako "kontrakty".

W poniższym przykładzie można zobaczyć, jak kwerenda zwraca dane przy użyciu jawnej klasy DTO ViewModel: OrderSummary klasy.

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

#### <a name="describe-response-types-of-web-apis"></a>Opis typów odpowiedzi interfejsów API sieci Web

Deweloperzy zużywający interfejsy API sieci web i mikrousług są najbardziej zaniepokojeni tym, co jest zwracane — w szczególności typy odpowiedzi i kody błędów (jeśli nie są standardowe). Są one obsługiwane w komentarzach XML i adnotacjach danych.

Bez odpowiedniej dokumentacji w interfejsie użytkownika Swagger konsument nie ma wiedzy o tym, jakie typy są zwracane lub jakie kody HTTP mogą być zwracane. Ten problem jest rozwiązany <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>przez dodanie , więc Swashbuckle może generować bogatsze informacje o modelu powrotu interfejsu API i wartości, jak pokazano w poniższym kodzie:

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

Jednak `ProducesResponseType` atrybut nie może używać dynamicznych jako typu, ale `OrderSummary` wymaga użycia jawnych typów, takich jak ViewModel DTO, pokazany w poniższym przykładzie:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Jest to kolejny powód, dla którego jawne zwracane typy są lepsze niż typy dynamiczne, w dłuższej perspektywie. Korzystając z `ProducesResponseType` atrybutu, można również określić, jaki jest oczekiwany wynik w odniesieniu do możliwych błędów HTTP / kody, takie jak 200, 400, itp.

Na poniższej ilustracji można zobaczyć, jak Swagger UI pokazuje informacje ResponseType.

![Zrzut ekranu przedstawiający stronę interfejsu użytkownika swagger dla interfejsu API zamawiania.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Rysunek 7-5**. Interfejs użytkownika swagger pokazujący typy odpowiedzi i możliwe kody stanu HTTP z interfejsu API sieci Web

Możesz zobaczyć na obrazku powyżej kilka przykładowych wartości na podstawie viewmodel typów plus możliwe kody stanu HTTP, które mogą być zwracane.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Punkty danych - Dapper, Entity Framework i Aplikacje hybrydowe (artykuł magazynu MSDN)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **ASP.NET core Web API Strony pomocy przy użyciu Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Poprzedni](eshoponcontainers-cqrs-ddd-microservice.md)
>[następny](ddd-oriented-microservice.md)
